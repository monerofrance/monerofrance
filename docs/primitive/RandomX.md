# **RandomX : l'Algorithme de Preuve de Travail de Monero**

## **Introduction**

RandomX est un algorithme de preuve de travail (PoW) innovant utilisé par Monero pour sécuriser son réseau et valider les transactions. Conçu pour être résistant aux ASIC (circuits intégrés spécifiques à une application) et optimisé pour les CPU généralistes, RandomX favorise la décentralisation du minage. Dans cette présentation, nous allons explorer les fondements mathématiques et les techniques cryptographiques qui sous-tendent RandomX.

## **1. Fonctions de Hachage Cryptographique**

### **Blake2b**

Blake2b est une fonction de hachage cryptographique utilisée dans RandomX pour générer des valeurs de hachage de 256 ou 512 bits. Elle est rapide et sécurisée, et sert de base pour plusieurs générateurs de nombres pseudo-aléatoires.

- **Définition** : Blake2b est définie par une série de transformations sur un état interne de 64 octets.
- **Utilisation** : Elle est utilisée pour initialiser des générateurs de nombres pseudo-aléatoires et pour créer des empreintes digitales sécurisées.

### **AES (Advanced Encryption Standard)**

L'AES est un standard de chiffrement symétrique utilisé dans RandomX pour générer des séquences de nombres pseudo-aléatoires.

- **AES Encryption Round** : Applique les transformations ShiftRows, SubBytes, et MixColumns suivies d'un XOR avec la clé de tour.
- **AES Decryption Round** : Applique les transformations inverses ShiftRows, SubBytes, et MixColumns suivies d'un XOR avec la clé de tour.

## **2. Générateurs de Nombres Pseudo-Aléatoires**

### **AesGenerator1R et AesGenerator4R**

Ces générateurs utilisent l'AES pour produire des séquences de nombres pseudo-aléatoires.

- **AesGenerator1R** : Utilise une seule ronde de chiffrement AES.
  - **État interne** : 64 octets divisés en quatre colonnes de 16 octets chacune.
  - **Clés de tour** : Utilise des clés spécifiques pour chaque colonne.

- **AesGenerator4R** : Utilise quatre rondes de chiffrement AES pour une sécurité accrue.
  - **Clés de tour** : Différentes pour chaque colonne et chaque ronde.

### **BlakeGenerator**

Basé sur Blake2b, ce générateur produit des nombres pseudo-aléatoires en réinitialisant périodiquement son état interne.

- **État interne** : 64 octets.
- **Réinitialisation** : Utilise Blake2b pour réinitialiser l'état interne.

## **3. Fonction de Diffusion : SuperscalarHash**

SuperscalarHash est une fonction de diffusion personnalisée conçue pour être intensive en calcul et en mémoire.

- **Entrée/Sortie** : Transforme une entrée de 64 octets en une sortie de 64 octets.
- **Instructions** : Utilise une séquence aléatoire d'instructions optimisées pour les CPU superscalaires.
- **Exemple d'instruction** :
  - **ISUB_R** : Soustraction entière de 64 bits.
  - **IXOR_R** : XOR de 64 bits.
  - **IMUL_R** : Multiplication entière de 64 bits.

## **4. Opérations Arithmétiques et Logiques**

RandomX utilise une variété d'opérations arithmétiques et logiques pour manipuler les données.

- **Additions, Soustractions, Multiplications** : Effectuées sur des entiers de 64 bits.
- **Opérations Bit à Bit** : XOR, AND, OR, décalages (shifts).
- **Opérations sur les Nombres à Virgule Flottante** : Conformes à la norme IEEE-754.

## **5. Algorithmes de Mélange de Mémoire**

### **Argon2d**

Argon2d est un algorithme de dérivation de clé résistant aux attaques par compromis temps-mémoire.

- **Utilisation** : Initialise la mémoire cache dans RandomX.
- **Paramètres** :
  - **Parallelisme** : Nombre de lanes parallèles.
  - **Mémoire** : Taille de la mémoire utilisée.
  - **Iterations** : Nombre d'itérations.

## **6. Optimisation pour les CPU Superscalaires**

RandomX est conçu pour maximiser l'utilisation des CPU superscalaires, qui peuvent exécuter plusieurs instructions en parallèle.

- **Modélisation du CPU de Référence** : Simule un CPU avec trois ports d'exécution (P0, P1, P5).
- **Génération de Programmes** : Optimisée pour maximiser l'utilisation de ces ports.

## **Conclusion**

RandomX intègre des techniques cryptographiques avancées et des optimisations mathématiques pour assurer la sécurité et l'efficacité du minage sur Monero. En favorisant les CPU généralistes et en résistant aux ASIC, RandomX contribue à la décentralisation du réseau Monero, rendant le minage plus accessible et équitable.

---

Cette présentation couvre les aspects mathématiques et techniques de RandomX, offrant une compréhension approfondie de son fonctionnement et de son importance dans l'écosystème Monero.

### Présentation des Adresses Furtives (Stealth Addresses) de Monero

Les adresses furtives (stealth addresses) sont une composante essentielle du protocole Monero, conçue pour renforcer la confidentialité des transactions. Elles permettent aux expéditeurs de créer des adresses uniques et non traçables pour les destinataires, garantissant ainsi que les transactions restent privées et impossibles à relier entre elles. Voici une présentation détaillée de ce protocole :

#### Qu'est-ce que les Adresses Furtives ?

Les adresses furtives sont une technique permettant à un expéditeur de transformer l'adresse publique d'un destinataire en une adresse unique à usage unique. Ces adresses uniques possèdent les propriétés suivantes :

1. **Non Liable Publiquement à l'Adresse Originale** : Personne ne peut relier l'adresse unique à l'adresse publique du destinataire.
2. **Non Liable Publiquement aux Autres Adresses Uniques** : Chaque adresse unique est distincte et ne peut être liée à d'autres adresses uniques.
3. **Le Destinataire Peut Relier Tous Ses Paiements** : Seul le destinataire peut relier tous ses paiements entre eux.
4. **Le Destinataire Peut Dériver la Clé Secrète** : Seul le destinataire peut dériver la clé secrète associée à l'adresse unique.

#### Fonctionnement des Adresses Furtives

Les adresses furtives dans Monero sont mises en œuvre à l'aide d'un système à double clé, impliquant une paire de clés de dépense et de visualisation. Voici une explication étape par étape de la création et de l'utilisation des adresses furtives :

1. **Échange de Clés Diffie-Hellman sur Courbes Elliptiques (ECDH)** : L'ECDH permet à deux parties de générer un secret partagé sur une connexion non sécurisée. Dans Monero, Alice (l'expéditeur) et Bob (le destinataire) utilisent l'ECDH pour créer un secret partagé.

2. **Paires de Clés** :
   - Alice possède une clé de dépense privée (z) et une clé de visualisation privée (y).
   - Bob possède une adresse publique composée d'une clé de visualisation publique (A) et d'une clé de dépense publique (B).

3. **Création d'une Adresse Furtive** :
   - Alice choisit un scalaire aléatoire (r) et calcule R = rG, où G est le point de base standard Ed25519.
   - Alice effectue un ECDH avec son scalaire aléatoire (r) et la clé de visualisation publique de Bob (A) pour obtenir un point D.
   - Alice utilise D pour générer un nouveau scalaire (f) en hachant D (f = Hs(D)).
   - Alice calcule F = fG puis P = F + B, où P est l'adresse furtive.

4. **Perspective de Bob** :
   - Bob reçoit la transaction et récupère R.
   - Bob calcule D' = aR, où a est sa clé de visualisation privée.
   - Bob calcule f' = Hs(D') et F' = f'G.
   - Bob calcule P' = F' + B et vérifie si P' correspond à P de la transaction. Si c'est le cas, Bob sait qu'il a reçu un paiement.

#### Étapes Supplémentaires pour Bob

Une fois que Bob a déterminé qu'une sortie lui appartient, il peut effectuer des étapes supplémentaires :

1. **Vérifier si la Sortie est Dépenser** : Bob calcule l'image clé (I = xHp(P)) et interroge la blockchain pour voir si elle est marquée comme dépensée.
2. **Dépenser la Sortie** : Bob doit signer une nouvelle transaction avec la clé secrète unique (x) pour dépenser la sortie.


Les adresses furtives sont une fonctionnalité puissante de confidentialité dans Monero. Elles garantissent que les transactions restent non traçables et impossibles à relier, offrant ainsi un haut niveau de confidentialité pour les expéditeurs et les destinataires. L'utilisation de l'ECDH et des systèmes à double clé rend les adresses furtives robustes et sécurisées pour maintenir la confidentialité des transactions dans la vie de tous les jours.

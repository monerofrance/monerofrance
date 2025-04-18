# Courbe Elliptique Edwards25519

## Remarque

L'auteur n'est en aucun cas un cryptographe. Soyez sceptique quant à l'exactitude des informations.

## Note

Cet article traite uniquement de la courbe sous-jacente. La dérivation des clés publiques et l'algorithme de signature seront abordés séparément.

Monero utilise la courbe elliptique Edwards25519 comme base pour la génération de ses paires de clés.

La courbe provient du schéma de signature Ed25519. Bien que Monero utilise la courbe telle quelle, il ne suit pas exactement le reste du schéma Ed25519.

La courbe Edwards25519 est birationnellement équivalente à la courbe Curve25519.

## Définition

Voici la définition standard de la courbe Edwards25519. Il n'y a rien de spécifique à Monero ici, à l'exception de la convention de nommage. Cette convention provient du livre blanc CryptoNote et est largement utilisée dans la littérature Monero.

### Équation de la Courbe

\[ -x^2 + y^2 = 1 - \left(\frac{121665}{121666}\right) \cdot x^2 \cdot y^2 \]

**Remarques :**

- La courbe est en deux dimensions (rien de compliqué, comme toutes les courbes étudiées au lycée).
- La courbe est symétrique par rapport à l'axe des y en raison du terme \( y^2 \) dans l'équation (ce n'est pas un polynôme).

### Point de Base : G

Le point de base est un point spécifique sur la courbe. Il sert de référence pour les calculs ultérieurs. C'est un choix arbitraire des auteurs de la courbe, simplement pour standardiser le schéma.

**Note :** Il suffit de spécifier la valeur de \( y \) et le signe de \( x \). En effet, la valeur spécifique de \( x \) peut être calculée à partir de l'équation de la courbe.

\[ G = (x, \frac{4}{5}) \] (en prenant le point avec \( x \) positif)

**Représentation hexadécimale du point de base :**

```
5866666666666666666666666666666666666666666666666666666666666666
```

### Ordre Premier du Point de Base : \( l \)

En termes simples, la "toile" sur laquelle la courbe est dessinée est supposée avoir une "résolution" finie, donc les coordonnées des points doivent "s'enrouler" à un certain moment. Cela est réalisé par un modulo de la valeur \( l \) (L minuscule). En d'autres termes, \( l \) définit le scalaire maximal que nous pouvons utiliser.

\[ l = 2^{252} + 27742317777372353535851937790883648493 \]

\[ \Rightarrow 7237005577332262213973186563042994240857116359379907606001950938285454250989 \]

\( l \) est un nombre premier spécifié par les auteurs de la courbe.

En pratique, cela correspond à la force de la clé privée.

### Nombre Total de Points sur la Courbe

Le nombre total de points sur la courbe est également un nombre premier :

\[ q = 2^{255} - 19 \]

En pratique, tous les points ne sont pas "utiles", donc la force de la clé privée est limitée à \( l \) décrit ci-dessus.

## Implémentation

Monero utilise (apparemment modifiée) l'implémentation Ref10 de Daniel J. Bernstein.

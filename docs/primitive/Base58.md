# Base58

Base58 est un schéma de codage binaire-texte. Il est similaire à Base64 mais a été modifié pour éviter les caractères non alphanumériques et les lettres qui pourraient sembler ambiguës lorsqu'elles sont imprimées. Les caractères exclus par rapport à Base64 sont : `I`, `O`, `l`, `0`, `+`, et `/`.

Base58 ne spécifie pas strictement le format. Cela entraîne l'incompatibilité de certaines implémentations avec d'autres, par exemple en ce qui concerne l'ordre des lettres de l'alphabet.

Pour plus de détails, consultez [Wikipedia](https://en.wikipedia.org/wiki/Base58).

## Base58 dans Monero

Monero utilise sa propre variante de Base58.

Dans Monero, le codage Base58 est effectué en blocs de 8 octets, à l'exception du dernier bloc qui contient les octets restants (8 ou moins).

Un bloc de 8 octets se convertit en 11 caractères Base58 ou moins. Si le bloc se convertit en moins de 11 caractères, la sortie est complétée avec des "1" (qui représentent 0 en Base58). Le bloc final est également complété pour atteindre la taille maximale possible pour ce nombre d'octets codés en Base58.

L'avantage de l'implémentation de Monero est que la sortie est de taille fixe, ce qui n'est pas le cas avec Base58 standard. L'inconvénient est que les bibliothèques par défaut ne fonctionneront pas.

Pour plus de détails, consultez l'implémentation de référence en C++ de Base58 et l'implémentation non officielle en Python de Base58.

# Fonction de Hachage Keccak-256

## Utilisation par Monero

Monero utilise Keccak comme fonction de hachage. Dans la plupart des contextes, Keccak-256 est spécifiquement employé, fournissant des hachages de 32 octets.

Keccak est la fonction de hachage de pointe, conçue par des cryptographes non affiliés à la NSA. Keccak a remporté la compétition NIST pour devenir le SHA-3 officiel.

## Cas d'Utilisation

Monero n'utilise pas Keccak pour la Preuve de Travail (Proof-of-Work). Au lieu de cela, Keccak est utilisé pour :

- Générateur de nombres aléatoires
- Hachage de blocs
- Hachage de transactions
- Image de clé privée pour les adresses furtives (pour la protection contre les doubles dépenses)
- Somme de contrôle des adresses publiques
- RingCT
- Multisignature
- Bulletproofs

... et probablement quelques autres choses.

## Keccak-256 vs SHA3-256

SHA3-256 est essentiellement Keccak-256, à l'exception du fait que le NIST a modifié le remplissage (padding). Pour cette raison, le Keccak-256 original produit une valeur de hachage différente de celle du SHA3-256 du NIST.

Monero utilise le Keccak-256 original. La norme NIST n'a été publiée qu'en août 2015, alors que Monero a été lancé le 18 avril 2014.

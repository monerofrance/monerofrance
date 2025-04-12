Sur les réseaux pair-a-pair, **il est possible de lier des transactions a des adresses IP** en faisant une écoute passive du réseau avec beaucoup de noeuds. 

Pour protéger ses utilisateurs, **la communautée Monero a implémenté la solution Dandelion++**. une version améliorée du protocole Dandelion original proposé pour Bitcoin.

Ce protocole comporte deux phases :
- La phase "stem" (tige)
- La phase "fluff" (duvet), représentant ensemble la forme d'un pissenlit.

#### La phase "stem":
Toutes les quelques minutes, le nœud émetteur choisit aléatoirement deux pairs parmi tous les nœuds auxquels il est connecté. Lorsque le nœud émetteur envoie une transaction, soit pour lui-même soit en transférant une transaction d'un autre nœud en phase "stem", il choisit aléatoirement l'un de ces deux pairs et lui envoie la transaction.

#### La phase "fluff":
Commence lorsqu'un nœud reçoit une transaction et la diffuse à toutes ses connexions sortantes, plutôt qu'à un seul pair choisi aléatoirement, permettant ainsi une véritable propagation de la transaction. Toutes les quelques minutes, un nœud se définit aléatoirement comme propagateur via "stem" ou "fluff". Une phase "stem" peut être assez longue si chaque nœud connecté se définit comme nœud "stem", mais une fois que la transaction atteint la phase "fluff", elle y reste.

Cela signifie qu'**un attaquant ne peut plus simplement écouter la direction d'une transaction**. Avant que la transaction soit propagée à tout le monde, elle a subi la phase "stem", et le nœud d'origine de la phase "fluff" n'est pas le nœud d'origine de la transaction. Il est inconnu combien de sauts le long de la "stem" la transaction a effectués.

Bien sûr, combiner les solutions comme des reseaux alternatifs (VPN/Tor/I2P) avec Dandelion++ offre des garanties de confidentialité encore plus fortes.

**Attention**: Il convient également de noter que **Dandelion++ protège pas le réseau contre une surveillance réalisée par les FAI**, mais cela dépasse le cadre de la presentation de dandelion++.

**Dandelion++ est activé par défaut sur tous les noœuds monero**, il est conseillé d'en avoir un pour ne pas dépendre d'une partie tierce qui pourrait vous surveiller.

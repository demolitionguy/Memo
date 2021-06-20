# Expressions régulières

\* n'importe quel nombre de fois

\+ présent au moins 1 fois

[ ... ] n'importe quel caractère de la liste

[^...] caractère non présent dans la liste

[ ...-...] plage. Exemple: [a-z4-8] lettre ou chiffre entre 4 et 8

(...) groupe répété ou récupéré d'un autre emplacement

\w mot

\d caractère numérique (soit [0-9])

\s space (soit [\t\r\n\f])

\D tout ce qui n'est pas nombre.

Majuscule: inverse quand c'est un ensemble

^ début d'une ligne

$ fin d'une ligne

\< début d'un mot

\> fin d'un mot

\0 \1 \2 ... \9 désigne le résultat d'un groupe du motif de recherche

\0 motif lui-même entier

() groupe pour stocker en mémoire

| ou

.

\*

\+ : supérieur ou égal à 1

? : 0 ou 1

a{2} : deux fois a -> aa

a{2,4} : aa ou aaa ou aaaa

a(bc)      \1 -> premier groupe -> bc

(a(bc))(de)      \1 -> abc  \2 -> bc \3 -> de

^(.) : premier caractère en début de ligne

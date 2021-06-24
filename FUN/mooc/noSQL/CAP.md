 ## [ACIDvsBASE](https://openclassrooms.com/en/courses/4462426-maitrisez-les-bases-de-donnees-nosql/4462471-maitrisez-le-theoreme-de-cap)
 
 Le NoSQL est très tentant lorsque l'on voit toutes les possibilités qu'il peut offrir. Mais il ne faut pas négliger certains fondamentaux qui rendent les SGBDR incontournables.

      Cela se résume dans une combinaison qu'il ne faut pas négliger :
      Faire des jointures entre les tables de la base de données
      Faire des requêtes complexes avec un langage de haut niveau sans se préoccuper des couches basses
      Gérer l'intégrité des données de manière infaillible
      
Atomicité : Une transaction s’effectue entièrement ou pas du tout

Cohérence : Le contenu d’une base doit être cohérent au début et à la fin d’une transaction

Isolation : Les modifications d’une transaction ne sont visibles/modifiables que quand celle-ci a été validée

Durabilité : Une fois la transaction validée, l’état de la base est permanent (non affecté par les pannes ou autre)

- [ACIDvsBASE](https://openclassrooms.com/en/courses/4462426-maitrisez-les-bases-de-donnees-nosql/4462471-maitrisez-le-theoreme-de-cap)

Basically Available : quelle que soit la charge de la base de données (données/requêtes), le système garantie un taux de disponibilité de la donnée

Soft-state : La base peut changer lors des mises à jour ou lors d'ajout/suppression de serveurs. La base NoSQL n'a pas à être cohérente à tout instant

Eventually consistent : À terme, la base atteindra un état cohérent

![DB CAP analysis](https://github.com/lindangulopez/l-internet-des-objets/blob/main/FUN/mooc/noSQL/triangleCAP.png?raw=true)

En 2000, Eric A. Brewer a formalisé un théorème très intéressant reposant sur 3 propriétés fondamentales pour caractériser les bases de données 
(relationnelles, NoSQL et autres) :

    Consistency (Cohérence) : Une donnée n'a qu'un seul état visible quel que soit le nombre de réplicas

    Availability (Disponibilité) : Tant que le système tourne (distribué ou non), la donnée doit être disponible

    Partition Tolerance (Distribution) : Quel que soit le nombre de serveurs, toute requête doit fournir un résultat correct
    
 Le théorème de CAP dit :

- Dans toute base de données, vous ne pouvez respecter au plus que 2 propriétés parmi
la cohérence, la disponibilité et la distribution.    

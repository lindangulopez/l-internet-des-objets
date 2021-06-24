Une base NoSQL est une base de données qui permet le passage à l'échelle via la réplication et la distribution des données (et de fait, des requêtes).
Par contre, la réplication empêche la gestion concurrentielle de transactions et la distribution de calcul lourd est propre à Map/Reduce et non les 
langages de plus haut niveau utilisés dans les solutions NoSQL.

Chaque solution NoSQL est associée à une famille. Cassandra, contrairement à ce que de nombreux sites web avancent, n'est plus une solution orientée 
colonne mais une solution orientée document. Comme cela est indiqué dans le chapitre "Choisissez votre famille NoSQL" :

Cassandra est souvent considérée comme une solution orientée colonnes. C'est une solution orientée documents appelée "wide-column store", dans le sens 
où le document est structuré comme en relationnel. La confusion vient du fait que l'on y définit des colonnes et des familles de colonnes dans le schéma, 
ce qui est différent du stockage de "colonnes".


MongoDB - orienté document

Neo4j - orienté graphe

Redis - orienté clé/valeur


Les bases NoSQL respectent les propriétés de types BASE, à opposer aux propriétés ACID des SGBDR.

Le théorème de CAP de Brewer repose sur les trois propriétés fondamentales d'une base de données : 
- Consistency, Availability, Partition Tolerance

HDFS, Clustered index, DHT, sont de techniques de sharding.

Par rapport, coût/cohérence/disponibilité/language/fonctionnalité python, MongoBD est top:

    MongoDB : 2+4+1+2+8 = 17
    Cassandra : 2+2+3+1+8 = 16
    HBase : 2+4+2+2+6 = 16
    DynamoDB : 1+2+4+0,5+8 = 15,5


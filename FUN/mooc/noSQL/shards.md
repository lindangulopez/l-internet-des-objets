- Les arbres
L’index le plus utilisé est l’arbre B (ou BTree), il adopte une structure arborescente pour chercher toute valeur indexée. Les feuilles de cet arbre contiennent des liens vers les pages contenant la valeur. Dans l'index d'un livre, les mots sont triés par ordre alphabétique. Dans un arbre, c’est la même chose en utilisant une recherche par dichotomie (plus petit/plus grand). Dans le cadre du NoSQL, l’arbre B va encore plus loin car les données sont triées : c’est un arbre B non-dense (ou clustered index). Notre livre devient alors un dictionnaire ! L’index est intégré directement au livre pour permettre de trouver directement la page de donnée.

- Le hachage
Le but d’une table de hachage est de placer les données par paquets, et à chaque donnée correspond un seul paquet de destination. Pour placer cette donnée, une fonction de hachage unique détermine le paquet. Pour reprendre notre analogie, nous parlerons cette fois de bibliothèque : les rangées A à C stockeront les livres dont le nom de l’auteur commence entre la lettre A et C. Pour retrouver un livre d’un auteur, il suffit d’aller dans la bonne rangée, même s’il faut ensuite examiner un certain nombre de livres pour le trouver.

- La distribution
Les bases de données distribuées existent depuis de nombreuses années ; le but de la distribution est de soulager le serveur central en répartissant les données sur plusieurs serveurs. Ce serveur central s’occupe ainsi de répartir la charge (données et requêtes), de fusionner le résultat et de gérer la cohérence des données. Cela vous fait penser au NoSQL ? Ne vous fiez pas aux apparences ! Les bases de données distribuées ne sont pas tolérantes aux pannes, la disponibilité est problématique en termes de synchronisation multi-serveurs, et il n’y a pas de techniques pour permettre l’élasticité de la base de données.

- L’élasticité
L’élasticité, nous n’en avons pas encore parlé. C’est la capacité du système à s’adapter automatiquement en fonction du nombre de serveurs qu’il dispose et de la quantité de données à répartir. Par exemple, vous avez 1To de données sur 1000 serveurs (1Go par serveur), lors d’un pic d’activité (soldes, période de Noël…), il serait utile de rajouter 1000 serveurs pour répartir la charge de calcul avec 500 Mo par serveur. L’élasticité va permettre de répartir uniformément les données sur les 2000 serveurs (déplacement de la moitié des données), et inversement lorsque le pic d’activité s’achève. De même, si le volume de données augmente et atteint 2To, l’élasticité garantira une répartition uniforme de 2Go par serveur.

- Le sharding
Le sharding est une technique permettant de distribuer des chunks (morceaux de fichiers) sur un ensemble de serveurs, avec la capacité de gérer l’élasticité (serveurs/données) et la tolérance aux pannes. Trois familles de distribution pour le NoSQL existent : HDFS (basé sur la distribution), le clustered index (basé sur le BTree) et le consistent hashing (basé sur les tables de hachage). Regardons comment elles fonctionnent, elles nous permettront d’orienter nos choix d’architecture.

## HDFS (Hadoop Distributed File System)
est une technique de distribution de fichiers volumineux. Chaque fichier sera découpé en "chunk" de 64Mo pour être distribué sur le réseau. Chaque serveur de ce réseau est un datanode contenant plusieurs chunks. La répartition de ces chunks est définie par le serveur central, le namenode.

## Un arbre distribué
La seconde famille de distribution de données repose sur le traditionnel BTree non-dense (ou clustered index) : il s'agit de l'arbre dont les données sont triées. Un serveur central s’occupe de l’arborescence de cet arbre, et les feuilles (les données) sont prises en charge par les nœuds du cluster.

![Sharding BTree](https://github.com/lindangulopez/l-internet-des-objets/blob/main/FUN/mooc/noSQL/ShardingBTree.png?raw=true)
Le serveur central agit comme "routeur" en donnant accès au serveur contenant la donnée requise. La gestion de l’arborescence lui permet de connaître la répartition des valeurs par nœud et, de fait, d'agir sur l’élasticité en modifiant les bornes de chaque nœud. Ceci permet de préserver en permanence le tri des données. Afin de garantir les pannes, le routeur est répliqué et oblige la synchronisation de l’arborescence.

Les nœuds contenant les données s’occupent des traitements (Map/Reduce), mais gèrent également la réplication des données. Contrairement à HDFS, la réplication est maintenue par le nœud lui-même, à cause de l’arborescence imposée par l’arbre. Nous pourrons voir dans le chapitre sur MongoDB la technique du ReplicaSet permettant d’effectuer cette réplication.

Les avantages de cette technique sont :

rassembler les données ayant des valeurs similaires (tri), et de fait toute opération sur ces données rassemblée (regroupement/reduce)

faciliter la gestion de la cohérence des données en verrouillant au niveau du nœud l’information et de synchroniser lui-même ses données avec ses replicas.

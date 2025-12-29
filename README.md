# Spring AOP : programmation orientée aspect

En programmation orientée objet, il arrive souvent que l’on trouve des portions de code qui se répètent à travers différentes méthodes. Par exemple, pour une application qui accède à une base de données, chaque interaction avec la base de données doit s’inscrire dans une transaction. Même si nous concevons une architecture objet avec une classe spécialisée pour gérer une transaction, nous allons devoir faire appel à une instance de cette classe dans chaque méthode qui interagit avec la base de données. Nous allons devoir répéter les actions dans notre code.

Dans des applications pour les entreprises, ce type de problématiques est souvent lié à des services techniques : gestion des connexions à un service tiers, gestion des transactions, écriture de fichiers de log ou encore sécurisation des accès.

La programmation orientée objet ne fournit pas de solution élégante à ces problématiques. C’est pour résoudre spécifiquement ces cas de figure que la Programmation Orientée Aspect (POA ou AOP pour Aspect Oriented Programming) a été introduite.

La POA n’est pas une notion propre au Spring Framework. Dans la communauté Java, le projet AspectJ est le projet le plus avancé pour intégrer la programmation orientée aspect au langage. Spring AOP est le module Spring chargé d’ajouter le support de la programmation aspect en se basant en grande partie sur AspectJ.

## Principe de la programmation orientée aspect

La programmation orientée aspect (POA) est utilisée pour implémenter des fonctionnalités transverses (cross-cutting concerns). Elle permet de rendre l’architecture plus modulaire. Un aspect représente une catégorie d’actions à réaliser dans certaines conditions. Par exemple, gérer les transactions, produire des informations de log, mettre en cache des informations… Plutôt que de répéter (ou d’appeler) ce code dans les différentes classes de l’application, nous allons définir des points à partir desquels l’aspect devra s’exécuter. Puis à l’aide d’un tisseur d’aspects (weaver), le flot normal d’exécution de l’application va être modifié afin d’exécuter les actions de cet aspect aux points voulus.

Dans la POA, on distingue l’approche statique et l’approche dynamique. L’approche statique modifie le code au moment de la compilation afin d’introduire aux points voulus l’exécution des aspects. Cette approche est complexe à prendre en charge car elle nécessite une étape supplémentaire à la compilation. L’approche dynamique est réalisée au moment de l’exécution de l’application. Elle ne nécessite donc pas de compilation particulière. Elle peut néanmoins nécessiter une instrumentation du code au moment du chargement des classes dans la JVM mais ce processus est transparent pour le développeur. L’approche dynamique introduit un coût supplémentaire à l’exécution puisqu’une bibliothèque tierce doit prendre en charge l’exécution des aspects. En pratique, ce surcoût est négligeable.

Notez cependant que le support de la programmation aspect par Spring est limité. Il ne permet d’appliquer les principes de la programmation qu’à l’appel de méthodes. Nous allons pouvoir exécuter du code supplémentaire avant, après l’appel d’une méthode. Nous avons même la possibilité de remplacer totalement l’exécution d’une méthode.

La création d’aspect est très certainement réservé à un usage avancé du Spring Framework. Néanmoins, comprendre les bases de la programmation orientée aspect vous permettra de mieux comprendre la manière donc le Spring Framework (et d’autres frameworks) peuvent instrumenter le code d’une application. Un exemple courant est la gestion des transactions que nous aborderons dans le chapitre Spring Transaction.

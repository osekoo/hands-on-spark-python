## Sommaire
1. [Objectifs](#objectifs)
2. [Prérequis](#prérequis)
3. [Lab Session](#lab-session)

## Objectifs
L'objectif de cette session pratique est:
- d'implémenter un mini-projet [Apache Spark](https://spark.apache.org/) en [Python] en utilisant [PyCharm](https://www.jetbrains.com/fr-fr/pycharm/),
- de lancer un cluster Spark sur une machine locale,
- de packager l'application et l'exécuter sur le cluster local Spark.

## Prérequis
_A faire avant la session_

## PyCharm
[PyCharm](https://www.jetbrains.com/pycharm/download/) est un IDE permettant de développer des applications en Python.
Nous allons l'utiliser lors de cette session pratique car il intègre plusieurs outils qui facilitent et accélèrent le développement des applications.  
  
La version PyCharm Community est disponible [ici](https://www.jetbrains.com/pycharm/download/).  
Téléchargez et installez la version compatible avec votre machine.
Commande spéciale pour Ubuntu 16.04 ou plus:
```
sudo snap install pycharm-community --classic
```
Note: votre compte étudiant de Dauphine vous donne accès gratuitement à la version Ultimate. Pour cela, il suffit de vous enregistrer avec votre adresse mail de Dauphine et de valider l'inscription.

Je vous invite à prendre en main PyCharm avec ce [tutoriel](https://www.jetbrains.com/help/pycharm/creating-and-running-your-first-python-project.html#create-file).


### Docker
Dans cette session, pour des raisons pratiques, nous allons utiliser des [dockers](https://www.docker.com/) ([conteneurs d'applications](https://fr.wikipedia.org/wiki/Docker_\(logiciel\))) pour exécuter nos applications.  
Un docker est un conteneur d'applications permettant d'exécuter une application indépendamment du système d'exploitation et de ses dépendances.  
L'application est packagée d'une façon autonome (avec toutes ses dépendances) pour être exécutée sur n'importe quel système.  
Les liens ci-dessous vous guident dans l'installation de Docker sur votre machine locale:  
[Windows](https://docs.docker.com/docker-for-windows/install/) | [Ubuntu](https://docs.docker.com/engine/install/ubuntu/) | [Mac](https://docs.docker.com/docker-for-mac/install/).  
Veuillez réaliser l'installation avant la session.

### Docker-compose
Les utilisateurs de Linux ont besoin d'installer [docker-compose](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-compose-on-ubuntu-20-04). Pour les autres (Mac et Windows), cet utilitaire est déjà inclus dans Docker Desktop (installé plus haut).

### Spark
Nous avons besoin d'installer Spark 3.0.2 en mode standalone afin de pouvoir utiliser la commande `spark-submit` pour envoyer nos jobs sur notre cluster local.  
Veuillez suivre les liens ci-dessous pour installer Spark sur votre machine en fonction de votre OS:  
- [Windows](http://www.xavierdupre.fr/app/sparkouille/helpsphinx/lectures/spark_install.html#installation-de-spark-sous-windows)
- [Linux](http://www.xavierdupre.fr/app/sparkouille/helpsphinx/lectures/spark_install.html#installation-de-spark-sous-linux)
- [Mac](https://notadatascientist.com/install-spark-on-macos/)
  
  
## Lab Session

### Exécution sur cluster Spark
Une fois le package obtenu, à l'aide de la commande `spark-submit` nous allons exécuter notre application sur notre cluster local que nous avons lancé un peu plus haut.
Si ce n'est pas encore le cas, c'est le moment de le lancer avec la commande `docker-compose up`.  

```(shell)
spark-submit \
  --master spark://localhost:7077 \
  --deploy-mode client \
  --executor-cores 4 \
  --num-executors 1 \
  --files ./ulysses.txt \
  --class WordCount \
  my-project.py
```

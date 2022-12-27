# Étude empirique des odeurs de code et d’odeurs d’architecture des applications développées avec des microservices

Le contexte de notre étude empirique est mené sur des applications avec un style architectural de microservices conçus et développés en tant que projet open source et hébergées sur github, nous allons analyser deux catégories de mauvaises odeurs (1) d’architecture, et (2) de code. 
    
## Collection de données 
    
Nous avons considéré un ensemble de 10 projets qui constituent notre jeu de données, Les projets sont de taille variable.

1. **Train ticket** : Un projet conçu avec une architecture microservice, est un système pour la réservation de billet de train. [https://github.com/FudanSELab/train-ticket] 

2. **Cloud native microservice strangler** : une application d’implémentation de cloud native en se basant sur des microservices, une application visant à mettre en valeur la relation d’intégration d’une architecture de microservice avec d’autre application utilisant de pratiques microservices du genre Netflix à l’aide de Spring Cloud. [https://github.com/kbastani/cloud-native-microservice-strangler-example]

3. **Netflix/genie** : développée par Netflix, est un moteur d’exécution Big data. [https://github.com/Netflix/genie]

4. **Apollo** : est un système de gestion de configuration centralisée des applications et clusters, y compris la gestion de configuration de microservices.  [https://github.com/apolloconfig/apollo] 

5. **Sitewhere** : est une plateforme conçue avec l’architecture microservices, dédiée à l’application IOT open source, afin de gérer les données des applications IOT en termes de stockage, traitement et intégration. [https://github.com/sitewhere/sitewhere]

6. **Ftgo application** : une application qui présente principalement l’aspect technique de l’architecture microservice, elle contient beaucoup de service qui sont déployés soit avec Doker ou Kubernetes. [https://github.com/microservices-patterns/ftgo-application]

7. **Online boutique** : un exemple d’application cloud native à base de microservices, est une boutique en ligne de commerce électronique pour la gestion d’articles, ajout, modification, consultation et achat par les clients. [https://github.com/GoogleCloudPlatform/microservices-demo]

8. **Warehouse-microservices** : une API d’entrepôt développée avec du java, contient huit microservices, et utilise Spring boot, Docker ainsi que le messaging. [https://github.com/hiejulia/warehouse-microservice]

9. **Cloud native starter** : est un projet qui démontre comment démarrer avec des applications Cloud native basées sur une architecture de microservices. Elle fournit du code qui permet de déployer ces applications dans différents environnements kubernetes. [https://github.com/IBM/cloud-native-starter]

10. **Tap And Eat MicroServices** : s’agit d’un projet destiné aux restaurants et aux magasins, conçu avec l’architecture microservices, inclut la gestion de clients, des comptes, des prix et de magasins. https://github.com/jferrater/Tap-And-Eat-MicroServices 
    
    
## Analyse de données 
    
### ETAPE 1
    
   En particulier, nous avons analyser ces applications afin de détecter la présence d’un ensemble d’odeurs traditionnelles en conception et en développement. Pour chaque application de notre jeu de données nous avons utilisé les outils suivant : 
   
 1. **_Designite_**  : pour sa capacité d’évaluer la qualité du code des applications, il permet de détecter les odeurs de conception spécifiques aux projets développés à base du java. Il suffit d’utiliser la commande suivante sur l’invite de commande : 

`C:\Users\DELL\Designite>  java -jar Designitejava.jar -i myProjetct -o myCSVResult` 

Analyse Designite Train ticket :

![alt text](https://github.com/HindaHeroine/MicroservicesRepository/blob/main/ImagesGit/Analyse%20Designite%20Train%20ticket.JPG "Logo Title Text 1")

Le majeur avantage que l’outil Designite offre, c’est qu’il affiche des résultats clairs des odeurs d’architecture détectée sur l’invite de commande directement, accompagnée des métriques de détection utilisées. Designite permet également d’exporter des fichiers CSV résultants. 

le lien suivant montre les resultats d'analyse Designite de chaque projet en entier et de l'ensemble des microservices de chaque projet : [https://etsmtl365-my.sharepoint.com/:f:/g/personal/hinda_abassi_1_ens_etsmtl_ca/EvQ2h3_YW7lFr_qP_h7hrUoBgmHQh-Mv97JyGEQMgFq9lg?e=iIJZdF]

 
2. L’outil **_Organic_** : est utilisé pour la détection des mauvaises odeurs de code source. Pour exécuter Organic, il suffit de lancer une commande sur un terminal dans le répertoire de chaque un de nos projets. En sortie en aura un fichier Json avec tous les détails. Voici la commande qui permet d’exécuter l’outil :		 

`C:\Users\DELL\organic-standalone-main\> gradle run --args="-sf 'Myresult.json' -src 'MyProject'" `

le lien suivant montre les fichiers json résultants d'analyse Organic de chaque projet en entier et de l'ensemble des microservices de chaque projet : [https://etsmtl365-my.sharepoint.com/:f:/g/personal/hinda_abassi_1_ens_etsmtl_ca/Em58097ZyuxAtmQXzFE5zLEB5-XuaP7X4mSa1YCZGiJA-w?e=XaLjnk]
  

3. **_IntelliJ_** : est l’outil qu’on a utilisé pour vérifier l’existence des dépendances cyclique dans le projet Apollo.

Analyse Intellij du projet Apollo :

![alt text](https://github.com/HindaHeroine/MicroservicesRepository/blob/main/ImagesGit/Analyse%20Intellij%20Apollo.JPG "Logo Title Text 2")

Le lien suivant montre en detail la matrice de dépendance: [https://etsmtl365-my.sharepoint.com/:f:/g/personal/hinda_abassi_1_ens_etsmtl_ca/Eqk5NbavODFOs2SIIC6U2T8BRDbk3OkvfePhoVgzifwVDQ?e=h052rg]
  
4. **_Understand_**: En ce qui concerne la validation de nos données collectées, nous avons utilisé l’outil Understand pour vérifier un ensemble de métrique comme le LOC, le nombre de méthodes et de fichiers, etc., nous l’avons utilisé également pour déduire le nombre de lignes de code de chaque projet et le nombre de chaque composant constituant chaque projet (Classes, méthodes…).

### ETAPE 2

Nous avons utilisé les données générées dans l'étape 1 pour créer des vues graphiques que ca soit pour les odeurs de code ou d'architecture, le lien suivant montre les résultats sur le  fichier EXCEL: [https://etsmtl365-my.sharepoint.com/:x:/g/personal/hinda_abassi_1_ens_etsmtl_ca/EfEojTeUbJZJiEHV71uFNXoBUOd8Oe0WfP1AP-Ld3n1vtw?e=Eqongf]

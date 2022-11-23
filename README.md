# MicroservicesRepository
Etudes empiriques pour analyser les odeurs de code et les odeurs d'architecture des projets microservices

Le contexte de notre étude empirique est mené sur des applications avec un style architectural de microservices conçus et développés en tant que projet open source et hébergées sur github.Nous avons analyser deux catégories de mauvaises odeurs (1) d’architecture, et (2) de code.

Nos cibles sont des applications développées principalement avec du java, nous avons considéré par la suite 10 projets qui constituent notre jeu de données final.

En particulier, nous allons analyser ces applications afin de détecter la présence d’un ensemble d’odeurs courantes, traditionnelles en conception et en développement ayant un impact négatif sur les attributs fonctionnels et non fonctionnels des applications.

Pour chaque application de notre jeu de données, nous avons utilisé les outils suivants:

1- Designite :  pour sa capacité d’évaluer la qualité de code des applications, il permet de détecter les odeurs de conception spécifiques aux projets développés à base de java. l'outil Designite mets en valeur les odeurs architecturales suivantes :

- Dépendance cyclique :	Dépendance directe ou indirecte entre deux composants architecturaux ou plus.
- Dépendance instable	: Un composant instable qui dépend d’un autre composant encore moins stable que lui.
- Interfaces ambiguës	: Une interface n’offrant qu’un seul point d’enterrée pour un composant.
- Composant God	: Un composant dans le nombre de lignes de code Loc est très élevé.
- Concentration de fonctionnalités :	Un composant dont sa responsabilité est importante, autrement dit, il se charge de réaliser plusieurs opérations.
- Fonctionnalité dispersée :	Un ensemble de composants qui résolvent tous le même problème de grande valeur.
- Structure dense	: Dépendance excessive entre les composants architecturaux dont la structure n’est pas précise.

2- L’outil Organic: est utilisé pour la détection et la résolution des mauvaises odeurs de code source. Pour exécuter Organic, on a besoin de lancer une commande sur un terminal dans le répertoire de chaque un de nos projets. En sortie en aura un fichier Json avec tous les détails concernant l’odeur de code détectée.
voici les odeurs de code que l'outil nous a permis d'analyser:

- Méthode longue :	Une méthode contient beaucoup de lignes de code. La complexité d’une méthode commence dès 10 lignes. Plus le nombre de lignes de code est élevée, plus la méthode devient difficiles à comprendre.
- Méthode complexe :	La complexité cyclomatique d’une méthode se calcule en fonction de nombre de chemins d’exécution, Plus le nombre de chemins est élevé, plus le nombre de tests nécessaire pour couvrir tous les chemins possibles devient important.
- Longue liste de paramètres	Une fonction avec beaucoup de paramètres est complexe. Plus de 3 à 4 paramètres pour une méthode. Or une longue liste de paramètre signifie que la méthode s’en charge d’un nombre excessif de responsabilités. 
- Jalousie de fonctionnalités	Une classe qui s’intéresse à accéder aux méthodes et attribue d’autres classes plus que ses attributs et méthodes a elle.
- Classe de données : Une classe ayant des champs, des getters et setters, mais qu’elle n’implémente pas de fonctionnalités qui agissent sur ses champs, elle est généralement manipulée par d’autres classes vu qu’elle manque de méthodes pertinentes pour justifier le fait qu’elle soit une classe.
- Chaînes de message	Un ensemble d’appels ($ a->b ()->c ()->d ()) signifie qu’un client demande à un objet, que cet objet demande à son tour encore à un autre objet, ce qui rend difficile de voir ou la fonction se produit réellement.
- Classe paresseuse	Une classe qui n’est pas utilisée, qui ne fait pas assez ou même inutile, elle ne fait qu’augmenter la complexité du code, donc elle doit être supprimée ou bien faire partie d’une classe utile.

3- Intellij : l'outil nous permet de générer la matrix de dépendance "Dependancy Structure Matrix", une analyse DSM qui nous permet de visualiser les relations complexes entre les package de chaque projet, Ainsi nous pouvons suivre la propagation de tous changement sur les composants système.



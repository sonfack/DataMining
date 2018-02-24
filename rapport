#Présentation de l'environement de travail 
Pour méner à bien notre project, nous avons utiliser le langage R  open source ainsique sont environement Serveur web déployé sur 
la distribution Linux Debian. R est un outil utiliser pour les statistiques, l'analyse des données et la visualisation.


#Présentation du jeu de donnée 

Notre jeu donnée a une taille de 1473 et represente un sous ensemble des données de l'enquete sur la contraception des femmes mariées
non enceinte ou qui ne save pas qu'elle sont enceinte au moment de l'enquete en Indonesie.


#Pretraitement de donnée 

Avant toute analyse sur notre jeu de données, nous allons suivre les étapes ci-dessous : 

1. au renomage des attributs et transformation des attributs
Cette étape va nous permettre d'avoir les noms des attributs normaux et facile à manipuler et la transformation des valeurs de ces attributs
va nous permettre de leurs traiter. 

- Wife's age                     (numérique)
Wage represente l'age de la femme 

- Wife's education               (categorie)      
Wedu representer le niveau d'education de la femme
	Transformation : 
	1=low, 2, 3, 4=high

- Husband's education            (categorie)      
Hedu reprense le niveau d'educaiton du mari
	Transformation : 
	1=low, 2, 3, 4=high

- Number of children ever born   (numérique)
Nbchild represente le nombre d enfant du couple 

- Wife's religion                (binaire)           
Wrelig represente la religion de la femme 
	Transformation :
	0=Non-Islam, 1=Islam

- Wife's now working?            (binaire)          
Wwork donnée si la femme travail ou pas 
	Transformation :
	 0=Yes, 1=No

- Husband's occupation           (categorie)      
Hoccup represente la categorie de l'education du mari
	Transformation :
	1, 2, 3, 4

- Standard-of-living index       (categorie)      
Stdlind represente l'index du niveau de vie
	Transformation :
	1=low, 2, 3, 4=high

- Media exposure                 (binaire)           
Mexp represente la couverture mediatique 
	Transformation :
	0=Good, 1=Not good

- Contraceptive method used     (classe) 
Cmethod  represente la methode de contraception
	Transformation :
	 1=No-use 
	 2=Long-term
         3=Short-term

2. Présentation des donnée sous forme de tableau 
Pour présenter nos données sous forme de tableau, nous avons appliquer un traitrement pour la transformer au format CSV(a separation de virgule). 
Nous avons apportés des traitements d'ajout de virgule de façon appropriée au niveau des données( cmc.data) et au niveau des entête ( cmc.name).

3. Verification
- Données manquantes
Après une vérification minisieuse sur notre jeu de données, nous n'avons nis les données manquantes, ni les données non standardisée. De ce fait, 
nous n'avons rien à ajouter ni retirer sur notre jeu de données. 
- Vérification de donnée 
La vérification de notre jeu de données fait appel à l'outil R vu que la taille de la donnée est grande, nous ne pouvons le faire manuellement. 
'''
	class(cmc)
	[1] "data.frame"
'''
- Vérification de la taille et dimension des donnée
'''
	dim(cmc)
	[1] 1473   10
'''
- Vérificaiton de la strucutre 
'''
	str(cmc)
	'data.frame':	1473 obs. of  10 variables:
	 $ Wage   : int  24 45 43 42 36 19 38 21 27 45 ...
	 $ Wedu   : int  2 1 2 3 3 4 2 3 2 1 ...
	 $ Hedu   : int  3 3 3 2 3 4 3 3 3 1 ...
	 $ Nbchild: int  3 10 7 9 8 0 6 1 3 8 ...
	 $ Wrelig : int  1 1 1 1 1 1 1 1 1 1 ...
	 $ Wwork  : int  1 1 1 1 1 1 1 0 1 1 ...
	 $ Hoccup : int  2 3 3 3 3 3 3 3 3 2 ...
	 $ Stdlind: int  3 4 4 3 2 3 2 2 4 2 ...
	 $ Mexp   : int  0 0 0 0 0 0 0 0 0 1 ...
	 $ Cmethod: int  1 1 1 1 1 1 1 1 1 1 ...
'''

-----------------------------------------------------------------------------------------

Le probleme est de predire la méthode de contraception d'une femme en se basant sur les criteres démographique et socio-economique. 
Notons que cette méthode peut être courte, longue ou pas de méthode du tout.
  
 

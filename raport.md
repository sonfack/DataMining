# Présentation de l'environement de travail 
Pour méner à bien notre project, nous avons utiliser le langage R  open source ainsique sont environement Serveur web déployé sur 
la distribution Linux Debian. R est un outil utiliser pour les statistiques, l'analyse des données et la visualisation.

# Présentation du problème 
Le probleme est de predire la méthode de contraception d'une femme en se basant sur les criteres démographique et socio-economique. 
Notons que cette méthode peut être courte, longue ou pas de méthode du tout.
  

# Présentation du jeu de donnée 

Notre jeu donnée a une taille de 1473 et represente un sous ensemble des données de l'enquete sur la contraception des femmes mariées
non enceinte ou qui ne save pas qu'elle sont enceinte au moment de l'enquete en Indonesie.


# Pretraitement de donnée 

Avant toute analyse sur notre jeu de données, nous allons suivre les étapes ci-dessous : 

1. au renomage des attributs et transformation des attributs
Cette étape va nous permettre d'avoir les noms des attributs normaux et facile à manipuler et la transformation des valeurs de ces attributs
va nous permettre de leurs traiter. 

- Wife's age                     (numérique)
Wage represente l'age de la femme 

- Wife's education               (categorie)      
Wedu representer le niveau d'education de la femme.<br>
	Transformation : 
	1=low, 2, 3, 4=high

- Husband's education            (categorie)      
Hedu reprense le niveau d'educaiton du mari<br>
	Transformation : 
	1=low, 2, 3, 4=high

- Number of children ever born   (numérique)
Nbchild represente le nombre d enfant du couple 

- Wife's religion                (binaire)           
Wrelig represente la religion de la femme <br>
	Transformation :
	0=Non-Islam, 1=Islam

- Wife's now working?            (binaire)          
Wwork donnée si la femme travail ou pas <br>
	Transformation :
	 0=Yes, 1=No

- Husband's occupation           (categorie)      
Hoccup represente la categorie de l'education du mari<br>
	Transformation :
	1, 2, 3, 4

- Standard-of-living index       (categorie)      
Stdlind represente l'index du niveau de vie<br>
	Transformation :
	1=low, 2, 3, 4=high

- Media exposure                 (binaire)           
Mexp represente la couverture mediatique <br>
	Transformation :
	0=Good, 1=Not good

- Contraceptive method used     (classe) 
Cmethod  represente la methode de contraception<br>
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
```
	class(cmc)
	[1] "data.frame"
```
- Vérification de la taille et dimension des donnée
```
	dim(cmc)
	[1] 1473   10
```
- Vérificaiton de la strucutre 
```
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
```

# Analyse exploratoire de chaque attribut 

```
summary(cmc)
      Wage            Wedu            Hedu         Nbchild           Wrelig      
 Min.   :16.00   Min.   :1.000   Min.   :1.00   Min.   : 0.000   Min.   :0.0000  
 1st Qu.:26.00   1st Qu.:2.000   1st Qu.:3.00   1st Qu.: 1.000   1st Qu.:1.0000  
 Median :32.00   Median :3.000   Median :4.00   Median : 3.000   Median :1.0000  
 Mean   :32.54   Mean   :2.959   Mean   :3.43   Mean   : 3.261   Mean   :0.8506  
 3rd Qu.:39.00   3rd Qu.:4.000   3rd Qu.:4.00   3rd Qu.: 4.000   3rd Qu.:1.0000  
 Max.   :49.00   Max.   :4.000   Max.   :4.00   Max.   :16.000   Max.   :1.0000  
     Wwork            Hoccup         Stdlind           Mexp          Cmethod    
 Min.   :0.0000   Min.   :1.000   Min.   :1.000   Min.   :0.000   Min.   :1.00  
 1st Qu.:0.0000   1st Qu.:1.000   1st Qu.:3.000   1st Qu.:0.000   1st Qu.:1.00  
 Median :1.0000   Median :2.000   Median :3.000   Median :0.000   Median :2.00  
 Mean   :0.7495   Mean   :2.138   Mean   :3.134   Mean   :0.074   Mean   :1.92  
 3rd Qu.:1.0000   3rd Qu.:3.000   3rd Qu.:4.000   3rd Qu.:0.000   3rd Qu.:3.00  
 Max.   :1.0000   Max.   :4.000   Max.   :4.000   Max.   :1.000   Max.   :3.00  


```

# Analyse de lien entre chaque paire d'atributs

- Wage - Wedu 
Hypothèse : les femmes agées sont les plus éduquées 

- Wage - Hedu 
Hypothèse : les femmes agées épouse les hommes agés

- Wage - Nbchild 
Hypothèse : les femmes agées ont plus d'enfants

- Wage - Wrelig 
Hypothèse : les femmes agées sont mulsumane

- Wage - Wwork 
Hypothèse : la plupart des femmes agées travaillent 

- Wage - Hoccup 
Hypothèse : les femmes agées sont mariées aux hommes qui travaillent

- Wage - Stdlind 
Hypothèse : les femmes agées ont un niveau de vie élévé

- Wage - Cmethod 
Hypothèse : les femmes agées n'utilisent pas de méthode de contraception



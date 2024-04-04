# Projet new-car

## Introduction

Pour ce projet que nous devions réaliser en binôme, nous devions réaliser une analyse exploratoire poussée afin d'appliquer l'algorithme de régression linéaire. Le but final de ce projet étant d'aider un individu à estimer le prix de sa future voiture en fonction de ses caractéristiques de recherche.

## Langages, outils & libraries

- [] Python
- [] Pandas
- [] Matplotlib
- [] Seaborn
- [] Numpy
- [] Scikit-learn
- [] Scipy
- [] VS Code
- [] GitHub

## Organisation du projet.

Etant deux à travailler sur ce projet, nous avons décidé de faire trois notebook:

- Un notebook par personne
- Un notebook commun qui réunit notre travail

Nous avons décidé de procéder comme ceci car premièrement, la charge de travail demandée nous permettait de faire chacun son analyse exploratoire puis, nous devions appliquer l'algorithme de régression linéaire avec deux librairies différentes:

- Scikit-learn
- Scipy

## Présentation du Notebook

Dans le notebook 'new_car.ipynb' vous pourrez donc retrouver:

- Une analyse exploratoire poussée
- Une veille sur la régression linéaire
- L'application de l'algorithme de Regression Linéaire univariée via Scikit-learn
- L'application de l'algorithme de Regression Linéaire univariée via Scipy
- Les interprétations de résultats de ces deux applications
- L'application de la Regression linéaire multivariée et une nouvelle interprétation de résultats
- L'évaluation des différents modèles
- La conclusion globale du projet
- L'application en fonction des caractéristiques de Martin afin de répondre à la problématique du projet.

### L'analyse exploratoire:

Pour cette analyse, nous avons tout d'abord chargé les données et affiché le type de celles-ci. Nous avons repréré les variables numériques qui pourraient nous être utiles pour l'analyse et affiché un aperçu en utilisant la fonction 'head()'. On vérifie en suite si notre target a un potentiel infini ou un espace restreint. en utilisant la fonction 'unique()'.  
Après avoir ciblé les variables utiles pour l'analyse, on commence par calculer les moyennes de celles-ci avec 'mean()', puis les médianes avec 'median()', on cherche en suite les quantiles avec 'quantile()'. On affiche en suite la distribution des données pour chacune des variables afin de terminer l'analyse des variables numériques. Pour les variables catégorielles, nous affichons le nombre de voitures par variable puis la taille du jeu de données.  
Nous passons en suite à la recherche de relations entre les variables et la target. Nous cherchons une correlation avec 'corr()' parmi ces variables: 'Year', 'Selling_Price', 'Present_Price', 'Kms_Driven', 'Owner' puis on affiche une heatmap. Nous avons en suite réalisé des boxplots entre la target et les variables catégorielles. Nous avons également fait des Pair Plot entre la target et ces variables puis un density plot afin de voir la répartition de la target.  
Pour poursuivre, nous avons quantifié la relation entre la target (prix de vente) et l'âge d'une voiture en utilisant les scatter points. Puis, nous avons vérifié si la regression linéaire s'applique dans ce cas avec certaines variables numériques. En voulant tracer une ligne de regression sur la relation entre le nombre de kilomètres d'une voiture et son prix de vente, nous nous sommes aperçu que la ligne est ascendante. Ce qui ne parait pas logique car communément, plus une voiture a roulé plus elle perd de sa valeur. 
Nous avons donc décidé de faire un boxplot du prix de vente pour vérifier les outliers.  
Nous avons vu qu'il y avait des entrées potentiellement abérrantes. Nous avons donc approfondi la recherche en faisant le calcul de l'écart interquartiles (IQR).
Après avoir conclut que ces valeurs n'étaient pas aberrantes, nous sommes passés à l'application de l'algorithme.  

### Regression linéaire avec Scipy: 

Utilisation de la fonction linegress de Scipy.

"slope": Est la pente qui indique la variation du prix de vente pour chaque année supplémentaire d'âge de la voiture.   
"intercept": Représente le prix de vente estimé théorique d'une voiture de 0 an.  
"r_value": Mesure la force et la direction de la relation linéaire entre l'âge de la voiture et son prix de vente.  
"p_value": Est la probabilité que la corrélation observée entre les deux variables soit due au hasard. Si p est faible cela indique que la relation est statistiquement significative.  
"std_err": Estime la précision de la pente calculée. Plus la valeur est faible plus l'estimation est précise.  


Interprétation des résultats:  
Après avoir appliqué l'algorithme de régression linéaire univariée voici comment nous pouvons interpréter nos résultats:  

- **Le coefficient** (ou la pente) est de 0.415, ce qui indique une augmentation de prix de vente associée a l'augmentation de la variable indépendante (Year). Donc pour chaque unité supplémentaire de cette variable indépendante, le prix de vente estimé augmente de 0.415 unité. Donc la relation entre les deux variables est positive.  

- **L'intercept** est nettement négatif, ce qui suggère que si la valeur de la variable indépendante était de 0, alors le prix de vente serait négatif.  

- **Le coefficient de relation** est de 0.236 ce qui indique une corrélation positive faible entre les deux variables. Il y a donc une relation positive mais mais la force de cette relation est faible.  

- **La valeur p** reste très faible, indiquant que la relation observée (la pente positive) est statistiquement significative, malgré la faible corrélation. Cela signifie que la relation positive entre la variable indépendante et le prix de vente n'est probablement pas due au hasard.  

- **L'erreur standard** de la pente est identique à l'analyse précédente, ce qui suggère que la précision de l'estimation de la pente est similaire.  


### Regression linéaire avec Scikit-learn:  
On utilise des outils de la bibliothèque sklearn pour construire un modèle qui va apprendre à estimer le prix de vente des voitures en fonction de l’année.

On divise les données en deux parties : une pour apprendre au modèle (entraînement) et une pour tester sa précision (test).

On crée un modèle de régression linéaire, qui est une façon simple de prédire une valeur numérique.

Après avoir entraîné le modèle avec les données d’entraînement, on l’utilise pour prédire les prix sur de nouvelles données.

Enfin, on calcule l’erreur de nos prédictions pour voir à quel point notre modèle est précis. Une erreur plus petite signifie de meilleures prédictions.



## Conclusion  
Après avoir utilisé la régression linéaire multiple avec plusieurs variables, nous pouvons constater que des variables comme 'Kms_Driven', 'Transmission', 'Fuel_Type' ou encore 'Year' sont succeptibles de faire varier le prix d'une voiture. 
Par exemple, plus une voiture est vieille moins elle est chère, plus elle a parcouru de kilomètres moins elle est chère aussi.
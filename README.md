This repository contains all codes associated to the article by Masson et al. Modelling the functional dependency between root and shoot compartments to predict the impact of the environment on the architecture of the whole plant: methodology for model fitting on simulated data using Deep Learning techniques - DOI : https://doi.org/10.1093/insilicoplants/diab036

Ce dossier contient tout le matériel nécessaire pour entrainer le reseau VoxNet à classer ou à deviner les paramètres environnements d’un jeu de simulation de croissance de l’espèce “plastique”.

Plusieurs entrainement de ce réseau ont déjà été effectués et sont sauvegardés dans ce dossier. Pour effectuer une prediction, nul besoin de réentrainer le réseau ! Suivez la deuxième procédure décrite dans ce document.

Procédure pour l’entrainement sur un nouveau jeu de données :

Etape Préliminaire :

Si vous souhaitez construire une base de test en plus de la base d’entrainement à partir de ce nouveau jeu de données, scinder le jeu de données en deux.


Etape 1 : Construction de la base de données d’entrée à partir de données brutes.

Pour construire la base de données d’entrée à partir de vos données brutes, ouvrez le script Get_database.py, renseignez-y les emplacements et noms de votre base de données brutes ainsi que de la base de données d’entrée que vous souhaitez construire, puis lancez le dans un terminal de commande.  python ./Get_database.py

Pour construire la base de test, suivez la meme procédure.


Etape 2 : Entrainement

Si vous souhaitez entrainer le VoxNet Géneratif, ouvrez le script VoxNet_Devine.py. Dans chacun de ces scipts, il vous faudra renseigner un certain nombre d’information : Emplacement de la base de données d’entrée, Emplacement de sauvegarde du modèle, Emplacement de sauvegarde des metrics d’entrainement, Emplacement de sauvegarde des poids du réseau, ainsi que les paramètres pour l’entrainement : loss, optimizer et metrics pour la compilation; batch_size, nombre de batch par step d’entrainement et nombre d’epoch pour l’entrainement.

Toutes les informations relatives à l’entrainement, et à la validation de l’entrainement seront stockées simultanément à l’entrainement aux différents emplacements renseignés dans ces scripts.

Une fois que vous avez renseignés les script, vous pouvez les lancer dans un terminal de commande  en tapant la commande python ./VoxNet_Devine.py


Etape 3 : Visualisation des résultats de l’entrainement

Pour visualiser les résultats de l’entrainement du VoxNet Generatif, ouvrez le script VisuPred_Devine.py et renseignez y l’emplacement des fichiers sauvegardés pendant l’entrainement, puis lancez le dans un terminal de commande en tapant la commande python ./VisuPred_Devine.py

Toutes les figures de visualisation seront sauvegardées au meme emplacement que les fichiers sauvegardés pendant l’entrainement.


Procédure pour la prédiction des paramètres environnement sur un ou plusieurs exemples :

Ici il s’agit d’utiliser le VoxNet Génératif pour deviner les paramètres environnement d’une ou de plusieurs simulations. Nul besoin de ré-entrainer le réseau, nous allons récupérer un modèle déjà en trainé du réseau.

Etape Préliminaire :

Si les exemples que vous avez à disposition sont sous forme de données brutes, il vous faudra les convertir en données d’entrée du réseau. (suivre l’Etape 1 de la procédure précédente).

Etape 1 : Prediction

Ouvrez le script VoxNet_Devine_Test.py. Renseignez y l’emplacement de votre base de d’exemples (path_to_data), ainsi que l’emplacement ou vous souhaitez voir apparaitre les résultats (path_to_results).
Il vous faudra également renseigner l’emplacement du modèle sauvegardé que vous souhaitez utiliser pour la prédiction. Il se situe dans le sous-dossier Models_specie pour le modèle en fin d’entrainement, ou dans le sous-dossier Wheights_specie pour tous les modèles sauvegardés au cours de l’entrainement.

Pour lancer la prédiction, ouvrez un terminal de commande et tapez la commande python ./VoxNet_Devine_Test.py

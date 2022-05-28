# OCR_P8_Kaggle_UW-Madison-GI-Tract-Image-Segmentation

# Introduction
Le notebook est la version finale comentée en français du kernel que j'ai soumis à la compétions Kaggle [UW-Madison GI Tract Image Segmentation](https://www.kaggle.com/competitions/uw-madison-gi-tract-image-segmentation)
Il porte sur la segmentation des intestins et de l'estomac sur les clichés d'IRMs de patients atteints de cancer afin de les éviter lors du traitement de la tumeur par radiothérapie.  

# Contexte
En 2019, environ 5 millions de personnes ont été diagnostiquées d’un cancer du tractus gastro-intestinal dans le monde. Parmi ces patients, environ la moitié sont éligibles à la radiothérapie qui est généralement administrée entre 10 à 15 minutes par jour, pendant 1 à 6 semaines. Le traitement consiste à délivrer de fortes doses de rayonnement à l'aide de faisceaux de rayons X dirigés vers les tumeurs tout en évitant l'estomac et les intestins. 

A l’aide de nouvelles technologies basée sur le couplage de l'imagerie par résonance magnétique et les systèmes d'accélérateur linéaire pour la radiothérapie (Magnetic Resonance Imaging Guided Linear Accelerator MRI-Linacs), les oncologues sont en mesure de visualiser la position quotidienne de la tumeur et des organes, qui peuvent varier d'un jour à l'autre. Afin d’éviter l'estomac et les intestins lors du traitement, les radio-oncologues doivent tracer manuellement la position de ces organes sur les scanners IRMs pour ajuster la direction des faisceaux de rayons X afin d’augmenter la dose administrée sur la tumeur. C’est un procédé long et laborieux qui peut prolonger les durées de traitement de 15 minutes à 1h par patient et ceci peut être difficile à tolérer pour les patients. Pour améliorer cela, l’apprentissage profond pourrait être utilisé afin de segmenter automatiquement l’estomac et les intestins et rendre les traitements beaucoup plus rapide et tolérable pour les patients et cela permettrait à un plus grand nombre de patients d’obtenir des traitements plus efficaces. 

Le « Carbone Cancer Center » qui est situé dans l’Université de Wisconsin-Madison (UW-Madison), est un pionnier de la radiothérapie basée sur la technique du MRI-LINAC. Cette université publique a accepté de soutenir ce projet en proposant ce challenge sur la plateforme Kaggle et en livrant des scanners IRMs anonymisées des patients traités au UW-Madison Carbone Cancer Center.

Dans ce concours, Nous allons créer un modèle pour segmenter automatiquement l'estomac et les intestins sur les images IRMs. Les IRMs proviennent de vrais patients atteints de cancer qui ont subi 1 à 5 IRMs à des jours différents au cours de leur radiothérapie.
Les participants au challenge ont été invités, du 14 avril au 14 juillet 2022, à proposer des modèles de machine learning permettant de localiser automatiquement les intestins et l’estomac sur les clichés d’IRM. Pour évaluer les modèles le coefficient de Dice moyen et la distance de Hausdorff 3D ont été retenus.

# Données
Les organisateurs ont mis à disposition des participants un [jeu de données](https://www.kaggle.com/competitions/uw-madison-gi-tract-image-segmentation/data) comportant des clichés d’IRMs de vrais patients atteints de cancer. Ces clichés sont accompagnés d’annotations permettant de localiser sous formes de masques encodés avec le format RLE, les intestins et l’estomac. Chaque cas de ce concours est représenté par plusieurs ensembles de tranches d'analyse (chaque ensemble est identifié par le jour où l'analyse a eu lieu). 

# modèle 
* Le modèle 1 ("baseline") utilise l'architecture "U-NET" pour segmenter les organes sur les clichés IRMs. Des couches de "Dropout" et de "BatchNormalisation" ont été ajoutées dans l'architecture permettant d'améliorer les métriques. 
* le modèle 2 reprends le modèle de référence avec l'ajout d'une étape d'encodage et de décodage dans l'architecture et une résolution d'image en entrée de modèle plus importante d'un facteur 2, passant de 128x128x3 à 256x256x3. Ces modifications ont permis d'améliorer légèrement les métriques.
* Le modèle 3 (modeèle final) reprends les améliorations du modèle précédent avec l'ajout de la méthode de "Data Augmentation". Ceci a permis également d'améliorer les métriques


modeèle final : 
* Part 1: [Train --> uwmgtis Keras train_03](https://www.kaggle.com/code/benoitdacosta/uwmgtis-keras-train-03) 
* Part 2: [Inference --> uwmgtis Keras infer_03](https://www.kaggle.com/code/benoitdacosta/uwmgtis-keras-infer-03)

Ancien modèle : 
* Part 1: [Train --> uwmgtis Keras train_01](https://www.kaggle.com/code/benoitdacosta/uwmgtis-keras-train-01) 
* Part 2: [Inference --> uwmgtis Keras infer_01](https://www.kaggle.com/code/benoitdacosta/uwmgtis-keras-infer-01)
* Part 1: [Train --> uwmgtis Keras train_02](https://www.kaggle.com/code/benoitdacosta/uwmgtis-keras-train-02) 
* Part 2: [Inference --> uwmgtis Keras infer_02](https://www.kaggle.com/code/benoitdacosta/uwmgtis-keras-infer-02)

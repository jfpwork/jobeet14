jobeet14
========

symfony 1.4 - jobeet

this projet is following the french tutorial for Symfony 1.4 / Doctrine

URL > http://symfony.com/legacy/doc/jobeet/1_4/fr?orm=Doctrine 


Le modèle de données
*********************

Créer le fichier du schéma
---------------------------

DIR > config/doctrine/schema.yml


Créer la base de données
------------------------
$ php symfony configure:database "mysql:host=localhost;dbname=jobeet" root mYsEcret


Construire les modèles à partir des fichiers du schéma
-------------------------------------------------------
$ php symfony doctrine:build --model
DIR > lib/model/

3 classes / table : 
	- X : 
		- Un objet de cette classe représente un seul enregistrement de la table
		- La classe est vide par défaut
	- BaseX :
		- La classe parent de X
		- doctrine:build --model => classe écrasée
	- XTable : 
		- La classe définit des méthodes qui renvoient surtout des collections d'objets de X 
		- La classe est vide par défaut


Générer et insérer le code SQL
-------------------------------
$ php symfony doctrine:build --sql
DIR>  data/sql/


Créer les tables dans la base de données
----------------------------------------
$ php symfony doctrine:insert-sql


Les données initiales
---------------------
$ php symfony doctrine:data-load
DIR > data/fixtures/*.yml

La tâche doctrine:build --all --and-load est un raccourci pour 
	la tâche doctrine:build --all suivie par la tâche doctrine:data-load.
	
Le voir en action dans le navigateur
------------------------------------
$ php symfony doctrine:build-forms
$ php symfony cache:clear
$ php symfony doctrine:generate-module --with-show --non-verbose-templates frontend job JobeetJob

génère un module job dans l'application frontend pour le modèle JobeetJob
# Journal de bord : Observatoire des métiers et de l'emploi
## Jour 1: Initialisation du projet

- Création d'un projet Data consacré à l'analyse du marché et de l'emploi en France.

L'objectif est de construire progressivement un observatoire permettant d'explorer les métiers, les compétences, les secteurs, les territoires et les tensions du marché du travail.

- Création du dépôt Github et de la branche de travail (audrey)
- Mise en place de notre première architecture du projet
- initation du contenu des différents fichiers: README.md, requirements.txt, journal de board.
- Mise en place de notre environnement virtuel de travail (.venv)
- Importation des différentes librairies nécessiare pour ce projet dans notre .venv.
- Identifier et documenter les sources des données publiques permettant de construire l'observatoire.
- Les principales sources de données envisagées sont les données publiques de :

France Travail : l'API du Marché du travail
l'API ROME 4.0 : Référentiel métiers utilisé pour décrire les métiers, leurs activités, les compétences.
DARES  : Statistiques emploi        

Nous observons que l'API Marché du Travail est particulièrement intéréssante pour notre travail.

## Jour 2 : Auditons les sources des données que nous utiliserons pour notre analyse
- Le jeu des offres d'emplois diffusées à France Travail qui contient les offres accessibles aux demandeurs d'emplois et qui proviennent des employeurs et des sites patenaires.

pour y avoir accès suivre le chemin data.gouv.fr -> mettre dans l'onglet France Travail -> Offres d'emploi diffusées à France Travail mais tout ce que nous avons ne sont que les données statistiques sur le nombre de contrat par trimestre. Ce qui n'est pas ce que nous voulons.

- Nous allons donc aller sur  https://francetravail.io/inscription afin de créer un compte et demander l'accès à l'API
- Après avoir créer le compte, nous avons créer une application et son descriptif : on aura Compte -> application -> API

- l'identifiant et la clé sécrète m'ont été générés et ils ne doivent pas être publier ou accessibles ouvertement. Il faut les garder en toute sécurité.

Nous avons sélectionner et enrégistrer pour un début ces 2 API:
    - API Marché du Travail v1 qui nous servira pour les statistiques du marché de l'emploi.
    - ROME 4.0 - Métiersv1 qui nous permettra de travailler avec les métiers et les codes du Répertoire Opérationnel des Métiers et des Emplois (ROME)
Les 2 API sont rattachées à mon application.
- Nous avons créer le fichier .env où nous allons stocker notre identifiant et notre clé 
- nous avons récupérer et examiner le fichier des offres de France Travail.



## prochainement
- Nous allons Auditer ces sources en comparant celles qui sont pertinentes, évolutives, accessibles, documenter et publiables.
- Puis nous choisirons la source principale après comparaison des données disponibles et de leur intérêt analytique.



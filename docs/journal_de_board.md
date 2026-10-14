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
- Nous avons créer le fichier .env/ où nous allons stocker notre identifiant et notre clé 
- Vérification de la documentation disponible : nous allons utiliser l'authentification OAuth 2.0 de France Travail avec les identifiants de mon application.
- Installer python-dotenv pour sécuriser les secrets et API keys donc permet surtout de charger les variables sensibles depuis .env sans les écrire directement dans le code. 
- Nous allons faire un test API pour récupérer la données d'un indicateur depuis l'API du marché du travail.
    - nous avons chercher comment construire l'URL d'un token

## Jour 3 et 4: 
- nous avons créer le fichier `test_api.ipynb` pour récupérer et construire l'API du marché de travail v1 mais l'erreyr persiste 403 à cause d'un manque d'autorisations spécifiques. 
- nous avons fait un courriel au service technique franetravail.io afin d'avoir de l'aide et nous attendons leur retour.

## Jour 6 Définition des objectifs métier

- Création du document `docs/objectifs_metier.md` pour formaliser le contexte, la problématique et les objectifs de l'Observatoire de l'emploi.
- Définition des principales questions métier : répartition des offres par métier et territoire, évolution des offres dans le temps et exploration des éventuelles tensions de recrutement.
- Identification des principaux indicateurs à étudier, sous réserve de la disponibilité des données.

### Difficultés rencontrées

* Les demandes d'accès à l'API Marché du travail de France Travail renvoient une erreur HTTP 403, alors que l'authentification OAuth fonctionne et fournit un jeton d'accès.
* Un courriel a été envoyé à France Travail pour obtenir des précisions sur les autorisations et les éventuelles conditions d'accès aux ressources de l'API.

### Décisions prises

* Poursuivre la préparation du projet pendant l'attente de la réponse de France Travail.
* Préparer la structure des données et les étapes de traitement sans considérer les données comme disponibles avant d'avoir confirmé leur accès.
* Étudier, si nécessaire, des sources publiques alternatives.

## Jour 7: Identifier les sources de données 
- Résoudre les difficultés d’accès à l’API Marché du travail 
- Identifier et explorer les indicateurs du Marché du travail
- identifier la structure nécessaire pour extraire les statistiques sur les offres d’emploi
- Consultation du référentiel GET /v1/referentiel/details-indicateurs pour étudier l’indicateur OFF_1
- Analyse des paramètres disponibles : périodes trimestrielles, types de territoires, types d’activités et nomenclatures.
- Identification de 252 croisements autorisés, dont 36 pour le territoire régional (REG).
- Retrouvaille et reconstruction de la requête POST /v1/indicateur/stat-offres avec un corps JSON.
- Test de la requête avec un jeton OAuth valide et obtention d’une réponse HTTP 200.
- Test effectué porte sur le métier « Agent / Agente d’entretien des espaces verts » (ROME A1203), en Nouvelle-Aquitaine (REG, code 75), pour le deuxième trimestre 2026.

### Difficultés et points de vigilance
- La documentation consultée ne permettait pas de retrouver facilement le format de la requête statistique.
- Le champ codeNomenclature doit être pris en compte pour distinguer les offres France Travail (PE) de toutes les offres (TOFF).
- Le test reste ponctuel : il ne constitue pas encore le jeu de données officiel du projet.

### prochainement

- Vérifier la cohérence des paramètres et des résultats retournés.
- Définir le périmètre de l’extraction : territoires, métiers et périodes.
- Structurer les réponses JSON en DataFrame avec pandas.
- Contrôler les données obtenues avant leur enregistrement dans data/raw/.
- Documenter la source, les paramètres de collecte et les limites des données dans le README.



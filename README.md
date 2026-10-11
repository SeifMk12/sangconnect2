Atelier 2 questions:

Activité 1:
1.Retrouver cette fonction dépend de l'organisation du projet, mais cela peut s'avérer complexe si le code n'est pas clairement structuré et documenté.

2.Si plusieurs fichiers ont besoin de getCentreById(), cela risque d'entraîner une duplication du code ou des difficultés de synchronisation entre les différentes versions.

3.Isoler cette fonction dans un fichier séparé permet de centraliser sa logique, d'éviter les redondances et de simplifier grandement sa maintenance.

4.Le rôle d'un module est de regrouper des fonctionnalités cohérentes pour structurer l'application, encourager la réutilisabilité du code et améliorer la lisibilité globale.

Activité 3:
1.Les accolades lors de l’import servent à effectuer un import nommé, ce qui permet de cibler précisément une ou plusieurs fonctions ou variables spécifiques exportées par un fichier.

2.Il est tout à fait possible d’exporter plusieurs fonctions depuis un même fichier en utilisant des exportations nommées.

3.Regrouper plusieurs fonctions liées dans un module permet d'organiser logiquement le code, d'encourager sa réutilisabilité et de simplifier sa maintenance.

Activité 4:
1.« Fin » apparaît avant « Opération terminée » car setTimeout() est une opération asynchrone qui décale son exécution, permettant au code synchrone situé après de s'exécuter immédiatement.

2.Le programme n'est pas bloqué pendant ces deux secondes, car JavaScript utilise un modèle non bloquant qui laisse le thread principal libre de traiter d'autres instructions.

3.L’opération programmée avec setTimeout() représente une tâche différée (ou asynchrone) qui sera exécutée une fois le délai imparti écoulé et la pile d'exécution libérée.

4.Ce comportement est intéressant pour un serveur car il lui permet de gérer de multiples requêtes simultanées de manière fluide sans paralyser ses ressources en attendant qu'une seule tâche se termine.

Activité 5:
1.Au début, la Promise contient un état « en attente » (pending) ainsi qu'une valeur initiale indéfinie en attendant que l'opération asynchrone soit résolue ou rejetée.

2.resolve() permet de changer l'état de la Promise de « en attente » à « tenu » (fulfilled) et de lui transmettre le résultat de l'opération réussie.

3.reject() sert à faire passer l'état de la Promise à « rejeté » (rejected) en transmettant une erreur ou un motif d'échec.

4.Après une seconde, le délai de la fonction asynchrone s'écoule, déclenchant l'exécution du resolve() ou du reject() programmé.

5.On utilise .then() pour récupérer et traiter le résultat renvoyé par la Promise une fois que celle-ci a été résolue avec succès.

Activité 6:
1.On utilise reject() pour signaler qu’une opération asynchrone a échoué en transmettant un motif d’échec ou une erreur.

2.Le rôle de .catch() est de capturer et de traiter spécifiquement les erreurs survenues lors de l'exécution d'une chaîne de Promesses.

3.Une valeur retournée correspond au résultat valide d'une opération réussie, tandis qu'une erreur indique un dysfonctionnement ou un échec qui interrompt le flux normal.

4.La gestion des erreurs est importante dans une API backend pour éviter les plantages du serveur, renvoyer des codes de statut HTTP appropriés et garantir la stabilité du service face aux imprévus.

Activité 7:
1.Le mot-clé async indique qu'une fonction est asynchrone et qu'elle retourne automatiquement une Promise.

2.Le mot-clé await permet de suspendre l'exécution d'une fonction asynchrone jusqu'à ce que la Promise associée soit résolue.

3.await ne bloque pas tout le serveur car il libère le thread principal, permettant de continuer à traiter d'autres requêtes ou tâches pendant l'attente.

4.Si la Promise est rejetée, await déclenche une exception qui peut être interceptée à l'aide d'un bloc try...catch.

Activité 8:

1.Le rôle de try est de regrouper un bloc de code susceptible de générer une erreur afin de surveiller son exécution de manière sécurisée.

2.Le rôle de catch est de capturer et de traiter l'erreur si une exception survient dans le bloc try associé.

3.La variable qui contient l’erreur est celle passée en paramètre du bloc catch (souvent nommée error ou err).

4.Ne pas laisser les erreurs asynchrones sans traitement est crucial pour éviter des plantages silencieux, des comportements imprévisibles et pour assurer le débogage ainsi que la stabilité de l'application.

Activité 9:
Les données sont désormais stockées dans un fichier persistant ou une base de données gérée de manière isolée de la logique applicative.

Ce fichier est appelé repository car son rôle exclusif est de centraliser et d'encapsuler toutes les opérations d'accès et de manipulation des données.

Le repository ne connaît pas HTTP, ce qui lui permet de rester totalement indépendant du protocole web utilisé.

Le repository ne connaît ni req ni res, car ces objets appartiennent exclusivement à la couche de gestion des requêtes et des réponses HTTP du serveur.

Cette séparation est intéressante car elle respecte le principe de séparation des préoccupations, facilitant la maintenance, la réutilisabilité du code et les tests unitaires.

Activité 10:

Le rôle du service est d'encapsuler et de traiter la logique métier de l'application en orchestrant les actions nécessaires entre les requêtes et les données.

Le service utilise le repository pour accéder aux données et les manipuler sans avoir à se soucier des détails techniques de leur stockage ou de leur persistance.

Le service ne manipule pas directement res car il est totalement découplé du protocole HTTP et se concentre exclusivement sur les règles et les traitements métier.

Une règle métier doit être placée dans le service, car c'est la couche dédiée à la logique, aux calculs et aux décisions de l'application.

Séparer le service du repository permet de découpler la logique métier de l'accès aux données, ce qui facilite grandement la testabilité, la maintenance et l'évolution du code.

Activité 11:

Le rôle du contrôleur est de faire l'interface entre le protocole HTTP et la logique applicative en récupérant les requêtes et en renvoyant les réponses appropriées.

Le contrôleur connaît HTTP car sa responsabilité principale est de manipuler directement les objets req et res pour dialoguer avec le client.

Il appelle le service pour lui déléguer le traitement des règles métier et garder son propre code centré uniquement sur la gestion des requêtes web.

Le service ne doit pas appeler sendJson() car il est totalement indépendant du protocole HTTP et ignore tout de la structure des réponses à envoyer au client.

L’erreur « Centre introuvable » est gérée au niveau du service (qui la lève lorsqu'un élément est absent) puis interceptée par le contrôleur pour renvoyer le code de statut HTTP adéquat.

Activité 12:
Le rôle de handleCentreRoutes() est d'analyser l'URL et la méthode de la requête entrante pour l'aiguiller vers la fonction de contrôle correspondante.

Cette fonction retourne true ou false pour indiquer au routeur principal si la route a été reconnue et traitée avec succès.

match[1] représente le premier groupe de capture d'une expression régulière, qui correspond ici à l'identifiant (ID) du centre extrait de l'URL.

On utilise Number() pour convertir l'ID extrait de l'URL (qui est une chaîne de caractères) en valeur numérique afin d'effectuer une recherche et une comparaison fiables.

La route /api/centres/1 doit être distinguée de /api/centres car la première cible une ressource spécifique via son identifiant tandis que la seconde concerne l'ensemble de la collection.

Activité 14:
La couche qui reçoit la requête HTTP en premier est le contrôleur (via le routeur), qui se charge de capter les requêtes entrantes.

La couche qui contient les données est le repository, qui centralise et gère toute la persistance et l'accès aux informations.

La couche qui contient la logique métier est le service, où sont concentrés tous les traitements et règles de gestion de l'application.

La couche qui produit la réponse HTTP est le contrôleur, qui formate et renvoie le résultat final au client via l'objet res.

Il est tout à fait possible de remplacer les données fictives par une vraie base de données sans modifier les routes ni la logique, grâce au découplage strict permis par le repository.

Activité 15:
Cette vérification doit se trouver dans le service car elle constitue une règle métier liée à la validation des données, tandis que le repository se consacre exclusivement à l'accès et à la manipulation brute des données.

Activité 16:
La couche qui génère l’erreur est le repository (findAll()), qui simule ici une défaillance de la base de données.

La couche qui la récupère est le contrôleur (ou le service selon la structure, mais généralement interceptée au niveau du contrôleur via un bloc try...catch) pour l'aiguiller vers la réponse HTTP adéquate.

Le code HTTP qui doit être retourné est le code 500 Internal Server Error, car il s'agit d'un problème technique inattendu du côté du serveur.

Il ne faut pas retourner le message technique complet au client pour des raisons de sécurité (évitant de révéler des informations sensibles sur l'architecture interne ou la pile technologique) et de lisibilité pour l'utilisateur final.

Activité 18:

Question 1 : async function indique qu'une fonction est asynchrone et retourne automatiquement une Promise, contrairement à une fonction classique qui s'exécute de manière synchrone.

    Question 2 : await suspend l'exécution de la fonction jusqu'à ce que la Promise soit résolue pour obtenir directement sa valeur, tandis que .then() utilise une approche par chaînage de rappels (callbacks).

    Question 3 : Les trois états principaux d'une Promise sont en attente (pending), résolue (fulfilled) et rejetée (rejected).

    Question 4 : try/catch permet de capturer et de gérer proprement les erreurs et rejets de Promesses survenant lors de l'utilisation de await.

    Question 5 : Éviter de tout regrouper dans server.js permet d'empêcher le code monolithique (spaghetti code), garantissant ainsi une meilleure lisibilité, maintenabilité et testabilité.

    Question 6 : Le repository a pour unique responsabilité de gérer l'accès, le stockage et la manipulation brute des données.

    Question 7 : Le service a pour responsabilité d'encapsuler et d'exécuter la logique métier ainsi que les règles de gestion de l'application.

    Question 8 : Le contrôleur a pour responsabilité de faire l'interface avec le protocole HTTP en récupérant les requêtes (req) et en renvoyant les réponses (res).

    Question 9 : Cette architecture facilite les tests grâce au strict découplage des responsabilités, permettant de tester chaque couche (service, repository, contrôleur) de façon isolée.

    Question 10 : Seul le repository est modifié ou remplacé pour interagir avec une base de données PostgreSQL, sans que les services ou les contrôleurs n'aient besoin d'être réécrits.


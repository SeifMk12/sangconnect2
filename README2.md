Atelier 1 questions:
activité 1:
1. v22.22.1
2. 9.2.0
3.Chemin de l'exécutable Node.js : Par défaut sous Windows, l'exécutable (node.exe) se trouve généralement dans le dossier C:\Program Files\nodejs\ ou dans le dossier AppData de votre utilisateur.

4.Chemin de l'exécutable npm : Le fichier de commandes et les modules associés de npm se trouvent généralement dans le même répertoire d'installation de Node.js (C:\Program Files\nodejs\) ou dans le dossier global des packages npm de votre profil utilisateur.

activité 2:
Le champ name : Définit le nom unique du projet ou du module (obligatoire pour npm).

Le champ version : Indique la version actuelle (selon le versionnage sémantique, ex: 1.0.0).

La section scripts : Contient les raccourcis de commandes (ex: npm start, npm run dev).

Importance dans un backend : Centralise la gestion des dépendances et assure la portabilité du projet.

Code vs Configuration : Le code gère la logique métier (ce que fait l'application), tandis que la configuration gère l'environnement et les outils (comment elle s'exécute).

"type": "module" : Permet à Node.js d'utiliser les modules ECMAScript (ESM) à la place du système historique CommonJS (require).

Importer un module ES : import { maFonction } from './module.js'; (ou import nom from './module.js';).

Exporter une fonction : export function maFonction() {} ou export { maFonction }; (ou export default maFonction;).

Extensions .js obligatoires : Node.js l'exige avec le système ESM pour résoudre correctement les chemins des fichiers locaux.

activité 3:
Rôle d’un éditeur de code : Permet d'écrire, modifier et organiser le code source avec de la coloration syntaxique et de l'autocomplétion.

Éditeur vs Environnement d’exécution : L'éditeur sert uniquement à rédiger le code, tandis que l'environnement d'exécution (ex: Node.js) sert à l'exécuter et le faire fonctionner.

Intérêt de l'ouverture de dossier dans VS Code : Offre une vue d'ensemble du projet, facilite la navigation entre les fichiers, la gestion des imports et la portée de la recherche.

Intérêt du formatage automatique : Harmonise le style du code, améliore sa lisibilité et évite de perdre du temps sur l'alignement ou l'indentation.

activité 4:
const vs let : const déclare une valeur dont la référence ne peut pas être réassignée, tandis que let permet de modifier (réassigner) la valeur par la suite. Toutes deux ont une portée de bloc.

Accents graves (`...`) : Ils permettent de définir des chaînes de caractères littérales (template literals), autorisant le texte sur plusieurs lignes et l'intégration directe de variables.

Rôle de l’interpolation ${...} : Permet d'insérer et d'évaluer directement des variables ou des expressions JavaScript au cœur d'une chaîne de caractères, évitant la concaténation lourde avec des +.

Préférer const : Empêche les réassignations accidentelles, sécurise le code et indique explicitement aux autres développeurs que la valeur est prévue pour rester fixe.

activité 5:
http.createServer() : Crée un objet serveur HTTP capable d'écouter les requêtes entrantes et d'y répondre.

Fonction (req, res) : Exécutée à chaque fois qu'une requête HTTP est reçue par le serveur.

req vs res : req (request) contient les informations envoyées par le client, tandis que res (response) permet de formuler et d'envoyer la réponse.

res.writeHead() : Définit les en-têtes HTTP (code de statut comme 200, type de contenu comme text/plain).

res.end() : Termine l'envoi de la réponse et envoie le tout au client.

Port 3000 déjà utilisé : Une erreur EADDRINUSE survient et le serveur refuse de démarrer.

Arrêter le serveur : En effectuant un Ctrl + C dans le terminal.

activité 6:
Propriété pour la méthode HTTP : req.method

Propriété pour l’URL demandée : req.url

Valeur de req.method dans un navigateur : "GET" (lors du chargement standard d'une page).

Valeur de req.url pour /api/health : "/api/health"

activité 7:
Utilisation de return : Permet d'interrompre l'exécution de la fonction pour éviter d'envoyer plusieurs réponses pour une seule requête (ce qui provoquerait une erreur ERR_HTTP_HEADERS_SENT).

Position de la réponse 404 : Car le serveur lit les routes de haut en bas ; placée au début, elle intercepterait toutes les requêtes avant les routes valides.

URL non définie : La requête reste en attente (timeout) ou le serveur retourne une réponse non gérée (souvent sans fin, ou une erreur 404 si prévue).

URL identique avec plusieurs méthodes : Oui, c'est tout à fait possible et courant (ex: GET /users pour lister, POST /users pour créer), car le routage s'appuie sur la combinaison de l'URL et de la méthode HTTP.

activité 8:
Utiliser return après sendJson() : Interrompt l'exécution de la fonction pour empêcher d'autres instructions de s'exécuter et d'envoyer une seconde réponse par erreur.

Si plusieurs réponses sont envoyées : Node.js lève une erreur critique (ERR_HTTP_HEADERS_SENT) car le protocole HTTP n'autorise qu'une seule réponse par requête.

Code de statut pour une réussite : Le code 200 (OK), ou parfois 201 (Created) lors de la création d'une ressource.

Retourner un code 404 : En configurant explicitement le statut dans la réponse (ex: res.writeHead(404, ...) ou en passant 404 à votre fonction d'envoi).

activité 9:
Code pour /api/health : Généralement 200 (OK) pour indiquer que le serveur fonctionne correctement.

Code pour une route inexistante : Le code 404 (Not Found).

Pourquoi éviter le code 200 sur une route inexistante : Pour ne pas induire en erreur le client ou les systèmes de surveillance en leur faisant croire que la ressource demandée existe.

Code HTTP vs Contenu JSON : Le code HTTP indique le statut global de la requête pour le protocole, tandis que le contenu JSON fournit les détails ou les messages explicatifs.

activité 10:
Objet de processus : L'objet global process.

Propriété de version : process.version (ou process.versions.node).

Séparation des versions : L'application a son propre cycle de développement et de versionnement, indépendant du moteur d'exécution Node.js qui la fait tourner.

Autres informations : Les arguments de ligne de commande (process.argv), les variables d'environnement (process.env), ou l'utilisation de la mémoire (process.memoryUsage()).

activité 11:
Propriété pour la méthode HTTP : req.method

Propriété pour l’URL : req.url

GET vs POST : GET récupère des données (sans modifier l'état), tandis que POST envoie et crée de nouvelles données sur le serveur.

Pourquoi tenir compte de la méthode : Permet de dissocier l'action à réaliser sur une même ressource (ex: afficher un profil vs le mettre à jour).

URL et plusieurs méthodes : Oui, tout à fait (ex: GET /api/users pour lister et POST /api/users pour créer).

activité 12:
Content-Type obligatoire : Non, mais c'est indispensable pour indiquer au client comment interpréter les données reçues (ex: JSON, texte brut).

Cohérence des codes HTTP : Oui, ils doivent refléter fidèlement le résultat (ex: 200 pour un succès, 404 pour une erreur) pour que le client comprenne l'état de la requête.

Arrêt du serveur : Le client subit une erreur de connexion (ex: ECONNREFUSED), car aucun processus n'écoute plus sur le port.

Tester routes existantes et inexistantes : Permet de valider à la fois le bon fonctionnement des fonctionnalités normales et la gestion correcte des cas d'erreur (404).

Intérêt de l'option -i (ex: avec curl) : Affiche les en-têtes HTTP (headers) de la réponse en plus du contenu (body), ce qui permet de vérifier le code de statut et le type de contenu.

activité 13:
Rôle de la route de santé : Permet de s'assurer rapidement que le serveur est démarré et capable de répondre (souvent utilisée par les outils de monitoring).

Pourquoi elle doit être rapide : Pour éviter de surcharger le serveur et permettre des interrogations fréquentes sans impacter les performances.

Disponibilité vs Vérification complète : La disponibilité teste juste si le serveur tourne, tandis que la vérification complète teste aussi les dépendances critiques.

Vérifications supplémentaires : Tester la connexion à la base de données, l'état du système de cache, l'espace disque ou la mémoire disponible.

activité 14:
Rôle de server.js : Il sert de point d'entrée principal de l'application pour initialiser, configurer et lancer le serveur HTTP.

Si l'application possède 30 routes : Le fichier devient un monolithe géant, extrêmement long, illisible et difficile à maintenir.

Complexité des conditions if : Elles créent une complexité cyclomatique élevée, augmentent le risque d'erreurs de routage et rendent le débogage laborieux.

Séparer les routes : En créant des fichiers de routage dédiés par ressource (ex: un fichier pour les utilisateurs, un autre pour les produits) et en les important.

Responsabilités distinctes : Isoler le routage, la logique métier (contrôleurs), l'accès aux données (modèles/repositories) et la configuration (base de données, variables d'environnement).



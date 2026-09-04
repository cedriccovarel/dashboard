MYTOOLAPP + GOOGLE AGENDA DANS PLASH
====================================

Cette version n'utilise plus OAuth dans Mytoolapp.
Google Agenda est lu par un petit Google Apps Script exécuté avec ton compte.
Mytoolapp récupère ensuite seulement les prochains événements via une URL protégée par une clé privée.

ETAPE 1 - CREER LE CONNECTEUR
1. Va sur https://script.google.com/
2. Clique sur Nouveau projet.
3. Supprime le contenu de Code.gs.
4. Copie-colle le contenu du fichier Code.gs fourni dans ce pack.
5. Enregistre le projet sous le nom : Mytoolapp Agenda Connector.

ETAPE 2 - GENERER LA CLE ET AUTORISER L'AGENDA
1. En haut de l'éditeur Apps Script, sélectionne la fonction setupConnector.
2. Clique sur Exécuter.
3. Accepte les autorisations Google demandées.
4. Ouvre Journal d'exécution / Execution log.
5. Copie uniquement la valeur après : CLE_ACCES_MYTOOLAPP=
   Garde cette clé privée.

ETAPE 3 - DEPLOYER EN APPLICATION WEB
1. Clique sur Déployer > Nouveau déploiement.
2. Type : Application Web.
3. Exécuter en tant que : Moi.
4. Qui a accès : Tout le monde.
5. Clique sur Déployer.
6. Copie l'URL qui se termine par /exec.

IMPORTANT : si l'option "Tout le monde" n'est pas disponible, une règle de ton organisation Google Workspace bloque les applications Web anonymes. Dans ce cas cette méthode ne pourra pas fonctionner telle quelle dans Plash.

ETAPE 4 - CONFIGURER MYTOOLAPP
1. Mets le nouveau index.html sur GitHub Pages.
2. Ouvre Mytoolapp > Réglages.
3. Dans Connecteur Google Agenda :
   - URL du connecteur = URL Apps Script terminant par /exec
   - Clé d'accès = clé générée par setupConnector()
4. Clique sur Enregistrer puis Tester la connexion.

SECURITE
- Ne mets jamais la clé d'accès directement dans le code GitHub.
- Mytoolapp la stocke dans le stockage local du navigateur / de Plash.
- Toute personne possédant à la fois l'URL du connecteur et la clé peut lire les prochains titres/horaires/lieux renvoyés par le connecteur.
- Si tu penses que la clé a fuité, exécute resetAccessKey() dans Apps Script puis remplace la clé dans Mytoolapp.
- Le connecteur est lecture seule : aucune création, modification ou suppression de rendez-vous.

MISE A JOUR
Le widget se rafraîchit automatiquement toutes les 5 minutes et via le bouton ↻.

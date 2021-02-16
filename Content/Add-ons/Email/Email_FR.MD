### Email 
par Haulmont

### Dernière Version
0.2.0

### Mise-à-jour
2 sem.

### Version Supportée
v0.2

### Licence
Apache 2.0

### Ressources
Documentation
Bugtracker

### Tags
Features

### Coordonnées Composant

Copier

APERCU
L'addon permet d'envoyer des courriers électroniques.

### DESCRIPTION
* Envoi synchrone ou asynchrone. En cas d'envoi synchrone, le code d'appel attend que le message soit envoyé au serveur SMTP. En cas d'envoi asynchrone, le message est persisté dans la base de données et le contrôle est renvoyé immédiatement au code de l'appelant. L'envoi effectif est effectué plus tard par une tâche planifiée.

* Suivi fiable de l'horodatage de l'envoi du message ou des erreurs dans la base de données pour les modes synchrone et asynchrone.

* Interface utilisateur permettant de rechercher et de visualiser des informations sur les messages envoyés, y compris tous les attributs et le contenu du message, le statut de l'envoi et le nombre de tentatives.

### INSTALLATION
Pour inclure la fonctionnalité d'envoi de courrier électronique dans votre application, ajoutez les lignes suivantes à la section des dépendances de votre fichier build.gradle :


BUGTRACKER
GITHUB
FORUM
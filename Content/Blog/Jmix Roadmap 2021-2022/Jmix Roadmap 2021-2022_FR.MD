Roadmap Jmix 2021-2022
Tout d'abord, permettez-moi de vous souhaiter à tous une bonne année et félicitons-nous que 2020 soit enfin terminée! Ce fut une année difficile pour le monde et j'espère que 2021 nous apportera des nouvelles plus positives.
Dans cet article, je voudrais récapituler les résultats de 2020 pour notre équipe et partager nos plans pour la prochaine 2021.
Nous avons presque gardé le silence sur nos projets de l'année dernière. J'espère que maintenant, avec la sortie de Jmix, vous comprendrez pourquoi. La quantité de changements et les travaux de R&D signifiaient qu'il était tout simplement trop difficile de faire des promesses. Nous devions être flexibles et évoluer à un rythme confortable.
Mais même si la majeure partie de l'équipe était concentrée sur Jmix, nous avons également fourni des fonctionnalités intéressantes pour CUBA:
-	Prise en charge de Kotlin et rôles de sécurité au moment du design dans CUBA 7.2
-	Le nouveau thème Helium avec un éditeur de thème visuel
-	Prise en charge de React Native dans le générateur frontend
-	CUBA SDK, pour vous aider à développer vos projets dans des environnements isolés
Bien sûr, il y eu des centaines d'autres améliorations dans Studio, le framework et le générateur frontend.
Du côté de la communauté, nous avons ajouté des versions italienne et française du site Web et du forum. Nous avons également déployé un formulaire simplifié pour les demandes de licence académique, de sorte que de plus en plus d'universités utilisent CUBA pour leurs cours de logiciels d'entreprise!
Nous accueillons de nouvelles grandes marques parmi nos clients, notamment Ingenico et Sber - la plus grande banque d'Europe de l'Est. Sber a signé un accord à grande échelle pour adapter et utiliser CUBA Studio pour accélérer le développement d'applications pour les utilisateurs internes dans toute la banque.
Que se passe-t-il en 2021?
La release récente de Jmix nous fournit une base solide, nous envisageons donc l'avenir avec confiance. Nous avons des plans ambitieux et actuellement nous agrandissons l'équipe pour les soutenir. Nous prévoyons que plus de 50 développeurs travailleront sur Jmix d'ici la fin de l'année prochaine!
Notre première priorité est bien entendu la sortie d'une version stable de Jmix. Cela comprend une documentation complète, la migration des modules complémentaires restants et des tests approfondis. Nous visons le T2 2021 pour terminer cette étape.
Les nouvelles fonctionnalités sont décrites ci-dessous. N'oubliez pas que beaucoup d'entre elles nécessitent encore de la R&D, alors ne me demandez pas les détails de leur mise en œuvre. Néanmoins, cela devrait vous donner suffisamment d’indices sur notre cible, et j’espère que cela vous plaira!


Frontend
Maintenant que notre backend CUBA est reconstruit autour de Spring Boot, la technologie côté serveur la plus utilisée pour les projets d'entreprise, il est temps de se concentrer sur le frontend. Pour être honnête, le moment est venu il y a quelques années, lorsque Vaadin 8 est devenu obsolète. Cependant, nous gardons toujours à l'esprit la pérennité et la compatibilité rétroactive. Malheureusement pour nous, le monde des frameworks web change si vite qu'il était difficile de faire un pari sûr. Même l'ensemble des composants de Vaadin continue d'évoluer activement dans les dernières versions.
Nous avons donc dû conserver l'interface utilisateur de Vaadin 8 qui, avec toutes ses limites, "fonctionne tout simplement". Néanmoins, l'équipe du frontend a exploré de nouvelles approches dans le module de portail et récemment dans le SDK TypeScript et le générateur de frontend React. Vous pouvez déjà échafauder des clients React et React Native, bien que ce soit encore un processus beaucoup plus compliqué et manuel comparé à l'interface utilisateur basée sur Vaadin. Vous pouvez brancher n'importe quel autre framework web à l'aide du SDK Typescript bien sûr, mais c'est un processus encore plus manuel.
Quoi qu'il en soit, la quête est terminée. Nous pensons que React est là pour rester assez longtemps. Ainsi, l'objectif principal pour 2021 est de pousser le client React UI pour le rendre aussi productif et facile à utiliser que celui de Vaadin. Naturellement, cela suppose un support complet dans le Studio, y compris un concepteur visuel avec des modèles d'écran, le rechargement à chaud, des thèmes et une suite complète de composants, au moins équivalents à leurs homologues de Vaadin. Comme d'habitude, nous essaierons d'abstraire (et non d'isoler) les développeurs des subtilités de l'écosystème de la JS dans la mesure du possible. Les avantages sont évidents : une interface utilisateur plus rapide et plus évolutive avec des options de personnalisation plus larges et un soutien massif de la communauté.
Cependant, il y a aussi un prix à payer. Une compréhension de base du Typscript, du HTML et du CSS sera nécessaire. Vous aurez également besoin du logiciel commercial IntelliJ IDEA Ultimate pour travailler confortablement avec Typescript. Nous prévoyons de publier une version de Studio fournie avec ce logiciel.
Qu'adviendra-t-il de Vaadin ? Pas de soucis, son histoire continue. Nous pensons toujours qu'il s'agit d'un excellent choix dans de nombreux scénarios. Il est parfait pour les développeurs qui n'ont pas beaucoup d’appétence pour le web. À moins que vous ne vous attendiez à des dizaines de milliers d'utilisateurs ou à des réseaux à forte latence, il fera parfaitement l'affaire, et ces hypothèses sont valables pour la plupart des applications de back-office. Nous continuons à suivre les progrès des utilisateurs de Vaadin dans les dernières versions, et nous espérons pouvoir passer de la version 8 à l'une d'entre elles en 2022.
Qu'en est-il des applications mobiles ? Comme mentionné ci-dessus, nous prenons déjà en charge la génération de clients React Native, ainsi que le PWA dans le client React. En outre, nous avons lancé une R&D à petite échelle autour de Flutter, une technologie d'interface utilisateur très prometteuse soutenue par Google. L'objectif ultime de Flutter est de fournir une seule technologie d'interface utilisateur pour toutes les plateformes : mobile, web et même desktop. Cette technologie sera également beaucoup plus familière aux développeurs, tandis que son idéologie est similaire à celle de React : tout est un composant (alias Widget) et l'interface utilisateur est une fonction d'état.
Flutter gagne rapidement du terrain et est déjà le choix le plus populaire pour les applications mobiles multiplateformes, tandis que le support web est en bêta. Cependant, nous devons encore voir si elle se généralisera.
Notre principal cas d'utilisation - les applications "métier" - suppose une manipulation avec des graphiques de données complexes. Flutter et React nécessitent donc tous deux une API côté serveur à cet effet. Après quelques expériences, nous avons fini par utiliser GraphQL, qui semble s'adapter très naturellement et qui deviendra une partie commune aux deux clients.
Pour conclure, Jmix supportera plus d'options pour fournir des frontaux de toute taille et complexité, pour les plateformes web et mobiles, et pour ceux qui aiment et détestent JS :)
DevOps & Clouds
Pendant des années, nous avons considéré que la partie déploiement n’était pas de notre ressort et nous nous sommes concentrés uniquement sur l'aspect développement. Cependant, nous recevons de plus en plus de demandes pour simplifier le côté cycle de vie des applications également. Nous avons donc décidé de former une équipe "DevOps" au sein de Jmix pour s'occuper de ce problème. La tâche est conforme à notre approche générale : abstraire (mais - je le souligne encore une fois - ne pas isoler) le développeur des spécificités des technologies sous-jacentes comme Jenkins, Docker, Kubernetes, Terraform et fournir des outils visuels simples et pratiques pour configurer vos environnements et vos pipelines de CI/CD.
Cela signifie en pratique :
-	Configuration, génération et publication d'images Docker
-	Configuration des environnements, par exemple pour les tests et la production
-	Décrire l'infrastructure requise en utilisant un concepteur visuel - basé sur Kubernetes et Terraform
-	Configuration des pipelines de CI/CD
Nous prévoyons de nous appuyer sur des infrastructures nuagiques publiques - AWS pour commencer - pour une partie de ces fonctionnalités. Mais AWS (Azure, Alibaba, etc.) offre tellement plus que le simple hébergement de votre application, que ce serait un crime d'ignorer ses capacités ! Nous vous donnerons donc le choix de créer des applications véritablement natives du cloud en plus de bénéficier des services du cloud, notamment la base de données, le stockage de fichiers, l'authentification, la recherche plein texte, la surveillance, la journalisation, l'équilibrage de charge, etc.
Le but ultime est de vous fournir tout ce dont vous avez besoin pour déployer et exécuter vos applications dans le cloud avec un minimum d'efforts. Comme il s'agit d'une orientation absolument nouvelle, il est difficile de fixer des délais. Mais nous avons pour objectif de sortir une version bêta à la fin de 2021.

Outils
L'équipe du studio devient progressivement la plus importante de Jmix. En effet, chaque sujet, qu'il s'agisse du cloud ou du frontend, suppose un support d'outillage pertinent du côté du Studio. En outre, nous voulons introduire cette année quelques améliorations importantes :

-	De nouveaux concepteurs visuels - pour les requêtes JPQL et GraphQL, les messages de chaîne de caractères et les expressions logiques simples. J'espère que tout le monde aimera l'idée de ne plus avoir à écrire de chaînes JPQL !
-	Génération de code basée sur des modèles pour des actions typiques : ouvrir un écran, enregistrer/charger des données, afficher un message, invoquer un service, lancer un processus métier.
-	Configuration visuelle des rapports au moment de la conception.
-	Configuration des processus BPM au moment de la conception.

Remonter les sujets au niveau de la conception
Je voudrais souligner les deux dernières caractéristiques. Jusqu'à présent, les addons Reporting et BProc ne prenaient en charge que la configuration à l'exécution. D'un point de vue, c'est très bien : les rapports et les processus métier peuvent être configurés par des non-développeurs sans qu'il soit nécessaire de redéployer l'application. Cependant, cela a un certain nombre d'effets secondaires :
-	Si le modèle de données change, votre rapport ou processus opérationnel peut cesser de fonctionner, et vous ne le remarquerez même pas avant de l'avoir exécuté.
-	Les rapports et les processus opérationnels peuvent facilement se désynchroniser entre les différentes installations d'une application. Il se peut que vous testiez une version sur le banc d'essai, alors que quelqu'un modifie quelque chose en cours de production...
-	Pour les rapports complexes, un développeur doit utiliser des éditeurs de code d'exécution peu pratiques.
-	Lors de la configuration d'un processus métier, un développeur doit faire des allers-retours entre Studio et une application en cours d'exécution avec des redémarrages fréquents pour ajouter de nouveaux formulaires, services, etc.
Dans l'ensemble, cela devient un processus fragile et lourd, qui laisse beaucoup de place aux erreurs. C'est pourquoi nous avons décidé de mettre en place des concepteurs de BPM et de rapports dans Studio.
La possibilité de créer des rapports et d'éditer des processus métier au moment de l'exécution sera également préservée. Vous remarquerez peut-être que cela est conforme à la prise en charge récente du support de conception pour les groupes d'accès et les rôles de sécurité.
Pour les rapports, cela signifie qu'un rapport devient une classe Java, configurée à l'aide d'un assistant Studio. Cela permet la validation au moment de compilation, la possibilité de tester et de déboguer les rapports, ainsi que de meilleurs outils visuels.
Pour le BPM, l'idée est similaire. L'éditeur de conception permettra de tester et de déboguer les définitions de processus, ainsi que de créer de nombreuses choses en ligne : services, formulaires, gestionnaires, etc. Il en résultera un environnement de développement homogène, suffisamment puissant pour concurrencer certaines solutions BPMS du marché.
Comme beaucoup d'autres fonctionnalités, nous visons à sortir une version bêta de ces nouveaux outils à la fin de 2021.


Calendrier
Pour simplifier, voici le calendrier qui résume les releases prévues :
-	T2 2021 - version stable de Jmix
-	T4 2021 - version stable du client React
-	T4 2021 - versions bêta de :
o	Outils DevOps et Clouds
o	Prise en charge des applications natives dans le cloud
o	Rapports visuels et configuration des processus métiers à la conception
o	Autres outils dans Studio
-	T2 2022 - versions stables de tout ce qui a été publié au T4 2021
Il s'agit d'un calendrier ambitieux et certaines échéances pourraient être reportées, mais nous sommes déterminés à faire ce qui est possible pour le respecter.
L'avenir
La mise en œuvre de tout ce qui est décrit ci-dessus fera de Jmix une puissante plate-forme pour la création d'applications d'entreprise modernes, en fournissant :
-	Une interface utilisateur évolutive pour les applications mobiles et web
-	Capacités natives du cloud et automatisation complète du déploiement
-	Des outils plus visuels, facilitant le développement productif et la montée en charge
En fait, Jmix devrait devenir un concurrent puissant sur le marché florissant des plateformes d'application à faible code (LCAP). Avec au moins le même niveau de productivité, Jmix comble de nombreuses lacunes des LCAP, nous espérons donc qu'il y aura un vent nouveau sur ce marché controversé.
Jmix est conçu pour les développeurs et leur offre un environnement de travail confortable, alors que la plupart des LCAP sont destinées aux utilisateurs professionnels (alias les « citizen developers » ou développeurs ad hoc) et offrent donc une expérience de développement médiocre. Jmix est également suffisamment ouvert et flexible pour permettre de construire les applications les plus complexes comme les ERP - cela a été prouvé à plusieurs reprises par nos projets communautaires. Enfin, contrairement à la plupart des LCAPs, il est construit autour d'un cadre open source - ce qui signifie que vos applications sont vraiment les vôtres.
Nous espérons que cette combinaison de fonctionnalités de Jmix vous aidera à fournir de belles applications puissantes en un temps record, et qu'elle attirera de nouveaux membres dans notre communauté. Comme d'habitude, vos commentaires sont très appréciés - n'hésitez pas à laisser vos remarques sur le forum ou à nous contacter directement.




### Jmix - L'avenir de la plateforme CUBA

TL; DR

Jmix est le nouveau nom et la nouvelle version majeure de CUBA Platform. Il est maintenant en version préliminaire et nous prévoyons de publier une version stable au deuxième trimestre 2021. En voici les principales caractéristiques:
-	Spring Boot comme technologie de base
-	Décomposition en modules enfichables séparés (données, sécurité, audit, etc.)
-	Une nouvelle approche de définition des modèles de données
-	Processus de mise à jour de la base de données fondée sur Liquibase
-	Approche de déploiement utilisant les fonctionnalités de Spring Boot, permettant une meilleure intégration avec les environnements cloud.
Nous nous concentrerons sur la simplification du développement des clients ReactJS. En attendant, nous conserverons l'interface utilisateur actuelle du client basée sur Vaadin, qui deviendra l'un des modules Jmix.
La plate-forme CUBA sera supportée pendant encore longtemps et nous fournissons un chemin de migration vers Jmix via des API de compatibilité.


			Essayez jmix.io		Donnez votre avis

### Introduction
CUBA a commencé son chemin en 2008. Depuis lors, la plate-forme a traversé quelques étapes très importantes. Au début, c'était un framework interne sans documentation et encore moins d'API. C'était un outil à l'échelle de l'entreprise qui a permis à Haulmont de développer plus rapidement des applications commerciales.
En 2015, CUBA a été introduit dans le monde entier sous une licence propriétaire. Nous n'avons eu que quelques utilisateurs cette année-là - c'était embarrassant. Il est devenu évident que la politique de licence devait passer à l'open source.
2016 et 2017 ont été des années très productives lorsque nous avons élargi notre communauté. C'était un grand changement dans l'esprit, nous avons vu ce qui était bien et ce qui était mal.
En 2018-2019, nous avons commencé à introduire un niveau d'API clair et bien documenté et avons migré CUBA Studio sur IntelliJ. Tout cela a amené une communauté encore plus grande avec encore plus de retours. Nous sommes maintenant à l’orée de la prochaine mise à jour majeure. Voyons ce qui arrivera en 2021.

### Objectifs de la nouvelle version
Dans la prochaine version de CUBA Platform, nous voulions faire ce qui suit:
1.	Rapprochez l'expérience du développeur des frameworks les plus populaires. CUBA Platform utilise Spring, mais de nos jours, Spring Boot a presque conquis le monde. De nouveaux frameworks émergent - Micronaut et Quarkus. Ils ont tous des principes similaires à la base: une configuration simple via des fichiers .properties ou .yaml, une utilisation étendue des annotations et des facilités d’intégration de plugins. Nous voulons donc que CUBA offre une expérience similaire aux développeurs.
2.	Ne pas réinventer la roue. Depuis 2008, de nombreuses nouvelles bibliothèques et outils ont été développés. Ils sont désormais matures et peuvent être utilisés pour des applications de niveau entreprise. Nous voulions donc remplacer certains modules personnalisés de CUBA par des bibliothèques éprouvées au combat. À titre d'exemple - système de migration de base de données.
3.	Réduire la taille des applications CUBA. Lors de la création d'applications avec CUBA, vous n'avez pas toujours besoin de toutes les fonctionnalités telles que l'audit. Mais cela a toujours fait partie du noyau du framework, polluant la base de données avec des tables inutiles (pour votre cas particulier) et démarrant des services supplémentaires sur votre serveur d'applications. Donc, ce serait bien d'avoir la possibilité d'exclure certaines fonctionnalités de CUBA et de les inclure uniquement lorsque cela est nécessaire.
4.	Et le plus important - conserver une expérience fluide et une certaine vitesse de développement d'applications.
Et la première chose à partir de laquelle nous allons commencer est ...

### Le nom
«Que signifie CUBA?» - Il est difficile de compter combien de fois on nous a posé cette question. Honnêtement, c'était juste un nom ni trop long ni trop court pour nommer le premier paquet de notre framework interne en 2008. Si vous creusez dans le noyau de CUBA, vous pouvez également trouver des paquets «chile» et «bali».
En 2021, nous allons publier une nouvelle version majeure - et le nom changera. «CUBA» devient «Jmix». Ce nom est beaucoup plus simple à expliquer: «J» pour «Java» et «mix» pour les technologies et les frameworks se mélangent dans une seule application. Moins de questions, pas d'associations ni avec l'île bien connue ni avec le cocktail alcoolisé bien connu.
En fait, Jmix est la prochaine version majeure de CUBA avec des API et une approche de développement éprouvées. Et il s’agit toujours du même ensemble d'outils pratiques et de générateurs de code.
Le changement de nom est important, mais nous allons également vers un grand changement dans la ...

### Technologie de base
Au sens large, avec CUBA, nous copions certaines des approches Spring Boot. Notre propre stockage de session, sous-système de sécurité, authentification… et bien sûr déploiement. En outre, les modules complémentaires CUBA ont été introduits en réponse aux starters Srping avec leur propre mécanisme d'encapsulation et d'autoconfiguration.
Lorsque nous avons commencé le développement de CUBA en 2008, nous avons utilisé Spring «pur» dans le noyau du framework. Dans Jmix, nous utiliserons Spring Boot comme technologie de base.
L'utilisation de Spring Boot nous offre les avantages suivants:
1.	Meilleure expérience de développement. Actuellement, presque tous les développeurs Java connaissent Spring Boot. Avec Jmix, l'expérience de développement Spring Boot peut être pleinement utilisée, pas besoin d'apprendre un nouveau framework, juste de nouveaux starters.
2.	En ce qui concerne les starters, le noyau basé sur Spring Boot nous permet d'utiliser presque tous les starters existants dans notre framework. Ainsi, nous pouvons compter sur l'infrastructure existante avec un énorme soutien de la communauté et une énorme base de documentation.
3.	Et encore une chose: Spring Boot propose d'excellentes fonctionnalités en matière de déploiement, notamment une excellente prise en charge de la conteneurisation, prête à l'emploi.
En mentionnant les démarreurs Spring Boot, nous ne pouvons pas oublier les modules complémentaires CUBA. Et cela nous amène à ...
[image]

### La modularisation
De temps en temps, nous recevons des commentaires selon lesquels une application CUBA «vide» qui ne contient pas une seule ligne d'une logique métier a trop de tables et beaucoup d'éléments fonctionnels qui ne sont jamais utilisés.
Dans la 7e version du framework, nous avons commencé à extraire les fonctionnalités de base pour séparer les modules complémentaires. Fondamentalement, CUBA est un ensemble d'API, et cette approche a fourni suffisamment de flexibilité pour pouvoir continuer le processus de modularisation.
À partir de Jmix, vous pouvez utiliser les fonctionnalités du framework (par exemple audit, sécurité) séparément et presque indépendamment. Toutes les fonctionnalités sont désormais fournies en tant que démarreurs Spring Boot. Par exemple, il y avait une fonctionnalité d'audit dans CUBA, qui est maintenant un module séparé dans Jmix. Et ce module à son tour est divisé en modules Core et UI. Cela signifie que vous pouvez utiliser le moteur d'audit dans son ensemble ou utiliser uniquement le moteur principal et implémenter votre propre interface utilisateur personnalisée au lieu de celle fournie.
Certaines fonctionnalités telles que le healthcheck sont remplacées par un actionneur Spring Boot (voir la section «Ne pas réinventer la roue»).
Jmix fournit plus de 20 starters qui peuvent être utilisés. En voici quelques-uns ainsi que leur dépendances:

### Fonction	Starter	     Dépend de
Piste d’audit des entités	Audit	Data
Stockage de fichiers	Core	
Préférences utilisateurs	UI Persistence	Data
Présentations de table	UI Persistence	Data
Piste d’audit des entités	Audit UI	Audit, UI
Paramètres de configuration en base de données	Core	
Restauration des entités supprimées	Data tools	Data, UI
Sessions utilisateurs	Core	
Attributs dynamiques	Dynamic attributes	Data, UI
Instantané d’entité	Audit	Data
Entités liées	Advanced Data Operations	Data, UI
Editeur en masse	Advanced Data Operations	Data, UI

Comme vous pouvez le voir, le starter «données» est utilisé par presque tous les modules Jmix. Et ce n'est pas une surprise, car l'un des aspects les plus forts de la plate-forme CUBA était sa ...

### Couche d'accès aux données
Nous allons introduire de nombreux changements ici, en conservant toutes les meilleures parties de CUBA et en introduisant de nouvelles fonctionnalités qui vous aideront à être plus productif.
Avec tous ses avantages, le modèle de données de CUBA a un défaut fondamental: il est assez rigide. Par exemple, si vous aviez besoin d'une suppression logicielle (« soft delete »), vous deviez implémenter une interface appropriée (ou faire hériter votre entité de BaseEntity) et introduire des colonnes avec des noms prédéfinis dans la table correspondante. Toutes les clés primaires devaient être stockées dans la colonne avec le nom d'id si vous utilisiez la classe StandardEntity.
Cela a conduit à des limitations lors du développement de nouveaux modèles de données. Et cela a également causé beaucoup de problèmes lorsque les développeurs ont essayé d'implémenter des applications avec CUBA en utilisant un modèle de données existant. C'était le cas lorsque CUBA était utilisé comme framework moderne pour migrer à partir de frameworks hérités ou non pris en charge.
Dans Jmix, le modèle Entity devient plus flexible. Vous n'avez plus besoin d'étendre la classe StandardEntity ou d'implémenter l'interface Entity. Ajoutez simplement l'annotation @JmixEntity à une classe pour la rendre accessible au framework.
Nous avons décidé de déprécier les interfaces qui spécifient la fonctionnalité d'une entité. Elles sont remplacées par des annotations courantes. Par exemple, nous utilisons l'annotation @Version de JPA et @CreatedBy de Spring Boot au lieu des interfaces propriétaires Versioned et Creatable.
Cela nous permet de rendre le code plus explicite - vous pouvez savoir quelles fonctionnalités sont prises en charge par l'entité en regardant simplement son code.

@JmixEntity
@Table(name = "CONTACT")
@Entity(name = "Contact")
public class Contact {

   @Id
   @GeneratedValue(strategy = GenerationType.IDENTITY)
   @Column(name = "ID", nullable = false)
   private Long id;

   @Version
   @Column(name = "VERSION", nullable = false)
   private Integer version;

   @InstanceName
   @NotNull
   @Column(name = "NAME", nullable = false, unique = true)
   private String name;

   @LastModifiedBy
   @Column(name = "LAST_MODIFIED_BY")
   private String lastModifiedBy;

   @Temporal(TemporalType.TIMESTAMP)
   @LastModifiedDate
   @Column(name = "LAST_MODIFIED_DATE")
   private Date lastModifiedDate;

Les "Vues CUBA" sont désormais des "Plans de récupération". Le nouveau nom décrit bien mieux le but de ces artefacts.
La couche d'accès aux données de Jmix prend désormais en charge le chargement différé automatique des références. Donc, si vous choisissez de ne pas utiliser les plans de récupération pour filtrer les attributs locaux, vous n'obtiendrez plus jamais la fameuse «UnfetchedAttributeException».
Un autre élément important est le processus de génération et de mise à jour de la base de données. Nous avons décidé d'utiliser Liquibase au lieu du moteur de mise à jour de base de données personnalisé. Spring Boot est responsable de l'exécution de ces scripts. Ceci est un autre exemple de «ne pas réinventer la roue» - en utilisant un moteur bien connu avec une bonne documentation.
Liquibase peut générer des scripts de mise à jour indépendants de la base de données. Ainsi, si vous développez un produit ou un module complémentaire avec Jmix, vous n’avez pas besoin de générer des scripts de création de base de données pour tous les SGBDR possibles. Liquibase utilisera le dialecte SQL approprié en fonction d'un pilote JDBC. En même temps, il permet la personnalisation SQL spécifique à la base de données, si vous en avez besoin.
Et nous gardons la bonne vieille magie de CUBA. Chaque fois que vous modifiez une entité, Jmix Studio génère une entrée de script Liquibase pour refléter les changements.
À quoi pouvons-nous penser d'autre lorsque nous parlons de CUBA? Bien sûr, ses fonctions avancées de ...

### Sécurité
Dans Jmix, la sécurité est un module séparé. Vous pouvez maintenant choisir si vous voulez ou non le moteur de sécurité CUBA ou autre chose.
Et nous avons retravaillé notre moteur de sécurité, maintenant il est étroitement intégré à la sécurité Spring. Afin de simplifier les choses pour les développeurs et de «ne pas réinventer la roue», nous avons remplacé notre moteur personnalisé par le cadre «standard» qui contient beaucoup de documentation et est familier aux développeurs. Le modèle a changé en conséquence - dans Jmix, nous utilisons des classes de Spring Security comme UserDetails et SessionRegistry, donc cela peut sembler moins familier au début.
Les rôles ont également changé - nous avons fusionné les rôles et les groupes d'accès pour simplifier la gestion de la sécurité. En plus de cela, nous avons ajouté un "Rôle d'agrégation". Il s'agit d'un rôle composé d'autres rôles - il y a eu beaucoup de demandes d'utilisateurs concernant cette fonctionnalité.
La sécurité Spring n'est pas la chose la plus facile à configurer, mais dans Jmix, nous avons rendu ce processus aussi transparent que possible. Vous pourrez définir l'accès aux entités, attributs, écrans, ainsi que configurer la sécurité basée sur les lignes comme c'était le cas dans CUBA.
Et comme c'était le cas avec CUBA, tout ce que vous avez à faire pour installer la sécurité dans votre application est d'ajouter une dépendance à votre projet et Jmix fera sa magie - vous aurez configuré la sécurité ainsi qu'une interface de gestion des utilisateurs (si vous le souhaitez).
Outre la sécurité, il y a une autre chose que tout le monde apprécie à propos de CUBA : la simplicité du développement d'une application ...

### Interface utilisateur
L'interface utilisateur du backoffice (ou interface utilisateur générique) reste intacte. L'interface utilisateur basée sur les composants était une grande partie de CUBA et nous prévoyons de la prendre en charge dans Jmix. Le support inclut des générateurs d'écran, des éditeurs d'interface utilisateur dans l'EDI, etc. Nous avons ajouté de nouveaux composants comme un composant de Pagination séparé ou ResponsiveGridLayout. La seule différence - vous pouvez désormais exclure complètement l'interface utilisateur générique de l'application grâce à la structure modulaire du framework Jmix.
Veuillez noter que les applications Jmix sont à un seul niveau; il n'y a plus de séparation «core-web». Cette approche est plus simple et s'inscrit dans l'approche architecturale moderne. Si vous souhaitez une séparation, vous pouvez y parvenir en implémentant deux applications Jmix et en créant une API REST pour la communication. Dans ce cas, l'interface utilisateur ne dépendra pas du modèle de données et vous passerez les DTO afin d'afficher les données sur le front-end ou de les traiter sur le back-end.
Lors de la planification de la nouvelle version de notre framework, nous ne pouvions ignorer la montée en puissance des frameworks JS UI. Nous avons donc commencé à développer des générateurs clients ReactJS (module frontal) dans CUBA 7 et nous continuons ce travail dans Jmix. Les frameworks JS ont généralement une courbe d'apprentissage assez raide, notre objectif est donc de rapprocher l'expérience de développement ReactJS avec Jmix du développement d'UI générique.
Nous avons introduit le SDK TypeScript et développé un ensemble de composants ReactJS personnalisés pouvant être utilisés pour le développement de l'interface utilisateur. Le module frontal repose sur l'API REST générique, familière aux développeurs CUBA. L'EDI prend en charge la génération d'interface utilisateur de base avec ReactJS.
Pour l'instant, un développeur peut générer des écrans d'interface utilisateur «navigateur» et «éditeur» familiers à l'aide de nos composants. Plus tard, nous prévoyons d'ajouter plus de composants et de simplifier le développement de l'interface utilisateur ReactJS dans le Studio.
Et maintenant, nous avons discuté de presque tous les changements majeurs dans Jmix, mais il serait injuste de ne pas mentionner le ...

[image]

### Déploiement
CUBA a deux formats de déploiement: WAR et UberJar et deux options: un déploiement d'application unique ou un déploiement de composant d’applications distincts (core + web + ...).
Jmix utilisera les plugins de build Spring Boot pour le déploiement de l'application. Cela signifie que vous pouvez exécuter une application Jmix en tant que fat JAR exécutable ou WAR déployable (sachant qu’elle peut également être exécutée en tant qu'application autonome).
Mais la meilleure chose ici est la conteneurisation. Désormais, vous n'avez plus besoin de créer votre propre fichier Docker pour créer une image d'application, sa génération est prise en charge dès le départ. En outre, vous pouvez créer des fichiers JAR en couches pour rendre les images Docker plus efficaces. En plus de cela, les buildpacks cloud natifs sont pris en charge.

Ainsi, les applications Jmix utiliseront les technologies de pointe pour le déploiement dans des environnements cloud modernes.
Et avec tant de changements, que diriez-vous de la ...

### Migration de CUBA vers Jmix
Première chose: nous n'allons pas abandonner CUBA. La version 7 est en mode support de long-terme et sera prise en charge pendant cinq ans. Et après cela, un support commercial sera disponible pour les cinq années suivantes. Ainsi, le framework CUBA vivra au moins 10 ans.
Pour le moment, Jmix est au stade de preview, nous allons donc le stabiliser pendant un certain temps avant d'annoncer une version stable prête pour la production - provisoirement au deuxième trimestre 2021. Mais si vous prévoyez de commencer à utiliser CUBA, jetez d'abord un coup d'œil à Jmix. Il est suffisamment stable pour démarrer le développement PoC. Et rappelez-vous que presque tout l'écosystème Spring Boot est à votre service.
Pour des raisons de compatibilité descendante, nous avons introduit un module jmix-cuba. Ce module contient la plupart des API implémentées dans CUBA. Vous n'aurez donc pas besoin de beaucoup modifier votre code pour migrer vers la prochaine version du framework. Le module de compatibilité sera ajouté automatiquement à votre application lors de la migration.
La plupart des modules complémentaires de CUBA seront progressivement migrés vers la plateforme Jmix: reporting, maps, processus métiers. Comme nous l'avons fait avec CUBA 7 auparavant, nous pourrions déprécier certains modules lors du passage à Jmix car il existe un démarreur Spring Boot avec la même fonctionnalité.
Le format des modules complémentaires a changé, mais les fonctionnalités restent les mêmes. Vous pouvez étendre les entités et les écrans en utilisant la même technique que celle utilisée dans CUBA. En ce qui concerne le remplacement des services, vous devrez utiliser l'approche Spring Boot - il suffit de marquer le service complémentaire avec l'annotation principale et la fonctionnalité sera remplacée.
Comme d'habitude, lorsqu’une version majeure est introduite (fondamentalement, Jmix est CUBA 8), des changements de rupture peuvent apparaître. Et ces changements, ainsi que les solutions de contournement, seront décrits en détail dans la documentation.
Et la grande partie de la migration est le nouveau Studio. Jmix Studio joue un rôle très important dans l'écosystème du framework. Ainsi, vous pouvez toujours utiliser tous les concepteurs familiers (entité et interface utilisateur), raccourcis et intentions. Et Jmix Studio vous aidera à créer des applications en utilisant le framework.

### Conclusion
Jmix est la prochaine grande étape dans l'évolution de la plateforme CUBA. Vous pouvez désormais profiter de presque tous les starters Spring Boot et utiliser des techniques applicables au framework Java le plus populaire au monde. En même temps, vous disposez toujours de toutes les API et fonctionnalités pratiques et familières fournies par Jmix - un descendant de CUBA ainsi qu'une excellente expérience de développement avec le nouveau Studio.

Essayez jmix.io		Donnez votre avis

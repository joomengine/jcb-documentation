> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="general-planning-joomla-component-builder"></a>
# **Planification générale : Joomla Component Builder**

<a id="video-reference"></a>
### Référence vidéo

[Regarder le didacticiel sur YouTube](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)

---

<a id="1-be-prepared-to-build-components"></a>
## **1. Soyez prêt à créer des composants**

[00:00:00](https://youtu.be/gEgwiVNj6N0?t=0)

Avant de créer avec Joomla Component Builder (JCB), la préparation est essentielle. Tu devrais:

* Comprenez **ce que fera votre composant**.
* Planifiez la **structure de base de données** que vous souhaitez mettre en place.
* Sachez comment vos tables et champs seront **mapper les uns aux autres**.

Revisitez la [Présentation des champs JCB](./JCB-Fields.md) avant de commencer la modélisation : sa répartition des workflows de schéma, de rendu, de validation et de référentiel vous aidera à traduire les exigences en définitions de champs réutilisables.

> **Conseil :** Une carte de données claire vous aidera à définir correctement les vues, les relations et les connexions de champ dans JCB.

Si vous débutez dans la conception de bases de données, passez en revue les **relations de table** de base (un-à-plusieurs, plusieurs-à-plusieurs) pour vous assurer que la logique de vos composants s'aligne sur la structure MVC de Joomla.

---

<a id="2-using-demo-components-as-learning-tools"></a>
## **2. Utiliser des composants de démonstration comme outils d'apprentissage**

[00:00:49](https://youtu.be/gEgwiVNj6N0?t=49)


Ce didacticiel utilise **Sermon Distributor**, un composant de démonstration, pour illustrer le processus de création.
En l'étudiant, vous apprendrez :

* Comment les **vues backend** se connectent à la base de données.
* Comment la dénomination et la structuration des composants affectent la cohérence.

Chaque vue backend dans Joomla est **étroitement liée à sa table de base de données**. Planifiez en conséquence.

---

<a id="3-understanding-the-purpose-of-conventions"></a>
## **3. Comprendre le but des conventions**

[00:01:40](https://youtu.be/gEgwiVNj6N0?t=100)


JCB permet de la flexibilité mais suit les **conventions de mise en œuvre** établies pour une raison :

* Ceux-ci garantissent une intégration fluide avec le système MVC de Joomla.
* Briser les conventions peut entraîner des problèmes ou la nécessité de reconstruire des sections plus tard.

> **Recommandation :** Suivez les conventions de dénomination et de structure par défaut de JCB, à moins que vous ne compreniez pleinement leurs implications.

---

<a id="4-backend-views-and-database-connections"></a>
## **4. Vues backend et connexions à la base de données**

[00:02:16](https://youtu.be/gEgwiVNj6N0?t=136)


Les vues backend constituent le **lien principal** vers les tables de votre base de données.
Par exemple, dans *Sermon Distributor* :

* Une **vue de liste** affiche plusieurs sermons.
* Une **vue d'édition** permet d'éditer des sermons individuels.

Les deux partagent la même table de base de données mais représentent des points d’entrée différents.

> Le backend se connecte et gère la base de données ; le frontend présente les données de manière dynamique.

---

<a id="5-dynamic-get-and-data-relationships"></a>
## **5. Relations d'obtention et de données dynamiques**

[00:04:44](https://youtu.be/gEgwiVNj6N0?t=284)


La fonctionnalité **Dynamic Get** est au cœur de la gestion des données dans JCB. Il:

* Connecte les vues du backend et du site.
* Récupère et mappe les modèles de données à partir des champs de base de données.
* Peut être réutilisé dans plusieurs contextes.

Considérez-le comme un pont entre la structure de la base de données et la sortie dynamique de votre composant.

---

<a id="6-mapping-views-to-database-tables"></a>
## **6. Mappage des vues aux tables de base de données**

[00:05:40](https://youtu.be/gEgwiVNj6N0?t=340)


Les vues backend dans JCB **se mappent directement à la base de données**.
Chaque champ défini dans JCB correspond à une colonne de la base de données.
Ce mappage direct garantit que les contrôleurs, modèles et classes de Joomla se comportent correctement.

Si vous avez besoin de données provenant de tables externes ou tierces, JCB propose des **Vues back-end personnalisées** qui agissent de manière plus dynamique, similaires aux vues front-end.

> **Exemple de cas d'utilisation :** Création d'un tableau de bord ou d'une vue de rapport qui regroupe les données de plusieurs tables.

---

<a id="7-using-dynamic-get-for-combined-data"></a>
## **7. Utilisation de Dynamic Get pour les données combinées**

[00:09:19](https://youtu.be/gEgwiVNj6N0?t=559)


Vous pouvez créer une **vue backend personnalisée** qui utilise la fonctionnalité *Dynamic Get* pour extraire des données de plusieurs tables associées (par exemple, sermons, prédicateurs, séries et téléchargements).

Un exemple pratique consiste à créer une vue *Analyse* pour :

* Combinez les données sur plusieurs tables.
* Modélisez et présentez les données de manière dynamique dans des graphiques ou des listes.

---

<a id="8-structuring-fields-and-data-mapping"></a>
## **8. Structuration des champs et mappage des données**

[00:13:05](https://youtu.be/gEgwiVNj6N0?t=785)


Avant de commencer, **cartographiez vos champs** :

* Sermons → nom, prédicateur, série, fichiers
* Prédicateurs → nom, email, description, site web
* Série → nom, description, statistiques
* Fichiers → nom de fichier, compteur, référence du sermon

> **Conseil :** Cette phase de planification évite les erreurs structurelles et simplifie la création de vues.

---

<a id="9-adding-compulsory-fields"></a>
## **9. Ajout de champs obligatoires**

[00:15:20](https://youtu.be/gEgwiVNj6N0?t=920)


Dans JCB, les champs obligatoires sont marqués d'un astérisque (*).
Lors de la création d'un nouveau composant :

1. Ajoutez les champs obligatoires (par exemple, *nom*, *image*).
2. Définissez l'**image du composant** (taille recommandée : *300x300px*).
3. Enregistrez avant de procéder à la visualisation de la création.

---

<a id="10-adding-and-creating-views"></a>
## **10. Ajout et création de vues**

[00:16:20](https://youtu.be/gEgwiVNj6N0?t=980)


Il y a une différence entre :

* **Ajout de vues** - attache de vues existantes à votre composant.
* **Création de vues** - en définissant de nouvelles à partir de zéro.

Vous ajoutez des vues via l'**onglet Paramètres** de votre composant.

---

<a id="11-adding-fields-to-views"></a>
## **11. Ajout de champs aux vues**

[00:16:44](https://youtu.be/gEgwiVNj6N0?t=1004)


Chaque vue doit être associée à des champs.
Vous ne pouvez pas ajouter un champ à une vue à moins que le champ n'existe dans votre configuration JCB.

Champs réutilisables courants :

* **Nom** (peut être réutilisé sur plusieurs vues)
* **Hits** (automatiquement ajouté par défaut)

---

<a id="12-admin-views-and-field-creation"></a>
## **12. Vues d'administration et création de champs**

[00:19:11](https://youtu.be/gEgwiVNj6N0?t=1151)


Après avoir configuré votre composant, procédez à la création de **Vues d'administration** :

1. Accédez à **Vues administrateur → Nouveau**.
2. Saisissez les informations de base (titre, nom de la table, etc.).
3. Créez et attachez des champs - évitez les doublons.
4. Marquez les **champs personnalisés** lors de la liaison des données associées (par exemple, les identifiants des prédicateurs).

> 📚 **Besoin d'un rappel sur ce qu'offrent les vues d'administration ?** Consultez le
> [JCB Admin Views propose une analyse approfondie](./Features/JCB-Admin-Views.md) avant de modéliser vos tables.

Les champs personnalisés vous permettent d'extraire des identifiants ou des valeurs de l'ensemble de données d'une autre vue, comme *Preachers* ou *Series*.

---

<a id="13-creating-normal-vs-custom-fields"></a>
## **13. Création de champs normaux ou personnalisés**

[00:21:54](https://youtu.be/gEgwiVNj6N0?t=1314)


Dans Joomla :

* **Les champs normaux** sont des entrées de données standard.
* **Champs personnalisés** liés dynamiquement à une autre vue ou table.

Les champs personnalisés dépendent de votre structure backend ; assurez-vous que vos champs de base sont prêts avant de les définir.

---

<a id="14-planning-your-component"></a>
## **14. Planification de votre composant**

[00:22:51](https://youtu.be/gEgwiVNj6N0?t=1371)


La création efficace de composants nécessite une **planification avant le développement**.
Mappez vos tables de base de données, définissez les relations entre les vues et identifiez les champs partagés.

La planification papier ou les diagrammes de flux peuvent aider à visualiser :

*Structure des composants
* Relations de données
* Champs réutilisables

> Cette planification préalable évite toute confusion et accélère la mise en œuvre dans JCB.

---

<a id="15-whats-next"></a>
## **15. Quelle est la prochaine étape**

[00:23:50](https://youtu.be/gEgwiVNj6N0?t=1430)


Ensuite, la série de didacticiels couvre :

* Création et gestion des **types de champs**.
* Création de **vues d'administration et de site**.
* Rendre votre composant **entièrement fonctionnel**.

Comprendre cette phase de planification garantit que vous pouvez créer efficacement des composants Joomla structurés et maintenables.

---

<a id="key-takeaways"></a>
### **Points clés à retenir**

* Planifiez les tables et les vues de la base de données **avant** d'ouvrir JCB.
* Utilisez **Dynamic Get** pour récupérer et réutiliser des données structurées.
* Les vues back-end sont mappées **directement aux tables**, tandis que les vues personnalisées peuvent regrouper les données.
* Suivez les **conventions JCB** pour maintenir la compatibilité.
* Toujours **créez d'abord des champs**, puis ajoutez-les aux vues.

---

> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="jab18-using-joomla-component-builder-jcb"></a>
# JAB18 Utilisation du Générateur de composants Joomla (JCB)

Joomla Component Builder (JCB) est un puissant outil open source permettant de créer des composants Joomla directement dans votre environnement Joomla. Il offre un flux de travail de développement complet basé sur des modèles qui permet aux développeurs de générer des composants robustes sans codage manuel répétitif.

[00:00:00](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

---

<a id="1-why-use-a-component-building-tool"></a>
## 1. Pourquoi utiliser un outil de création de composants ?

[00:00:40](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m40s)

La création de composants dans Joomla implique traditionnellement un travail répétitif : écriture manuelle du code passe-partout, configuration des dossiers MVC et maintien des conventions de dénomination. Des outils comme Component Creator et JoomDD existent pour automatiser certaines parties de ce processus, mais JCB va plus loin en proposant :

* **Contrôle local complet :** JCB s'exécute directement dans votre installation Joomla.
* **Aucune dépendance SaaS :** Tout se passe dans votre environnement.
* **Accès open source :** La source compilée est ouverte ; vous pouvez inspecter, modifier et redistribuer.
* **Capacité aller-retour :** Vous pouvez modifier votre composant généré et réimporter les modifications dans JCB.

Contrairement aux outils SaaS qui vous limitent à quelques tableaux ou fonctionnalités, JCB n'a pas de telles restrictions.

---

<a id="2-understanding-the-jcb-environment"></a>
## 2. Comprendre l'environnement JCB

[00:02:18](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m18s)

JCB est un **composant qui construit d'autres composants**. Une fois installé, vous travaillez entièrement depuis l'interface administrateur de Joomla. Le constructeur de composants lui-même a été construit avec JCB, ce qui témoigne de sa puissance et de son autonomie.

<a id="key-features"></a>
### Principales fonctionnalités

* Génération complète de composants MVC
* Prise en charge intégrée des champs ACL, multilingues, de gestion des versions et personnalisés
* Intégration de bibliothèques, de modèles et de mises en page
* Compilation aller-retour et synchronisation des modifications de code

---

<a id="3-starting-with-the-dashboard"></a>
## 3. Commencer par le tableau de bord

[00:12:35](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m35s)

Après l'installation, le **Dashboard** de JCB sert de centre de contrôle. De là, vous pouvez accéder :

* **Wiki et tutoriels :** Tous les guides et didacticiels vidéo JCB.
* **Gestion des composants :** Ajoutez, modifiez ou gérez des composants.
* **Configuration globale :** Accès aux options à l'échelle du système et aux paramètres de la bibliothèque.

Le tableau de bord comprend également un **lien Wiki** qui pointe vers la documentation officielle et l'index vidéo de JCB, ce qui facilite l'exploration de didacticiels sur des sujets tels que la création de champs, les vues et la gestion dynamique des données.

---

<a id="4-builder-workflow-overview"></a>
## 4. Aperçu du flux de travail du générateur

[00:14:16](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m16s)

Le workflow JCB suit une structure logique :

1. **Créer un composant**
2. **Définir les types de champs**
3. **Créer des champs**
4. **Créer des vues (liste, élément ou personnalisé)**
5. **Lier les données avec Dynamic GET**
6. **Ajouter des modèles, des mises en page et des bibliothèques**
7. **Intégrer un code personnalisé/sur mesure**
8. **Compiler et installer**
9. **Collaborer ou exporter des packages**

Ce flux garantit que votre composant est généré proprement et entièrement fonctionnel avec l'architecture native de Joomla.

---

<a id="5-creating-a-component"></a>
## 5. Création d'un composant

[00:15:04](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m04s)

Accédez à **Composants → Joomla Component Builder → Composants → Nouveau**.

<a id="tabs-overview"></a>
### Présentation des onglets

* **Détails :** Définissez le nom du composant, le préfixe et les paramètres de débogage.
* **Paramètres :** Configurez les comportements et les options des composants.
* **Vues administrateur et site :** Gérez les interfaces administrateur et frontale.
* **Bibliothèques et assistants :** Incluez des assistants PHP réutilisables ou des bibliothèques externes.
* **Tableau de bord :** Personnalisez le tableau de bord d'administration de votre composant.
* **Données MySQL :** Définissez les données SQL initiales ou les scripts de création de tables.
* **Lisez-moi :** Ajoutez la documentation qui sera livrée avec votre composant.

---

<a id="6-defining-field-types-and-fields"></a>
## 6. Définir les types de champs et les champs

[00:16:26](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m26s)

<a id="field-types"></a>
### Types de champs

Les types de champs définissent des structures d'entrée réutilisables - par exemple, texte, calendrier, catégorie, case à cocher, couleur ou entrées personnalisées. Ils sont **globaux** sur tous vos composants, favorisant la réutilisabilité.

<a id="fields"></a>
### Champs

[00:17:28](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h17m28s)

Chaque champ représente une colonne de base de données et une instance d'un type de champ. Tu peux:

* Attribuez des étiquettes, des info-bulles et des valeurs par défaut
* Configurer les règles de validation des champs
* Attacher des filtres et un comportement de recherche
* Définir la visibilité par vue (Admin/Site)

> **Conseil :** Utilisez les attributs de champ pour contrôler le tri, le filtrage et les autorisations à un niveau granulaire.

---

<a id="7-creating-views"></a>
## 7. Création de vues

[00:18:59](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h18m59s)

Les vues définissent la façon dont vos données sont présentées.

<a id="types-of-views"></a>
### Types de vues

* **Vue en liste :** Affiche un tableau d'éléments avec des filtres et des outils par lots.
* **Vue des éléments :** Affiche des informations détaillées sur un seul enregistrement.
* **Vue personnalisée :** Permet des mises en page spécialisées telles que des rapports ou des tableaux de bord.

Vous pouvez attribuer des champs à chaque vue, configurer des autorisations et définir des comportements personnalisés tels que :

* Ajax appelle à la récupération d'éléments
* Déclencheurs post-sauvegarde
* Filtres de requête personnalisés

<a id="linked-fields"></a>
### Champs liés

[00:22:17](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h22m17s)

Les vues affichent les champs liés et leur configuration (triables, consultables, obligatoires). Vous pouvez également définir la visibilité par onglet ou afficher les champs de manière conditionnelle.

<a id="conditional-logic"></a>
### Logique conditionnelle

[00:23:05](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h23m05s)

Définissez les conditions de champ pour contrôler le moment où un champ est affiché en fonction d'autres valeurs de champ, ce qui est idéal pour des formulaires plus propres et sensibles au contexte.

---

<a id="8-layouts-templates-and-libraries"></a>
## 8. Mises en page, modèles et bibliothèques

[00:23:55](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h23m55s)

<a id="templates"></a>
### Modèles

Gérez les fichiers de vue PHP (par exemple, `default.php`) et divisez-les en **sous-mises en page** plus petites et réutilisables.

<a id="layouts"></a>
### Mises en page

[00:24:37](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h24m37s)

Les mises en page définissent la structure des éléments frontend et backend, entièrement compatibles avec le système de mise en page de Joomla.

<a id="libraries"></a>
### Bibliothèques

[00:25:04](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h25m04s)

Vous pouvez intégrer des bibliothèques CSS/JS externes (par exemple, Bootstrap, UIKit) à l'aide d'un CDN ou d'un chemin local. Chaque référence est automatiquement chargée là où cela est nécessaire.

---

<a id="9-using-the-dynamic-get-builder"></a>
## 9. Utilisation du Dynamic GET Builder

[00:26:52](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h26m52s)

La fonctionnalité **Dynamic GET** vous permet de créer visuellement des requêtes de base de données avancées.

* **Filtres :** Restreindre les données par niveau d'accès, état de publication ou conditions définies par l'utilisateur.
* **Tri :** Définissez les ordres par défaut et remplacez-les dynamiquement.
* **Variables globales :** Créez et réutilisez des paramètres globaux dynamiques.

<a id="table-joins"></a>
### Jointures de tables

[00:29:16](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h29m16s)

Utilisez des jointures pour combiner plusieurs tables en un seul ensemble de données. Vous pouvez ajouter autant de jointures que nécessaire (intérieure, gauche ou droite) directement via l'interface graphique. Cela fournit un modèle relationnel sans écrire SQL manuellement.

---

<a id="10-adding-custom-and-bespoke-code"></a>
## 10. Ajout de code personnalisé et sur mesure

<a id="custom-code"></a>
### Code personnalisé

[00:31:16](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h31m16s)

Vous pouvez définir des extraits de code réutilisables que JCB injecte automatiquement au moment de la compilation. Ces extraits centralisent la logique dans votre composant.

<a id="bespoke-modifications"></a>
### Modifications sur mesure

[00:32:17](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h32m17s)

Le code sur mesure est la fonctionnalité la plus puissante de JCB : il vous permet d'insérer ou de modifier du code n'importe où dans le composant compilé.

Quand vous reconstruisez, JCB :

* Extrait et réinsère vos modifications
* Met à jour uniquement les parties modifiées
* Conserve votre logique intacte lors des mises à niveau ou des changements de version de Joomla

Cela garantit un **véritable développement aller-retour** : vous pouvez modifier le code généré en toute sécurité et le reconstruire à tout moment sans perdre vos modifications.

---

<a id="11-compiling-your-component"></a>
## 11. Compilation de votre composant

[00:35:57](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h35m57s)

Une fois la structure de vos composants prête :

1. Ouvrez **JCB → Compiler**.
2. Sélectionnez votre composant dans la liste.
3. Cliquez sur **Compiler le composant**.

Après compilation :

* Vous pouvez **l'installer immédiatement** sur votre site.
* Ou **téléchargez le package ZIP** pour un usage externe.
* JCB crée automatiquement tous les dossiers MVC et tables MySQL.

Vous pouvez également **exporter/importer** des packages pour déplacer des projets entre les installations Joomla.

---

<a id="12-collaborative-development"></a>
## 12. Développement collaboratif

[00:38:48](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h38m48s)

JCB prend en charge la **collaboration basée sur Git** :

* Chaque composant peut être contrôlé en version dans Git.
* Plusieurs développeurs peuvent travailler indépendamment et fusionner les modifications.
* Le "composant mappé" (le fichier du projet JCB) peut être partagé et dupliqué.

> **Astuce :** Cette approche évite le problème de verrouillage des enregistrements de Joomla, permettant ainsi le développement parallèle.

---

<a id="13-package-distribution-and-giveaways"></a>
## 13. Distribution de colis et cadeaux

[00:40:29](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h40m29s)

VDM, le créateur de JCB, offre désormais un **accès gratuit** à des exemples de packages clés :

* Générateur de composants Joomla
* Composant questions et réponses
* Distributeur de sermons

Les utilisateurs peuvent obtenir des clés en créant ou en mettant en vedette les référentiels publics, puis en les important via la fonction **Import Packages** de JCB.

---

<a id="14-final-notes-and-community-contribution"></a>
## 14. Notes finales et contribution de la communauté

[00:44:29](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h44m29s)

Le modèle open source de JCB encourage la collaboration. En apportant des améliorations ou en partageant vos composants, vous contribuez au développement d'un écosystème puissant pour les développeurs Joomla.

> "Le fait que vous puissiez modifier n'importe quel emplacement au sein de votre composant tout en conservant un développement aller-retour est ce qui rend JCB unique."

---

<a id="summary"></a>
### Résumé

| Fonctionnalité | Descriptif |
| -------------------- | --------------------------------------------- |
| **Développement local** | Créez des composants directement dans Joomla |
| **Types de champs réutilisables** | Créez une seule fois, utilisez sur plusieurs projets |
| ** OBTENIR dynamique ** | Définir visuellement les jointures et les filtres de bases de données |
| **Code sur mesure** | Insérez et conservez en toute sécurité une logique personnalisée |
| **Compilateur** | Génère des packages ZIP installables complets |
| **Collaboration** | Intégration Git pour la création de composants partagés |

---

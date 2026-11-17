> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="quick-subform-demonstration"></a>
# Démonstration rapide de sous-formulaire

**Source du didacticiel :** [YouTube – Démonstration rapide du sous-formulaire](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)
---

<a id="1-introduction---community-request"></a>
## 1. Introduction – Demande de la communauté

**[00:00:00](https://www.youtube.com/watch?v=3j4xPQC4apI&t=0s)**

Un membre de la communauté a demandé des conseils sur la façon de générer et de gérer des sous-formulaires dans Joomla Component Builder (JCB), en particulier :

* Comment générer un sous-formulaire directement dans JCB.
* Où trouver les détails XML pour les champs de sous-formulaire répétés.
* Comment les données du sous-formulaire sont remplies, validées et enregistrées.

Ils ont supposé que cette fonctionnalité était automatisée au sein de JCB, sans nécessiter d'édition XML manuelle.
Alors que les didacticiels précédents couvraient les *champs répétables*, ceux-ci ont depuis été **abandonnés** et remplacés par le **type de champ de sous-formulaire** plus puissant.

---

<a id="2-understanding-subforms"></a>
## 2. Comprendre les sous-formulaires

**[00:01:13](https://www.youtube.com/watch?v=3j4xPQC4apI&t=73s)**

Un **sous-formulaire** dans Joomla vous permet de regrouper plusieurs champs en un seul ensemble de champs qui peut être répété.
Chaque instance d'un sous-formulaire agit comme un mini-formulaire à l'intérieur de votre formulaire principal - idéal pour stocker des ensembles de données associés.

**Exemple de cas d'utilisation :**

* Une section « Membres de l'équipe » où chaque membre dispose des champs *Nom*, *E-mail* et *Site Web*.

<a id="in-jcb"></a>
### Chez JCB

JCB simplifie cela en :

* Générer automatiquement le XML correct pour le sous-formulaire.
* Gestion automatique du stockage JSON.
* Gérer à la fois le chargement et la sauvegarde des données du sous-formulaire via son compilateur.

---

<a id="3-step-1---create-the-fields-for-your-subform"></a>
## 3. Étape 1 - Créez les champs de votre sous-formulaire

**[00:01:44](https://www.youtube.com/watch?v=3j4xPQC4apI&t=104s)**

Chaque sous-formulaire nécessite un ensemble de champs standards (par exemple : *Nom*, *E-mail*, *Site Web*, *Description*).
Avant de créer le champ de sous-formulaire lui-même, ces champs individuels doivent exister dans JCB.

<a id="to-create-the-fields"></a>
### Pour créer les champs

1. Dans JCB, accédez à **Admin → Champs**.
2. Cliquez sur **Nouveau**.
3. Choisissez le **type de champ** approprié (par exemple, *Texte*, *E-mail*, *Checkbox*, *List*).
4. Configurez chaque champ comme vous le souhaitez.
5. Enregistrez chacun individuellement.

**Conseil :** Utilisez des noms de champs et des étiquettes clairs : ils apparaîtront dans le sous-formulaire.

---

<a id="4-step-2---create-the-subform-field"></a>
## 4. Étape 2 - Créer le champ du sous-formulaire

**[00:02:06](https://www.youtube.com/watch?v=3j4xPQC4apI&t=126s)**

Une fois vos champs de base existants, vous pouvez créer le sous-formulaire qui les référencera.

<a id="procedure"></a>
### Procédure

1. Accédez à **Admin → Champs** et cliquez sur **Nouveau**.
2. Définissez **Type de champ** sur `Subform`.
3. JCB remplira automatiquement une structure XML de base pour le sous-formulaire.
4. Donnez au champ un **libellé** et un **nom** (par exemple : `Options` ou `options_test`).
5. Attribuez un **type de données** - généralement `TEXT` ou `MEDIUMTEXT`.

* JCB détecte automatiquement que ce champ est un sous-formulaire et gère l'encodage/décodage JSON lors du stockage ou du chargement des données.
6. Enregistrez le nouveau champ.

---

<a id="5-step-3---assign-the-fields-to-the-subform"></a>
## 5. Étape 3 - Attribuez les champs au sous-formulaire

**[00:04:57](https://www.youtube.com/watch?v=3j4xPQC4apI&t=297s)**

Chaque sous-formulaire doit référencer les ID de champs existants pour savoir quels champs inclure.

<a id="how-to-add-fields-by-id"></a>
### Comment ajouter des champs par ID

1. Recherchez les **ID** des champs que vous avez créés précédemment.

* Accédez à **Admin → Champs** et notez les identifiants numériques dans la vue liste.
2. Dans la configuration des champs de votre sous-formulaire, localisez la zone de saisie **"Champs"**.
3. Saisissez une liste d'ID de champ séparés par des virgules (par exemple, `199,280,100`).

* Exemple:

     ```
     Fields: 199,280,100
     ```

Cela inclura *Nom*, *Site Web* et *E-mail* dans votre sous-formulaire.

---

<a id="6-step-4---configure-additional-options"></a>
## 6. Étape 4 - Configurer les options supplémentaires

**[00:05:33](https://www.youtube.com/watch?v=3j4xPQC4apI&t=333s)**

JCB vous permet de personnaliser le comportement et la validation des champs de votre sous-formulaire.

| Options | Descriptif |
| --------------- | --------------------------------------------------------------------------- |
| **Description** | Texte facultatif décrivant ce que fait ce sous-formulaire.                            |
| **Maximum** | Le nombre maximum d'entrées répétables autorisées.                           |
| **Filtre** | Définit la façon dont chaque valeur de champ est validée (par exemple, `string`, `email`, `url`). |
| **Affiché** | Contrôle l'affichage conditionnel du sous-formulaire en fonction de la valeur d'un autre champ. |

**Remarques de validation :**
Chaque champ d'un sous-formulaire est validé en fonction de son propre type de champ et de son propre filtre.
Vous n'avez pas besoin d'ajouter une validation personnalisée, sauf si vous souhaitez une logique avancée.
JCB intègre automatiquement la validation de champ native de Joomla lors de la compilation.

---

<a id="7-step-5---optional-form-source-file"></a>
## 7. Étape 5 - Facultatif : Fichier source du formulaire

**[00:03:51](https://www.youtube.com/watch?v=3j4xPQC4apI&t=231s)**

L'option **Formsource** vous permet de charger un fichier XML externe définissant la disposition du sous-formulaire.
Cependant, ceci est **facultatif** dans JCB car il génère déjà automatiquement du XML.

* Utilisez **Formsource** uniquement si vous conservez du XML personnalisé en dehors de JCB (par exemple, un fichier XML dans le dossier `models/forms` de votre composant).
* Vous pouvez utiliser **soit** l'option `Fields` **ou** `Formsource` - pas les deux.

Si vous incluez un `Formsource`, le compilateur de JCB le reconnaît et le gère correctement lors de la compilation du composant.

---

<a id="8-step-6---add-the-subform-to-a-view"></a>
## 8. Étape 6 - Ajouter le sous-formulaire à une vue

**[00:08:19](https://www.youtube.com/watch?v=3j4xPQC4apI&t=499s)**

Une fois votre champ de sous-formulaire créé, ajoutez-le à n'importe quelle **Vue administrateur** de votre composant.

<a id="example"></a>
### Exemple

Pour ajouter le sous-formulaire `Options (test)` à la vue **Afficher** :

1. Ouvrez vos **Vues d'administration** dans JCB.
2. Sélectionnez la vue **Look** (à partir du composant *Demo*).
3. Dans l'onglet *Champs*, ajoutez le champ de sous-formulaire `Options (test)` sous la section **Détails**.
4. Définissez la largeur d'affichage (par exemple, pleine largeur).
5. Enregistrez la vue.

---

<a id="9-step-7---compile-and-install-the-component"></a>
## 9. Étape 7 - Compiler et installer le composant

**[00:08:49](https://www.youtube.com/watch?v=3j4xPQC4apI&t=529s)**

Maintenant que votre sous-formulaire fait partie d'une vue :

1. Allez dans **Composants → Joomla Component Builder → Compiler**.
2. Compilez le composant qui contient votre sous-formulaire.
3. Installez-le ou mettez-le à jour dans Joomla via le **Extensions Installer**.

---

<a id="10-step-8---test-the-subform-in-joomla"></a>
## 10. Étape 8 - Testez le sous-formulaire dans Joomla

**[00:09:26](https://www.youtube.com/watch?v=3j4xPQC4apI&t=566s)**

Accédez à votre composant dans le backend Joomla :

1. Ouvrez la vue qui contient votre sous-formulaire (par exemple, *Looks* dans le composant Démo).
2. Ajoutez des données dans les champs du sous-formulaire (par exemple, nom, site Web, e-mail).
3. Cliquez sur le bouton **"+" (Ajouter)** pour ajouter un autre ensemble de champs.
4. Saisissez plusieurs entrées et enregistrez.

**Résultat :**
Les données du sous-formulaire sont stockées au format JSON dans la base de données et lorsque vous rouvrez l'enregistrement, les valeurs sont chargées et affichées correctement.

**[00:10:45](https://www.youtube.com/watch?v=3j4xPQC4apI&t=645s)**
Vous pouvez réorganiser les entrées (glisser-déposer ou utiliser les flèches de classement), enregistrer à nouveau et l'ordre persistera.

---

<a id="11-summary"></a>
## 11. Résumé

Les sous-formulaires dans Joomla Component Builder permettent des structures de données puissantes et flexibles à l'intérieur de vos composants sans écrire manuellement du XML ou du PHP.

<a id="key-points"></a>
### Points clés :

* Créez d'abord tous les champs individuels.
* Utilisez le type de champ Sous-formulaire pour les regrouper.
* Attribuez les champs par leurs identifiants.
* Définissez le type de données sur `TEXT` ou `MEDIUMTEXT`.
* Ajoutez le sous-formulaire à la vue souhaitée.
* JCB gère automatiquement la logique de sauvegarde et de chargement.

---

<a id="12-additional-resources"></a>
## 12. Ressources supplémentaires

* **Tutoriels Joomla Component Builder (YouTube) :**
  [https://www.youtube.com/playlist?list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE](https://www.youtube.com/playlist?list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)

* **Documentation officielle JCB :**
  [https://git.vdm.dev/joomla/pkg-component-builder/wiki](https://git.vdm.dev/joomla/pkg-component-builder/wiki)

---

<a id="helpful-tips"></a>
### Conseils utiles

* Testez toujours les sous-formulaires à petite échelle avant de mettre en œuvre une logique complexe.
* Évitez d'imbriquer les sous-formulaires (ils peuvent générer des structures de données complexes).
* Utilisez des **Zones de code personnalisées** dans JCB si vous devez manipuler les données du sous-formulaire par programme.
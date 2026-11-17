> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="library-manager---anticipated-functionality"></a>
# Gestionnaire de bibliothèque - Fonctionnalité prévue

<a id="overview"></a>
## Aperçu

[00:00:00](https://www.youtube.com/watch?v=joT8weuPcwU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

Le **Library Manager** est une fonctionnalité à venir dans Joomla Component Builder (JCB), conçue pour gérer dynamiquement les intégrations de bibliothèques externes et internes telles que Bootstrap, UIkit et FooTable. Ce didacticiel décrit la **structure et le comportement attendus** du gestionnaire de bibliothèques, la manière dont les développeurs configureront les bibliothèques et comment ils interagiront avec les options des composants.

La fonctionnalité est actuellement en cours de développement. L'interface utilisateur (UI) a été prototypée et ses principes fondamentaux sont en cours d'affinement avant l'intégration du compilateur.

---

<a id="1-introduction-to-library-configuration"></a>
## 1. Introduction à la configuration de la bibliothèque

[00:00:34](https://www.youtube.com/watch?v=joT8weuPcwU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m34s)

Chaque bibliothèque de JCB, telle que **Bootstrap**, est représentée comme une entité qui se connecte à plusieurs extraits de code et son nom de base ne peut pas être modifié une fois ajoutée au **Référentiel d'extraits de communauté**.

* Une fois qu'une bibliothèque fait partie du référentiel communautaire, son nom devient **immuable** pour éviter les incohérences.
* Même si vous modifiez le nom et cliquez sur « Enregistrer », il reviendra automatiquement à l'original.

Cela garantit que les bibliothèques partagées restent cohérentes dans les environnements des développeurs.

---

<a id="2-adding-external-library-resources"></a>
## 2. Ajout de ressources de bibliothèque externes

[00:01:46](https://www.youtube.com/watch?v=joT8weuPcwU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m46s)

Par exemple, la bibliothèque **Bootstrap 4** utilise ces URL externes par défaut :

```text
https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-alpha.6/js/bootstrap.min.js
https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-alpha.6/css/bootstrap.min.css
```

L'option « Toujours ajouter » garantit que ces ressources sont automatiquement incluses partout où la bibliothèque est appliquée.

À l'avenir, lorsque **Joomla 4** sera publié, les développeurs préféreront peut-être utiliser les **bibliothèques natives Joomla** via son API interne plutôt que des URL distantes. Pour répondre à cela, une option **Script personnalisé** a été introduite.

---

<a id="3-two-key-functions-preparedocument-and-setdocument"></a>
## 3. Deux fonctions clés : `prepareDocument` et `setDocument`

[00:02:30](https://www.youtube.com/watch?v=joT8weuPcwU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m30s)

Il existe deux fonctions principales responsables de l'ajout de bibliothèques aux vues :

1. **`prepareDocument()`** - Utilise directement la variable de document pour attacher des scripts et des styles.
2. **`setDocument()`** - Utilise une variable de document globale, en fonction de l'héritage de classe.

Lorsque vous utilisez l'option **Script personnalisé**, vous pouvez cibler ces méthodes pour ajouter dynamiquement les ressources requises.

---

<a id="4-conditional-library-loading"></a>
## 4. Chargement conditionnel de la bibliothèque

[00:03:39](https://www.youtube.com/watch?v=joT8weuPcwU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m39s)

L'**option conditionnelle** introduit une approche dynamique de l'inclusion de fichiers :

* Vous pouvez définir des règles telles que **Inclure** ou **Exclure** en fonction des conditions du champ.
* La logique conditionnelle reflète le **système conditionnel de terrain** de JCB, en utilisant la logique **Isolate** ou **Chain**.
* Les conditions reposent sur des **champs de configuration**, qui sont pré-créés dans votre composant.

Par exemple, lier un champ radio nommé `Bootstrap v4` permet de choisir si les actifs Bootstrap doivent être inclus.

---

<a id="5-linking-option-fields"></a>
## 5. Liaison des champs d'options

[00:05:40](https://www.youtube.com/watch?v=joT8weuPcwU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m40s)

Lors de la sélection d'un **Champ d'option**, tel qu'un bouton Oui/Non :

* Si le champ « Ajouter Bootstrap » est défini sur **Oui**, les fichiers CSS et JS Bootstrap liés seront chargés.
* Cela propose une **méthode conditionnelle** pour inclure des actifs.

Cependant, pour l’instant, JCB ne crée pas automatiquement ces champs conditionnels dans tous les systèmes. Le développeur peut choisir d'ajouter manuellement ou de scripter sa génération.

---

<a id="6-creating-and-linking-local-files"></a>
## 6. Création et liaison de fichiers locaux

[00:07:03](https://www.youtube.com/watch?v=joT8weuPcwU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m03s)

Pour inclure des fichiers personnalisés ou locaux :

1. Cliquez sur **Modifier** dans la bibliothèque.
2. Sélectionnez **Ajouter de nouveaux fichiers**.
3. Utilisez l'icône plus verte pour joindre un fichier ou une URL.
4. Exemple de chemin local :

   ```
   /media/bootstrap4/js/bootstrap.min.js
   ```

Ces fichiers peuvent être ajoutés sous condition à l’aide de champs personnalisés. Par exemple, créez un nouveau champ `Add More` (radio) et lorsqu'il est défini sur **Oui**, le fichier correspondant (par exemple, `bootstrap.min.js`) sera chargé.

---

<a id="7-dynamic-integration-and-custom-scripts"></a>
## 7. Intégration dynamique et scripts personnalisés

[00:09:33](https://www.youtube.com/watch?v=joT8weuPcwU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m33s)

Auparavant, cette fonctionnalité était **codée en dur dans le compilateur**, par exemple, détectant automatiquement l'utilisation d'UIkit v2. Le nouveau système vise à rendre ce comportement **dynamique et axé sur les développeurs**.

Vous pouvez toujours exploiter les boutons de la bibliothèque globale tels que :

* **Fichiers, dossiers et URL de bibliothèque**
* **Configuration de la bibliothèque**

Ceux-ci peuvent être référencés dans vos scripts à l'aide de variables globales telles que :

```php
$this->fooTableStyle
```

Cela permet une inclusion conditionnelle ou personnalisée via `prepareDocument` et `setDocument`.

---

<a id="8-global-vs-page-level-conditions"></a>
## 8. Conditions globales ou au niveau de la page

[00:10:50](https://www.youtube.com/watch?v=joT8weuPcwU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m50s)

Une amélioration prévue est la **logique conditionnelle à deux niveaux** :

* **Valeur globale** - Applique les règles d'inclusion de bibliothèque à l'ensemble du composant.
* **Valeur de la page** - Permet les remplacements par vue.

Ceci est particulièrement utile lorsqu'une vue spécifique charge déjà la même bibliothèque et que vous souhaitez l'exclure pour éviter la duplication.

Par exemple, un élément de menu peut nécessiter Bootstrap globalement, mais une vue individuelle peut le remplacer si un autre composant inclut déjà Bootstrap.

---

<a id="9-always-add-vs-conditional-add"></a>
## 9. Toujours ajouter ou ajouter conditionnellement

[00:12:15](https://www.youtube.com/watch?v=joT8weuPcwU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m15s)

* **Toujours ajouter** garantit que le fichier est inclus sur toutes les pages utilisant la bibliothèque.
* **Ajout conditionnel** inclut uniquement les fichiers spécifiés lorsque les conditions définies sont remplies.
* Les fichiers sans conditions explicites sont toujours ajoutés automatiquement.

Exemples d'URL d'amorçage par défaut :

```text
http://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-alpha.6/js/bootstrap.min.js
http://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-alpha.6/css/bootstrap.min.css
```

---

<a id="10-community-collaboration-and-ongoing-development"></a>
## 10. Collaboration communautaire et développement continu

[00:13:09](https://www.youtube.com/watch?v=joT8weuPcwU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m09s)

Des discussions sur le développement de cette fonctionnalité sont en cours dans **GitHub Issue #92 : UIkit v3 ou Bootstrap Option**.

Les développeurs sont encouragés à :

* Enregistrez de courts tutoriels expliquant des idées ou des améliorations.
* Contribuez aux fils de discussion GitHub.

---

<a id="11-implementation-outlook"></a>
## 11. Perspectives de mise en œuvre

[00:13:57](https://www.youtube.com/watch?v=joT8weuPcwU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m57s)

Une fois publiée, cette fonctionnalité comprendra :

* Configurations prédéfinies pour **Bootstrap**, **UIkit** et **FooTable**.
* Prise en charge du chargement dynamique de la bibliothèque sans modifications du compilateur.
* Séparation claire entre le comportement d'inclusion global et par vue.

Une fois mises en œuvre, les utilisateurs pourront adapter et étendre ces bibliothèques localement sans perturber la cohérence de la communauté.

---

<a id="12-final-notes"></a>
## 12. Notes finales

[00:16:04](https://www.youtube.com/watch?v=joT8weuPcwU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m04s)

Ce didacticiel présente l'orientation prévue du nouveau gestionnaire de bibliothèque. L'objectif est de rendre la gestion des bibliothèques dans JCB **dynamique, modulaire et extensible**, permettant aux développeurs d'intégrer efficacement les frameworks tout en préservant l'intégrité structurelle.

---

<a id="key-takeaways"></a>
### Points clés à retenir

* Les bibliothèques auront des **noms immuables** pour la stabilité de la communauté.
* **La logique conditionnelle** permet l'inclusion/exclusion intelligente de fichiers.
* **Le contrôle global et par vue** garantit une flexibilité dans la gestion des ressources.
* **Les scripts personnalisés** offrent un contrôle ultime aux utilisateurs avancés.
* **Les commentaires de la communauté** continuent de façonner la conception et la mise en œuvre.

---

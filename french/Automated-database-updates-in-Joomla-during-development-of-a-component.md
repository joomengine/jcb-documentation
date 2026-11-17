> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="automated-database-updates-in-joomla-during-component-development"></a>
# Mises à jour automatisées de la base de données dans Joomla pendant le développement des composants

<a id="overview"></a>
## Aperçu

** Horodatages de la transcription inclus pour référence **

Joomla Component Builder (JCB) automatise la création et les mises à jour des tables de base de données pendant le développement des composants en adhérant aux conventions de fichiers SQL natifs de Joomla. Cette automatisation garantit que votre composant reste synchronisé avec les modifications de la base de données, que vous ajoutiez de nouvelles vues, créiez de nouveaux champs ou restructuriez des champs existants.

[00:00:00](https://www.youtube.com/watch?v=zN2M15fzf_M)

Lorsque vous compilez un composant JCB, tel que **Sermon Distributor**, JCB génère une structure de fichiers conforme aux standards Joomla. Dans le composant compilé (`com_sermondistributor`), accédez à :

```
admin/sql/
```

Ici, vous trouverez le fichier **install.mysql.utf8.sql** - le script standard de Joomla pour créer les tables de base de données initiales lors de l'installation.

---

<a id="understanding-joomlas-sql-behavior"></a>
## Comprendre le comportement SQL de Joomla

[00:01:17](https://www.youtube.com/watch?v=zN2M15fzf_M)

* Le fichier `install.mysql.utf8.sql` s'exécute **une seule fois**, lors de la première installation.
* Même si vous modifiez ou ajoutez de nouvelles données ultérieurement, Joomla **ne réexécutera pas** ce fichier.
* JCB maintient automatiquement ce fichier à jour avec toutes les nouvelles vues (tables) ou champs (colonnes) que vous ajoutez.
* Cependant, ces mises à jour ne concernent que les **nouvelles installations**, pas pour les sites sur lesquels le composant est déjà installé.

Pour les installations existantes, Joomla utilise des **fichiers SQL de mise à jour** situés dans le dossier `updates`.

---

<a id="how-jcb-handles-updates"></a>
## Comment JCB gère les mises à jour

[00:02:44](https://www.youtube.com/watch?v=zN2M15fzf_M)

1. **Installez le composant**
   Installez votre composant pour initialiser le schéma de base de données.

2. **Ajouter un nouveau champ**
   Exemple : dans la vue d'administration « Sermon », ajoutez un champ nommé **Téléphone portable** en quatrième position (onglet de gauche).

3. **Ajouter une nouvelle vue (facultatif)**
   Vous pouvez ajouter une toute nouvelle vue à ce stade.
   JCB détectera les **deux modifications** (le nouveau champ et la nouvelle vue) et préparera un **fichier de mise à jour SQL** incluant les deux.

[00:03:34](https://www.youtube.com/watch?v=zN2M15fzf_M)

4. **Compilez le composant**
   Après avoir enregistré vos modifications, exécutez à nouveau le **compilateur**.
   JCB incrémente automatiquement la version du composant (par exemple de `2.0.0` à `2.0.1`) et génère un nouveau fichier de mise à jour SQL.

5. **Vérifiez les fichiers générés**
   Extrayez votre composant compilé et ouvrez :

   ```
   admin/sql/updates/
   ```

Vous trouverez le nouveau fichier de mise à jour SQL versionné, par ex. `2.0.1.sql`.

---

<a id="inside-the-update-file"></a>
## Dans le fichier de mise à jour

[00:04:53](https://www.youtube.com/watch?v=zN2M15fzf_M)

Chaque nouveau fichier de mise à jour peut contenir :

* Instructions SQL pour **ajouter de nouveaux champs** aux tables existantes.
* Instructions SQL pour **créer de nouvelles tables**.

Par exemple:

```sql
ALTER TABLE `#__sermondistributor_sermon` ADD `mobile` VARCHAR(255) NOT NULL;
CREATE TABLE `#__sermondistributor_look` (...);
```

Lorsque vous installez ce composant mis à jour :

* Le champ **Mobile** apparaît dans la table `Sermon`.
* La table **Look** est nouvellement créée.

---

<a id="version-management"></a>
## Gestion des versions

[00:06:09](https://www.youtube.com/watch?v=zN2M15fzf_M)

JCB incrémente automatiquement la version du composant à chaque compilation incluant des modifications de la base de données. À l’intérieur de JCB :

* Ouvrez la zone **Mises à jour** de votre composant.
* Vous verrez les entrées versionnées avec les modifications SQL correspondantes.
* Mettez à jour manuellement l'**URL du serveur de mise à jour**, car elle ne peut pas être déterminée dynamiquement.

Cette URL est référencée dans le fichier **XML du serveur de mise à jour** du composant, garantissant que Joomla peut récupérer correctement les mises à jour.

---

<a id="workflow-for-reliable-database-updates"></a>
## Workflow pour des mises à jour fiables de la base de données

1. **Effectuer une modification** (nouveau champ, vue ou relation).
2. **Enregistrez et fermez** l'élément concerné.
3. **Compilez le composant** pour déclencher l'incrément de version.
4. **Installez ou mettez à jour** le composant dans Joomla.
5. **Vérifiez les modifications de la base de données** dans phpMyAdmin ou un autre outil de base de données.

---

<a id="when-jcbs-automation-may-not-work-as-expected"></a>
## Quand l'automatisation de JCB peut ne pas fonctionner comme prévu

[00:07:24](https://www.youtube.com/watch?v=zN2M15fzf_M)

Un scénario connu implique **l'importation ou l'exportation** de composants entre instances JCB.

Lorsque vous importez un composant :

* JCB recrée toutes les données structurelles mais **ne restaure pas l'historique des modifications du composant** ni les **ID d'actifs**.
* Sans cet historique, JCB ne peut pas détecter ce qui a changé et ne générera donc pas de mises à jour SQL appropriées.

---

<a id="restoring-history-after-import"></a>
## Restauration de l'historique après l'importation

[00:08:02](https://www.youtube.com/watch?v=zN2M15fzf_M)

Pour rétablir le suivi des modifications :

1. Ouvrez chaque **Vue administrateur** et cliquez sur **Enregistrer et fermer**.
2. Ouvrez chaque **Champ** dans la vue et **Enregistrez** à nouveau.

Cela crée des entrées d'historique de base dans JCB.
À partir de là, JCB peut détecter correctement les modifications ultérieures.

[00:08:36](https://www.youtube.com/watch?v=zN2M15fzf_M)

Après avoir enregistré :

* Compilez le composant.
* Commencez à apporter de nouveaux changements comme d'habitude.

Cela garantit que le cycle de vie du composant et les mises à jour de la base de données se comportent à nouveau naturellement.

---

<a id="best-practices"></a>
## meilleures pratiques

* **Toujours enregistrer** après avoir modifié des vues ou des champs avant la compilation.
* **Ne sautez pas** l'enregistrement après l'importation ; c'est essentiel pour le suivi des versions.
* **Examinez le dossier des mises à jour SQL** après chaque compilation pour vérifier les nouveaux fichiers.
* **Utilisez un versioning clair** (par exemple, 1.0.0 → 1.0.1 → 1.1.0) pour maintenir la clarté des mises à jour.
* **Conservez des sauvegardes** de votre composant et de votre base de données avant les mises à jour majeures.

---

<a id="conclusion"></a>
## Conclusion

[00:09:51](https://www.youtube.com/watch?v=zN2M15fzf_M)

L'intégration de JCB avec la convention de mise à jour SQL de Joomla garantit que les structures de bases de données évoluent en douceur à mesure que votre composant se développe.
En suivant des workflows de sauvegarde, de compilation et de mise à jour appropriés, vous pouvez conserver des composants robustes, sensibles aux versions et à mise à jour automatique sans gestion SQL manuelle.

[00:10:16](https://www.youtube.com/watch?v=zN2M15fzf_M)

Ce processus automatisé rationalise le développement des composants Joomla, en minimisant les erreurs et en s'alignant parfaitement sur le comportement de mise à jour standard de la base de données Joomla.

---

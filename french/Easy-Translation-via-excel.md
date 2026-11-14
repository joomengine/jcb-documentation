> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="easy-translation-via-excel-in-joomla-component-builder-jcb"></a>
# Traduction facile via Excel dans Joomla Component Builder (JCB)

<a id="overview"></a>
### Aperçu

**Référence vidéo :** [00:00:00](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

Cette fonctionnalité introduit une **nouvelle implémentation** dans JCB qui permet d'effectuer des traductions à l'aide d'une **feuille de calcul Excel**, rendant ainsi le développement de composants multilingues plus simple et plus rapide.
Vous pouvez désormais **exporter des chaînes de langue**, les envoyer aux traducteurs et **importer** les valeurs traduites dans JCB - sans modifier manuellement les fichiers de langue `.ini`.

---

<a id="1-understanding-how-jcb-handles-language-strings"></a>
## 1. Comprendre comment JCB gère les chaînes de langue

<a id="11-jcb-works-with-english-strings-not-placeholders"></a>
### 1.1. JCB fonctionne avec des chaînes anglaises, pas des espaces réservés

[00:00:51](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m51s)

JCB ne s'appuie **pas** sur des espaces réservés (comme `COM_MYCOMPONENT_BACK`). Au lieu de cela, il utilise directement la **chaîne anglaise** (par exemple, « Retour »).

* Le même mot (par exemple, *back*) peut apparaître dans plusieurs contextes ou vues.
* JCB garantit intelligemment que vous **traduisez chaque chaîne anglaise unique une seule fois**, quel que soit le nombre de fois où elle apparaît.

**Exemple :**
Le mot *"Créer nouveau"* est utilisé dans de nombreuses vues d'administration et de site, mais JCB ne vous demande de le traduire qu'une seule fois.

---

<a id="2-translating-shared-strings-across-components"></a>
## 2. Traduction des chaînes partagées entre les composants

[00:02:36](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m36s)

Des mots courants tels que `Back`, `Cancel` ou `Close` apparaissent dans plusieurs composants.
JCB réutilise automatiquement ses traductions dans le monde entier, donc une fois traduites, elles s'appliquent partout.

---

<a id="3-how-jcb-populates-the-translation-strings"></a>
## 3. Comment JCB remplit les chaînes de traduction

[00:03:26](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m26s)

Lors de la compilation de votre composant :

* JCB rassemble les chaînes anglaises à partir des **champs**, des **vues du site** et des **vues d'administration**.
* Ceux-ci sont renseignés dynamiquement dans la zone **Traductions linguistiques**.
* Vous n'avez pas besoin de cliquer manuellement sur "Nouveau" - le compilateur s'en charge.

**Conseil de pro :** Si vous exécutez le compilateur une fois, puis revisitez « Traductions de langues », vous verrez toutes les chaînes répertoriées, prêtes à être traduites.

---

<a id="4-editing-and-managing-strings"></a>
## 4. Modification et gestion des chaînes

[00:05:34](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m34s)

Si vous devez modifier une chaîne, **modifiez-la à sa source** :

* Accédez au **Champ**, à la **Vue administrateur** ou à la **Vue du site** où la chaîne a été créée.
* Mettez à jour la chaîne anglaise (par exemple, en changeant « Demo » par « Demoo »).
* Recompilez votre composant.
* L'ancienne chaîne sera automatiquement supprimée et la nouvelle apparaîtra dans les traductions linguistiques.

---

<a id="5-setting-up-languages"></a>
## 5. Configuration des langues

[00:07:23](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m23s)

Vous devez d’abord créer la ou les langues dans lesquelles vous souhaitez traduire :

1. Accédez à **Langues** dans JCB.
2. Cliquez sur **Nouveau**.
3. Saisissez le **Nom de la langue** (par exemple, Afrikaans) et le **Tag** (par exemple, `af-ZA`).
4. Enregistrez-le et publiez-le.

Si vous n'êtes pas sûr de la balise de langue correcte, visitez la [page de traduction de Joomla](https://community.joomla.org/translations.html) pour trouver le code approprié (par exemple, `nl-NL` pour le néerlandais).

---

<a id="6-adding-translations"></a>
## 6. Ajouter des traductions

[00:09:31](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m31s)

Pour traduire une chaîne :

1. Ouvrez **Traductions de langues**.
2. Sélectionnez la chaîne anglaise (par exemple, « Auteur »).
3. Choisissez votre **langue** cible (par exemple, l'afrikaans).
4. Saisissez la valeur traduite (par exemple, « Outeur »).
5. Enregistrez et fermez.

Désormais, chaque instance de « Auteur » utilisera automatiquement la traduction afrikaans.

---

<a id="7-new-feature---translation-via-excel"></a>
## 7. Nouvelle fonctionnalité - Traduction via Excel

[00:10:51](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m51s)

Vous pouvez désormais **exporter et importer des traductions** via Excel pour faciliter la collaboration.

<a id="exporting-strings"></a>
### Exportation de chaînes :

1. Accédez à **Traductions linguistiques**.
2. Sélectionnez les chaînes que vous souhaitez traduire.
3. Cliquez sur **Exporter les données**.
4. Enregistrez le fichier Excel généré.

Le dossier comprend :

* **Identifiants**
* **Chaînes anglaises**
* **Balises de langue**
* **Traductions actuelles**

Vous pouvez envoyer ce fichier à un traducteur qui complète les traductions par colonne de langue.

---

<a id="8-importing-translated-spreadsheets"></a>
## 8. Importation de feuilles de calcul traduites

[00:12:13](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m13s)

Lors de l'importation :

* Assurez-vous que l'en-tête supérieur correspond à la **balise de langue** (par exemple, `af-ZA`).
* La langue correspondante doit déjà exister dans JCB.
* **Ne modifiez pas les chaînes anglaises** - JCB correspond à la fois par **ID** et **string**.

<a id="import-steps"></a>
### Étapes d'importation :

1. Cliquez sur **Importer des données**.
2. Choisissez et téléchargez le fichier Excel.
3. JCB mappera automatiquement les colonnes de la feuille de calcul aux champs de la base de données.
4. Vérifiez et confirmez l'importation.

Si vous avez plusieurs langues mais que vous souhaitez n'en importer qu'une seule, ajoutez l'en-tête de colonne **"Ignorer cette colonne"** au-dessus de celles à ignorer.

**Remarque :** Si JCB ne peut pas correspondre à une chaîne anglaise (en raison de modifications), cette ligne sera ignorée.

---

<a id="9-troubleshooting-import-errors"></a>
## 9. Dépannage des erreurs d'importation

[00:14:06](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m06s)

Si l'importation s'arrête en raison d'une incompatibilité ou d'un problème de format, JCB ignorera les entrées problématiques.
Les versions ultérieures incluent des correctifs pour une importation plus fluide.

Après une importation réussie :

* Les traductions sont automatiquement liées à leurs chaînes.
* Les modifications apparaissent immédiatement dans la vue **Traductions linguistiques**.

---

<a id="10-automatic-language-inclusion"></a>
## 10. Inclusion automatique de la langue

[00:15:38](https://www.youtube.com/watch?v=q5NwKGnOHoQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m38s)

Si **plus de 50 %** des chaînes d'un composant ont été traduites, JCB ajoute automatiquement cette langue au composant compilé.

Vous pouvez ajuster ce seuil :

1. Ouvrez **JCB → Options**.
2. Sous **Ajouter une langue**, modifiez le seuil du **pourcentage de traduction**.
3. Enregistrez les modifications.

Cela garantit que seules les langues suffisamment traduites sont incluses dans les builds.

---

<a id="11-summary"></a>
## 11. Résumé

Ce nouveau **workflow de traduction basé sur Excel** simplifie considérablement la gestion des composants Joomla multilingues :

* Exportez facilement vos chaînes.
* Envoyer aux traducteurs dans Excel.
* Importez des traductions en quelques secondes.
* Synchronisez automatiquement tous les composants.

Vous n'avez besoin de traduire chaque chaîne unique qu'une seule fois - JCB s'occupe de tout le reste de manière dynamique.

---

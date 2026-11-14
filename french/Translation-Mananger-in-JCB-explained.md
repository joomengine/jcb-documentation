> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="translation-manager-in-joomla-component-builder-jcb"></a>
# Gestionnaire de traduction dans Joomla Component Builder (JCB)

> **Référence vidéo :** [Explication du gestionnaire de traduction dans JCB](https://www.youtube.com/watch?v=zzAcVkn_cWU)
> (*Les horodatages inclus dans cette documentation sont directement liés aux sections vidéo.*)

---

<a id="overview"></a>
## Aperçu

Joomla Component Builder (JCB) inclut désormais un **puissant système de gestion de traduction** qui permet aux développeurs d'extraire, de gérer et de maintenir automatiquement les chaînes multilingues de leurs composants.
Cette amélioration a été développée en collaboration par les contributeurs et intégrée au noyau JCB pour garantir la stabilité et la maintenabilité à long terme.

JCB gère automatiquement :

* Génération de fichiers en langue anglaise
* Extraction des espaces réservés `JText` à partir du code, des modèles et du XML
* Gestion des traductions pour plusieurs langues
* Purge des chaînes inutilisées
* Import/export pour collaboration avec les équipes de traduction

---

<a id="1-automatic-english-language-file-generation"></a>
## 1. Génération automatique de fichiers en anglais

[00:00:49](https://www.youtube.com/watch?v=zzAcVkn_cWU&t=49s)

JCB est construit comme un premier constructeur de composants anglais. Chaque fois que vous définissez des **champs, modèles ou vues**, JCB détecte et extrait automatiquement le **texte traduisible**.

<a id="how-it-works"></a>
### Comment ça marche

Lors de la création d'un champ, certaines zones de texte, telles que les étiquettes ou les descriptions, peuvent être marquées comme *traduisibles*.
Si vous ajoutez une description comme :

```xml
<field
    name="acronym"
    type="text"
    label="Enter Acronym"
    description="Enter a short acronym"
/>
```

JCB convertit automatiquement `"Enter a short acronym"` en **espace réservé de langue** (par exemple, `COM_EXAMPLE_FIELD_ACRONYM_DESC`) et l'ajoute au fichier de langue `en-GB`.

Cela se produit dans tout le compilateur (pour les vues d'administration, les vues de site et les modèles), garantissant que tout le texte visible peut être traduit ultérieurement.

---

<a id="2-placeholder-conversion-with-jtext"></a>
## 2. Conversion d'espace réservé avec `JText`

[00:01:25](https://www.youtube.com/watch?v=zzAcVkn_cWU&t=85s)

Dans les modèles et les mises en page, chaque fois que vous encapsulez du texte dans un appel `JText`, par exemple :

```php
<?php echo JText::_('COM_EXAMPLE_HELLO_WORLD'); ?>
```

L'analyseur de JCB capture automatiquement la chaîne anglaise et garantit qu'elle est ajoutée au bon fichier `en-GB` lors de la compilation.

**Conseil :** Vous n'avez pas besoin de gérer manuellement les fichiers en anglais : JCB les compile et les met à jour pour vous.

---

<a id="3-adding-additional-languages"></a>
## 3. Ajout de langues supplémentaires

[00:02:43](https://www.youtube.com/watch?v=zzAcVkn_cWU&t=163s)

Les développeurs ont demandé une prise en charge multilingue afin que JCB puisse compiler plusieurs fichiers de traduction.
Vous pouvez désormais définir des **balises de langue multiples** (par exemple, `fr-FR`, `de-DE`, `es-ES`) et JCB générera automatiquement des fichiers `.ini` distincts.

<a id="steps"></a>
### Étapes :

1. Ouvrez l'onglet **Gestionnaire de traduction**.
2. Cliquez sur **Nouvelle langue**.
3. Saisissez :

* **Balise de langue** (par exemple, `fr-FR`)
   * **Nom de la langue** (par exemple, français)
4. JCB utilisera les conventions de dénomination de Joomla pour les préfixes (des liens vers des références pourront être ajoutés ultérieurement).
5. Lors de la compilation, toutes les chaînes sont extraites dans le fichier `en-GB`, puis les versions traduites sont créées en fonction des entrées de votre base de données.

---

<a id="4-internal-code-flow-for-language-extraction"></a>
## 4. Flux de code interne pour l'extraction du langage

[00:03:50](https://www.youtube.com/watch?v=zzAcVkn_cWU&t=230s)

La logique principale réside dans la classe `a_Get.php`, dans une fonction appelée `setLangStrings()`.

<a id="key-process"></a>
### Processus clé :

* Rassemble toutes les chaînes de langue potentielles (`sprintf`, `JText`, etc.)
* Les convertit en un tableau standardisé d'entrées de langue
* Construit un tableau maître `langContent` classé par zone :

  * `admin`
  * `site`
  * `system`
  * `both`

Lors de la compilation, JCB place chaque paire clé/valeur de langue dans le fichier approprié pour le contexte correct.

---

<a id="5-adding-strings-to-language-files"></a>
## 5. Ajout de chaînes aux fichiers de langue

[00:06:04](https://www.youtube.com/watch?v=zzAcVkn_cWU&t=364s)

Lorsque la compilation atteint l'étape finale :

* Les fonctions `setLangAdmin`, `setLangSite` et `setLangSys` de **Interpreter** gèrent la création de fichiers.
* Chaque zone (admin/site/système) reçoit son fichier `en-GB` `.ini` correspondant.
* Toutes les chaînes par défaut et générées dynamiquement sont ajoutées.

Cela garantit qu'aucune chaîne de langue codée en dur n'est perdue lors de la compilation du composant.

---

<a id="6-multi-language-string-implementation"></a>
## 6. Implémentation de chaînes multilingues

[00:07:09](https://www.youtube.com/watch?v=zzAcVkn_cWU&t=429s)

Le système multilingue vérifie dans la base de données les chaînes anglaises existantes et détermine si des traductions existent déjà.

<a id="process-summary"></a>
### Résumé du processus :

1. JCB compile le composant et rassemble toutes les chaînes anglaises.
2. Il vérifie la **Table de base de données de traduction** :

* Si une chaîne existe, les traductions sont récupérées.
   * Si elle est nouvelle, la chaîne est insérée en tant qu'entrée en anglais.
3. Les traductions sont regroupées par :

* Balise de langue
   * Zone de composants
4. Les méthodes `getMultipleLangStrings`, `setLangPlaceholders` et `purgeLanguageStrings` effectuent ce travail.

Ces fonctions résident dans `a_Get.php` (open source).

---

<a id="7-reintegrating-translations-during-compilation"></a>
## 7. Réintégrer les traductions lors de la compilation

[00:09:13](https://www.youtube.com/watch?v=zzAcVkn_cWU&t=553s)

Après avoir récupéré les traductions, JCB les réinjecte dans le composant compilé.
Lors de la construction, chaque chaîne est évaluée et fusionnée dans les fichiers `.ini` correspondant à sa langue cible.

Vous pouvez voir cela en action en compilant n'importe quel composant (par exemple, "Document Manager").
JCB va automatiquement :

* Collectez toutes les chaînes anglaises
* Faire correspondre les traductions de la base de données
* Générer des fichiers de langue traduits par langue

---

<a id="8-purging-unused-strings"></a>
## 8. Purger les chaînes inutilisées

[00:10:05](https://www.youtube.com/watch?v=zzAcVkn_cWU&t=605s)

Lorsque les noms ou les descriptions des champs changent, certaines anciennes chaînes peuvent ne plus être nécessaires.
JCB utilise un **mécanisme de purge intelligent** pour gérer cela.

<a id="how-purging-works"></a>
### Comment fonctionne la purge

1. JCB détecte les chaînes inutilisées lors de la compilation.
2. Il vérifie si d'autres composants y font toujours référence.

* ✅ Si un autre composant l'utilise → la chaîne est conservée.
   * ❌ Si inutilisé quelque part :

* Si traduit → déplacé vers l'état **Archivé**.
     * Si non traduit → supprimé.

Cela préserve un travail de traduction précieux tout en nettoyant les entrées obsolètes.

---

<a id="9-translation-tab-in-component-view"></a>
## 9. Onglet Traduction dans la vue des composants

[00:12:14](https://www.youtube.com/watch?v=zzAcVkn_cWU&t=734s)

Chaque composant de JCB inclut désormais un **onglet Traduction** sous ses paramètres.

<a id="features"></a>
### Caractéristiques:

* Affiche toutes les chaînes anglaises liées à ce composant.
* Indique si une traduction existe.
* Répertorie le nombre de composants utilisant chaque chaîne.
* Permet de visualiser mais pas de modifier les chaînes source anglaises.
* Permet d'ajouter ou de modifier des traductions dans un nombre illimité de langues.

Une fois enregistrées, les traductions se propagent automatiquement à tous les composants liés.

---

<a id="10-accessing-translation-data"></a>
## 10. Accéder aux données de traduction

<a id="a-via-component"></a>
### A. Via un composant

[00:13:21](https://www.youtube.com/watch?v=zzAcVkn_cWU&t=801s)

L'onglet Traduction de chaque composant vous permet de :

* Afficher les chaînes spécifiques aux composants.
* Importer/exporter des ensembles de traduction pour la collaboration.

* Utile pour envoyer des packs de langue aux traducteurs.
  * Les fichiers traduits renvoyés peuvent être importés et automatiquement liés.

*(Cette fonctionnalité est en cours de développement.)*

<a id="b-via-global-language-translations"></a>
### B. Via les « traductions linguistiques » globales

[00:14:03](https://www.youtube.com/watch?v=zzAcVkn_cWU&t=843s)

Vous pouvez également ouvrir **Composants → Traductions de langues** pour gérer **toutes les chaînes de composants ensemble**.

* Affiche efficacement des milliers d'entrées (même plus de 8 000 lignes).
* Prend en charge le filtrage par statut actif/archivé.
* Permet la gestion groupée des traductions entre les composants.

---

<a id="11-community-translation-sharing"></a>
## 11. Partage de traduction communautaire

[00:15:15](https://www.youtube.com/watch?v=zzAcVkn_cWU&t=915s)

Une future amélioration à l'étude est un **échange de traduction communautaire**, permettant aux utilisateurs de :

* Transférez les chaînes anglaises vers un référentiel partagé.
* Extrayez les traductions existantes pour les réutiliser.

La contribution de la communauté est encouragée – ouvrez les suggestions et les problèmes sur [GitHub](https://github.com/vdm-io/Joomla-Component-Builder).

---

<a id="pro-tips"></a>
## Conseils de pro

* Marquez toujours le texte de l'interface utilisateur comme traduisible lors de la définition de champs ou de la rédaction de modèles.
* Utilisez des clés d'espace réservé cohérentes et descriptives (par exemple, `COM_YOURCOMPONENT_FIELD_LABEL`).
* Vérifiez régulièrement l'onglet Traduction pour détecter les chaînes nouvelles ou manquantes.
* Avant de compiler des composants volumineux, purgez les anciennes chaînes pour maintenir l'efficacité.
* Exportez les traductions avant les mises à jour majeures pour la sauvegarde et la collaboration.

---

<a id="summary-of-key-jcb-classes--methods"></a>
## Résumé des classes et méthodes clés de JCB

| Classe | Fonctions clés | Objectif |
| ----------- | --------------------------------------------------------------------------------- | ----------------------------------------- |
| `a_Get.php` | `setLangStrings`, `getMultipleLangStrings`, `purgeLanguageStrings` | Extraire et gérer des chaînes multilingues |
| Interprète | `setLangAdmin`, `setLangSite`, `setLangSys` | Écrire des chaînes dans les fichiers `.ini` respectifs |
| Infusion | Fusionne les données de langue par défaut et dynamiques | Compilation finale des fichiers de traduction |

---

<a id="final-thoughts"></a>
## Réflexions finales

Le **Translation Manager** de Joomla Component Builder automatise l'une des parties les plus chronophages du développement de composants multilingues.
En centralisant toute la logique de traduction, la détection de chaînes et la purge au sein de JCB, les développeurs peuvent se concentrer sur les fonctionnalités tout en conservant des extensions entièrement traduisibles.

---

> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="jcb-manual-custom-code"></a>
# Code personnalisé manuel JCB

[00:00:01](https://www.youtube.com/watch?v=KiAtJawZ3oo&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m01s)
(_Cliquez sur ces liens horaires pour voir la vidéo Youtube_)

<a id="1-introduction"></a>
## 1. Introduction

**[00:00:01](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h00m01s)**

L'*importation automatique du code personnalisé* est l'une des fonctionnalités les plus innovantes de JCB, conçue pour rendre la gestion et la réutilisation du code personnalisé dans votre composant faciles et efficaces.

Lorsqu'elle est activée, cette fonctionnalité permet à JCB de détecter et d'extraire automatiquement les scripts personnalisés que vous avez ajoutés directement dans votre composant compilé (dans votre installation Joomla), et de réimporter ces scripts dans la base de données JCB lors de la prochaine compilation.

Cela garantit que toutes les modifications manuelles que vous avez apportées à la base de code de votre composant installé sont préservées et synchronisées avec les données de votre composant JCB.

---

<a id="2-how-the-automatic-code-import-works"></a>
## 2. Comment fonctionne l'importation automatique de code

**[00:00:52](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h00m52s)**

À l'origine, cette fonctionnalité visait à vous permettre de modifier le code du composant généré directement dans Joomla, puis de le recompiler dans JCB sans perdre ces modifications.

Cependant, il a évolué vers deux systèmes complémentaires :

1. **Synchronisation automatique du code à l'aide de références de hachage**.
2. **Gestion manuelle du code via des espaces réservés JCB**.

---

<a id="21-why-line-numbers-arent-used"></a>
### 2.1 Pourquoi les numéros de ligne ne sont pas utilisés

**[00:01:43](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h01m43s)**

JCB ne s'appuie **pas** sur les numéros de ligne pour localiser l'endroit où votre code personnalisé doit être inséré. Étant donné que les numéros de ligne changent à mesure que le code change, cela entraînerait des insertions ou des écrasements dans des positions incorrectes.

Au lieu de cela, JCB utilise des **empreintes digitales basées sur le hachage** :

* Un hachage est calculé à partir de plusieurs lignes **au-dessus et en dessous** de votre bloc de code personnalisé.
* Cela fournit une référence stable et contextuelle même si la structure du fichier change.

**[00:02:50](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h02m50s)**
Le nombre de lignes environnantes utilisées pour cette empreinte digitale peut varier, mais il varie généralement de **6 à 10 lignes** pour des raisons de stabilité.

---

<a id="3-updating-code-from-jcb-in-the-editor"></a>
## 3. Mise à jour du code de JCB dans l'éditeur

**[00:03:01](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h03m01s)**

Dans le système de compilation de JCB, la fonction responsable de l'analyse et de la synchronisation du code personnalisé est :

```php
searchfilecontent()
```

Cette fonction fait partie du fichier du compilateur **Aget**. Il:

* Lit les fichiers sources PHP ou JavaScript de votre composant.
* Détecte les balises d'espace réservé.
* Collecte les lignes entre ces espaces réservés.
* Stocke ce code dans la base de données de JCB pour le réutiliser lors de la recompilation.

**[00:04:27](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h04m27s)**
Pour éviter une utilisation excessive de la mémoire, JCB veille à ce que le tableau d'empreintes digitales ne dépasse jamais 10 lignes.

---

<a id="4-insert-and-replace-placeholders"></a>
## 4. Insérer et remplacer des espaces réservés

**[00:05:43](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h05m43s)**

JCB utilise des **espaces réservés** dans le code pour déterminer où le code personnalisé est inséré ou remplacé.

Deux types d'espace réservé sont disponibles :

<a id="insert-placeholder"></a>
### Insérer un espace réservé

```php
///***[INSERT<>$$$$]***///
Your custom code here
///***[INSERT<>$$$$]***///
```

<a id="replace-placeholder"></a>
### Remplacer l'espace réservé

```php
///***[REPLACE<>$$$$]***///
Code to replace
///***[REPLACE<>$$$$]***///
```

**[00:07:25](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h07m25s)**
Après compilation :

* `INSERT<>` devient `INSERTED$$$`
* `REPLACE<>` devient `REPLACED$$$`

Cela indique que le code a été importé avec succès.

---

<a id="important-note"></a>
### Remarque importante

**[00:08:49](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h08m49s)**
Ne modifiez **pas** l'identifiant numérique qui suit un espace réservé. Ce numéro identifie l'entrée dans la base de données de votre code stocké. Le modifier entraînera la perte par JCB de ce script personnalisé.

Pour relancer les mises à jour manuellement, **ajoutez le symbole en forme de losange (<>)** dans votre espace réservé - cela signale à JCB que le bloc de code a été modifié et doit être réimporté lors de la prochaine compilation.

---

<a id="5-jcb-manual-custom-code-option"></a>
## 5. Option de code personnalisé manuel JCB

**[00:11:52](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h11m52s)**

Parallèlement à l'automatisation du hachage, JCB propose un **Mode manuel** pour la gestion du code personnalisé.
Cette option permet aux développeurs de définir des extraits de code personnalisés réutilisables dans JCB lui-même, d'attribuer des espaces réservés et d'injecter dynamiquement des valeurs lors de la compilation.

---

<a id="51-creating-a-manual-custom-code"></a>
### 5.1 Création d'un code personnalisé manuel

**[00:12:47](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h12m47s)**

1. Ouvrez la section **Code personnalisé** dans JCB.
2. Créez un nouveau script personnalisé et sélectionnez **"JCB Manual"** comme méthode.
3. Copiez l'**espace réservé** fourni, par exemple :

   ```
   [CUSTOMCODE=myReusableBlock]
   ```

> 📌 **Remarque sur l'héritage :** les anciennes vidéos et exportations peuvent toujours afficher la syntaxe d'espace réservé arrondi `(((customcode)))`. JCB standardise désormais le format `[CUSTOMCODE=...]` entre crochets afin que la transmission des arguments soit explicite.

4. Collez cet espace réservé dans votre **champ**, **vue** ou **mise en page** où le code doit apparaître. Vous pouvez intégrer des codes personnalisés manuels dans n'importe quel bloc PHP, XML, HTML ou JavaScript rendu par JCB.

---

<a id="52-example-reusable-javascript-code"></a>
### 5.2 Exemple : code JavaScript réutilisable

**[00:13:52](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h13m52s)**

Supposons que vous disposiez d'un champ glisser-déposer pour télécharger des images, contenant du JavaScript pour le comportement de l'interface utilisateur. Au lieu de dupliquer le script sur plusieurs champs, vous pouvez :

* Déplacez le script vers la zone Code personnalisé de JCB.
* Remplacez le texte dynamique tel que `image`, `teaser`, etc. par des **espaces réservés arg**.
* Insérez l'espace réservé là où cela est nécessaire, par exemple `[CUSTOMCODE=myReusableBlock]` ou `[CUSTOMCODE=myReusableBlock+image,image,teaser]` lors du passage des arguments.

---

<a id="53-using-arg-placeholders"></a>
### 5.3 Utilisation des espaces réservés ARG

**[00:15:19](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h15m19s)**

Le code personnalisé peut inclure des **valeurs arg**, agissant comme des variables transmises lors de la compilation.

Exemple d'utilisation d'un espace réservé :

```text
[CUSTOMCODE=myReusableBlock+image,image,teaser]
```

Dans votre script, référencez les valeurs avec des espaces réservés de base zéro :

```php
[[[arg0]]] // image
[[[arg1]]] // image
[[[arg2]]] // teaser
```

Si vous devez inclure des caractères réservés tels que des virgules ou des signes plus dans les arguments, encodez-les sous forme d'entités HTML (`&#44;`, `&#43;`, `&#61;`, etc.) avant de compiler.

**Règles pour les espaces réservés ARG :**

* Encodez les caractères réservés (`[`, `]`, `,`, `+`, `=`) à l'aide d'entités HTML avant de les transmettre comme arguments.
* Vous pouvez inclure `$` si nécessaire.
* Le nombre d'arguments doit **correspondre** au nombre d'espaces réservés dans le code.

---

<a id="6-editor-changes-vs-custom-code-updates"></a>
## 6. Modifications de l'éditeur et mises à jour du code personnalisé

**[00:18:39](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h18m39s)**

* **Code personnalisé statique** (sans argument) : peut être modifié directement dans l'éditeur Joomla, et JCB réimportera ces modifications.
* **Code dynamique** (avec espaces réservés ARG) : impossible de synchroniser automatiquement les modifications externes dans JCB.

Pour garantir la stabilité, JCB évite actuellement de réimporter les modifications provenant de modifications externes lorsque des ARG sont utilisés, car les valeurs peuvent varier selon plusieurs points d'utilisation.

**[00:22:22](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h22m22s)**
Les futures mises à jour visent à unifier les deux systèmes, permettant à JCB de réimporter en toute sécurité les modifications de code dynamiques depuis l'éditeur.

---

<a id="7-component-and-view-placeholders"></a>
## 7. Espaces réservés pour les composants et les vues

**[00:23:43](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h23m43s)**

Les espaces réservés supplémentaires pour la dénomination dynamique incluent :

* `(((view)))` → remplacé par le nom de la vue actuelle (minuscules).
* `[[[Component]]]` → remplacé par le nom de votre composant (majuscule).

Exemple de cas d'utilisation :

```js
console.log('Loaded view: (((view))) for [[[Component]]]');
```

Lors de la compilation, JCB les remplace automatiquement en fonction du contexte.

---

<a id="8-compilation-and-testing"></a>
## 8. Compilation et tests

**[00:25:11](https://www.youtube.com/watch?v=KiAtJawZ3oo&t=00h25m11s)**

Après avoir configuré le code personnalisé et les espaces réservés :

1. Compilez votre composant.
2. Installez le package généré.
3. Inspectez la zone de code où votre code personnalisé doit apparaître.

* Confirmez que les ARG ont été remplacés.
   * Vérifiez que le script apparaît à la position prévue.

L'exemple de composant utilisé dans le didacticiel était **"Registry"**, démontrant l'injection de script au niveau du champ lors de la compilation.

---

<a id="9-summary-and-best-practices"></a>
## 9. Résumé et meilleures pratiques

* Utilisez le **Code personnalisé manuel** pour les extraits réutilisables qui nécessitent des espaces réservés dynamiques.
* Utilisez **Automatic Hash Import** pour les modifications directes à l'intérieur des composants compilés.
* Conservez toujours une syntaxe d'espace réservé cohérente (`///***[INSERT<>$$$$]***///`).
* Évitez de modifier les marqueurs d'identification de la base de données.
* Pour mettre à jour manuellement le code stocké, **ajoutez le symbole du diamant (<>)** pour déclencher la réimportation.
* Gardez les valeurs ARG simples et alignées avec vos espaces réservés.

---

<a id="tip"></a>
### Conseil

Si vous réutilisez souvent des extraits JavaScript ou PHP complexes dans des vues, des champs ou des mises en page, stockez-les dans le **Custom Code Manager** de JCB. Il réduit considérablement la redondance et maintient la cohérence de votre composant lors des mises à jour.

---

Souhaitez-vous que je formate ceci sous la forme d'une **page de documentation JCB prête à être publiée** (avec des éléments de présentation, une introduction et un style cohérent utilisé dans les manuels précédents de votre projet) ?
Cela le rendrait prêt à être inclus dans votre série JCB Docs.

---

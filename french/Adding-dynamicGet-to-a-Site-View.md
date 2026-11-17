> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="adding-dynamicget-to-a-site-view"></a>
# Ajout de DynamicGet à une vue de site

<a id="checking-the-target-dataset"></a>
### Vérification de l'ensemble de données cible

[00:00:00](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m57s)

Maintenant que DynamicGet est en place, l'étape suivante consiste à **l'ajouter à une vue de site** et à observer son fonctionnement au sein du composant. Dans le flux de travail Site View actualisé, le Dynamic Get principal ancre les données qui circulent dans vos modèles et mises en page, tandis que les Gets personnalisés supplémentaires alimentent les espaces réservés de code réutilisables, les chargeurs AJAX ou les widgets d'interface utilisateur alimentés par la bibliothèque.

1. Accédez à **Vues du site** dans Joomla Component Builder.
2. Cliquez sur **Nouveau** pour créer une nouvelle vue du site.
3. Pour cet exemple, puisqu'une vue de site existe déjà, ouvrez la vue **Preacher**.

Cette configuration vous permettra de connecter les méthodes DynamicGet précédemment créées à votre vue de site.

---

<a id="populate-fields-from-gets"></a>
### Remplir les champs à partir de Get

[00:00:32](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m32s)

Sur le côté droit de l'éditeur Site View, vous trouverez **trois champs clés** pour renseigner les méthodes DynamicGet :

1. **DynamicGets personnalisés** -

* Ajoutez ici une ou plusieurs méthodes DynamicGet personnalisées.
   * Il s'agit de requêtes ou d'ensembles de données supplémentaires que vous souhaiterez peut-être utiliser dans la même vue.

2. **DynamicGet principal** -

* This is the **primary** DynamicGet method.
   * Un seul DynamicGet principal peut être ajouté par vue de site.
   * Il détermine comment le modèle récupère les données (via `getItem` ou `getItems`).

3. **DynamicGets personnalisés (facultatif)** -

* Vous pouvez inclure autant de DynamicGets personnalisés que nécessaire.
   * Ceux-ci fourniront des objets de données supplémentaires à la vue.

> **Conseil :** Le DynamicGet principal détermine si les données récupérées sont une liste (`getItems`) ou un élément unique (`getItem`).

---

<a id="dynamic-values"></a>
### Valeurs dynamiques

[00:01:36](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m36s)

Le **troisième champ** de l'éditeur Site View est destiné aux **Valeurs dynamiques**.
Il s'agit d'extraits de code générés automatiquement pour vous aider à implémenter les données DynamicGet dans votre vue.

Vous pouvez sélectionner :

* **Main Gets** - affiche les données du DynamicGet principal.
* **Custom Gets** - affichez les données de vos DynamicGets personnalisés.
* **Les deux** - affiche toutes les options DynamicGet ensemble.

[00:02:04](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m04s)

Lorsque vous sélectionnez un get principal, il affiche une **impression d'exemples de code** montrant comment accéder à l'ensemble de résultats dans vos vues.

[00:02:32](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m32s)

Chaque bloc de code peut être copié facilement :

* **Cliquez avec le bouton droit et copiez** ou utilisez **Ctrl+C / Cmd+C**.
* Vous pouvez également sélectionner uniquement une partie du code (par exemple, sans l'instruction `echo`).

[00:03:05](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m05s)

> **Remarque pour les utilisateurs de macOS :** Une fois que vous relâchez la souris, macOS peut sélectionner automatiquement le bloc complet. Pour copier une partie, appuyez sur **Cmd+C** avant de relâcher.

---

<a id="inserting-values-into-view"></a>
### Insertion de valeurs dans la vue

[00:03:36](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m36s)

Utilisez le code **Dynamic Values** dans le modèle PHP de votre vue pour afficher les données récupérées.
Par exemple, dans la vue Prédicateur :

* Assurez-vous d'avoir un objet Preacher valide.
* Utilisez l'extrait de code fourni pour **vérifier si les principaux éléments de données sont chargés** sur la page.
* Les principaux éléments typiques incluent `sermons`, `preacher.id` ou l'ensemble de données `getList`.

[00:04:08](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m08s)

Ces éléments sont stockés dans des tableaux (`items`) qui peuvent être parcourus en boucle pour afficher les données de manière dynamique.

[00:04:38](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m38s)

Les modèles sont ensuite utilisés pour gérer différentes **dispositions d'affichage** pour ces données.

---

<a id="making-use-of-data-being-passed-through-to-the-view"></a>
### Utilisation des données transmises à la vue

[00:05:19](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m19s)

Chaque Get personnalisé fournit une structure de données qui définit la manière dont ses résultats sont compressés et transmis à la vue.

[00:05:36](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m36s)

Par exemple:

* Une méthode nommée `numbersermons` rendrait ses données disponibles sous le nom `$this->numbersermons`.
* Cette structure peut varier en fonction de la manière dont vous modifiez le code personnalisé de votre composant.

> **Conseil :** Utilisez les valeurs dynamiques pour prévisualiser l'apparence des données avant d'apporter des modifications personnalisées.

---

<a id="var-dump"></a>
### Var Dump

[00:06:13](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m13s)

Pour comprendre la structure de votre ensemble de données :

1. Insérez un `var_dump()` au point de données souhaité dans votre modèle.
2. Reconstruisez le composant.
3. Affichez la sortie sur le frontend pour inspecter la structure des données.

[00:06:45](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m45s)

Cela permet d'identifier si les données sont un tableau, un objet ou une structure imbriquée, vous permettant d'ajuster votre logique d'accès en conséquence.

[00:07:20](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m20s)

Répétez cette étape pour d’autres Gets personnalisés si nécessaire pour vérifier leurs structures de données.

---

<a id="gets-in-the-code-eg-preacherphp"></a>
### Entre dans le code (par exemple, Preacher.php)

[00:07:33](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m33s)

Pour voir comment les récupérations personnalisées deviennent disponibles dans votre vue de site, ouvrez le **fichier modèle** - par exemple, `preacher.php`.

[00:07:55](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m55s)

À l’intérieur du modèle, localisez la méthode `getListQuery()`.
Ici, vous verrez comment les tables principales et jointes sont définies :

* `sermon` as `a`
* `series` as `c`
* `preacher` as `d`
* `categories` as `b`

[00:08:18](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m18s)

Ces jointures déterminent la manière dont les données sont récupérées, filtrées et renvoyées à la vue.

[00:08:41](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m41s)

De retour dans l'interface JCB, vous remarquerez que le DynamicGet principal (par exemple, `sermon (preacher.id) getlist`) correspond à la structure utilisée dans ce modèle.

---

<a id="looking-at-the-dynamic-get"></a>
### En regardant le Get dynamique

[00:09:06](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m06s)

Lors de l'affichage de la définition DynamicGet dans JCB :

* `Sermon` est défini comme table principale (`a`).
* `Series` (`c`) et `Preacher` (`d`) sont joints pour les valeurs de sélection.
* `Statistics` (`e`) est une jointure **liste**, c'est-à-dire plusieurs entrées.
* `Category` (`b`) est ajouté en tant que jointure **unique**.

[00:10:01](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m01s)

Dans le code, cette configuration apparaît dans `getItem()` et ses méthodes de support, garantissant que les statistiques et les données associées sont disponibles pour chaque élément.

[00:10:30](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m30s)

Des méthodes personnalisées définies dans DynamicGet peuvent également être ajoutées pour renvoyer des valeurs supplémentaires à utiliser dans la vue du site.

---

<a id="preacher-viewhtmlphp-generated-code"></a>
### Preacher view.html.php Code généré

[00:10:55](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m55s)

Dans le fichier **view.html.php** généré pour la vue Preacher :

* La méthode `getItems()` récupère l'ensemble de données du modèle.
* Ces éléments sont ensuite stockés sous le nom `$this->items` dans la classe de vue, ce qui les rend disponibles pour une utilisation dans vos modèles.

[00:11:26](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m26s)

La sélection du DynamicGet correspondant dans JCB montre que les variables correspondent aux champs de code générés (comme `id`, `asset_id`, etc.).

---

<a id="checking-the-target-datasets"></a>
### Vérification des ensembles de données cibles

[00:11:48](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m48s)

En inspectant plus profondément le code, vous remarquerez des clés telles que `idsermonstatisticsE`, qui représentent des valeurs de tableau contenant d'autres sous-tableaux.

[00:12:03](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m03s)

Vous pouvez cibler ces ensembles de données en référençant leurs clés correspondantes.

[00:12:28](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m28s)

Chaque **Obtention personnalisée** (telle que `preacher` ou `numberdownloads`) apporte sa propre structure de données accessible depuis la vue.

[00:12:53](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m53s)

Dans le fichier `view.html.php`, ces valeurs sont liées à des variables comme `$this->preachernumberdownloads` ou `$this->numbersermons`.

---

<a id="site-preacher-tmpl-folder"></a>
### Dossier Tmpl du prédicateur du site

[00:13:33](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m33s)

Tous les modèles de vue de site sont stockés sous :
`/components/com_yourcomponent/views/preacher/tmpl/`

[00:13:50](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m50s)

Le fichier **default.php** représente la présentation de sortie principale, tandis que d'autres modèles de présentation (dans le dossier `layouts`) peuvent étendre ou remplacer cette présentation par défaut.

[00:14:24](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m24s)

---

<a id="keep-data-powered-views-maintainable"></a>
### Maintenir les vues basées sur les données

Les Gets dynamiques, les modèles et les bibliothèques sont contrôlés en version dans les référentiels JCB. Lorsqu'une vue de site maintenue est mise à jour, sélectionnez-la dans JCB et cliquez sur **Réinitialiser** pour extraire les dernières liaisons Dynamic Get et la structure de mise en page, puis recompilez. Si votre projet a besoin d'une variante sur mesure, créez le référentiel, pointez JCB vers votre copie et continuez à faire évoluer vos espaces réservés de code personnalisé en synchronisation avec votre modèle de données.

---

<a id="summary"></a>
## Résumé

En liant un **DynamicGet** à une **Site View** :

* Vous permettez à JCB de charger automatiquement des structures de données jointes complexes dans votre vue frontale.
* Utilisez **Valeurs dynamiques** pour prévisualiser et insérer des extraits de code permettant d'accéder à ces données.
* Inspectez les ensembles de données à l'aide de `var_dump()` pour comprendre leur structure.
* Affichez les résultats de manière dynamique via vos modèles de vue et vos mises en page.

> **Étape suivante :** Expérimentez en créant vos propres Gets personnalisés, attachez-les à différentes vues de site et examinez le code du modèle généré pour comprendre comment JCB automatise ce flux de données.

---

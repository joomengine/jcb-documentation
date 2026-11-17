> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="adding-templates-and-layouts-to-a-site-view"></a>
# **Ajout de modèles et de mises en page à une vue de site**

<a id="understanding-the-relationship-between-templates-and-layouts"></a>
### Comprendre la relation entre les modèles et les mises en page

[00:00:00](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(*Cliquez sur l'horodatage pour ouvrir la vidéo sur YouTube.*)

Après avoir ajouté un **Dynamic Get** à une vue de site, il est essentiel de comprendre comment les **modèles** et les **mises en page** s'intègrent à ces vues. Les modèles agissent comme des wrappers de haut niveau qui orchestrent HTML, PHP, les mises en page réutilisables et tous les espaces réservés de code personnalisé ou bibliothèques frontales que vous attachez à la vue. Cette section vous montre où réside chaque morceau de code, comment Joomla le charge et comment JCB les structure lors de la compilation des composants.

> **Nouveau dans les modèles JCB ?** Considérez-les comme des structures de vue modulaires pouvant inclure d'autres modèles, des présentations d'appels et même être synchronisées à partir de référentiels partagés. Maîtriser la façon dont ils enveloppent votre logique de vue rendra le reste de ce didacticiel beaucoup plus facile à suivre.

---

<a id="1-exploring-templates-in-a-site-view"></a>
## **1. Explorer les modèles dans une vue de site**

<a id="example-preacher-view"></a>
### Exemple : *Vue Prédicateur*

[00:00:33](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h00m33s)

Dans l'exemple **Sermon Distributor** (`/components/com_sermondistributor/views/preacher/tmpl/`), vous trouverez plusieurs fichiers PHP, tels que :

```
default.php
default_preacherbox.php
default_preacherpanel.php
default_preachersmall.php
```

[00:00:58](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h00m58s)

Chacun d'eux est un **modèle**, et ils sont reconnus comme tels en raison de la façon dont ils sont inclus dans le fichier par défaut.

---

<a id="the-default-file---the-site-view-core"></a>
### **Le fichier par défaut - Le noyau de la vue du site**

[00:01:18](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h01m18s)

Le fichier `default.php` est le fichier principal de la vue du site - essentiellement **le point d'entrée de la vue**.
Dans ce fichier, les modèles sont chargés et rendus.
Lorsque vous ouvrez l'**éditeur Site View dans JCB**, le code qui y est affiché correspond directement au contenu de ce fichier par défaut.

---

<a id="locating-template-snippets-in-jcb"></a>
### **Localisation des extraits de modèle dans JCB**

[00:01:50](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h01m50s)

Au bas d'une vue de site dans JCB, vous trouverez les **appels d'extraits de modèle**, tels que :

```php
$this->loadTemplate('preacherpanel');
```

[00:02:19](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h02m19s)

Vous pouvez voir des options de modèle telles que :

```
preacher, grid, list, table, panel, box, small
```

Ces extraits font référence aux fichiers modèles associés que JCB compile dans votre composant.

---

<a id="switching-between-php-and-html-in-templates"></a>
### **Basculer entre PHP et HTML dans les modèles**

[00:02:37](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h02m37s)

Les modèles peuvent mélanger PHP et HTML. Par exemple:

```php
<?php if ($this->preacher) : ?>
    <div class="uk-card uk-card-default">
        <?php echo $this->preacher->name; ?>
    </div>
<?php endif; ?>
```

[00:03:04](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h03m04s)

Cette structure vous permet d'alterner entre les blocs PHP et HTML selon les besoins pour une conception claire de l'interface utilisateur et une séparation logique.

---

<a id="2-how-jcb-integrates-templates-into-site-views"></a>
## **2. Comment JCB intègre les modèles dans les vues du site**

[00:03:31](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h03m31s)

Dans le composant compilé, ouvrez `default.php` pour confirmer l'inclusion du modèle.
Vous remarquerez les mêmes transitions PHP vers HTML reflétées dans le code généré.

[00:04:22](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h04m22s)

Les modèles ont accès à tous les **champs globaux et méthodes de classe** disponibles dans la vue par défaut.
Par exemple, les deux peuvent accéder :

```php
$this->preacher;
$this->params;
```

[00:05:07](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h05m07s)

Lorsque vous placez un extrait tel que `$this->loadTemplate('preacherpanel');` dans le code Site View, JCB le lie automatiquement au fichier modèle correspondant sous `tmpl/`.
C'est ainsi que les **modèles font partie de la vue du site** lors de la compilation.

---

<a id="3-working-with-layouts"></a>
## **3. Travailler avec des mises en page**

<a id="quick-layout-example"></a>
### **Exemple de mise en page rapide**

[00:05:52](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h05m52s)

Les mises en page sont utilisées différemment des modèles. Alors que les modèles structurent l'affichage d'une vue unique, les **mises en page** sont des éléments d'affichage réutilisables qui peuvent être partagés entre plusieurs modèles ou vues.

[00:06:53](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h06m53s)

Dans les conventions Joomla :

* **Les modèles** peuvent inclure d'autres **modèles**,
* **Les mises en page** peuvent inclure d'autres **mises en page**,
* Mais les modèles ne peuvent pas inclure directement les mises en page.

[00:07:44](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h07m44s)

Ces règles proviennent de la façon dont Joomla implémente le rendu, et non des limitations de JCB.

> 📚 **Besoin du flux de travail du référentiel ?** Lisez le [Guide des mises en page JCB](./JCB-Layouts.md) pour voir comment les options Init, Reset, Push et Fork maintiennent ces fichiers réutilisables alignés avec les référentiels de mise en page partagés.

---

<a id="passing-data-into-layouts"></a>
### **Transmission de données dans des mises en page**

[00:08:02](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h08m02s)

Les mises en page n'ont pas automatiquement accès à la même étendue `$this` que les modèles.
Vous devez **passer les variables manuellement** lors de leur rendu :

```php
echo JLayoutHelper::render('my_layout', ['items' => $this->items]);
```

Cela permet un contrôle précis sur les données reçues par chaque mise en page.

[00:08:53](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h08m53s)

Dans JCB, lors de la création d'une mise en page, vous pouvez choisir quel **ensemble de données Dynamic Get** est disponible. Cependant, la mise en page elle-même n'affectera pas le modèle de données de la vue du site : elle est uniquement destinée à l'affichage.

---

<a id="adding-layouts-to-the-component"></a>
### **Ajout de mises en page au composant**

[00:09:51](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h09m51s)

Lorsque vous incluez un extrait de mise en page (par exemple, dans la vue du site par défaut), JCB garantit que le fichier de mise en page correspondant est créé dans le répertoire `/layouts/` de votre composant.
Cela permet à cette mise en page d'être réutilisée dans d'autres modèles et vues selon les besoins.

[00:10:19](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h10m19s)

> **Conseil :** Les mises en page et les modèles fonctionnent de manière identique dans les **Vues d'administration personnalisées** de JCB.
> Les deux s'appuient sur des extraits pour inclure et restituer le contenu de manière modulaire.

---

<a id="4-summary-of-template-and-layout-integration"></a>
## **4. Résumé de l'intégration des modèles et de la mise en page**

[00:11:10](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h11m10s)

En combinant efficacement les modèles et les mises en page :

* Vous gardez le code modulaire et maintenable.
* Vous pouvez réutiliser des structures communes dans plusieurs vues.
* Component Builder automatise leur liaison via des extraits lors de la compilation.

Les **Modèles** forment le squelette visuel de chaque vue.
Les **mises en page** vous permettent d'organiser des blocs de code plus petits pour une utilisation répétée dans votre composant.

---

<a id="key-takeaways"></a>
### **Points clés à retenir**

* Les modèles résident dans le dossier `tmpl/` de chaque vue et sont ajoutés à l'aide de `$this->loadTemplate('name');`.
* Les mises en page sont des morceaux de code partagés stockés dans `/layouts/`, ajoutés à l'aide de `JLayoutHelper::render()`.
* Les modèles ont accès à `$this` et à toutes les propriétés de vue globale.
* Les mises en page nécessitent un passage explicite de variables.
* Les conventions de Joomla régissent la manière dont les modèles et les mises en page peuvent être imbriqués.
* L'onglet **Modèles** de JCB vous permet d'importer, de réinitialiser ou de transférer ces wrappers à partir de référentiels de modèles afin que les équipes restent synchronisées.

Lorsqu'une vue de site partagée évolue, sélectionnez-la dans JCB et choisissez **Réinitialiser** pour synchroniser les références de modèle, de mise en page et de bibliothèque avec la version maintenue avant de recompiler. Si votre équipe a besoin d'une expérience divergente à long terme, créez le référentiel de modèles, pointez JCB vers votre fork et conservez le contrôle de version de vos espaces réservés de code personnalisés aux côtés de vos mises en page.

---

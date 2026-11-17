> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

Voici quelques « conseils » lors de l’utilisation de code personnalisé. Pour un aperçu narratif de la manière dont les espaces réservés manuels et l'automatisation du hachage fonctionnent ensemble, lisez [Présentation des codes personnalisés JCB](./JCB-Custom-Codes.md) avant de plonger dans les tableaux de syntaxe ci-dessous.

<a id="the-custom-php-script-placeholders"></a>
# Les espaces réservés de script PHP personnalisés

|UTILISATION|PHP DÉBUT|PHP FIN
|---|---|---|
|Nouveau<br/>Insérer le code|`/***[INSERT<>$$$$]***/`|`/***[/INSERT<>$$$$]***/`|
|Nouveau<br/>Remplacer le code|`/***[REPLACE<>$$$$]***/`|`/***[/REPLACE<>$$$$]***/`|
||**QUAND JCB L'AJOUTE À NOUVEAU**|
|Existant<br/>Code inséré|`/***[INSERTED$$$$]***//*23*/`|`/***[/INSERTED$$$$]***/`|
|Existant<br/>RCode remplacé|`/***[REPLACED$$$$]***//*25*/`|`/***[/REPLACED$$$$]***/`|
||**CHANGEMENT DU CODE PERSONNALISÉ EXISTANT**|
|Mise à jour<br/>Code inséré|`/***[INSERTED<>$$$$]***//*23*/`|`/***[/INSERTED<>$$$$]***/`|
|Mise à jour<br/>RCode remplacé|`/***[REPLACED<>$$$$]***//*25*/`|`/***[/REPLACED<>$$$$]***/`|

> "`/*23*/`" et "`/*25*/`" (ou numéros d'identification similaires) sont l'ID du code dans le système, ne le changez pas !!!!

<a id="the-custom-html-script-placeholders"></a>
# Les espaces réservés de script HTML personnalisés

|UTILISATION|DEBUT HTML|FIN HTML
|---|---|---|
|Nouveau<br/>Insérer le code|`<!--[INSERT<>$$$$]-->`|`<!--[/INSERT<>$$$$]-->`|
|Nouveau<br/>Remplacer le code|`<!--[REPLACE<>$$$$]-->`|`<!--[/REPLACE<>$$$$]-->`|
||**QUAND JCB L'AJOUTE À NOUVEAU**|
|Existant<br/>Code inséré|`<!--[INSERTED$$$$]--><!--23-->`|`<!--[/INSERTED$$$$]-->`|
|Existant<br/>RCode remplacé|`<!--[REPLACED$$$$]--><!--25-->`|`<!--[/REPLACED$$$$]-->`|
||**CHANGEMENT DU CODE PERSONNALISÉ EXISTANT**|
|Mise à jour<br/>Code inséré|`<!--[INSERTED<>$$$$]--><!--23-->`|`<!--[/INSERTED<>$$$$]-->`|
|Mise à jour<br/>RCode remplacé|`<!--[REPLACED<>$$$$]--><!--25-->`|`<!--[/REPLACED<>$$$$]-->`|

> "`<!--23-->`" et "`<!--25-->`" (ou numéros d'identification similaires) sont l'ID du code dans le système, ne le changez pas !!!!

<a id="insert-examples-php"></a>
# Insérer des exemples (PHP)

> l'espace réservé doit être sur sa propre ligne !

<a id="new-php-insert-code"></a>
### Nouveau code d'insertion PHP```php {.line-numbers}
$bar = 'easy';
$foo = 'some code';
/***[INSERT<>$$$$]***/
$var = 4;
/***[/INSERT<>$$$$]***/
$more = 'more some code';
```

### Code d'insertion PHP existant```php {.line-numbers}
$bar = 'easy';
$foo = 'some code';
/***[INSERTED$$$$]***///*23*/
$var = 4;
/***[/INSERTED$$$$]***/
$more = 'more some code';
```

<a id="existing-php-insert-code"></a>
### Mettre à jour le code d'insertion PHP```php {.line-numbers}
$bar = 'easy';
$foo = 'some code';
/***[INSERTED<>$$$$]***///*23*/
$var = 4;
/***[/INSERTED<>$$$$]***/
$more = 'more some code';
```

# Remplacer les exemples (PHP)

> l'espace réservé doit être sur sa propre ligne !

### Nouveau code de remplacement PHP```php {.line-numbers}
$bar = 'easy';
/***[REPLACE<>$$$$]***/
$foo = 'some code changed';
/***[/REPLACE<>$$$$]***/
$more = 'more some code';
```

<a id="update-php-insert-code"></a>
### Code de remplacement PHP existant```php {.line-numbers}
$bar = 'easy';
/***[REPLACED$$$$]***//*25*/
$foo = 'some code changed';
/***[/REPLACED$$$$]***/
$more = 'more some code';
```

### Mettre à jour le code de remplacement PHP```php {.line-numbers}
$bar = 'easy';
/***[REPLACED<>$$$$]***//*25*/
$foo = 'some code changed';
/***[/REPLACED<>$$$$]***/
$more = 'more some code';
```

<a id="replace-examples-php"></a>
# Insérer des exemples (HTML)

> l'espace réservé doit être sur sa propre ligne !

<a id="new-php-replace-code"></a>
### Nouveau code d'insertion HTML```html {.line-numbers}
<div class="easy">
<?php echo '<a href="'.$item->url.'" title="url" >'; ?>
<!--[INSERT<>$$$$]--><!--23-->
<?php echo '<a href="'.$item->new_url.'" title="new url" >'; ?>
<!--[/INSERT<>$$$$]-->
</div>
```

### Code d'insertion HTML existant```html {.line-numbers}
<div class="easy">
<?php echo '<a href="'.$item->url.'" title="url" >'; ?>
<!--[INSERTED$$$$]--><!--23-->
<?php echo '<a href="'.$item->new_url.'" title="new url" >'; ?>
<!--[/INSERTED$$$$]-->
</div>
```

<a id="existing-php-replace-code"></a>
### Mettre à jour le code d'insertion HTML```html {.line-numbers}
<div class="easy">
<?php echo '<a href="'.$item->url.'" title="url" >'; ?>
<!--[INSERTED<>$$$$]--><!--23-->
<?php echo '<a href="'.$item->new_url.'" title="new url" >'; ?>
<!--[/INSERTED<>$$$$]-->
</div>
```

# Remplacer les exemples (HTML)

> l'espace réservé doit être sur sa propre ligne !

### Nouveau code de remplacement HTML```html {.line-numbers}
<div class="easy">
<!--[REPLACE<>$$$$]-->
<?php echo '<a href="'.$item->url.'" title="updated url" >'; ?>
<!--[/REPLACE<>$$$$]-->
</div>
```

<a id="update-php-replace-code"></a>
### Code HTML remplacé existant```html {.line-numbers}
<div class="easy">
<!--[REPLACED$$$$]--><!--25-->
<?php echo '<a href="'.$item->url.'" title="updated url" >'; ?>
<!--[/REPLACED$$$$]-->
</div>
```

### Mettre à jour le code HTML remplacé```html {.line-numbers}
<div class="easy">
<!--[REPLACED<>$$$$]--><!--25-->
<?php echo '<a href="'.$item->url.'" title="updated url" >'; ?>
<!--[/REPLACED<>$$$$]-->
</div>
```
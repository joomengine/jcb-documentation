Here are some 'tips' when using custom code. For a narrative overview of how manual placeholders and hash automation work together, read [JCB! Custom Codes Overview](./JCB-Custom-Codes.md) before diving into the syntax tables below.

# The custom PHP script placeholders

|USAGE|PHP START|PHP END
|---|---|---|
|New<br/>Insert Code|`/***[INSERT<>$$$$]***/`|`/***[/INSERT<>$$$$]***/`|
|New<br/>Replace Code|`/***[REPLACE<>$$$$]***/`|`/***[/REPLACE<>$$$$]***/`|
||**WHEN JCB ADDS IT BACK AGAIN**|
|Existing<br/>Inserted Code|`/***[INSERTED$$$$]***//*23*/`|`/***[/INSERTED$$$$]***/`|
|Existing<br/>Replaced Code|`/***[REPLACED$$$$]***//*25*/`|`/***[/REPLACED$$$$]***/`|
||**CHANGING EXISTING CUSTOM CODE**|
|Update<br/>Inserted Code|`/***[INSERTED<>$$$$]***//*23*/`|`/***[/INSERTED<>$$$$]***/`|
|Update<br/>Replaced Code|`/***[REPLACED<>$$$$]***//*25*/`|`/***[/REPLACED<>$$$$]***/`|

> "`/*23*/`" and "`/*25*/`" (or similar id numbers) are the ID of the code in the system don't change it!!!!

# The custom HTML script placeholders

|USAGE|HTML START|HTML END
|---|---|---|
|New<br/>Insert Code|`<!--[INSERT<>$$$$]-->`|`<!--[/INSERT<>$$$$]-->`|
|New<br/>Replace Code|`<!--[REPLACE<>$$$$]-->`|`<!--[/REPLACE<>$$$$]-->`|
||**WHEN JCB ADDS IT BACK AGAIN**|
|Existing<br/>Inserted Code|`<!--[INSERTED$$$$]--><!--23-->`|`<!--[/INSERTED$$$$]-->`|
|Existing<br/>Replaced Code|`<!--[REPLACED$$$$]--><!--25-->`|`<!--[/REPLACED$$$$]-->`|
||**CHANGING EXISTING CUSTOM CODE**|
|Update<br/>Inserted Code|`<!--[INSERTED<>$$$$]--><!--23-->`|`<!--[/INSERTED<>$$$$]-->`|
|Update<br/>Replaced Code|`<!--[REPLACED<>$$$$]--><!--25-->`|`<!--[/REPLACED<>$$$$]-->`|

> "`<!--23-->`" and "`<!--25-->`" (or similar id numbers) are the ID of the code in the system don't change it!!!!

# Insert Examples (PHP)

> placeholder must be on its own line!

### New PHP Insert Code
```php {.line-numbers}
$bar = 'easy';
$foo = 'some code';
/***[INSERT<>$$$$]***/
$var = 4;
/***[/INSERT<>$$$$]***/
$more = 'more some code';
```

### Existing PHP Insert Code
```php {.line-numbers}
$bar = 'easy';
$foo = 'some code';
/***[INSERTED$$$$]***///*23*/
$var = 4;
/***[/INSERTED$$$$]***/
$more = 'more some code';
```

### Update PHP Insert Code
```php {.line-numbers}
$bar = 'easy';
$foo = 'some code';
/***[INSERTED<>$$$$]***///*23*/
$var = 4;
/***[/INSERTED<>$$$$]***/
$more = 'more some code';
```

# Replace Examples (PHP)

> placeholder must be on its own line!

### New PHP Replace Code
```php {.line-numbers}
$bar = 'easy';
/***[REPLACE<>$$$$]***/
$foo = 'some code changed';
/***[/REPLACE<>$$$$]***/
$more = 'more some code';
```

### Existing PHP Replace Code
```php {.line-numbers}
$bar = 'easy';
/***[REPLACED$$$$]***//*25*/
$foo = 'some code changed';
/***[/REPLACED$$$$]***/
$more = 'more some code';
```

### Update PHP Replace Code
```php {.line-numbers}
$bar = 'easy';
/***[REPLACED<>$$$$]***//*25*/
$foo = 'some code changed';
/***[/REPLACED<>$$$$]***/
$more = 'more some code';
```

# Insert Examples (HTML)

> placeholder must be on its own line!

### New HTML Insert Code
```html {.line-numbers}
<div class="easy">
<?php echo '<a href="'.$item->url.'" title="url" >'; ?>
<!--[INSERT<>$$$$]--><!--23-->
<?php echo '<a href="'.$item->new_url.'" title="new url" >'; ?>
<!--[/INSERT<>$$$$]-->
</div>
```

### Existing HTML Insert Code
```html {.line-numbers}
<div class="easy">
<?php echo '<a href="'.$item->url.'" title="url" >'; ?>
<!--[INSERTED$$$$]--><!--23-->
<?php echo '<a href="'.$item->new_url.'" title="new url" >'; ?>
<!--[/INSERTED$$$$]-->
</div>
```

### Update HTML Insert Code
```html {.line-numbers}
<div class="easy">
<?php echo '<a href="'.$item->url.'" title="url" >'; ?>
<!--[INSERTED<>$$$$]--><!--23-->
<?php echo '<a href="'.$item->new_url.'" title="new url" >'; ?>
<!--[/INSERTED<>$$$$]-->
</div>
```

# Replace Examples (HTML)

> placeholder must be on its own line!

### New HTML Replace Code
```html {.line-numbers}
<div class="easy">
<!--[REPLACE<>$$$$]-->
<?php echo '<a href="'.$item->url.'" title="updated url" >'; ?>
<!--[/REPLACE<>$$$$]-->
</div>
```

### Existing HTML Replaced Code
```html {.line-numbers}
<div class="easy">
<!--[REPLACED$$$$]--><!--25-->
<?php echo '<a href="'.$item->url.'" title="updated url" >'; ?>
<!--[/REPLACED$$$$]-->
</div>
```

### Update HTML Replaced Code
```html {.line-numbers}
<div class="easy">
<!--[REPLACED<>$$$$]--><!--25-->
<?php echo '<a href="'.$item->url.'" title="updated url" >'; ?>
<!--[/REPLACED<>$$$$]-->
</div>
```
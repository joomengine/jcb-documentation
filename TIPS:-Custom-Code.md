Here are some 'tips' when using custom code.

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
|New<br/>Insert Code|`<!--[INSERT<>$$$$]-->`|`<--[/INSERT<>$$$$]-->`|
|New<br/>Replace Code|`<!--[REPLACE<>$$$$]-->`|`<--[/REPLACE<>$$$$]-->`|
||**WHEN JCB ADDS IT BACK AGAIN**|
|Existing<br/>Inserted Code|`<!--[INSERTED$$$$]--><!--23-->`|`<--[/INSERTED$$$$]-->`|
|Existing<br/>Replaced Code|`<!--[REPLACED$$$$]--><!--25-->`|`<--[/REPLACED$$$$]-->`|
||**CHANGING EXISTING CUSTOM CODE**|
|Update<br/>Inserted Code|`<!--[INSERTED<>$$$$]--><!--23-->`|`<--[/INSERTED<>$$$$]-->`|
|Update<br/>Replaced Code|`<!--[REPLACED<>$$$$]--><!--25-->`|`<--[/REPLACED<>$$$$]-->`|

> "`<!--23-->`" and "`<!--25-->`" (or similar id numbers) are the ID of the code in the system don't change it!!!!

# Insert Examples (PHP)

> placeholder must be on its own line

### New PHP Insert Code
```php
$bar = 'easy';
$foo = 'some code';
/***[INSERT<>$$$$]***/
$var = 4;
/***[/INSERT<>$$$$]***/
$more = 'more some code';
```

### Existing PHP Insert Code
```php
$bar = 'easy';
$foo = 'some code';
/***[INSERTED$$$$]***///*23*/
$var = 4;
/***[/INSERTED$$$$]***/
$more = 'more some code';
```

### Update PHP Insert Code
```php
$bar = 'easy';
$foo = 'some code';
/***[INSERTED<>$$$$]***///*23*/
$var = 4;
/***[/INSERTED<>$$$$]***/
$more = 'more some code';
```

# Replace Examples (PHP)

> placeholder must be on its own line

### New PHP Replace Code
```php
$bar = 'easy';
/***[REPLACE<>$$$$]***/
$foo = 'some code changed';
/***[/REPLACE<>$$$$]***/
$more = 'more some code';
```

### Existing PHP Replace Code
```php
$bar = 'easy';
/***[REPLACED$$$$]***//*25*/
$foo = 'some code changed';
/***[/REPLACED$$$$]***/
$more = 'more some code';
```

### Update PHP Replace Code
```php
$bar = 'easy';
/***[REPLACED<>$$$$]***//*25*/
$foo = 'some code changed';
/***[/REPLACED<>$$$$]***/
```

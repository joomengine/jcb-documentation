Here are some 'tips' when using custom code.

# The custom PHP script placeholders

|USAGE|PHP START|PHP END
|---|---|---|
|New Insert Code|`/***[INSERT<>$$$$]***/`|`/***[/INSERT<>$$$$]***/`|
|New Replace Code|`/***[REPLACE<>$$$$]***/`|`/***[/REPLACE<>$$$$]***/`|
||WHEN JCB ADDS IT BACK AGAIN|
|JCB Add Inserted Code|`/***[INSERTED$$$$]***///*23*/`|`/***[/INSERTED$$$$]***/`|
|JCB Add Replaced Code|`/***[REPLACED$$$$]***///*25*/`|`/***[/REPLACED$$$$]***/`|
||CHANGING EXISTING CUSTOM CODE|
|Update Inserted Code|`/***[INSERTED<>$$$$]***///*23*/`|`/***[/INSERTED<>$$$$]***/`|
|Update Replaced Code|`/***[REPLACED<>$$$$]***///*25*/`|`/***[/REPLACED<>$$$$]***/`|

> "`/*23*/`" and "`/*25*/`" (or similar id numbers) are the ID of the code in the system don't change it!!!!

# The custom HTML script placeholders

|USAGE|HTML START|HTML END
|---|---|---|
|New Insert Code|`<!--[INSERT<>$$$$]-->`|`<--[/INSERT<>$$$$]-->`|
|New Replace Code|`<!--[REPLACE<>$$$$]-->`|`<--[/REPLACE<>$$$$]-->`|
||WHEN JCB ADDS IT BACK AGAIN|
|JCB Add Inserted Code|`<!--[INSERTED$$$$]--><!--23-->`|`<--[/INSERTED$$$$]-->`|
|JCB Add Replaced Code|`<!--[REPLACED$$$$]--><!--25-->`|`<--[/REPLACED$$$$]-->`|
||CHANGING EXISTING CUSTOM CODE|
|Update Inserted Code|`<!--[INSERTED<>$$$$]--><!--23-->`|`<--[/INSERTED<>$$$$]-->`|
|Update Replaced Code|`<!--[REPLACED<>$$$$]--><!--25-->`|`<--[/REPLACED<>$$$$]-->`|

> "`<!--23-->`" and "`<!--25-->`" (or similar id numbers) are the ID of the code in the system don't change it!!!!
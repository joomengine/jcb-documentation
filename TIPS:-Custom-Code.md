Here are some 'tips' when using custom code.

# The custom script placeholders

|USAGE|PHP START|PHP END|HTML START|HTML END
|---|---|---|---|---|
|New Insert Code|/***[INSERT<>$$$$]***/|/***[/INSERT<>$$$$]***/|`<!--[INSERT<>$$$$]-->`|`<--[/INSERT<>$$$$]-->`|
|New Replace Code|/***[REPLACE<>$$$$]***/|/***[/REPLACE<>$$$$]***/|`<!--[REPLACE<>$$$$]-->`|`<--[/REPLACE<>$$$$]-->`|
||WHEN JCB ADDS IT BACK AGAIN|
|JCB Add Inserted Code|/***[INSERTED$$$$]***///23|/***[/INSERTED$$$$]***/|`<!--[INSERTED$$$$]-->`|`<--[/INSERTED$$$$]-->`|
|JCB Add Replaced Code|/***[REPLACED<>$$$$]***///25|/***[/REPLACED<>$$$$]***/|`<!--[REPLACED$$$$]-->`|`<--[/REPLACED$$$$]-->`|
||CHANGING EXISTING CUSTOM CODE|
|Update Inserted Code|/***[INSERTED<>$$$$]***///23|/***[/INSERTED<>$$$$]***/|`<!--[INSERTED<>$$$$]-->`|`<--[/INSERTED<>$$$$]-->`|
|Update Replaced Code|/***[REPLACED<>$$$$]***///25|/***[/REPLACED<>$$$$]***/|`<!--[REPLACED<>$$$$]-->`|`<--[/REPLACED<>$$$$]-->`|

"//23" and "//25" (or similar id numbers) are the ID of the code in the system don't change it!!!!
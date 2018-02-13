Here are some 'tips' when using custom code.

# The custom script placeholders

|   |   |   |   |   |
|---|---|---|---|---|
| USAGE | PHP START | PHP END | HTML START | HTML END |
| New Insert Code | `/***[INSERT<>$$$$]***/` | `/***[/INSERT<>$$$$]***/` | `<!--[INSERT<>$$$$]-->` | `<!--[/INSERT<>$$$$]-->` |
| New Replace Code | `/***[REPLACE<>$$$$]***/` | `/***[/REPLACE<>$$$$]***/` | `<!--[REPLACE<>$$$$]-->` | `<!--[/REPLACE<>$$$$]-->` |
| when JCB adds it back |
| JCB Add Inserted Code | `/***[INSERTED$$$$]***///23` | `/***[/INSERTED$$$$]***/` |
| JCB Add Replaced Code | `/***[REPLACED<>$$$$]***///25` | `/***[/REPLACED<>$$$$]***/` |
| changeing existing custom code |
| Update Inserted Code | `/***[INSERTED<>$$$$]***///23` | `/***[/INSERTED<>$$$$]***/` |
| Update Replaced Code | `/***[REPLACED<>$$$$]***///25` | `/***[/REPLACED<>$$$$]***/` |

"//23" and "//25" (or similar id numbers) are the ID of the code in the system don't change it!!!!
> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

Les répertoires, dossiers et fichiers du composant JCB Demo, trouvés dans le package d'installation de JCB Demo nommé com_demo_v2_0_0__J3.zip sont présentés ici pour votre commodité. D'autres sujets sont présentés pour faciliter le processus. Pour plus de simplicité, il est recommandé d'installer uniquement Joomla! et le composant JCB sans installer le composant JCB Demo à l'aide de Joomla! installateur. Cela vous permet de vous concentrer sur les éléments suivants :

*JCB
* Importation du package de démonstration JCB
* Zones JCB contenant le code du composant de démonstration
* Fonctionnalités et fonctionnalités JCB utilisées lors de la création du composant de démonstration
* Interaction JCB avec Joomla! API

Notez la dernière puce ci-dessus. Il y aura des répertoires, des fichiers et du code dans le package de composants JCB Demo sur lesquels vous pourrez réfléchir ; vous vous demanderez comment ils sont arrivés là. JCB exploite Joomla! API pour accomplir cela. Pour voir comment cela se fait, faites un effort supplémentaire et croisez tout comme cela a été fait ici. Le processus est fastidieux, mais renforcera votre compréhension des nombreux domaines de JCB où les répertoires et fichiers des composants ont été créés automatiquement par JCB. Cela inclut les extraits de code que vous avez écrits et placés dans diverses zones du composant JCB pendant le processus de construction tout en utilisant les caractéristiques et fonctionnalités standard de JCB pour améliorer votre extrait de code, mais pour lesquels vous n'avez écrit aucun code. Ce processus permet également de comprendre que JCB réutilise et étend les classes de code, méthodes et propriétés de base de Joomla! API autant que possible.

L'analyse des composants de démonstration JCB présentée dans ce chapitre vous présentera une structure de répertoires MVC typique et les fichiers qu'elle contient, pour un composant qui devrait être facile à comprendre. Cependant, le paradigme MVC s'applique à tous les composants, quelle que soit leur complexité, de sorte que l'analyse peut être appliquée à n'importe quel composant. À mesure que la complexité augmente, développer avec les éléments suivants réduit considérablement le temps nécessaire à la création d'un composant :

* Un environnement de développement local comme [WAMP](http://wampserver.aviatechno.net/?lang=en&prerequis=afficher) avec des capacités natives [XDEBUG](https://xdebug.org/).
*Joomla! Constructeur de composants.
* [NetBeans](https://netbeans.org/) ou un environnement de développement intégré (IDE) similaire avec les fonctionnalités natives XDEBUG et GitHub.
* [Chrome](https://www.google.com/chrome/) plus ses [Outils de développement](https://developers.google.com/web/tools/chrome-devtools/) et [Extensions de développeur](https://chrome.google.com/webstore/category/ext/11-web-development) ou d'autres comme [Firefox](https://www.mozilla.org/en-US/firefox/new/) avec des fonctionnalités et des modules complémentaires similaires.
*Joomla! Débogage, en particulier sa Stack Trace, et XDEBUG incluant de manière compatible des liens vers la source dans chaque trace
* [Joomla J!Dump](https://extensions.joomla.org/extension/j-dump/) qui fonctionne bien pour le dumping dans Joomla! composants au lieu d'utiliser PHP echo et var_dump.
* Les outils de développement dans Chrome sont une très bonne source pour déboguer JavaScript en temps réel avec des fonctionnalités similaires au débogueur NetBeans.
* Les outils de développement de Chrome disposent de nombreuses autres fonctionnalités pour vous aider à déboguer et à peaufiner votre site à la volée.

Il existe [de nombreuses autres possibilités](https://docs.joomla.org/Setting_up_your_workstation_for_web_development), notamment avec l'EDI, mais cette combinaison s'intègre bien, et une grande partie de ses fonctionnalités sont natives des applications qui la composent. Ceci s'applique également à tout autre composant utilisé comme exemple dans les vidéos et les chapitres qui les accompagnent dans ce manuel. L'arborescence des répertoires paraîtra également plus complexe à mesure que vous progressez et contiendra de nombreux fichiers supplémentaires. Cependant, ils partagent tous une chose en commun qui est le [paradigme MVC](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller) ; tous suivent sa structure de répertoires de base et ses conventions de dénomination, y compris les fichiers contenus dans les répertoires. Cela inclut également les emplacements des fichiers. Le code et les constructions nécessaires spécifiques à un modèle, une vue ou un contrôleur pour que chacun fonctionne et s'interconnecte les uns avec les autres et avec Joomla! Les API au niveau le plus élémentaire sont communes à tous, si elles sont développées en utilisant le paradigme MVC dans son sens le plus strict.

Décompressez com_demo_v2_0_0__J3.zip et à l'aide du shell ou de la ligne de commande, listez ses répertoires, sous-répertoires et tous les fichiers qu'ils contiennent, en passant à la racine du répertoire et en tapant par exemple dir > demoDirectory.txt /s si vous utilisez la ligne de commande Microsoft Windows. D'autres systèmes d'exploitation ont une commande similaire dans leur shell. Ensuite, parcourez les répertoires et les fichiers à l'aide du gestionnaire de fichiers de votre système d'exploitation comme l'Explorateur Windows ou mieux encore, un environnement de développement intégré (IDE) comme [NetBeans](https://netbeans.org/) ou un environnement de développement intégré (IDE) similaire avec les fonctionnalités natives XDEBUG et GitHub. Un IDE est recommandé car il possède de nombreuses fonctionnalités facilitant cette analyse. Certains d'entre eux incluent :

* Un gestionnaire de fichiers pour parcourir l'arborescence des répertoires et les fichiers
* La possibilité d'ouvrir un ou plusieurs fichiers à la fois dans des fenêtres séparées
* Utilisation de l'EDI pour localiser rapidement les classes de base dans Joomla! API réutilisées et étendues par JCB
* Recherche sur un site ou un fichier de développement pour produire une liste de toutes les occurrences où le mot ou l'expression recherchée apparaît
* Disponibilité de nombreux autres outils dans l'EDI, notamment des [plugins téléchargeables](http://plugins.netbeans.org/) pour étendre ses capacités
* Capacités de débogage étendues ; NetBeans prend en charge nativement le [débogage XDEBUG](https://netbeans.org/kb/docs/php/debugging.html) et la [gestion des versions GitHub](https://netbeans.org/kb/docs/ide/git.html)
* [Interaction avec Chrome](https://chrome.google.com/webstore/detail/netbeans-connector/hafdlehgocfcodbgjnpecfajgkeejnaa?hl=en) ou les navigateurs Firefox, par ex. Extensions NetBeans et XDEBUG de Chrome ainsi que [Firebug Lite](https://getfirebug.com/releases/lite/chrome/)

Les outils de débogage sont une partie essentielle de l'EDI de tout développeur. Passer des heures à essayer de localiser un bug d'exécution en lisant des centaines, voire des milliers de lignes de code pour trouver un seul caractère égaré est exaspérant et non productif. [Bonnes compétences en débogage](https://docs.joomla.org/How_to_debug_your_code) permettent généralement de localiser la ou les lignes de code incriminées en quelques minutes. Il est généralement facile de corriger un problème, il est presque toujours difficile de trouver où il s'est produit, surtout avec toutes les interconnexions que l'on trouve dans un composant utilisant le paradigme MVC, et encore moins ceux utilisant le Joomla! API largement comme le fait JCB. Il peut également être utilisé pour faciliter votre analyse et vos efforts de développement. Certaines des fonctionnalités offertes par un bon débogueur IDE sont :

* Une seule étape dans le code pendant son exécution
* Ajout de points d'arrêt et de surveillance pour suspendre l'exécution et examiner le contenu des variables
* Traces de pile qui montrent le chemin de chaque script et ressource utilisé lors de l'exécution
* Montres pour examiner le contenu des variables en fonction de leur contenu
* Un dump de toutes les variables en jeu tout en parcourant le code
* Examiner facilement les classes, les méthodes et les propriétés, y compris leur source, à la volée pendant l'exécution

Il existe [de nombreuses autres fonctionnalités](https://netbeans.org/kb/docs/php/debugging.html) et fonctionnalités non mentionnées ici. Un débogage efficace est indispensable pendant le cycle de développement d’un composant. Il améliore le processus de construction de JCB et vous permet d'identifier et de résoudre rapidement les problèmes dans le composant une fois que JCB l'a compilé avec succès, mais que le composant présente des erreurs d'exécution. Utilisez également Joomla! débogage intégré activé dans ses paramètres de configuration. La trace de pile qu'il affiche, y compris les liens si vous utilisez XDEBUG, sont également indispensables. De plus, il s'intègre à un IDE comme NetBeans en utilisant l'[extension Chrome NetBeans](https://chrome.google.com/webstore/detail/netbeans-connector/hafdlehgocfcodbgjnpecfajgkeejnaa?hl=en).

Faire fonctionner XDEBUG avec votre navigateur et votre IDE peut être une tâche ardue. [Ce guide](https://quantumwarp.com/kb/articles/87-netbeans/928-debugging-with-netbeans-xdebug-and-xampp-in-windows) et [un autre](https://articlebin.michaelmilette.com/making-xdebug-work-with-netbeans-on-windows/) contiennent d'excellents conseils sur l'utilisation de XDEBUG avec NetBeans et d'autres IDE et incluent son utilisation avec un navigateur. Ils ont également des instructions sur la façon de dépanner le port par défaut qu'il utilise et comment différencier si le port par défaut (9000) utilisé par XDEBUG est le problème, par exemple s'il est bloqué par votre pare-feu et a besoin d'une règle pour le traverser ou si les lignes requises dans le php.ini ne sont pas là ou sont incorrectes, ou pour une autre raison. Il est également recommandé d'utiliser [cet excellent outil](https://xdebug.org/wizard.php) car il crée les lignes php.ini nécessaires dont vous aurez besoin pour remplacer ce que NetBeans y met qui n'est qu'un stub à l'exception de la ligne qui charge la DLL correcte. Les deux liens précédents permettent de comprendre XDEBUG et ce qui doit être fait pour l'installer correctement, ainsi que d'excellentes instructions de dépannage. Les lignes php.ini suggérées par les deux ne sont généralement pas nécessaires, utilisez donc les lignes php.ini générées par l'outil dans le dernier lien de ce paragraphe.

WAMP permet de basculer entre les versions 5.x et 7.x de PHP. Pour faciliter XDEBUG, WAMP utilise une DLL XDEBUG différente dans le php.ini entre laquelle WAMP bascule lorsque différentes versions de PHP sont utilisées. La version actuelle de WAMP permet de basculer entre cette dernière version 5.x et trois versions 7.x. Ne changez donc pas ce qui a été installé par WAMP à la fin du php.ini. Commentez toutes les lignes ci-dessous en utilisant un point-virgule (;) dans chaque php.ini utilisé par WAMP pour chaque version de PHP vers laquelle il vous permet de basculer, ce qui est très agréable, disons, pour regarder la dernière version de Joomla ! version, par exemple Joomla! 4alpha.

Ne pas utiliser la bonne DLL est l'erreur la plus courante lors de l'utilisation de XDEBUG et WAMP la configure correctement. L'autre erreur très courante est de ne pas avoir installé les [Packages Visual C++](http://wampserver.aviatechno.net/?lang=en&prerequis=afficher) pour la version correspondante de PHP qui a été compilée. Laissez WAMP faire cela pour vous. Le lien précédent semble être le meilleur à utiliser pour une installation complète de WAMP qui constitue une page unique pour tout ce dont vous avez besoin. Comme il existe de nombreuses versions de WAMP, même si vous devriez utiliser la version actuelle, cela ne fera pas de mal d'installer tous les packages Visual C++. Cela prend un certain temps et vous devez installer les versions 32 et 64 bits et je suggère de le faire par ordre de date en commençant par la plus ancienne et en terminant par la dernière. Lisez la page dans son intégralité pour installer tout ce qui est nécessaire. Suivez toutes les recommandations qui se trouvent également sur la page.

Vous pouvez installer tous les packages Visual C++ car vous aurez alors la version du package nécessaire pour la version dont vous disposez de PHP. Ne vous inquiétez pas, deux sont français. Ils fonctionnent bien, mais vous devrez peut-être vous assurer de cliquer sur le bouton OK au lieu de Annuler car ils sont en français. À part cela, tout le reste de la page est installé en anglais. La dépendance de la version PHP avec chaque version du package Visual C++ dépend de la version du package Visual C++ utilisée pour compiler la version PHP. Comme pour tout ce qui en vaut la peine, faites le travail et lisez les informations sur les sites que j'ai mentionnés précédemment.

Souvent, XDEBUG fonctionnera si vous l’installez simplement et laissez l’installation s’occuper de tout. Essayez de le faire d'abord et si tout fonctionne correctement, vous avez installé le bon package Visual C++ et php.ini avait la bonne section XDEBUG qui fonctionne avec lui. Si vous changez de version de PHP et qu'il cesse de fonctionner, vous devrez vous assurer que l'environnement est correctement configuré pour cette version. Cela ne se produira pas si vous installez tous les packages Visual C++ 32 et 64 bits. Mais il semble que beaucoup aient des problèmes avec cela car ils dépendaient de l'installation pour tout faire, y compris leur environnement, malgré le passage à une autre version de PHP.

XAMPP installera XDEBUG sans trop d'effort de votre part, mais WAMP est un bien meilleur environnement dans lequel travailler. Il en va de même pour LAMP et MAMP. Il n'entre pas dans le cadre de ce manuel d'aborder également les systèmes d'exploitation Linux et Mac, mais les mêmes concepts s'appliquent et de nombreux liens font également référence à ces systèmes d'exploitation.

Il convient de mentionner que pour ceux qui souhaitent emprunter le chemin rapide, vous pouvez parcourir com_demo_v2_0_0__J3.zip directement en utilisant l'Explorateur de fichiers Windows à titre d'exemple et parcourir l'arborescence et les fichiers sans les extraire. Cependant, il s'agit d'un [Joomla! component install package](https://docs.joomla.org/File_Structure_and_Naming_Conventions) et ne correspondra donc pas à la structure des répertoires. Si vous connaissez Joomla! les exigences et la structure du package d'installation, cela ne devrait pas poser de problème. Pour certains, c'est tout ce dont ils ont besoin, surtout s'ils sont des développeurs PHP très expérimentés, qui ont utilisé Joomla! API de manière approfondie et j'ai découvert que JCB n'était pas très difficile à apprendre en utilisant JCB Component Builder après son installation, ainsi qu'en parcourant son code.

Si vous n'avez pas encore atteint ce niveau, créer le fichier texte et effectuer la même analyse que celle effectuée ici est un excellent exercice. Faites de même pour vos propres composants et lorsque vous êtes prêt, importez les composants JCB les plus complexes distribués gratuitement dans JCB et faites de même. Prenez des notes dans votre fichier texte pendant que vous parcourez les répertoires et les fichiers de votre site de développement pour les réviser ultérieurement ou revisiter des concepts qui n'étaient peut-être pas très clairs à l'époque. Suivez-nous tout au long de l'arborescence des répertoires de votre système. Localisez et ouvrez les fichiers dans chacun indiqué ci-dessous et affichez son contenu. De bonnes habitudes d'étude vous permettront de progresser rapidement pour devenir un développeur avancé de Joomla! composants construits à l'aide du paradigme MVC, JCB et Joomla! API. Celui-ci, avec les autres outils mentionnés ici, vous permet de gagner beaucoup de temps, de développer plus de composants et surtout d'adhérer au [paradigme MVC](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller) qui est un gain de temps en soi.

Sous la structure des répertoires et les fichiers présentés ensuite, vous trouverez une brève explication de leur relation avec le composant, les zones du composant JCB qui les construisent et l'interaction de JCB avec Joomla! API. Vous verrez comment JCB réutilise et étend les classes de base abstraites de Joomla!, y compris leurs méthodes et propriétés pour implémenter les nombreuses fonctionnalités et fonctions intégrées à JCB que vous utilisez lors de la création d'un composant. Lorsque vous parcourez la structure des répertoires et les fichiers, des liens sont disponibles vous permettant d'accéder rapidement au texte explicatif situé sous la structure des répertoires de ce fichier, y compris une référence à son origine dans JCB et à toute interaction entre JCB et Joomla! API.
***
\administrateur  
***
	\composants	
		\com_demo	
			\actifs	
				\css	
					\admin.css
					\tableau de bord.css
					\index.html
					\look.css
					\looks.css
				\images
					\icônes
						\index.html
					\import.gif
					\index.html
				\js
					\admin.js
					\index.html

\contrôleurs
				\démo.php  
[demo.php](https://github.com/vdm-io/Joomla-Component-Builder/wiki/4a.-JCB-Demo-Component-Directory,-Folders-and-Files#administratorcomponentscom_democontrollersdemophp)

\importer.php  
[importer.php](https://github.com/vdm-io/Joomla-Component-Builder/wiki/4a.-JCB-Demo-Component-Directory,-Folders-and-Files#administratorcomponentscom_democontrollersimportphp)

\index.html

\look.php  
[look.php](https://github.com/vdm-io/Joomla-Component-Builder/wiki/4a.-JCB-Demo-Component-Directory,-Folders-and-Files#administratorcomponentscom_democontrollerslookphp)

\looks.php  
[looks.php](https://github.com/vdm-io/Joomla-Component-Builder/wiki/4a.-JCB-Demo-Component-Directory,-Folders-and-Files#administratorcomponentscom_democontrollerslooksphp)

\aides
				\html
					\batch.php
					\index.html
				\PHPExcel
				\démo.php
				\headercheck.php
				\index.html
				\PHPExcel.php
			\langue
				\fr-FR
					\fr-GB.com_demo.ini
					\en-GB.com_demo.sys.ini
					\index.html
				\index.html
			\layouts
				\regarde
					\details_above.php
					\details_fullwidth.php
					\details_under.php
					\index.html
					\métadonnées.php
					\more_left.php
					\more_right.php
					\édition.php
				\batchselection.php
				\index.html
			\modèles
				\champs
					\index.html
				\formes
					\index.html
					\look.js
					\look.xml
				\règles
					\index.html
				\démo.php
				\importer.php
				\index.html
				\look.php
				\looks.php
			\sql
				\mises à jour
					\mysql
						\1.0.5.sql
						\index.html
					\index.html
				\index.html
				\install.mysql.utf8.sql
				\uninstall.mysql.utf8.sql
			\tables
				\index.html
				\look.php
			\vues
				\démo
					\tmpl
						\par défaut.php
						\default_main.php
						\default_vdm.php
						\index.html
					\index.html
					\view.html.php
				\importer
					\tmpl
						\par défaut.php					
						\index.html					
					\index.html
					\view.html.php
				\regarde
					\tmpl
						\edit.php
						\index.html
					*\index.html
					\submitbutton.js
					\view.html.php
				\regarde
					\tmpl
						\par défaut.php
						\default_batch_body.php
						\default_batch_footer.php
						\default_body.php
						\default_foot.php
						\default_head.php
						\default_toolbar.php
						\index.html
				\index.html
				\view.html.php

***
\composants  
***
	\com_demo
		\actifs
			\css
				\index.html
				\look.css
				\looking.css
				\looks.css
				\site.css
			\images
				\index.html
			\js
				\index.html
				\site.js
			\index.html
		\index.html
		\contrôleurs
			\index.html
			\look.php
		\aides
			\category.php
			\démo.php
			\headercheck.php
			\index.html
			\route.php
		\langue
			\fr-FR
				\fr-GB.com_demo.ini
				\en-GB.com_demo.sys.ini
				\index.html
			\index.html
		\layouts
			\regarde
				\details_above.php
				\details_fullwidth.php
				\details_under.php
				\index.html
				\métadonnées.php
				\more_left.php
				\more_right.php
				\publication
			\index.html
		\média
			\css
				\index.html
			\images
				\index.html
			\js
				\index.html
			\uikit-v2
			\index.html

\modèles
			\formes
				\index.html
				\look.js
				\look.xml
			\index.html
			\look.php
			\looking.php
			\looks.php
		\vues
			\regarde
				\tmpl
					\edit.php
					\index.html
				\submitbutton.js
				\view.html.php
			\regarder
				\tmpl
					\par défaut.php
					\index.html
				\index.html
				\view.html.php
			\regarde
				\tmpl
					\par défaut.php
					\default.xml
					\index.html
				\index.html
				\view.html.php

\contrôleur.php  
		\démo.php  
[démo.php](https://github.com/vdm-io/Joomla-Component-Builder/wiki/4a.-JCB-Demo-Component-Directory,-Folders-and-Files#com_demodemophp)

\index.html  
		\routeur.php
***
Gardez toujours à l’esprit que JCB effectue la plupart des tâches liées aux éléments ci-dessous faisant référence aux répertoires, fichiers, classes, méthodes et propriétés Joomla. Vous n'êtes pas obligé, par exemple, de placer un fichier index.html à la racine de chaque répertoire ; vous n'êtes pas obligé d'ajouter le chèque pour un accès direct au fichier ; vous n'avez pas besoin d'écrire du code pour les vues d'administration ou de site, sauf si vous étendez JCB avec votre propre code personnalisé.

Certains des liens ci-dessous et vus précédemment dans ce document peuvent être obsolètes et de nombreux liens Joomla! les classes utilisées ont des origines anciennes et sont indiquées comme telles dans la documentation. Les emplacements des fichiers de classe varient selon la version, et les trouver et examiner le code dans chacun d'eux est rendu un peu plus insaisissable avec Joomla ! 4 changements d'espace de noms mais la standardisation en vaut la peine. Il existe actuellement une compatibilité ascendante et, par conséquent, des listes d'alias existent, comme nous le verrons ci-dessous.

Il existe une carte de classes d'alias pour les classes qui ne sont pas conformes à Joomla 4 ! convention de dénomination des espaces de noms. Lors de l'écriture de vos propres composants, ce fichier doit être consulté :  
* \bibliothèques\classmap.php

Le chemin de droite contient les emplacements actuels ainsi que la nouvelle convention de dénomination standard qui lui est associée sur la gauche. Il existe quelques autres domaines où cela se produit et qui sont inclus sous la liste. Jetez un œil à cet exemple qui appelle une méthode de classe :  
* JLoader::registerAlias('JControllerLegacy', '\\Joomla\\CMS\\MVC\\Controller\\BaseController', '5.0')

Le chemin physique dans Joomal! la version 3.8.12 est :
* \libraries\src\Application\BaseController.php

Le site Joomla! La classe dans le fichier de cet exemple est nommée BaseController qui étend JObject.  
***
Notez que ce qui suit s'applique en général à tout composant :  
**index.html**  
Fichier contenant une ligne de HTML qui fait que l'arrière-plan de la page est blanc, ce qui bloque la vue du répertoire. Doit être à la racine de chaque dossier.
 
**Tous les fichiers de classe Joomla doivent commencer par ce code :**  
// Pas d'accès direct à ce fichier  
set('_JEXEC') ou die('Accès restreint');  
***  
<a id="demophp"></a>
## \demo.php  
Connectez-vous en tant que super administrateur à la zone d'administration. La modification de la vue du site de JCB dans la zone d'administration du site est l'endroit où vous ajoutez le code pour le point d'entrée de la vue du site pour le composant de démonstration JCB ; son chemin est /demo.php. Ce code a été inséré pour vous. Vous devrez fournir du code pour vos propres composants et le code du composant JCB Demo fournit les éléments de base pour tout composant autorisant CRUD (Create, Read, Update Delete) sur les enregistrements de table de base de données, dans ce cas, regardez.

Le super-administrateur peut :
* Connectez-vous à l'administrateur en tant que super-administrateur et créez un look.
* Ajouter un utilisateur enregistré.
* Créez un site Joomla! élément de menu pour les apparences du composant de démonstration, l'accès doit être enregistré.
* Assurez-vous que lors de la création d'une apparence pour un utilisateur enregistré, la propriété de l'apparence est remplacée par celui qui devrait posséder l'apparence, le cas échéant. Sinon, ils ne pourront pas le visualiser ou le modifier depuis la zone du site.
 
Les utilisateurs enregistrés peuvent :
* Modifiez l'enregistrement look dans la table demo_look, en réutilisant le formulaire adminForm pour ce faire. Pour afficher, l'ID utilisateur enregistré de l'utilisateur connecté doit correspondre à la valeur create_by dans l'enregistrement.
* Connectez-vous en tant qu'utilisateur enregistré et sélectionnez l'option Looks dans le menu principal.
* Observez les affichages de la vue du site avec le nom et la description de l'apparence de l'utilisateur enregistré et une barre d'outils d'édition en dessous.
* Cliquez sur la barre d'outils d'édition et affichez l'apparence de la vue administrateur, affichant uniquement les boutons représentant les actions de formulaire définies pour ce groupe d'utilisateurs qui sont Enregistrer, Enregistrer et Fermer, Fermer.
* Cliquez sur le bouton Plus, activé lorsque l'enregistrement a été saisi par le super-administrateur à l'aide de la zone d'administration du site. Cela permet à l'utilisateur enregistré d'accéder à des champs supplémentaires sur le formulaire.

Modification de la vue administrateur - Apparence du nom du système - Paramètres - Implémentation des autorisations - Paramètres  
Ce n'est que si vous ajoutez des autorisations ici que cette vue disposera d'autorisations. [Veuillez regarder ce didacticiel](https://youtu.be/CdSKSCTzmRA?list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=6m19score.edit) pour plus d'informations.

Par défaut, la vue du site n'est autorisée pour aucun utilisateur autre que le super-administrateur, bien qu'elle s'affiche dans le menu principal après la connexion à un utilisateur enregistré et supérieur. Si l'accès est donné dans l'ACL de Joomla! au composant de démonstration JCB pour le groupe enregistré de Joomla! utilisateurs, la vue s’affichera après la connexion en tant qu’utilisateur enregistré. Pour que cela se produise, Joomla! L'ACL doit autoriser l'accès au composant comme suit à l'aide de l'option du menu principal de la zone d'administration :

Composants - Démo - Apparences - Options - Onglet Autorisations - Enregistré  
* Recherche d'accès (au site) autorisé  
* Il semble que l'accès soit autorisé  
* Accès aux looks (site) autorisé  
* Looks Modifier le propre autorisé

La première option permet uniquement l'accès au site. La vue affichera un look mais c'est tout. Le second permet l'accès et donc tous les looks s'afficheront et pourront être consultés (mais pas modifiés) tant que le troisième accès est également accordé. Le quatrième permet de modifier le look si l'identifiant de l'utilisateur correspond à celui de la table look_demo. Plus de détails sur Joomla! L'ACL à ce sujet peut être vue dans [cette vidéo](https://www.youtube.com/watch?v=gWjQjdhYqXI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&index=36).

Assurez-vous d'ajouter un filtre en utilisant la zone d'administration du site, option du menu principal en sélectionnant :

Composants - Générateur de composants - Obtentions dynamiques - Apparences - Ajustement  
* Où Table Key a.created_by égal = $this->user->id

Ce réglage est appliqué au Dynamic Get dans JCB pour le composant Demo :
* Apparence de la vue du site - Dynamic Get - getListQuery

Il l'étend pour inclure uniquement les enregistrements de la table créés par l'utilisateur ayant le même identifiant que l'utilisateur actuel. Celui-ci est disponible auprès de : 
* Apparence de la vue du site - $ cette variable - élément de formulaire d'identification utilisateur

Le changement prend effet une fois que vous utilisez JCB pour compiler le composant et que vous l'installez à nouveau à l'aide de Joomla! programme d'installation d'extensions. Le même ajustement est requis dans :
* Recherche de vue du site - Dynamic Get - getItem.

Faire ce qui précède garantit également que seules certaines actions sont autorisées pour certains utilisateurs. Dans notre cas, un utilisateur enregistré devrait uniquement être autorisé à :  
* Enregistrer  
* Enregistrer et fermer  
* Fermer

Le filtre leur permet de modifier uniquement leurs propres enregistrements look dans la table demo_look. Si vous avez besoin de voir tous les enregistrements de démonstration, en utilisant toutes les fonctionnalités d'édition et les boutons disponibles, et plus encore, connectez-vous à la zone du site en tant que super administrateur pour voir tous les enregistrements dans la vue administrateur. Si vous suivez les instructions précédentes, les actions d'un utilisateur enregistré seront limitées à l'affichage uniquement des boutons suivants dans la vue suivante :

* Bouton Enregistrer  
* Bouton Enregistrer et fermer  
* Bouton Fermer

Si vous ajoutez plus d'autorisations telles que Créer, deux boutons supplémentaires apparaîtront, Enregistrer et Copier plus Enregistrer et Nouveau. Vous pouvez supprimer des boutons en redéfinissant les autorisations sur héritées, ce qui devrait alors s'afficher comme non autorisé. N'oubliez pas qu'ils doivent avoir été définis au préalable, comme mentionné précédemment, pour apparaître dans la liste des Autorisations. Après avoir ajouté les actions et autorisations appropriées à la vue et l'avoir compilée, les modifications prendront effet. Notez que vous pouvez modifier le composant JCB Demo Joomla! Autorisations ACL et voyez l'effet puisque les composants n'ont pas besoin d'être compilés par JCB pour que ces paramètres soient modifiés puisque la modification est effectuée dans Joomla!.

Poursuivons avec la fonctionnalité d'édition :  
* Modifiez l'enregistrement look dans la table demo_look. Il est important que vous compreniez qu'il s'agit de réutiliser l'apparence de la vue administrateur, l'apparence de modification. Si vous utilisez les outils de développement Chrome pour afficher la source de la page et accédez à la balise de formulaire, vous verrez qu'elle utilise le formulaire d'administration dans la vue Looks :  
<form action="/comdemo/index.php?option=com_demo&amp;view=looks&amp;Itemid=104" method="post" name="adminForm" id="adminForm">

* L'ID utilisateur enregistré de l'utilisateur connecté doit correspondre à la valeurcreated_by pour qu'il s'affiche et permette à l'utilisateur de modifier l'enregistrement. Utilisez l'onglet Publié dans n'importe quel Joomla! pour changer cela pour un Joomla! Utilisateur par exemple pour s'assurer qu'il est le créateur d'un enregistrement de look spécifique dans la table demo_look.

Ce qui précède permet toujours à tous les types d'utilisateurs, à l'exception des groupes d'utilisateurs publics et invités, d'afficher tous les looks, qu'ils les aient créés ou non. Pour restreindre la vue des looks à la liste uniquement des enregistrements appartenant à un utilisateur spécifique, outre les modifications apportées à Joomla! ACL, il faut filtrer les enregistrements look dans la table demo_looks par la colonnecreated_by. Notez que ceux-ci prendront effet sans compiler la démo JCB et les autres composants construits à l'aide de celle-ci. La raison en est que Joomla! L'ACL ou les autorisations des options globales du composant JCB Demo sont modifiées pour le groupe d'utilisateurs enregistrés de Joomla! et non pour les autorisations individuelles au sein du composant JCB. Ce dernier permet une certaine granularité, mais vous devez normalement utiliser les valeurs par défaut autant que possible. À mesure que la granularité augmente, la maintenance requise augmente également.

* Tout d'abord, connectez-vous en tant qu'utilisateur enregistré et sélectionnez l'option Looks dans le menu principal.  
* L'apparence de la vue du site s'affiche avec le nom et la description de l'apparence de l'utilisateur enregistré et une barre d'outils d'édition en dessous.

Ensuite, cliquez sur la barre d'outils d'édition et affichez l'apparence de la vue administrateur, affichant uniquement les actions de formulaire définies pour ce groupe d'utilisateurs :

* Enregistrer  
* Enregistrer et fermer  
* Fermer

Le rôle des bibliothèques doit être mentionné à ce stade puisqu'elles formatent les éléments visibles dans toutes les vues, modèles et mises en page. Le code dans la vue d'ensemble des démos JCB permet de :  
* Regardez - en utilisant la vue du site à un moment donné  
* Regardez - en utilisant la vue du site Look en utilisant  
* Looks - qui est la vue du site qui répertorie les looks

L'apparence de la vue administrateur permet de modifier dans les zones d'administration et de site. Toutes les vues utilisent les enregistrements de la table demo_look qui stockent tous les enregistrements de look.

Il est essentiel de comprendre la bibliothèque UIkit et de se familiariser avec [FooTable](https://fooplugins.github.io/FooTable/docs/getting-started.html) et [Bootstrap](https://getbootstrap.com/docs/4.1/getting-started/introduction/) puisque JCB les implémente. Les composants UIKit sont assez utilisés dans les composants distribués gratuitement par JCB. Pour construire une vue dans JCB, vous devez vous familiariser avec celle-ci. Son empreinte est petite mais puissante. Il est suggéré d'avoir le lien suivant à proximité dans les onglets de votre navigateur lorsque vous codez les vues de votre site en utilisant son composant bouton comme exemple.

https://getuikit.com/docs/button

JCB utilise la version suivante d'UIkit :
/*! UIkit 2.27.4 | http://www.getuikit.com | (c) Thème YOO 2014 | Licence MIT */

UIkit JavaScript pour le composant bouton se trouve à l'adresse :
\media\com_componentbuilder\uikit-v2\js\components\button.js

Un bouton est appelé composant dans l'UIkit et il en existe de nombreux autres qui encapsulent le code côté client dans des fonctions plus généralisées qui peuvent être traitées comme des objets avec des méthodes et des propriétés individuelles. Ils sont identifiés par le préfixe « ui- ». Un exemple est la classe uk-comment trouvée dans le fichier CSS UIkit situé à l'adresse :  
* \media\com_componentbuilder\uikit-v2\css\uikit.css

JCB ajoute cette classe et d'autres en ajoutant les fichiers UIkit à :  
* \media\com_demo\uikit-v2 dans Joomla! Package d'installation de démonstration.

Pour plus de détails, consultez le lien et la liste des composants UIkit et du code requis pour les implémenter, comme cela a été fait ci-dessous dans la zone de JCB intitulée Vue par défaut de la vue du site. Une grande partie du code est du PHP simple. Utilisez la référence $this de la vue à l'objet actuel pour obtenir la valeur d'un élément sur la page. Par exemple, le modèle du composant JCB Demo expose l'identifiant de l'utilisateur connecté dans $this. La valeur de l'identifiant est obtenue en utilisant $this->user->id et une bonne explication de ce qu'est $this peut être trouvée [here ](http://www.php.net/manual/en/language.oop5.basic.php). D'autres valeurs sont également disponibles et observez la réutilisation du code de Joomla! Classes API, plus HTML standard. Comme le montre l'exemple, JCB utilise également des balises telles que ComponentHelper.  
* Recherche de la vue du site

Le code pour faire cela se trouve dans JCB dans la vue préfacée par :  
* Script personnalisé - Ajouter PHP (après avoir obtenu les éléments) * - Oui - Méthode PHP getItems - Valeurs $items cibles (tableau) *

<a id="jcb---editing-the-site-viewadministratorindexphpoptioncom_componentbuilderviewdynamic_getlayouteditid36"></a>
## [JCB - Modification de la vue du site](/administrator/index.php?option=com_componentbuilder&view=dynamic_get&layout=edit&id=36)

Ensuite, nous examinons demo.php à la racine du répertoire des composants JCB Demo et parcourons son contenu, résumant les actions effectuées par les lignes de code de chacun, y compris l'emplacement des fichiers de classe derrière chacune.
-[Ajoutez une prise en charge JavaScript discrète pour conserver un état d'onglet.](https://api.joomla.org/cms-3/classes/JHtmlBehavior.html#method_tabstate)  
\bibliothèques\cms\html\behavior.php
- [Obtenez un objet document et définissez le composant css/js.](https://api.joomla.org/cms-2.5/classes/JFactory.html#method_getDocument)  
\bibliothèques\src\Factory.php  
\components\com_demo\assets\css\site.css  
\components\com_demo\assets\js\site.js  
- [Nécessite des fichiers d'aide.](https://api.joomla.org/cms-3/classes/JLoader.html#method_register)  
\bibliothèques\Joomla\JLoader.php
\helpers\demo.php  
\helpers\route.php  
- [Importer la bibliothèque du contrôleur Joomla](https://docs.joomla.org/J2.5:Developing_a_MVC_Component/Basic_backend#Basic_backend)  
\bibliothèques\Joomla\Controllers\controller.php  
- Obtenez une instance du contrôleur préfixée par démo  
[Méthode pour obtenir une seule instance de contrôleur.](https://api.joomla.org/cms-2.5/classes/JControllerLegacy.html#method_getInstance)  
- Effectuer la tâche de demande. Initialement, c'est la valeur par défaut.  
[Effectuez la tâche de demande.](https://api.joomla.org/cms-2.5/classes/JFactory.html)  
[Récupérer la demande.](https://docs.joomla.org/Retrieving_request_data_using_JInput)  
- Redirection si définie par le contrôleur.
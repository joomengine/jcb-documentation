> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="php-settings-documentation-for-joomla-component-builder-jcb"></a>
## Documentation sur les paramètres PHP pour Joomla Component Builder (JCB)

Une configuration appropriée des paramètres PHP est cruciale pour optimiser les performances et la fiabilité de votre environnement Joomla Component Builder (JCB). Ci-dessous, nous discuterons de l'importance de chaque paramètre PHP spécifié dans le code et fournirons des instructions étape par étape pour configurer ces paramètres sur différentes plates-formes.

<a id="important-php-settings"></a>
### Paramètres PHP importants

<a id="1-upload_max_filesize-128m"></a>
#### 1. `upload_max_filesize` (128M)
Ce paramètre détermine la taille maximale d'un fichier téléchargé. Pour JCB, où des fichiers volumineux tels que des composants et des médias peuvent être téléchargés, il est essentiel d'avoir une limite élevée pour éviter les échecs de téléchargement.

<a id="2-post_max_size-128m"></a>
#### 2. `post_max_size` (128M)
Ce paramètre limite la taille des données POST acceptées par PHP, qui incluent les fichiers téléchargés. Définir cette valeur sur une valeur supérieure à `upload_max_filesize` garantit que les données ne sont pas tronquées lors des soumissions, ce qui est essentiel pour l'intégrité des données dans les formulaires et les téléchargements.

<a id="3-max_execution_time-60-seconds"></a>
#### 3. `max_execution_time` (60 secondes)
Ce paramètre contrôle la durée maximale d'exécution d'un script avant qu'il ne soit terminé par l'analyseur. Un temps plus long permet d’exécuter des opérations complexes sans interruption, ce qui est crucial lors de l’installation ou des mises à jour de composants volumineux.

<a id="4-max_input_vars-7000"></a>
#### 4. `max_input_vars` (7000)
Le paramètre `max_input_vars` limite le nombre de variables d'entrée (par exemple, à partir des données GET, POST et COOKIE). L'augmentation de cette limite prend en charge des formulaires plus détaillés et des configurations complexes dans JCB.

<a id="5-max_input_time-60-seconds"></a>
#### 5. `max_input_time` (60 secondes)
Ce paramètre détermine combien de temps PHP attendra pour recevoir les téléchargements de fichiers et les données POST, ce qui est important pour gérer de gros volumes de données dans des conditions de charge importante.

<a id="6-memory_limit-256m"></a>
#### 6. `memory_limit` (256M)
Ce paramètre spécifie la quantité maximale de mémoire qu'un script peut consommer. Il est essentiel de traiter de grands ensembles de données et d’effectuer des calculs complexes sans interruption ni plantage.

<a id="configuring-php-settings"></a>
### Configuration des paramètres PHP

<a id="on-local-machines-windows-mac-and-linux"></a>
#### Sur les machines locales (Windows, Mac et Linux)

1. **Localisez votre fichier PHP.ini :**
   - **Windows :** Se trouve généralement dans `C:\php\php.ini`.
   - **Mac/Linux :** Généralement `/etc/php/{version}/php.ini` ou `/usr/local/etc/php/{version}/php.ini`.

2. **Modifiez le fichier PHP.ini :**
   - Utilisez un éditeur de texte pour ouvrir `php.ini`.
   - Modifiez les paramètres comme suit :```
     upload_max_filesize = 128M
     post_max_size = 128M
     max_execution_time = 60
     max_input_vars = 7000
     max_input_time = 60
     memory_limit = 256M
     ```- Enregistrez les modifications.

3. **Redémarrez votre serveur Web :**
   - Redémarrez Apache/Nginx pour appliquer les modifications.

<a id="on-development-ubuntu-server-octojoom-docker-cpanel-virtualmin-or-cwp"></a>
#### Sur le développement du serveur Ubuntu (OctoJoom->Docker, cPanel, VirtualMin ou CWP)

**Utilisation de [OctoJoom](https://git.vdm.dev/octoleo/octojoom)->Docker :**
- Réglez Octojoom en mode expert, puis lors de la création d'un nouveau conteneur Joomla, il vous demandera si vous souhaitez définir des valeurs PHP personnalisées.

**Utilisation de cPanel :**
- Accédez à « Logiciel » et recherchez « Sélectionner la version PHP ».
- Cliquez sur "Passer aux options PHP".
- Ajustez les valeurs selon vos besoins et enregistrez les paramètres.

**Utilisation de VirtualMin :**
- Allez dans "Services" > "Configuration PHP".
- Ajustez les paramètres PHP dans l'interface utilisateur fournie.

**Utilisation de CWP (Panneau Web CentOS) :**
- Accédez à l'éditeur de configuration PHP sous "Paramètres PHP".
- Modifier et enregistrer les valeurs souhaitées.

<a id="required-php-modules-for-joomla"></a>
### Modules PHP requis pour Joomla

Pour garantir un fonctionnement optimal de Joomla, les modules PHP suivants doivent être activés. Ceux-ci sont généralement inclus dans les installations PHP standard et peuvent être vérifiés via la fonction `phpinfo()` ou la ligne de commande (`php -m`) :

- **mysqli** ou **pdo_mysql** (pour les bases de données MySQL)
- **gd** (pour le traitement d'image)
- **curl** (pour la récupération de données à partir de sources externes)
- **xml** et **json** (pour l'analyse XML et JSON, respectivement)
- **mbstring** (pour le traitement des chaînes multi-octets)
- **zip** (pour gérer les archives zip)
- **openssl** (pour une transmission sécurisée des données)

Pour une configuration plus détaillée et des modules supplémentaires, consultez les instructions fournies par [l'image officielle Joomla Docker](https://github.com/joomla/docker-joomla).

<a id="conclusion"></a>
### Conclusion

La configuration correcte de votre environnement PHP est essentielle pour un fonctionnement efficace et fiable de Joomla Component Builder. Ces paramètres fournissent les ressources nécessaires pour gérer les opérations complexes, les fichiers volumineux et les charges de données élevées typiques du développement et de la gestion de composants. Pour plus de détails et les dernières recommandations, reportez-vous toujours à la [documentation officielle PHP](https://www.php.net/manual/en/ini.core.php).
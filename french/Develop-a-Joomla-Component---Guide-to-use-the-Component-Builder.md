> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="introduction"></a>
# Présentation
<a id="what-will-this-guide-cover"></a>
## Que couvrira ce guide ?
Ce guide s'étoffera continuellement et tentera de couvrir le processus complet de création d'un composant.

<a id="what-are-we-going-to-build"></a>
## Qu'allons-nous construire ?
Nous allons créer un composant d'archive, afin que par ex. un musée peut gérer ses objets et savoir où tout se trouve. Le composant aura les fonctionnalités suivantes :
* Objet : Ajouter, gérer, supprimer

<a id="prerequisites"></a>
## Prérequis
Tout d’abord, vous aurez besoin du Component Builder installé et prêt à l’emploi.

<a id="tips-and-tricks"></a>
## Trucs et astuces
Voici quelques points importants à prendre en compte lors de l'utilisation du _Component Builder_ :
* Si des nombres sont utilisés, commencez par 1 et non par 0. Vous pouvez avoir des problèmes de fonctionnalité si vous n'y réfléchissez pas. Et ils peuvent devenir ennuyeux à résoudre.

<a id="our-first-component"></a>
# Notre premier composant
<a id="a-new-component"></a>
## Un nouveau composant
Pour commencer, nous commençons par créer un nouveau composant.
* Allez à `Component Builder --> Joomla Components --> New`
  * Détails de l'onglet
    * Nom du système `Archiver` (Il s'agit du nom du système utilisé par le constructeur du composant.
    * Nom `Archiver` (c'est le nom du composant)
    * Nom dans le code `Archiver` (Il s'agit du nom du composant utilisé dans le code)
    * Version `0.0.1` (Il s'agit de la version du composant. Elle sera utilisée pour le processus de mise à jour)
    * Débogage (numéros de ligne) `No`
    * Espaces réservés pour code personnalisé `No`
    * Utiliser Afficher la version et la date `No`
    * Brève description `Archiver helps to get away with all archive objects.`
    * Droit d'auteur `Copyright (C) 2017. All Rights Reserved`
    * Nom de l'entreprise `Component Builder Beginner`
    * Auteur `My Name`
    * Courriel `iForgotMyEmail@oh-no.com`
    * Site Web `https://www.find-me-here-or-not.ch`
    * Ajouter une licence (whmcs) `No`
    * Licence `GNU/GPL Version 2 or later - http://www.gnu.org/licenses/gpl-2.0.html`

*Onglet `Libs & Helpers`
    * Réglez tout sur `No` 
* Enregistrer et fermer

<a id="compiler"></a>
## Compilateur
Pour vérifier ce que nous avons fait et à quoi ressemble notre composant, nous souhaitons compiler notre composant et l'installer.
* Allez à `Component Builder --> Compiler`
  * Ajouter au dossier Git `No`
  * Sélectionnez le composant `Archiver`
  * Cliquez sur `Compile Component`
  * Cliquez sur `Install`

<a id="the-first-admin-view"></a>
## La première vue d'administration
Comme vous pouvez le constater, jusqu'à présent, nous ne sommes pas en mesure d'installer le composant. Le problème est que jusqu'à présent, nous n'avons aucune vue connectée à notre composant. Commençons donc par résoudre ce problème et construisons notre première vue d'administration.
* Allez à `Component Builder --> Admin Views --> New`
  * Nom du système `Archiver - Object` (j'aime nommer mes vues avec le nom de leur composant devant. Comme ça, je peux facilement distinguer mes vues d'administrateur que j'aimerais utiliser et en même temps, je suis obligé d'avoir des vues individuelles pour chaque composant. Ainsi, chaque composant a sa propre adaptation à une certaine situation.)
  * Nom (enregistrement unique) `Object`
  * Nom (liste des enregistrements) `Objects`
  * Brève description `The object view collects all object data`
  * Cliquez sur `Fields --> Add`, ajoutez le champ titre et alias comme indiqué sur cette image, puis cliquez sur `Save`.
[image]
  * Enregistrez la vue administrateur

<a id="add-an-admin-view-to-our-component"></a>
## Ajouter une vue administrateur à notre composant
* Accédez à `Component Builder --> Joomla Components` et sélectionnez `Archiver`
  *Onglet `Settings`
    * `Admin Views --> Add` (_Important : s'il ne se charge pas avec toutes les options choisies, fermez-le et rouvrez-le._)
      * Sélectionnez `Archiver - Object`
      * Entrez-le comme indiqué sur cette image, `Save`
[image]

<a id="check-our-first-component-v-001"></a>
## Vérifiez notre premier composant (V. 0.0.1)
* Compiler et installer (Voir [Chapitre Compilateur](#compiler))
Comme vous pouvez le constater, le processus d'installation fonctionne désormais puisque nous connectons notre première vue d'administration à notre composant. Vous pouvez utiliser votre premier composant.

<a id="references"></a>
## Références

<a id="our-first-update"></a>
# Notre première mise à jour
Au fur et à mesure que nous poursuivons notre composant, nous devrons souvent adapter nos tables à de nouveaux champs, supprimer d'anciens champs inutilisés, etc. Pour faire cela facilement, et parce que nous pouvons mettre à jour nos composants au lieu de toujours les réinstaller avec le problème de perdre ou de toujours penser à sauvegarder nos données, nous devons ajouter cette information au constructeur de composants.

<a id="preparation"></a>
## Préparation
Pour passer à l'étape suivante, nous répétons tout ce qui est mentionné pour créer une nouvelle vue administrateur (commence ici : [La première vue administrateur](#the-first-admin-view) ). Cette fois, nous appelons la vue `Place` au lieu de `Object`. **Ne compilez pas encore !**

<a id="adjust-the-component-settings-for-the-update"></a>
## Ajustez les paramètres des composants pour la mise à jour
Maintenant que nous avons ajouté une nouvelle vue, nous devons ajuster notre composant.
* Accédez à `Component Builder --> Joomla Components` et sélectionnez `Archiver`
  * Ajoutez la nouvelle vue si vous ne l'avez pas encore fait. Faites attention à la charge de tous les champs. S'ils ne sont pas définis, rouvrez les champs modaux.
  * Changez la version actuelle en `0.0.2`
  * Cliquez sur `Add Update SQL`
  * Créez une nouvelle entrée pour la version 0.0.1 avec le contenu suivant :

CRÉER UNE TABLE SI N'EXISTE PAS `#__archiver_place` (  
        `id` INT(11) NON NULL AUTO_INCREMENT,  
        `asset_id` INT(10) non signé NOT NULL DEFAULT 0 COMMENTAIRE 'FK vers la table #__assets.',  
        `alias` CHAR(64) NON NULL PAR DÉFAUT '',  
        `title` CHAR(64) NON NULL PAR DÉFAUT '',  
        Texte `params` NON NULL PAR DÉFAUT '',  
        `published` TINYINT(3) NON NULL PAR DÉFAUT 1,  
        `created_by` INT(10) non signé NON NULL PAR DÉFAUT 0,  
        `modified_by` INT(10) non signé NON NULL PAR DÉFAUT 0,  
        `created` DATETIME NON NULL PAR DÉFAUT '0000-00-00 00:00:00',  
        `modified` DATETIME NON NULL PAR DÉFAUT '0000-00-00 00:00:00',  
        `checked_out` int(11) non signé NON NULL PAR DÉFAUT 0,  
        `checked_out_time` DATETIME NON NULL PAR DÉFAUT '0000-00-00 00:00:00',  
        `version` INT(10) non signé NOT NULL PAR DÉFAUT 1,  
        `hits` INT(10) non signé NON NULL PAR DÉFAUT 0,  
        `access` INT(10) non signé NON NULL PAR DÉFAUT 0,  
        `ordering` INT(11) NON NULL PAR DÉFAUT 0,  
        `metakey` TEXTE NON NULL PAR DÉFAUT '',  
        `metadesc` TEXTE NON NULL PAR DÉFAUT '',  
        `metadata` TEXTE NON NULL PAR DÉFAUT '',  
        CLÉ PRIMAIRE (`id`),  
        CLÉ `idx_access` (`access`),  
        CLÉ `idx_checkout` (`checked_out`),  
        CLÉ `idx_createdby` (`created_by`),  
        CLÉ `idx_modifiedby` (`modified_by`),  
        CLÉ `idx_state` (`published`),  
        CLÉ `idx_title` (`title`),  
        CLÉ `idx_alias` (`alias`)  
    ) MOTEUR=MyISAM AUTO_INCREMENT=0 DEFAULT CHARSET=utf8;
  * Enregistrez le composant

<a id="check-our-first-component-update-v-002"></a>
## Consultez notre première mise à jour de composant (V. 0.0.2)
* Compiler et installer (Voir [Chapitre Compilateur](#compiler))
Comme vous pouvez le constater, le processus d'installation a désormais fonctionné comme prévu, car nous avons ajouté la mise à jour de notre base de données. Sans cette partie, vous ne pourriez pas profiter de la vue du lieu, car il n'y avait pas de table.

<a id="references-1"></a>
## Références


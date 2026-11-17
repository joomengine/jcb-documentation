> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="installation-of-joomla-component-builder"></a>
# Installation du générateur de composants Joomla

(*Cliquez sur les liens d'horodatage pour ouvrir la vidéo YouTube au bon moment.*)

<a id="introduction---how-to-build-a-component"></a>
## Introduction - Comment créer un composant

[00:00:00](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

Dans ce didacticiel, nous commençons par le **tableau de bord Joomla Component Builder (JCB)** dans le backend Joomla. L'objectif est de démontrer les puissantes capacités de JCB, suivi d'une explication étape par étape sur la façon de créer votre propre composant Joomla à partir de zéro.

Joomla Component Builder permet aux développeurs de créer, gérer et compiler des composants Joomla complexes entièrement à partir de l'interface Joomla. Il fournit un environnement dans lequel plusieurs composants peuvent coexister, partager des vues et utiliser la même infrastructure.

L'instructeur présente plusieurs composants déjà construits avec JCB, y compris plusieurs versions du Component Builder lui-même, toutes gérées dans une seule instance de JCB.
[00:01:10](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m10s)

> **Conseil :** Vous pouvez facilement créer différentes versions de votre composant pour les clients en **dupliquant** un composant dans JCB et en apportant des ajustements spécifiques à la copie. Cela permet une gestion rapide des versions et un développement rationalisé.

---

<a id="jcb-is-fully-open-source"></a>
## JCB est entièrement open source

Joomla Component Builder est un projet unique et unifié publié sous la licence GNU GPL. Il n'y a **pas d'édition « pro » cachée** ni de mise à niveau payante qui débloque des fonctionnalités supplémentaires. Tous les outils avancés, scripts d'assistance, plugins et matériel de démonstration sont livrés dans le package public que vous téléchargez. La communauté a décidé de rendre l'ensemble des fonctionnalités ouvertement disponibles afin que tout le monde puisse étudier, utiliser et améliorer JCB sans rencontrer de barrière de paiement. Lorsque vous installez l’extension, vous recevez la chaîne d’outils complète qui alimentait auparavant la version « pro » fermée.

---

<a id="using-the-compiler"></a>
## Utilisation du compilateur

[00:01:55](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m55s)

Le **Compilateur** est le cœur de JCB. Il transforme tous les paramètres, configurations et modèles de code de la base de données en un composant Joomla prêt à installer.

1. Sélectionnez le composant que vous souhaitez compiler (dans cet exemple, le package Component Builder lui-même est choisi).
2. Cliquez sur **Compiler** pour commencer.
3. JCB exécute ses scripts internes, récupère les données de la base de données et génère le code complet pour votre composant.
   [00:02:14](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m14s)

Une fois la compilation terminée, JCB fournit des statistiques sur :

* Le nombre de lignes écrites
* Estimation du temps de développement gagné
* La possibilité d'**installer**, de **télécharger** ou de **copier l'URL d'installation**

[00:03:18](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m18s)

Si vous développez en ligne, vous pouvez utiliser le lien fourni pour installer le composant directement sur un autre site Joomla. Dans un environnement hors ligne, vous le téléchargerez et l’installerez manuellement.

---

<a id="clear-your-temporary-folder"></a>
## Effacez votre dossier temporaire

[00:03:37](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m37s)

Après avoir compilé et téléchargé un composant, il est **crucial de vider votre dossier temporaire Joomla**.

S'il n'est pas décoché, le fichier `.zip` de votre composant compilé reste accessible dans le dossier `/tmp` de votre site. Cela peut présenter un **risque de sécurité**, car toute personne pouvant accéder à ce chemin de fichier peut télécharger votre package de composants privés.

> **Important :** Supprimez toujours les fichiers `.zip` compilés du dossier temporaire pour garantir que votre travail reste privé et sécurisé.
> *Ceci est particulièrement important lors du développement d'extensions commerciales ou spécifiques au client.*

[00:04:22](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m22s)

---

<a id="setting-up-a-blank-test-website"></a>
## Configuration d'un site Web de test vierge

[00:04:47](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m47s)

Pour tester votre composant, il est préférable de l'installer sur une **nouvelle installation de Joomla**. Cela garantit que toutes les tables et données de configuration sont créées proprement, sans interférence des versions précédentes.

1. Accédez à votre **site de test Joomla**.
2. Utilisez le lien d'installation ou téléchargez le package `.zip` généré par JCB.
3. Cliquez sur **Installer**.
   Une fois l'installation terminée, Joomla affichera un message de réussite confirmant que votre composant est installé.

---

<a id="understanding-the-included-sample-data"></a>
## Comprendre les exemples de données inclus

[00:05:19](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m19s)

JCB est livré avec la collection complète de types de champs, de composants de démonstration et d'exemples de configuration qui étaient historiquement fournis avec les éditions fermées. Ces éléments de référence se trouvent dans les fichiers SQL du package afin que chaque installation démarre avec le même ensemble de données riches. Si jamais vous expérimentez les données et souhaitez les comparer aux valeurs par défaut, les sections suivantes expliquent comment inspecter et restaurer ces enregistrements.

---

<a id="accessing-database-information-in-your-component"></a>
## Accès aux informations de la base de données dans votre composant

[00:05:49](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m49s)

1. Localisez votre fichier `.zip` compilé dans votre système de fichiers.
2. Extrayez-le et accédez au répertoire `admin/sql/`.
   [00:06:02](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m02s)
3. Ouvrez le fichier `install.sql`. Ce fichier définit les tables de base de données pour votre composant.
4. Faites défiler vers le bas de ce fichier pour afficher les **entrées de données sauvegardées**.
   [00:06:28](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m28s)

Le programme d'installation inclut désormais l'ensemble de données complet par défaut. Vous trouverez de nombreux types de champs prédéfinis, des menus d'aide et des enregistrements de démonstration prêts à être explorés ou adaptés à vos propres projets.

---

<a id="option-1-reinstall-jcb-to-restore-default-data"></a>
## Option 1 : Réinstaller JCB pour restaurer les données par défaut

[00:07:05](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m05s)

Si vous souhaitez réinitialiser JCB à l'ensemble de données d'origine, effectuez une réinstallation propre :

1. Accédez à **Extensions → Gérer → Gérer**.
2. Sélectionnez votre installation existante de Component Builder.
3. Cliquez sur **Désinstaller**.
4. Installez le package public actuel que vous avez téléchargé.

> Joomla ne crée des tables que lors d'une **nouvelle installation**, pas lors des mises à jour.
> Par conséquent, la désinstallation garantit que les données par défaut sont restaurées exactement telles qu'elles ont été expédiées.

[00:07:29](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m29s)

---

<a id="option-2-restore-sample-data-manually-via-mysql"></a>
## Option 2 : Restaurer les exemples de données manuellement via MySQL

[00:07:41](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m41s)

Les utilisateurs avancés peuvent importer manuellement le contenu de la base de données :

1. Ouvrez **phpMyAdmin** ou un autre outil de gestion MySQL.
2. Localisez les tableaux JCB pertinents (par exemple, `#__fieldtypes`).
3. **Tronquez** le tableau pour effacer les anciennes données.
   [00:08:30](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m30s)
4. Copiez les données de vidage SQL à partir du fichier `install.sql` du package.
5. Remplacez le préfixe de table (`#__`) par votre préfixe de table Joomla actuel.
6. Collez et exécutez la requête SQL.
   [00:09:49](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m49s)

Cela mettra à jour vos tables JCB avec l'ensemble de données par défaut, sans réinstaller l'intégralité du composant. Cependant, cette approche nécessite des connaissances SQL et une manipulation minutieuse.

[00:10:29](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m29s)

---

<a id="reinstalling-jcb-after-a-reset"></a>
## Réinstallation de JCB après une réinitialisation

[00:10:53](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m53s)

Après une réinstallation propre à partir de **VDM.IO**, vous partirez d'une table rase :

* Il ne reste aucune ancienne donnée de composant.
* Seuls les types de champs et les structures mis à jour sont installés.

Après l'installation, accédez à **Composants → Component Builder** dans le backend.
[00:11:20](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m20s)

Vous verrez une liste de composants vide mais avec un ensemble complet de **types de champs améliorés** disponibles pour les projets futurs.

---

<a id="exploring-the-included-field-types"></a>
## Explorer les types de champs inclus

[00:12:15](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m15s)

Avec le package public installé :

* Accédez à **Types de champs** dans Component Builder.
* Notez une plus grande sélection de types de champs prédéfinis.
* Certains champs et configurations de démonstration sont également inclus.
  [00:12:44](https://www.youtube.com/watch?v=t6Eux157428&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m44s)

Cette version fournit une excellente base pour commencer à créer des composants Joomla complexes.
Le didacticiel se poursuivra en explorant en détail les **Types de champs**, prochaine étape de votre parcours JCB.

---

<a id="summary"></a>
## Résumé

| Étape | Actions | Descriptif |
| ---- | ------------------------------- | ------------------------------------------------------------ |
| 1 | Installer ou compiler un composant | Utilisez le compilateur de JCB pour générer un package `.zip` installable |
| 2 | Effacer le dossier temporaire | Supprimez les fichiers `.zip` de `/tmp` pour des raisons de sécurité |
| 3 | Installer sur le site de test Joomla | Testez sur une installation vierge pour confirmer le succès |
| 4 | Restaurer les données par défaut (facultatif) | Réinstallez JCB ou importez l'exemple de jeu de données si vous avez besoin d'une réinitialisation |
| 5 | Vérifier les types de champs | Confirmez que la bibliothèque complète de types de champs est disponible |

---

> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="jcb-packaging-engine"></a>
# Moteur d'emballage JCB

<a id="why-the-packaging-engine-matters"></a>
<a id="-why-the-packaging-engine-matters"></a>
## 📦 Pourquoi le moteur de packaging est important

Joomla Component Builder (JCB) est désormais livré avec un **moteur de packaging piloté par Git** qui remplace le
flux de travail de package ZIP hérité utilisé à l’époque de Joomla 3. Au lieu d'exporter des archives cryptées
et en les transmettant manuellement, vous pouvez lier n'importe quelle entité JCB à un référentiel Git, lire son
documentation, synchronisez le plan et collaborez via des demandes d'extraction standard.

Considérez le moteur d'empaquetage comme l'**échange de plans** pour JCB :

* Un **package de composants Joomla** (le ZIP que vous installez dans Joomla) contient les fichiers PHP, XML,
  et les actifs qui alimentent un site.
* Un **package JCB** stocke la *définition* de ce composant : les vues d'administration, les champs, le champ
  types, extraits de code, modèles, super pouvoirs et autres métadonnées résidant dans la base de données JCB.

En publiant ces définitions dans les référentiels Git, les équipes peuvent créer des branches, des branches, réviser et fusionner.
change exactement comme n’importe quelle autre base de code.

---

<a id="what-can-be-packaged"></a>
<a id="-what-can-be-packaged"></a>
## 🧱 Que peut-on emballer

Chaque entité majeure de JCB peut être exportée, versionnée et synchronisée via le moteur de packaging :

* Champs et types de champs
* Vues d'administrateur, vues de site et vues d'administrateur personnalisées
* Composants et leurs paramètres
* Extraits, mises en page et modèles
* Superpouvoirs et pouvoirs Joomla
* Toute autre entité apparaissant dans l'interface du packaging

Pour rendre le système prévisible, JCB regroupe les entités en **canaux de contenu cibles**. Chaque canal
mappe vers un ou plusieurs référentiels :

1. **Superpuissances** – Classes PHP entièrement hébergées dans JCB
2. **Joomla Powers** – références aux services de base de Joomla
3. **Types de champs** – modèles et logique pour les entrées de formulaire réutilisables
4. **Extraits** – Blocs de construction HTML/CSS/JS
5. **Packages** – composants complets, vues, mises en page et autres plans
6. **Dépôts** – métadonnées utilisées pour amorcer l'ensemble du réseau

JCB lira et écrira dans chaque référentiel partageant le même contenu cible et publié.

---

<a id="repository-index"></a>
<a id="-repository-index--documentation-engine"></a>
## 🗂 Index du référentiel et moteur de documentation

Le moteur de packaging fait également office de navigateur de documentation. Chaque référentiel contient un `package.json`
fichier plus le contenu Lisez-moi Markdown que JCB restitue directement dans l'interface. Lorsque vous naviguez ou
initialisez un référentiel, vous importez non seulement les données, vous voyez également les informations du référentiel.
propre documentation sur le fonctionnement de ce plan.

Pour charger le catalogue officiel :

1. Ouvrez **Composants → Générateur de composants → Dépôts**.
2. Cliquez sur **Nouveau** et saisissez :
   * **Organisation :** `joomengine`
   * **Dépôt :** `repoindex`
   * **Lire la branche :** `master`
   * **Type :** `GitHub`
   * **Contenu cible :** `repositories`
   * **Accès :** `global`
   * **Nom :** toute étiquette descriptive (par exemple *JoomEngine Repo Index*)
3. Enregistrez l'entrée du référentiel et cliquez sur **Init** dans la liste Référentiels.
4. Sélectionnez la nouvelle entrée et choisissez **Initialiser les référentiels sélectionnés**.

JCB clone l'index du repo, lit son catalogue et crée des enregistrements locaux pour chaque référencement.
référentiel. Leurs fichiers Lisez-moi apparaissent directement dans l'interface utilisateur afin que vous importiez toujours les plans avec
contexte.

---

<a id="init-reset-push"></a>
<a id="-button-flow-init--reset--push"></a>
## 🚀 Flux de boutons : Init → Réinitialiser → Appuyer

Une fois les référentiels existants, chaque entité empaquetable expose trois actions :

<a id="-init"></a>
### 🔹 Initialisation
Lie l'entité actuelle à un référentiel et répertorie les plans distants qui peuvent être importés. Utilisez-le
lorsque vous souhaitez introduire une entité dans votre installation pour la première fois.

<a id="-reset"></a>
### 🔹 Réinitialiser
Actualise l'entité locale à partir de la dernière version du référentiel. JCB honore la commande du dépôt
pour le même contenu cible – publiez les sources auxquelles vous faites confiance et dépublier ou archiver le reste. Quand
vous souhaitez uniquement lire à partir d'un référentiel, dépublier temporairement les autres avant d'appuyer sur Réinitialiser.

<a id="-push"></a>
### 🔹Pousser
Renvoie vos modifications locales au référentiel. Exigences:

* L'entrée du référentiel doit définir une **branche d'écriture** et être publiée.
* Votre site Joomla doit avoir un **jeton GitHub** valide – soit globalement dans
  *Options → Paramètres GitHub* ou par référentiel via **Remplacer les paramètres globaux**.
* Votre compte utilisateur a besoin d'un accès en écriture au référentiel de destination.

Push s'exécute pour **chaque référentiel publié** attribué au même contenu cible. Supprimer l'écriture
branchez ou annulez la publication des référentiels inutilisés lorsque vous souhaitez limiter la destination push.

---

<a id="git-authentication"></a>
<a id="-git-authentication"></a>
## 🔐 Authentification Git

Vous pouvez stocker un jeton d'accès personnel à deux endroits :

* **Jeton global** – définissez-le une fois sous *Components → Component Builder → Options → GitHub*.
* **Remplacement du référentiel** : modifiez une entrée du référentiel, activez *Remplacer les paramètres globaux* et ajoutez un
jeton qui ne doit être utilisé que pour ce référentiel.

Les jetons sont stockés cryptés dans JCB. Assurez-vous qu'ils autorisent la portée `repo` pour que les poussées réussissent.

---

<a id="dependency-resolution"></a>
<a id="-dependency-resolution--ordering"></a>
## 🔄 Résolution et commande des dépendances

L’importation ou la réinitialisation d’un plan extrait automatiquement chaque entité liée. Si une vue administrateur
utilise un type de champ ou un composant dépend d'extraits de code, ces références sont résolues à partir du
référentiels. Lorsque plusieurs référentiels fournissent la même entité, JCB honore l'ordre de la liste au sein
qui ciblent le contenu :

1. Publiez uniquement les référentiels auxquels vous faites confiance.
2. Faites-les glisser dans l'ordre de priorité souhaité.
3. Utilisez **Reset** pour réhydrater vos entités locales.

Cela permet de mettre en scène des référentiels expérimentaux, de conserver un canonique en amont, et seulement
changez de source lorsque vous modifiez délibérément l’ordre.

---

<a id="example-workflow"></a>
<a id="-example-workflow"></a>
## 🧰 Exemple de workflow

1. **Créez un référentiel** pour vos plans de composants (par exemple `your-org/component-blueprints`).
2. Dans JCB, ajoutez une entrée de référentiel avec le contenu cible correct (`packages` pour les composants complets,
   `field_types` pour les bibliothèques de champs, etc.) et définir des branches de lecture/écriture.
3. Concevez votre composant comme d'habitude dans JCB.
4. Cliquez sur **Push** sur le composant pour publier le plan sur Git.
5. Les membres de l'équipe ajoutent la même entrée de référentiel, appuyez sur **Init** et sélectionnez le composant à importer.
6. Chacun édite dans sa propre instance JCB, applique les modifications et collabore via des pull request
   exactement comme n’importe quel autre projet Git.

Étant donné que les référentiels incluent de la documentation Markdown, votre plan peut être livré avec des guides d'utilisation,
notes de configuration, exemples de données ou instructions de mise à niveau.

---

<a id="fork-and-pr"></a>
<a id="-forks-pull-requests--community-repos"></a>
## 🤝 Forks, demandes de tirage et dépôts communautaires

Le catalogue officiel de JoomEngine se trouve sur [github.com/joomengine](https://github.com/joomengine).
Pour contribuer :

1. **Fork** le référentiel qui correspond au contenu cible (par exemple `joomengine/packages`).
2. Ajoutez votre fourche à l'intérieur de JCB pour qu'elle apparaisse à côté de l'officiel en amont.
3. Développez localement, appuyez sur **Push** et validez depuis votre client Git.
4. Ouvrez une pull request décrivant ce qui a changé. Les liens vers des problèmes ou des discussions sont encouragés.

Étant donné que les plans se trouvent dans Git, vous pouvez examiner les différences, baliser les versions et automatiser les tests, tout comme
tout projet logiciel.

---

<a id="best-practices"></a>
<a id="-best-practices"></a>
## ✅ Bonnes pratiques

* **Référentiels de segments** par objectif : gardez les types de champs séparés des plans de composants pour éviter
  dépendances inutiles.
* **Nommez clairement les référentiels** et faites correspondre le nom du système JCB au slug Git pour une découverte facile.
* **Documentez tout** dans le fichier Lisez-moi du référentiel – JCB le présente directement dans l'interface.
* **Toujours Init avant Push** lorsque vous travaillez sur une nouvelle machine afin que vos entités locales soient liées au
  corriger l'historique du référentiel.
* **Dépublier les référentiels inutilisés** pour éviter les poussées ou réinitialisations accidentelles.
* **Traitez le référentiel comme la source de vérité** – la base de données Joomla n'est que votre copie de travail.

---

<a id="further-reading"></a>
<a id="-further-reading"></a>
## 📚 Lectures complémentaires

* Index du référentiel officiel : [https://github.com/joomengine/repoindex](https://github.com/joomengine/repoindex)
* Fil de discussion sur l'emballage : [JoomEngine Discussions #995](https://github.com/orgs/joomengine/discussions/995)
* Guide de workflow collaboratif : [Flux de travail collaboratif proposé dans JCB](./Proposed-Collaborative-Workflow-in-JCB.md)
* Tutoriels de publication : [Ajoutez vos propres packages JCB au répertoire](./Add-your-own-JCB-packages-to-the-JCB-Communty-Directory.md)

Utilisez ces ressources pour concevoir des flux de travail reproductibles où chaque modification apportée à vos plans JCB est prise en compte.
révisé, versionné et partageable.
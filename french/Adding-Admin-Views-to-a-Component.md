> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="adding-admin-views-to-a-component"></a>
# **Ajout de vues d'administration à un composant**

*(Basé sur la vidéo du didacticiel Joomla Component Builder)*
[Regarder la vidéo](https://www.youtube.com/watch?v=39vY66X7GGU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

---

<a id="overview"></a>
## **Aperçu**

Dans ce didacticiel, nous allons explorer comment **ajouter des vues d'administration** à un composant à l'aide de **Joomla Component Builder (JCB)**.
Vous apprendrez comment connecter vos vues d'administration créées à votre composant, configurer les paramètres de visibilité, activer les fonctionnalités clés de Joomla telles que **Auto Check-In**, **Historique des versions**, **Import/Export** et **Front-End Editing**, et comprendre comment celles-ci affectent votre flux de travail et votre composant généré.

> 🔎 **Nouveau dans les vues d'administration ?** Commencez par le [JCB Admin Views feature overview](./Features/JCB-Admin-Views.md) pour comprendre le
> concepts avant de les appliquer à l'intérieur d'un composant.

Les vues d'administration constituent la couche obligatoire de définition de schéma pour chaque composant construit par JCB. Chacun est lié à une table de base de données et fournit automatiquement les modèles générés, les contrôleurs, les dispositions de liste/modification et la gestion des autorisations qui alimentent la pile MVC de Joomla. Pour cette raison, un composant ne peut pas être compilé sans au moins une vue d'administration, et tout comportement de composant supplémentaire doit toujours s'appuyer sur ces fondations CRUD générées.

Cette section suppose que vous avez déjà :

* Installé le générateur de composants Joomla.
* Création d'une ou plusieurs **Vues administrateur** avec des champs (voir les didacticiels précédents sur les types de champs et les vues administrateur).

> **Besoin de mettre à jour une vue d'administration partagée ?** Dans JCB, sélectionnez la vue, cliquez sur **Réinitialiser** pour extraire la dernière version de ce référentiel, ou pointez votre instance vers un fork si vous conservez une référence personnalisée. Cela maintient les projets collaboratifs alignés tout en autorisant les remplacements par projet.

---

<a id="1-connecting-admin-views-to-a-component"></a>
## **1. Connexion des vues d'administration à un composant**

[00:00:28](https://www.youtube.com/watch?v=39vY66X7GGU&t=00h00m28s)

1. Dans JCB, ouvrez votre **Composant** (par exemple, *Sermon Distributor*).
2. Accédez à **Paramètres → Vues d'administration**.
   C'est ici que vous liez vos vues d'administration existantes au composant.
3. Cliquez sur le bouton **Ajouter**, puis sélectionnez une **Vue administrateur** dans la liste déroulante.
4. Répétez ce processus pour chaque vue que vous souhaitez joindre.

**Conseil :**
Si vous disposez de nombreuses vues d'administrateur, saisissez le nom de la vue dans la barre de recherche pour la localiser rapidement.

---

<a id="2-adding-view-icons"></a>
## **2. Ajout d'icônes de vue**

[00:01:39](https://www.youtube.com/watch?v=39vY66X7GGU&t=00h01m39s)

Lorsque vous attribuez une vue administrateur, vous pouvez définir une **icône** pour la représenter dans l'interface backend.

* JCB utilise **Joomla Standard Icomoon Fonts** pour ces icônes.
* Lorsque vous sélectionnez une icône, vous verrez immédiatement un aperçu.
* L'icône que vous choisissez apparaît dans la barre latérale et le tableau de bord des composants de l'administrateur Joomla.

**Conseil :**
Choisissez des icônes qui correspondent visuellement à l'objectif de votre vue (par exemple, une icône de document pour « Articles », une icône d'utilisateur pour « Auteurs »).

---

<a id="3-admin-menu-visibility"></a>
## **3. Visibilité du menu administrateur**

[00:02:29](https://www.youtube.com/watch?v=39vY66X7GGU&t=00h02m29s)

JCB vous propose des commutateurs pour contrôler la manière dont chaque vue apparaît dans le menu d'administration de votre composant.

* **Menu administrateur :**
  Activez ceci si vous souhaitez que la vue apparaisse dans la barre latérale de Joomla (sous le menu de votre composant).

---

<a id="4-dashboard-item-visibility"></a>
## **4. Visibilité des éléments du tableau de bord**

[00:03:04](https://www.youtube.com/watch?v=39vY66X7GGU&t=00h03m04s)

* **Tableau de bord (liste des enregistrements) :**
  Ajoute une icône de raccourci au tableau de bord principal pour afficher les enregistrements.
* **Tableau de bord (Ajouter un enregistrement) :**
  Ajoute un bouton qui permet la création rapide de nouveaux enregistrements directement à partir du tableau de bord du composant.

Si vous préférez ne pas afficher « Ajouter un enregistrement » sur le tableau de bord, définissez-le sur **Non**.

---

<a id="5-submenu-inclusion"></a>
## **5. Inclusion de sous-menu**

[00:03:41](https://www.youtube.com/watch?v=39vY66X7GGU&t=00h03m41s)

Vous pouvez inclure ou exclure une vue du **sous-menu** (la zone de navigation réductible à l'intérieur de chaque vue d'administration).

* Activez ceci si la vue doit être accessible en tant qu'option de sous-menu.

---

<a id="6-auto-check-in-feature"></a>
## **6. Fonction d'enregistrement automatique**

[00:03:57](https://www.youtube.com/watch?v=39vY66X7GGU&t=00h03m57s)

Cette fonctionnalité archive automatiquement les éléments qui ont été extraits pendant plus d'une période définie.

* Activez **l'enregistrement automatique** dans les paramètres de votre vue d'administration.
* Configurez la durée du délai d'expiration dans les **Paramètres globaux** de votre composant sous "Période d'enregistrement automatique".

**Exemple :**
Si un utilisateur oublie de fermer un élément, la fonction d'enregistrement automatique de JCB libèrera automatiquement le verrou après un délai défini.

---

<a id="7-enable-version-history"></a>
## **7. Activer l'historique des versions**

[00:05:06](https://www.youtube.com/watch?v=39vY66X7GGU&t=00h05m06s)

L'intégration du **Composant Historique** permet à Joomla de suivre chaque modification apportée aux enregistrements dans votre composant.

**Étapes pour utiliser l'historique des versions :**

1. Activez **Conserver l'historique** dans la vue Administrateur.
2. Modifiez un élément (par exemple, « Prédicateur → Musique A Capella »).
3. Cliquez sur **Versions** dans la barre d'outils supérieure.
4. Vous pouvez :

* Afficher toutes les versions enregistrées précédentes.
   * Restaurez une version antérieure si nécessaire.

**Conseil :**
Vous pouvez également définir le nombre de versions historiques que Joomla conserve pour chaque élément.

---

<a id="8-add-metadata-support"></a>
## **8. Ajouter la prise en charge des métadonnées**

[00:14:23](https://www.youtube.com/watch?v=39vY66X7GGU&t=00h14m23s)

Si les données de votre vue apparaissent sur le front-end, activez la prise en charge des **Métadonnées**.

* Les métadonnées ajoutent des données liées au référencement (titre, description, mots-clés) à vos pages.
* Bien que moins crucial pour les moteurs de recherche aujourd'hui, il améliore néanmoins l'organisation du contenu et les aperçus du partage social.

Activez les métadonnées pour les vues de contenu qui représentent des pages frontales uniques ou indexables.

---

<a id="9-enable-access-control"></a>
## **9. Activer le contrôle d'accès**

[00:15:37](https://www.youtube.com/watch?v=39vY66X7GGU&t=00h15m37s)

Le **Access Switch** active le menu déroulant de niveau d'accès standard de Joomla (par exemple, *Public*, *Registered*, *Special*).

Cela permet de restreindre la visibilité du contenu en fonction des rôles ou des groupes d'utilisateurs.

* Activez **Accès** dans votre vue administrateur si vous souhaitez un contrôle d'accès par élément.
* Souvent combiné avec des **autorisations**, mais généralement pas les deux à la fois.

---

<a id="10-importexport-data"></a>
## **10. Importer/Exporter des données**

[00:16:38](https://www.youtube.com/watch?v=39vY66X7GGU&t=00h16m38s)

JCB peut ajouter automatiquement la fonctionnalité **Importer/Exporter** à chaque vue d'administration.

* Basculez **Exporter/Importer des données** sur « Oui » pour l'activer.
* Après compilation, chaque vue de liste d'administrateurs aura :

* Un bouton **Exporter** (télécharger les données CSV).
  * Un bouton **Importer** (télécharger et mapper les données CSV aux champs de la base de données).

**Remarque :**
Les champs chiffrés nécessitent des précautions : les données importées ne seront pas automatiquement rechiffrées à moins d'être traitées manuellement.

---

<a id="11-editcreate-site-views"></a>
## **11. Modifier/Créer des vues de site**

[00:18:20](https://www.youtube.com/watch?v=39vY66X7GGU&t=00h18m20s)

C'est l'une des fonctionnalités les plus puissantes de JCB.
Lorsqu'il est activé, il permet la **modification frontale** de vos données administratives.

<a id="how-it-works"></a>
### **Comment ça marche**

1. Activez le commutateur **Modifier Créer une vue de site** dans les paramètres de votre vue d'administration.
2. Lors de la compilation :

* JCB génère une version **site view** de votre formulaire d'administration.
   * Cela inclut tous les champs, validations et contrôles d'autorisation.
3. Vous pouvez ensuite ajouter des liens de menu ou des modules pour exposer l'interface d'édition frontale.

**Exemple :**
Une vue d'administration « Entreprise », lorsqu'elle est activée, génère une page frontale où les utilisateurs connectés peuvent :

* Modifier les données de l'entreprise.
* Ajouter de nouveaux enregistrements (si autorisé).

Les autorisations sont appliquées automatiquement : si un utilisateur n'est pas autorisé à modifier certains champs, ceux-ci n'apparaîtront pas dans son formulaire.

**Important :**
JCB génère le code frontal mais ne crée pas automatiquement les liens de menu.
Vous devez lier manuellement ces vues de site via des éléments de menu Joomla ou des modèles personnalisés.

---

<a id="12-ordering-and-display"></a>
## **12. Commande et affichage**

[00:24:48](https://www.youtube.com/watch?v=39vY66X7GGU&t=00h24m48s)

La colonne **Commander** dans les paramètres de la vue administrateur détermine :

* L'ordre dans lequel les vues apparaissent dans la barre latérale d'administration.
* L'ordre des éléments et des icônes du sous-menu.

Ajustez ces chiffres pour organiser votre panneau d'administration de manière logique (par exemple, répertorier les vues avant de modifier les vues).

---

<a id="conclusion"></a>
## **Conclusion**

L'ajout et la configuration de vues d'administration constituent une partie essentielle du flux de travail de JCB.
Grâce à ces paramètres, vous pouvez définir le comportement de chaque vue dans le backend et, éventuellement, comment elle s'intègre au front-end de votre site.

En suivant ces étapes, vous garantirez que votre composant :

* Est convivial pour les administrateurs.
* Prend en charge les fonctionnalités natives de Joomla telles que l'enregistrement automatique et l'historique des versions.
* Fournit un accès flexible et des capacités d'importation/exportation.
* Peut s'étendre de manière transparente au front-end pour l'édition au niveau du site.

---

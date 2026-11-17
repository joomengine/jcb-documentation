> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="joomla-component-builder---admin-views"></a>
# **Joomla Component Builder - Vues d'administration**

<a id="based-on-admin-views-tutorialhttpswwwyoutubecomwatchvcdsksctzmralistplqrgfi8xz_wtgvpqzwbfdzzlerlqgpmre"></a>
### Basé sur [Tutoriel des vues d'administration](https://www.youtube.com/watch?v=CdSKSCTzmRA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)

(*Cliquez sur les horodatages pour afficher les sections de la vidéo du didacticiel original.*)

---

> 📘 **Besoin d'un résumé global des fonctionnalités ?** Lisez le [Guide des fonctionnalités JCB Admin Views](./Features/JCB-Admin-Views.md) pour en savoir plus
> pourquoi ce domaine augmente la productivité avant de plonger dans le didacticiel détaillé ci-dessous.

---

<a id="1-overview"></a>
## **1. Aperçu**

[00:00:00](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=00h00m00s)

Dans cette leçon, nous explorons comment configurer des **Vues administrateur** dans Joomla Component Builder (JCB).
Les vues d'administration constituent le **fondement de la structure de base de données de votre composant** : chaque vue d'administration correspond à une **table de base de données** qui définit la manière dont les données de votre composant sont stockées et gérées.

Avant cette étape, vous devez déjà comprendre :

* La présentation de [JCB Fields](./JCB-Fields.md) qui explique comment chaque définition de champ régit le stockage, le rendu et le partage.
* **Types de champs** et **Champs de base** (tutoriels précédents)
* La structure de **Planification Générale** de votre composant

Les vues d'administration rassemblent ces champs pour former l'interface backend réelle et la logique de votre composant.

<a id="what-are-admin-views"></a>
### Que sont les vues d'administration ?

Les vues d'administration constituent la couche d'interface fondamentale de chaque composant Joomla construit par JCB. Chaque vue d'administration est étroitement liée à un
table de base de données et génère automatiquement les **formulaires**, **modèles**, **contrôleurs**, **vues de liste et d'édition** requis, ainsi que
gestion des autorisations et validation des champs. Étant donné que les vues d'administration produisent l'intégralité de la pile CRUD, chaque composant JCB doit inclure au
au moins une vue Admin pour être considérée comme valide et compiler correctement. Ils garantissent que votre composant reste aligné avec celui de Joomla
architecture MVC native et offre une expérience administrative cohérente et prête à l'emploi.

<a id="why-are-admin-views-important"></a>
### Pourquoi les vues d'administrateur sont-elles importantes ?

Les vues d'administration servent d'ancre de données pour un composant :

* Lien direct vers les tables de la base de données Joomla
* Attachez automatiquement plusieurs champs tout en respectant leur visibilité et leurs autorisations de modification
* Activer les sous-formulaires qui font référence à d'autres vues d'administration pour les structures de données imbriquées
* Respecter l'ACL Joomla par vue **et** par champ
* Restez réutilisable sur plusieurs composants grâce à une compilation prenant en compte les espaces de noms

Cela fait des vues d'administration le cœur de chaque composant, définissant son schéma, son expérience d'édition et sa structure administrative. Alors que
Les vues d'administration personnalisées ou les vues de site se concentrent sur la mise en page et le rendu, les vues d'administration définissent la définition des données structurelles et la logique de base.

<a id="versioning-and-sharing-admin-views"></a>
### Gestion des versions et partage des vues d'administration

Lorsque vous devez mettre à jour les vues d'administration dans un projet JCB, vous pouvez :

1. Sélectionnez les vues que vous souhaitez mettre à jour dans JCB.
2. Cliquez sur **Réinitialiser** pour extraire la dernière version de ce référentiel.
3. Ou **Fork** ce référentiel et pointez votre instance JCB vers ce fork si vous avez besoin de votre propre base de référence.

Ce flux de travail permet de maintenir les vues d'administration partagées tout en vous offrant la flexibilité de les personnaliser par projet. N'oubliez pas que l'administrateur
Les vues sont plus que des modèles d'interface utilisateur : ce sont des déclarations sur la manière dont votre composant gère les données. L'examen du composant de démonstration livré est
un moyen efficace de voir les meilleures pratiques en action.

---

<a id="2-naming-conventions"></a>
## **2. Conventions de dénomination**

[00:00:35](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=00h00m35s)

Chaque vue d'administration dans JCB utilise trois identifiants de nom :

| Tapez | Descriptif | Exemple |
| --------------- | ------------------------------------------ | -------------------------------- |
| **Nom unique** | Utilisé pour éditer un seul enregistrement | `preacher` |
| **Nom au pluriel** | Utilisé pour répertorier les enregistrements | `preachers` |
| **Nom du système** | Nom unique pour différencier les vues similaires | `com_sermondistributor_preacher` |

> **Conseil :**
> Si vous créez deux composants dotés tous deux d'une vue administrateur « prédicateur », utilisez le **Nom du système** pour les différencier (par exemple, incluez le nom du composant).

Ce système de dénomination active le **contrôle de version** et vous permet de réutiliser les vues d'administration sur différents composants.

---

<a id="3-creating-an-admin-view"></a>
## **3. Création d'une vue administrateur**

[00:02:49](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=00h02m49s)

1. Dans le tableau de bord JCB, accédez à **Vues administrateur** → **Nouveau**.
2. Remplissez le **Nom unique** (par exemple, `preacher`) et le **Nom pluriel** (`preachers`).
3. Ajoutez éventuellement une **Description courte** et une **Description complète**.
4. Définissez le **Type** :

* `Read/Write` → champs modifiables
   * `Read Only` → accès en visualisation seule

> **Remarque :**
> Les champs comme **Modifié par** sont automatiquement mis à jour et ne peuvent pas être modifiés manuellement.

---

<a id="4-assigning-view-icons"></a>
## **4. Attribution d'icônes de vue**

[00:04:16](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=00h04m16s)

Des icônes apparaissent sur le tableau de bord d'administration pour chaque vue.

1. Passez la souris sur le champ de l'icône pour voir les dimensions recommandées.
2. Choisissez **Ajouter une icône** ou **Icône** → parcourez le dossier `/images`.
3. Sélectionnez une image qui représente visuellement votre point de vue (par exemple, catégorie, prédicateur).

> **Conseil :**
> Pour une conception cohérente, utilisez des icônes correspondantes dans toutes les vues associées (par exemple, si les catégories s'appliquent à toutes les entités, utilisez la même icône pour chacune).

---

<a id="5-permissions-setup"></a>
## **5. Configuration des autorisations**

[00:06:15](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=00h06m15s)

JCB intègre la liste de contrôle d'accès (ACL) de Joomla mais l'étend avec des **autorisations granulaires par vue**.

<a id="common-permission-types"></a>
### Types d'autorisations courants

| Autorisation | Descriptif |
| --------------------------------- | ---------------------------------------------------- |
| **core.edit** / **view.edit** | Accès en modification (global ou spécifique à une vue) |
| **core.create** / **view.create** | Autoriser les nouveaux enregistrements |
| **core.delete** / **view.delete** | Autoriser la suppression |
| **core.edit.state** | Changer l'état de publication/dépublication |
| **core.edit.own** | Modifier uniquement ses propres enregistrements |
| **core.access** | Accès en visualisation seule |
| **core.batch.use** | Contrôler l'accès aux opérations par lots |

**Core** = paramètre global (s'applique à toutes les vues)
**Vue** = paramètre spécifique (s'applique uniquement à la vue donnée)

> **Meilleure pratique :**
> Utilisez des **autorisations préfixées par vue** (`view.edit`, `view.delete`, etc.) pour les composants volumineux où chaque vue a des règles distinctes.

Les autorisations peuvent également cibler des **champs individuels** via le **Commutateur d'autorisation** dans la configuration des champs.

---

<a id="6-tabs"></a>
## **6. Onglets**

[00:19:26](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=00h19m26s)

Les onglets organisent les champs dans la présentation du formulaire principal.

* **Onglets créés automatiquement :**

* *Publication* (champs système par défaut)
  * *Autorisations* (si les autorisations sont activées)

* **Onglets personnalisés :**
  Vous pouvez créer des onglets tels que *Détails*, *Sermons*, *Paramètres*, etc.

Chaque champ doit préciser son **numéro d'onglet** (1, 2, 3, etc.) dans les paramètres du champ.
JCB placera le champ à l'intérieur de l'onglet correspondant.

---

<a id="7-linked-views"></a>
## **7. Vues liées**

[00:20:53](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=00h20m53s)

Les vues liées connectent deux vues d'administration (relation parent-enfant).
Exemple : *Prédicateur → Sermons.*

<a id="steps-to-create-a-linked-view"></a>
### Étapes pour créer une vue liée

1. Dans la **Vue parent** (`preacher`), ouvrez l'onglet **Vues liées**.
2. Sélectionnez **Vue enfant** (`sermons`).
3. Définir :

* **Onglet** (par exemple, onglet Sermons)
   * **Clé parent** → `id` (du parent)
   * **Clé enfant** → champ associé (par exemple, `preacher`)
4. Activez **Ajouter un nouveau bouton** si vous souhaitez autoriser de nouvelles entrées enfants à partir de la vue parent.

> **Conseil :**
> Assurez-vous que les relations avec la base de données correspondent - la table enfant doit stocker l'ID du parent.

---

<a id="8-field-configuration"></a>
## **8. Configuration sur le terrain**

[00:32:30](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=00h32m30s)

Une fois la vue créée, attribuez-lui des champs :

1. Accédez à l'onglet **Champs** dans la vue Administrateur.
2. Utilisez la barre de recherche pour trouver votre champ.
3. Configurez les options :

* **Afficher dans la liste d'administration** - affichage en vue liste
   * **Commande** - position d'affichage
   * **Triable / Recherchable / Filtrable / Cliquable** - activez ces fonctionnalités

> **Exemple :**
> Le champ *Nom* peut être rendu **cliquable**, ouvrant directement la vue d'édition.

> **Conseil d'intégration Joomla :**
> Incluez toujours un champ **Titre** et **Alias** pour les vues prêtes pour le frontend (important pour le référencement, l'historique et les balises).

---

<a id="9-field-alignment"></a>
## **9. Alignement du champ**

[00:37:54](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=00h37m54s)

Contrôlez où un champ apparaît dans le formulaire d'édition :

| Poste | Descriptif |
| ----------------------- | ------------------------------- |
| Onglet Droite/Gauche **dans** | Dans l'onglet actuel |
| Droite / Gauche **de** l'onglet | Zone d'onglet extérieure |
| Onglet **Ci-dessus** | Toujours visible en haut |
| Onglet **Ci-dessous** | Apparaît sous tous les onglets |
| **Pleine largeur** | S'étend sur toute la largeur du réseau |

Les champs pleine largeur apparaissent sous les sections gauche et droite.
Vous pouvez également **ajouter des contrôles d'autorisation** à des champs individuels.

---

<a id="10-field-titles-and-aliases"></a>
## **10. Titres de champs et alias**

[00:41:39](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=00h41m39s)

* Chaque vue ne doit avoir ** qu'un seul titre ** et ** un seul alias **.
* Le système ignore les doublons.
* Définissez les options **Filtre**, **Triable** et **Cliquable** selon vos besoins.

---

<a id="11-conditional-fields"></a>
## **11. Champs conditionnels**

[00:43:47](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=00h43m47s)

Les conditions définissent quand un champ doit apparaître en fonction des valeurs des autres.

<a id="example"></a>
### Exemple:

> Afficher le champ *Script personnalisé* uniquement lorsque *Ajouter JavaScript* = Oui.

Utiliser:

* **Champ cible :** le champ à afficher/masquer
* **Action :** `Show` ou `Hide`
* **Champ de condition :** champ de contrôle
* **Valeur :** valeur de déclenchement

Ce système étend la logique de base « ShowOn » de Joomla et se compile automatiquement en JavaScript personnalisé.

---

<a id="12-isolate-and-chain"></a>
## **12. Isoler et enchaîner**

[00:45:55](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=00h45m55s)

Utilisé lorsque **plusieurs conditions** doivent être vraies.

* **Isoler** - conditions distinctes (un seul déclencheur)
* **Chaîne** - toutes les conditions doivent être vraies

> **Exemple :**
> Afficher « Dropbox Auto Note » uniquement si :
>
> * Source = Dropbox
> * Option construite = Automatique

Le compilateur de JCB génère automatiquement toute la logique JavaScript nécessaire.

---

<a id="13-adding-custom-code-css-js-ajax-php"></a>
## **13. Ajout de code personnalisé (CSS, JS, AJAX, PHP)**

[01:00:18](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=01h00m18s)

Vous pouvez insérer des **scripts personnalisés** directement dans votre vue administrateur :

<a id="css"></a>
### CSS

Ajoutez du CSS personnalisé pour :

* **Vue unique (Modifier)**
* **Vue Liste**

<a id="javascript"></a>
### JavaScript

Choisissez entre :

* **Inclusion de fichier** (ajoute au fichier JS)
* **Inclusion du pied de page** (bloc de script en ligne)

<a id="ajax-integration"></a>
### Intégration AJAX

[01:01:48](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=01h01m48s)

JCB génère automatiquement un contrôleur `ajax.json.php` et un modèle `ajax`.

1. Définissez votre **tâche AJAX** et votre **méthode** (publique).
2. Ajoutez des valeurs d'entrée telles que `view`, `type` ou `user`.
3. Utilisez `checkDropboxListing` (du didacticiel) comme exemple fonctionnel.

La logique AJAX garantit une validation sécurisée des jetons et peut exécuter des événements globaux tels que la mise à jour de listes ou de données externes.

---

<a id="14-php-hook-methods"></a>
## **14. Méthodes de hook PHP**

[01:10:41](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=01h10m41s)

Vous pouvez injecter du code PHP dans ces méthodes de modèle/contrôleur :

| Méthode | Objectif |
| ---------------------------- | -------------------------------------- |
| `getItem()` | Modifier les données récupérées avant le rendu |
| `save()` | Exécutez le code personnalisé avant d'enregistrer |
| `postSaveHook()` | Exécuter le code après la sauvegarde (au niveau du contrôleur) |
| `batchCopy()`, `batchMove()` | Personnaliser les opérations par lots |

> **Conseil :**
> Écrivez votre logique dans le bloc PHP et utilisez `parent::save($data)` après vos modifications.

---

<a id="15-mysql-dump-test-data"></a>
## **15. Données de test de vidage MySQL**

[01:15:06](https://www.youtube.com/watch?v=CdSKSCTzmRA&t=01h15m06s)

JCB peut **générer des vidages de données de test** pour précharger votre composant avec des exemples d'enregistrements.

1. Accédez à l'onglet **Dumps MySQL**.
2. Sélectionnez la table à vider (par exemple, `sermon`).
3. Cliquez sur **Exporter** → génère la structure SQL et les insertions.
4. Remplacez les préfixes de table (`cb_` → `#__`) pour la compatibilité Joomla.
5. Enregistrez sur votre composant pour le réutiliser lors de la réinstallation.

> **Avantage :**
> Gain de temps lors des tests puisque vous pouvez réinstaller votre composant avec les données de démonstration préchargées.

---

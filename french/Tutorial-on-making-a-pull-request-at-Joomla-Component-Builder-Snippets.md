> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="making-a-pull-request-at-joomla-component-builder-snippets"></a>
# Faire une pull request sur les extraits de Joomla Component Builder

Ce guide explique comment **soumettre vos contributions d'extraits** au référentiel officiel d'extraits de code Joomla Component Builder (JCB) en créant une **demande d'extraction** (PR). Il suit exactement le flux de travail démontré dans le [didacticiel vidéo](https://www.youtube.com/watch?v=vQ-yxVtc-Co&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s) et fournit une explication claire et conviviale de chaque étape. Le gestionnaire d'extraits de code actualisé utilise désormais le flux **Reset → Init → Push**, afin que vous puissiez préparer, valider et diffuser les mises à jour directement depuis JCB avant d'ouvrir votre PR.

---

<a id="1-overview-of-the-pull-request-process"></a>
## 1. Présentation du processus de demande de tirage

[00:00:00](https://www.youtube.com/watch?v=vQ-yxVtc-Co&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

Une pull request (PR) vous permet de soumettre vos **modifications validées** de votre **version forkée** du référentiel `joomengine/snippets` au référentiel officiel.

* Vous contribuerez à la **bibliothèque de snippets** utilisée par la communauté JCB.
* L'équipe JCB et d'autres gestionnaires de communauté examineront et fusionneront les contributions valides.
* Travaillez toujours sur votre **propre référentiel forké** plutôt que sur la branche principale.

---

<a id="2-preparing-your-fork-for-contribution"></a>
## 2. Préparer votre fourchette pour la contribution

[00:01:05](https://www.youtube.com/watch?v=vQ-yxVtc-Co&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m05s)

Avant de créer un PR, assurez-vous d'avoir :

1. **Forked** le référentiel principal (`joomengine/snippets`).
2. **Configuré le Snippet Manager** dans JCB pour utiliser votre fork via la boîte de dialogue **Réinitialiser**.
3. **Initialisez** le référentiel afin que les extraits de code que vous envisagez de modifier soient disponibles localement.
4. **Commis** vos modifications depuis JCB à l'aide de l'action **Push** (qui écrit sur votre fork).
5. **Synchronisez votre branche** avec la branche amont (généralement la branche `main`) avant d'ouvrir une pull request.

> **Conseil :** Si vous n'êtes pas sûr de pouvoir créer ou synchroniser votre référentiel, regardez le **tutoriel précédent** dans la playlist avant de continuer.

---

<a id="3-checking-your-commit-status"></a>
## 3. Vérifier votre statut de validation

[00:01:43](https://www.youtube.com/watch?v=vQ-yxVtc-Co&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m43s)

Une fois que vos commits sont prêts et transférés vers GitHub :

* Accédez à votre référentiel forké.
* Vous verrez un message comme :

  ```
  This branch is 4 commits ahead of joomengine:main.
  ```* Cliquez sur **"Pull request"** pour démarrer le processus de relations publiques.

---

<a id="4-confirming-repository-and-merge-status"></a>
## 4. Confirmation du statut du référentiel et de la fusion

[00:02:08](https://www.youtube.com/watch?v=vQ-yxVtc-Co&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m08s)

GitHub affichera :

* **Dépôt de base :** `joomengine/snippets (main)`
* **Référentiel principal :** votre fork et votre branche

Si GitHub affiche **"Capable de fusionner"**, tout est prêt.

Vous pouvez également consulter :

* Chaque **message de validation**
* Chaque **changement de fichier**
* Les exemples incluent les changements de nom d'extrait tels que :

  ```
  FooTable - (Layout) FooTable.json → FooTable - (Table) FooTable.json
  ```

> **Bonne pratique :** Rédigez des messages de validation clairs et concis pour faciliter et accélérer la révision.

---

<a id="5-submitting-smaller-contributions"></a>
## 5. Soumettre des contributions plus petites

[00:04:08](https://www.youtube.com/watch?v=vQ-yxVtc-Co&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m08s)

Commencez petit. Soumettez quelques extraits à la fois, surtout s'il s'agit de votre première contribution.

* Évitez de soumettre des **modifications massives**, sauf si vous êtes un contributeur de confiance.
* Les PR plus petits sont plus faciles à examiner et à fusionner rapidement.

---

<a id="6-creating-the-pull-request"></a>
## 6. Création de la Pull Request

[00:04:41](https://www.youtube.com/watch?v=vQ-yxVtc-Co&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m41s)

1. Cliquez sur **"Créer une demande d'extraction"**.
2. Fournissez un **titre** et une **description** résumant la contribution.

<a id="example"></a>
### Exemple:

**Titre:**

> "Ajout d'un extrait d'accordéon et mise à jour des mises en page FooTable"

**Description:**

> * Ajout d'un nouvel extrait d'accordéon
> * Mise à jour de la disposition des extraits de FooTable en type de tableau
> * Champ de description d'utilisation amélioré

> À l'avenir, JCB pourra inclure des conventions de dénomination prédéfinies et des modèles pour les titres des demandes d'extraction.

---

<a id="7-admin-review-process"></a>
## 7. Processus d'examen par l'administrateur

[00:05:43](https://www.youtube.com/watch?v=vQ-yxVtc-Co&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m43s)

Seuls les administrateurs peuvent gérer les champs suivants :

* **Réviseurs**
* **Cessionnaires**
* **Étiquettes**
* **Projets**
* **Jalons**

Vous n'avez pas besoin de les remplir - les responsables de JCB s'en chargeront.

---

<a id="8-writing-the-pull-request-description"></a>
## 8. Rédaction de la description de la demande de tirage

[00:06:27](https://www.youtube.com/watch?v=vQ-yxVtc-Co&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m27s)

Utilisez vos **messages de validation** comme base pour la description de votre demande d'extraction.

1. Consultez le résumé de votre demande de tirage avant de la soumettre.
2. Cliquez sur **"Créer une pull request"** une fois que tout semble bon.

Après soumission :

* Attendez que les administrateurs examinent.
* Ils peuvent poser des questions ou demander des éclaircissements avant de fusionner.

> **Remarque :** Le processus de révision garantit un contrôle de qualité ainsi qu'une dénomination et une documentation cohérentes dans tous les extraits de communauté.

Une fois approuvée par au moins **deux évaluateurs**, votre pull request peut être fusionnée.

---

<a id="9-merging-into-the-master-branch"></a>
## 9. Fusionner dans la branche principale

[00:08:19](https://www.youtube.com/watch?v=vQ-yxVtc-Co&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m19s)

Les administrateurs disposent de plusieurs options de fusion :

* Cliquez sur **"Merge pull request"** directement sur GitHub.
* S'il y a des conflits, les administrateurs avancés peuvent les résoudre à l'aide d'**outils de ligne de commande**.

En cas de conflits, suivez le lien **"instructions de ligne de commande"** de GitHub pour savoir comment fusionner manuellement.

---

<a id="10-post-merge-visibility-in-jcb"></a>
## 10. Post-fusion : visibilité dans JCB

[00:09:12](https://www.youtube.com/watch?v=vQ-yxVtc-Co&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m12s)

Une fois fusionné :

* Les extraits nouveaux ou mis à jour deviennent visibles lorsque les utilisateurs cliquent sur **Init** dans la vue Extraits de JCB.
* Les autres utilisateurs peuvent désormais les sélectionner et les intégrer directement dans leurs projets à partir du même workflow de référentiel.

Cette intégration simplifiée maintient les extraits de communauté synchronisés via GitHub sans nécessiter de mises à jour manuelles de la base de données.

---

<a id="11-managing-your-snippets"></a>
## 11. Gérer vos extraits

[00:09:52](https://www.youtube.com/watch?v=vQ-yxVtc-Co&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m52s)

Via votre référentiel forké et JCB :

* Vous pouvez **ajouter**, **mettre à jour**, **supprimer** et **corbeille** des extraits de code.
* Les extraits supprimés n'apparaîtront plus dans votre zone Extraits JCB.

Exemple:

* Accédez à **Extraits → Accordéon → Corbeille**
* Ensuite, **supprimez-le définitivement** de la section *Corbeille*.

Cela le marquera comme **inexistant** dans votre référentiel d'extraits de code.

> **Objectif :** Rendre le partage d'extraits de code simple et collaboratif sans mises à jour complexes de la base de données.

---

<a id="12-community-collaboration"></a>
## 12. Collaboration communautaire

Lorsque vous contribuez des extraits :

* Votre **nom** est associé au changement dans l'historique Git.
* Cela vous permet de **gagner en reconnaissance** au sein de la communauté JCB.

> "Partagez vos extraits, aidez les autres et renforcez Joomla Component Builder !"

---

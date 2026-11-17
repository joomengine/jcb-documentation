> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="how-to-set-up-tabs-after-upgrade-to-jcb-v258"></a>
# Comment configurer les onglets après la mise à niveau vers JCB v2.5.8

Ce guide explique comment configurer et gérer les **onglets** dans Joomla Component Builder (JCB) après la mise à niveau vers la **version 2.5.8**.
Il reflète les dernières interfaces et flux de travail JCB, en particulier dans les sections **Admin Views** et **Admin Fields**.

---

<a id="1-understanding-the-tab-system-in-jcb"></a>
## 1. Comprendre le système d'onglets dans JCB

[00:00:00](https://www.youtube.com/watch?v=NFp_CtE0LZI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

Dans JCB v2.5.8, la façon dont les **onglets** sont configurés dans une **vue administrateur** a légèrement changé.
Les onglets aident à organiser les champs en sections logiques dans le backend de votre composant Joomla, rendant votre interface d'administration plus propre et plus conviviale.

Les onglets sont désormais définis dans la zone **Paramètres de la vue Administrateur** et liés aux champs via leur **liste déroulante de sélection d'onglets**.

---

<a id="2-adding-tabs-in-admin-view-settings"></a>
## 2. Ajout d'onglets dans les paramètres de la vue administrateur

[00:00:00](https://www.youtube.com/watch?v=NFp_CtE0LZI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

<a id="steps-to-add-tabs"></a>
### Étapes pour ajouter des onglets :

1. Ouvrez votre **Vue administrateur** dans Joomla Component Builder.
2. Faites défiler jusqu'à la section intitulée **Paramètres**.
3. Localisez la zone appelée **Onglets**.
4. Cliquez sur le bouton **Ajouter (+)** pour créer une nouvelle entrée d'onglet.
5. Nommez vos onglets de manière appropriée (par exemple, `General`, `Options`, `Advanced`, `Permissions`).
6. Après avoir saisi tous les noms d'onglets souhaités, **cliquez sur « Enregistrer »**.

> **Astuce :** Les onglets ne sont stockés dans la base de données qu'après leur enregistrement.
> Si vous oubliez de sauvegarder, vos onglets n'apparaîtront pas ultérieurement dans la liste déroulante.

Lorsque vous enregistrez, JCB stocke ces onglets et les rend disponibles sous forme d'options sélectionnables pour vos champs d'administration.

---

<a id="3-assigning-fields-to-tabs"></a>
## 3. Affectation de champs aux onglets

[00:00:52](https://www.youtube.com/watch?v=NFp_CtE0LZI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m52s)

Une fois vos onglets créés et enregistrés, ouvrez les **Champs d'administration** associés à cette vue.

1. Accédez aux **Champs d'administration** dans JCB.
2. Modifiez ou créez un champ.
3. Dans la liste déroulante **Onglet** (située sous les paramètres du champ), vous verrez maintenant tous les noms d'onglets que vous avez créés précédemment.
4. Sélectionnez sous quel onglet chaque champ doit apparaître.
5. Enregistrez le champ.

Lorsque vous compilerez et installerez ultérieurement votre composant, le formulaire backend affichera les champs regroupés sous leurs onglets respectifs.

---

<a id="4-behavior-when-no-tabs-are-defined"></a>
## 4. Comportement lorsqu'aucun onglet n'est défini

[00:01:29](https://www.youtube.com/watch?v=NFp_CtE0LZI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m29s)

Si aucun onglet n'est défini dans les **Paramètres** de la vue Admin, JCB affiche automatiquement par défaut tous les champs sous un seul onglet appelé **Détails**.

Cela signifie:

* Le formulaire n'affichera pas plusieurs onglets.
* Tous les champs apparaîtront dans la section « Détails ».

Pour avoir plusieurs onglets, vous devez les ajouter dans les **Options de configuration des onglets** comme décrit ci-dessus.

---

<a id="5-managing-tab-setup-options"></a>
## 5. Gestion des options de configuration des onglets

Si vous souhaitez ultérieurement renommer ou réorganiser vos onglets :

1. Rouvrez votre **Vue Administrateur**.
2. Faites défiler jusqu'à **Paramètres → Onglets**.
3. Modifiez les noms des onglets ou supprimez ceux dont vous n'avez pas besoin.
4. Cliquez à nouveau sur **Enregistrer** pour appliquer les modifications.

> **Remarque :** La modification des noms d'onglets vous obligera à mettre à jour les champs attribués à ces onglets afin qu'ils continuent de correspondre.

---

<a id="6-compiling-and-testing-your-component"></a>
## 6. Compiler et tester votre composant

Après avoir configuré vos onglets et attribué des champs :

1. Cliquez sur **Compile** dans JCB pour créer votre package de composants.
2. Installez le fichier `.zip` généré sur votre site Joomla.
3. Ouvrez la vue backend du composant pour confirmer que vos onglets apparaissent comme prévu.

Vous devriez maintenant voir vos champs soigneusement regroupés sous chaque onglet, exactement comme défini dans votre vue administrateur.

---

<a id="7-summary"></a>
## 7. Résumé

* Les onglets sont créés dans **Admin View → Paramètres**.
* Les champs renvoient aux onglets via leur **liste déroulante des onglets**.
* Toujours **Enregistrer** après avoir créé ou modifié des onglets.
* S'il n'existe aucun onglet, JCB utilise par défaut l'onglet **Détails**.
* Les modifications dans la configuration des onglets doivent être suivies d'une recompilation.

---

<a id="example-workflow-recap"></a>
### Exemple de récapitulatif du flux de travail

| Étape | Actions | Résultat |
| ---- | ------------------------------- | ---------------------- |
| 1 | Ajouter des onglets dans les paramètres de la vue administrateur | Onglets stockés dans DB |
| 2 | Enregistrer la vue administrateur | Les onglets deviennent sélectionnables |
| 3 | Modifier les champs d'administration | Attribuer des champs aux onglets |
| 4 | Compiler le composant | Des onglets apparaissent dans le backend |

---

> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="the-custom-dashboard-option-in-joomla-component-builder-jcb"></a>
# L'option de tableau de bord personnalisé dans Joomla Component Builder (JCB)

> **Référence du didacticiel :** [Vidéo 60 - L'option de tableau de bord personnalisé dans JCB](https://www.youtube.com/watch?v=tU7TeYn1Djo)
---

<a id="overview"></a>
## Aperçu

[00:00:00](https://www.youtube.com/watch?v=tU7TeYn1Djo&t=00h00m00s)

JCB offre désormais aux développeurs la possibilité d'**ajouter leur propre tableau de bord personnalisé** à n'importe quel composant Joomla créé avec lui.
Cette amélioration permet une **plus grande flexibilité de l'interface utilisateur** et une **expérience administrative unique**, qui ne se limite plus à la présentation du tableau de bord par défaut.

Dans les versions précédentes de JCB, tous les composants utilisaient le même tableau de bord par défaut. La mise en page et les icônes ont été générées automatiquement en fonction de la configuration de votre composant. Désormais, vous pouvez **remplacer ou reconcevoir** entièrement ce tableau de bord pour qu'il corresponde aux besoins de votre marque ou de vos fonctionnalités.

---

<a id="1-default-dashboard-behavior"></a>
## 1. Comportement du tableau de bord par défaut

Lorsque vous créez un nouveau composant dans JCB sans définir de tableau de bord personnalisé, le système en génère automatiquement un en fonction de votre :

* Vues d'administration
* Icônes
* Dispositions des champs

Il s'agit du **tableau de bord JCB par défaut** - fonctionnel, mais non personnalisable.

> **Conseil :** Si vous n'ajoutez pas votre propre tableau de bord, JCB continue de créer cette présentation par défaut pour vous.

---

<a id="2-adding-tabs-optional"></a>
## 2. Ajout d'onglets (facultatif)

[00:00:43](https://www.youtube.com/watch?v=tU7TeYn1Djo&t=00h00m43s)

Le tableau de bord par défaut de JCB prend en charge les **onglets**, qui vous permettent de structurer l'interface d'administration en sections. Les onglets sont assez puissants et vous permettent d'intégrer des listes, des statistiques ou même du contenu dynamique.
Cependant, pour de nombreux développeurs, cela ressemble encore *"trop ​​à la JCB"* et manque d'originalité.

[00:01:22](https://www.youtube.com/watch?v=tU7TeYn1Djo&t=00h01m22s)

JCB a été conçu pour aider les développeurs à **créer des composants uniques**, et non des composants à l'emporte-pièce. Si vous êtes à l'aise avec HTML, CSS et JavaScript, vous pouvez concevoir une **vue de tableau de bord d'administration entièrement personnalisée**.

> **Conseil :** Un tableau de bord personnalisé vous permet d'exprimer votre propre marque et votre propre présentation tout en conservant la même logique backend JCB.

---

<a id="3-viewing-the-dashboard-in-the-hello-world-component"></a>
## 3. Affichage du tableau de bord dans le composant Hello World

[00:02:41](https://www.youtube.com/watch?v=tU7TeYn1Djo&t=00h02m41s)

Ouvrons le célèbre **composant Hello World** dans JCB à titre d'exemple.

1. Accédez à **Composants → Hello World** dans Joomla.
2. Vous verrez la disposition du tableau de bord par défaut.
3. Nous allons maintenant supprimer ou remplacer ce tableau de bord.

---

<a id="4-accessing-the-dashboard-settings"></a>
## 4. Accéder aux paramètres du tableau de bord

[00:03:27](https://www.youtube.com/watch?v=tU7TeYn1Djo&t=00h03m27s)

À l’intérieur de JCB :

1. Accédez à votre composant.
2. Ouvrez l'onglet **"Dash & Install"** dans la configuration du composant.
3. Vous trouverez deux options clés sous **Type de tableau de bord** :

* **Par défaut** - le tableau de bord standard généré par JCB.
   * **Dynamique** - permet de sélectionner un administrateur personnalisé ou une vue de site pour servir de nouveau tableau de bord.

Lorsque vous sélectionnez **Dynamique**, JCB affiche une liste de toutes les **Vues d'administration et d'administration personnalisées** disponibles associées à votre composant.

---

<a id="5-setting-a-custom-dashboard"></a>
## 5. Définition d'un tableau de bord personnalisé

[00:03:52](https://www.youtube.com/watch?v=tU7TeYn1Djo&t=00h03m52s)

Pour changer le tableau de bord :

1. Choisissez **Dynamique** dans la liste déroulante.
2. Sélectionnez n'importe quelle vue d'administration ou d'administration personnalisée disponible (par exemple, « Compilateur » ou « Extraits »).
3. Cliquez sur **Enregistrer et fermer**.
4. Reconstruisez votre composant en ouvrant le **Compilateur** dans JCB et en cliquant sur **Compiler**.
5. Installez le composant mis à jour dans Joomla.

[00:04:17](https://www.youtube.com/watch?v=tU7TeYn1Djo&t=00h04m17s)

Après réinstallation :

* L'ancien tableau de bord disparaît.
* La vue sélectionnée (par exemple, une vue de liste) devient la **page de destination de l'administrateur par défaut**.

> **Résultat :** Votre composant Hello World s'ouvre désormais directement dans la vue choisie au lieu du tableau de bord par défaut.

---

<a id="6-using-a-custom-dashboard-example-jcb-compiler-view"></a>
## 6. Utilisation d'un tableau de bord personnalisé (exemple : vue du compilateur JCB)

[00:04:34](https://www.youtube.com/watch?v=tU7TeYn1Djo&t=00h04m34s)

Testons cette fonctionnalité en utilisant JCB lui-même.

JCB propose plusieurs **Vues d'administration personnalisées**, telles que :

* **Compilateur**
* **Extraits**
* **Champs**
* **Mise en page**

Pour en attribuer un comme tableau de bord :

1. Ouvrez la configuration des composants de JCB.
2. Dans **Dash & Install**, sélectionnez **Dynamique**.
3. Choisissez l'une des vues (par exemple, "Compilateur").
4. Cliquez sur **Enregistrer et fermer**.
5. Recompilez et réinstallez JCB.

---

<a id="testing-the-custom-dashboard"></a>
### Test du tableau de bord personnalisé

[00:05:20](https://www.youtube.com/watch?v=tU7TeYn1Djo&t=00h05m20s)

Après recompilation :

* Le tableau de bord de JCB est remplacé par la **Vue Compilateur**.
* Certains éléments du tableau de bord (comme les informations de version, les onglets et les mises à jour) ne sont plus disponibles, car les fichiers du tableau de bord ont été supprimés.

Si vous actualisez la page d'administration :

* Le nouveau **Tableau de bord du compilateur** apparaît comme écran d'accueil.
* Tous les codes et fichiers du tableau de bord précédents sont supprimés de la build.

[00:06:23](https://www.youtube.com/watch?v=tU7TeYn1Djo&t=00h06m23s)

Le changement est **propre et complet** : aucun fichier de tableau de bord résiduel ne reste dans la structure des composants.

---

<a id="7-reverting-to-the-default-dashboard"></a>
## 7. Revenir au tableau de bord par défaut

[00:07:17](https://www.youtube.com/watch?v=tU7TeYn1Djo&t=00h07m17s)

Pour restaurer le tableau de bord d'origine :

1. Rouvrez le composant dans JCB.
2. Dans **Dash & Install**, redéfinissez le type de tableau de bord sur **Par défaut**.
3. Cliquez sur **Enregistrer et fermer**.
4. Compilez et réinstallez le composant.

Une fois fait :

* Le tableau de bord JCB d'origine est restauré.
* Tous les fichiers du tableau de bord sont réajoutés automatiquement.

> **Conseil :** Le basculement entre les tableaux de bord n'endommage pas votre composant.
> Vous pouvez expérimenter en toute sécurité différentes mises en page ou restaurer les valeurs par défaut à tout moment.

---

<a id="8-why-use-a-custom-dashboard"></a>
## 8. Pourquoi utiliser un tableau de bord personnalisé ?

La création d'un tableau de bord personnalisé donne à votre composant une **identité distincte** et une meilleure **expérience utilisateur**.

Vous pouvez concevoir des tableaux de bord qui :

* Afficher **des résumés de données personnalisés**
* Intégrez **des graphiques, des diagrammes ou des statistiques**
* Fournir des **boutons d'accès rapide**
* Intégrer **HTML, JavaScript ou modules personnalisés**

> **Exemples de cas d'utilisation :**
>
> * Un composant de gestion des ventes peut afficher des statistiques de revenus ou des graphiques de ventes.
> * Un créateur de contenu peut afficher des actions rapides pour créer ou publier des éléments.

---

<a id="9-summary"></a>
## 9. Résumé

| Fonctionnalité | Descriptif |
| ------------------------------------ | --------------------------------------------------------------------- |
| **Tableau de bord par défaut** | Généré automatiquement par JCB avec une mise en page et des onglets standard.                  |
| **Tableau de bord dynamique** | Vous permet d'attribuer un administrateur personnalisé ou une vue d'administrateur personnalisée comme tableau de bord. |
| **Compiler et installer** | Obligatoire après avoir apporté des modifications pour les refléter dans Joomla.              |
| **Option de retour** | Revenez aux valeurs par défaut à tout moment sans perte de données ou de structure.     |

---

<a id="final-thoughts"></a>
### Réflexions finales

La fonctionnalité **Tableau de bord personnalisé** constitue une étape majeure vers la flexibilité de JCB.
Vous avez désormais le pouvoir de vous approprier réellement le backend de vos composants, en alliant l'automatisation de JCB à votre créativité de conception.
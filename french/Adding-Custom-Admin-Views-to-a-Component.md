> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="adding-custom-admin-views-to-a-component"></a>
# **Ajout de vues d'administration personnalisées à un composant**

---

<a id="overview"></a>
## **Aperçu**

Dans Joomla Component Builder (JCB), les *Vues d'administration personnalisées* permettent aux développeurs de créer des vues administratives dynamiques et flexibles à l'intérieur de leurs composants. Ces vues améliorent l'interface back-end en fournissant des sections de tableau de bord supplémentaires, des liens de menu et des fonctionnalités telles que des boutons personnalisés et des affichages de résultats.

Considérez-les comme l'équivalent côté administrateur des vues de site : vous utilisez les mêmes blocs de construction : **Mise en page**, **Modèles**, **Objets dynamiques**, **Blocs de code personnalisés** et **bibliothèques JavaScript/CSS facultatives**, mais vous dirigez la sortie vers les administrateurs plutôt que vers les visiteurs publics. Cela vous permet de prototyper des tableaux de bord, des utilitaires de données ou des assistants de flux de travail ponctuels sans abandonner le cycle de compilation JCB.

Dans cet exemple, nous utiliserons le composant **Cost-Benefit Projection** pour montrer comment ajouter et configurer des *Vues d'administration personnalisées* dans JCB.

<a id="before-you-start-assemble-the-ingredients"></a>
### **Avant de commencer : assemblez les ingrédients**

1. **Planifiez les sources de données.** Décidez quelles vues d'administration ou tables de base de données alimenteront votre vue d'administration personnalisée et modéliseront les relations via des acquisitions dynamiques.
2. **Esquissez l'interface.** Déterminez si vous avez besoin d'un comportement d'élément, de liste ou hybride et décrivez les onglets, les filtres et les actions de la barre d'outils qui prennent en charge le flux de travail.
3. **Préparez les ressources réutilisables.** Identifiez les mises en page partagées, les méthodes d'assistance, JavaScript ou CSS auxquelles la vue doit faire référence afin d'éviter de dupliquer la logique dans la zone d'administration.

Faire ces devoirs permet de garder votre implémentation concentrée et d'éviter les réécritures de dernière minute lorsque vous commencez à câbler des boutons, des requêtes et des modèles ensemble.

---

<a id="1-accessing-the-custom-admin-views-section"></a>
## **1. Accès à la section des vues d'administration personnalisées**

1. Ouvrez **Component Builder** dans votre panneau d'administrateur Joomla.
2. Accédez à **Paramètres → Vues d'administration personnalisées**.
3. Cliquez sur **Nouveau** pour créer une nouvelle vue d'administration personnalisée.

Vous remarquerez qu'une *Vue d'administration personnalisée* a plus d'options de configuration qu'une *Vue du site*. En effet, le côté administrateur est conçu pour être plus dynamique et intégré à l'interface d'administration de Joomla.

---

<a id="2-understanding-the-custom-admin-view-options"></a>
## **2. Comprendre les options d'affichage d'administration personnalisé**

<a id="icons-and-menu-placement"></a>
### **Icônes et placement des menus**

Chaque vue d'administration personnalisée peut être associée à une **icône de menu** et peut apparaître dans un ou plusieurs des emplacements suivants :

* **Menu principal** - Le menu principal visible sur le tableau de bord des composants Joomla.
* **Tableau de bord (Liste des enregistrements)** - La zone centrale affichant les données clés ou les liens rapides.
* **Sous-menu** - La barre latérale verticale visible lors de la navigation dans les vues des composants.

Ces paramètres contrôlent la façon dont votre vue apparaîtra et comment les utilisateurs y accéderont depuis le backend.

> **Conseil :**
> Utilisez des icônes distinctes pour chaque vue d'administration personnalisée pour rendre la navigation intuitive. JCB prend en charge les classes d'icônes standard de Joomla.

---

<a id="3-targeting-specific-items-and-views"></a>
## **3. Ciblage d'éléments et de vues spécifiques**

Les vues d'administration personnalisées peuvent cibler d'autres vues ou éléments à l'intérieur de votre composant. Cela vous permet de créer des boutons contextuels ou des résumés de données directement liés aux éléments associés.

1. Dans votre nouvelle vue d'administration personnalisée, recherchez la liste déroulante **Vue cible**.
2. Sélectionnez la cible appropriée (par exemple, `Company`).
3. Définissez **Possède des métadonnées** et **Ajouter un accès** sur `Yes` si nécessaire.

Cela garantit que la vue d'administration personnalisée interagit correctement avec la vue ciblée et dispose des autorisations d'accès appropriées.

> **Exemple :**
> Si votre vue `Company Results` doit afficher des données relatives à des sociétés spécifiques, définissez la vue cible sur `Company`.

---

<a id="4-linking-the-custom-admin-view-inside-the-component"></a>
## **4. Lier la vue d'administration personnalisée à l'intérieur du composant**

Après la configuration, ouvrez le **Tableau de bord** ou la **Vue cible** de votre composant (par exemple, *Entreprises*) et vérifiez le nouveau bouton ou la nouvelle icône qui apparaît.

Lorsqu'il est correctement configuré :

* Le bouton **Résultats de l'entreprise** apparaîtra dans la barre d'outils ou le tableau de bord.
* En cliquant dessus, vous ouvrirez la *Vue d'administration personnalisée* (par exemple, des graphiques ou des résultats combinés).
* Le `item_id` sélectionné dans la vue `Company` est transmis dynamiquement à la nouvelle vue.

Cette liaison dynamique est gérée automatiquement par JCB une fois que les paramètres de cible et de placement sont correctement configurés.

---

<a id="5-using-order-before-options"></a>
## **5. Utilisation des options « Commander avant »**

Les champs **Commander avant** sont utilisés lorsque votre vue d'administration personnalisée est ajoutée à un **Menu principal** ou un **Sous-menu**.

Ces champs définissent où votre nouvel élément de menu doit apparaître par rapport aux éléments existants.
Par exemple:

* Si vous sélectionnez *Tableau de bord (liste des enregistrements)* comme « Commander avant », votre nouvelle vue apparaîtra directement avant le lien du tableau de bord dans le menu d'administration.

Cette étape garantit que votre interface d’administration reste logiquement organisée.

---

<a id="6-implementing-custom-buttons"></a>
## **6. Implémentation de boutons personnalisés**

Les vues d'administration personnalisées incluent souvent des **boutons personnalisés** qui déclenchent des actions spécifiques ou permettent d'accéder à d'autres vues.

1. Accédez à votre vue d'administration personnalisée (par exemple, *Résultats de l'entreprise*).
2. Faites défiler jusqu'à la section **Boutons personnalisés**.
3. Définissez la logique PHP pour chaque bouton selon vos besoins (par exemple : `editCompany`, `gotoCompany`).

Ces boutons interagissent avec la logique du contrôleur du composant. Vous pouvez définir si chaque bouton cible un *élément unique* ou fonctionne au *niveau de liste*.

> **Note technique :**
> JCB génère le code PHP de ces boutons dans votre composant. Vous pouvez inspecter le code généré après la compilation pour comprendre ou ajuster davantage le comportement.

---

<a id="7-the-combined-results-example"></a>
## **7. L'exemple des « Résultats combinés »**

Dans l'exemple de *Projection coûts-avantages* :

* Le bouton **Résultats combinés** a été ajouté à la barre d'outils.
* Il affiche les résultats en combinant les données de plusieurs éléments sélectionnés.
* L'icône associée (par exemple, une icône d'engrenage ou de graphique) aide les utilisateurs à identifier rapidement sa fonction.

Dans la vue **Résultats combinés**, des boutons supplémentaires tels que *Tableau de bord* et *Entreprises* ont été ajoutés.
Celles-ci correspondent aux actions disponibles *dans* cette vue spécifique.

> **N'oubliez pas :**
> Les boutons définis **avant l'ouverture de la vue** apparaissent dans la barre d'outils.
> Les boutons définis **à l'intérieur de la vue** apparaissent une fois la vue ouverte.

---

<a id="8-linking-data-using-dynamic-get-and-selected-ids"></a>
## **8. Lier les données à l'aide de Dynamic GET et des ID sélectionnés**

Lorsque plusieurs enregistrements sont sélectionnés dans une vue de liste, leurs ID (`cid`) peuvent être transmis dynamiquement à votre vue d'administration personnalisée.
Cela permet le filtrage ou l’agrégation des données en fonction de la sélection de l’utilisateur.

Pour y parvenir :

1. Dans la section **Dynamic GET (Data Query)** de votre vue d'administration personnalisée, accédez aux ID sélectionnés à l'aide de PHP :

   ```php
   $input = JFactory::getApplication()->input;
   $ids = $input->get('cid', array(), 'array');
   ```2. Vérifiez que l'utilisateur est autorisé à accéder à ces données.
3. Utilisez `$ids` dans votre requête SQL ou votre modèle de données pour récupérer l'ensemble de données approprié.

Dans JCB, cela est généralement implémenté dans la méthode **getListQuery()** du modèle.
Vous pouvez le modifier ou l'étendre via le générateur Dynamic GET pour l'adapter à la logique de votre composant.

---

<a id="9-testing-and-troubleshooting"></a>
## **9. Tests et dépannage**

Si votre vue ou vos boutons n'apparaissent pas comme prévu :

* Rouvrez la vue d'administration personnalisée et vérifiez les options de placement.
* Assurez-vous que la **Vue cible** est correctement définie.
* Recompilez le composant et installez la version mise à jour.
* Inspectez le code PHP généré pour vérifier que votre logique a été incluse.

L'expérimentation fait partie du processus d'apprentissage. Ajustez les emplacements et les paramètres, recompilez et observez le comportement dans Joomla jusqu'à ce que tout fonctionne comme prévu.

---

<a id="10-menu-structure-and-placement-summary"></a>
## **10. Structure du menu et résumé des emplacements**

Une fois compilé :

* Les éléments du menu principal **apparaissent en haut de l'interface d'administration de votre composant.
* Les éléments du sous-menu apparaissent sur le côté gauche lors de la visualisation d'une section spécifique.
* **Les éléments du tableau de bord (liste des enregistrements)** servent de boutons d'accès rapide ou de rapports sur la page principale du composant.

Utilisez-les de manière stratégique pour créer une présentation backend propre et conviviale pour votre composant.

---

<a id="conclusion"></a>
## **Conclusion**

L'ajout de vues d'administration personnalisées dans Joomla Component Builder permet aux développeurs de concevoir des interfaces d'administration riches et interactives. En définissant correctement l'emplacement des menus, les vues cibles et la gestion dynamique des données, vous pouvez créer des tableaux de bord et des outils de gestion back-end professionnels sans écrire manuellement tout le code passe-partout. Et comme les vues d'administration personnalisées prennent en charge le même workflow **Init → Reset → Push → Fork** utilisé dans tout le référentiel, vous pouvez parcourir ces interfaces en toute confiance tout en gardant vos mises en page sur mesure sous contrôle source.

---

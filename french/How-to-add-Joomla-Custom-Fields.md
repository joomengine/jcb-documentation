> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="how-to-add-joomla-custom-fields-in-joomla-component-builder-jcb"></a>
# Comment ajouter des champs personnalisés Joomla dans Joomla Component Builder (JCB)

**Référence du didacticiel vidéo :** [YouTube - Comment ajouter des champs personnalisés Joomla](https://www.youtube.com/watch?v=n5RBmP0uNCM)
*(Les horodatages tout au long de ce guide correspondent à la vidéo ci-dessus.)*

---

<a id="overview"></a>
## Aperçu

[00:00:00](https://www.youtube.com/watch?v=n5RBmP0uNCM&t=00h00m00s)

Les champs personnalisés Joomla vous permettent d'ajouter des options de saisie de données supplémentaires aux entités Joomla telles que les **articles**, les **utilisateurs** ou les **composants personnalisés**. Chaque champ personnalisé peut être regroupé en **Groupes de champs**, donnant une organisation structurée aux formulaires de saisie de données dans Joomla.

Avec des mises à jour récentes, **Joomla Component Builder (JCB)** prend désormais en charge de manière native **Joomla Custom Field Integration**, permettant aux développeurs d'inclure ces champs directement dans leurs composants générés.

---

<a id="1-understanding-joomla-custom-fields-and-groups"></a>
## 1. Comprendre les champs et groupes personnalisés Joomla

Avant de plonger dans l'intégration de JCB, il est important de comprendre le système de champs personnalisés de Joomla :

* **Les champs** sont des options de saisie personnalisées (par exemple, texte, liste, image) attachées au contenu.
* **Les groupes de champs** organisent les champs en ensembles logiques.
* Dans le noyau Joomla, ceux-ci se trouvent sous :

* **Contenu → Champs**
  * **Contenu → Groupes de champs**

Vous pouvez désormais créer des champs similaires directement dans votre **composant généré par JCB**, avec des fonctionnalités back-end et front-end complètes.

---

<a id="2-linking-joomla-fields-to-an-admin-view"></a>
## 2. Lier les champs Joomla à une vue administrateur

[00:00:52](https://www.youtube.com/watch?v=n5RBmP0uNCM&t=00h00m52s)

Pour rendre les champs personnalisés Joomla disponibles dans un composant JCB :

1. **Ouvrez votre composant** dans JCB.
2. Accédez à **Vues administrateur**.
3. Sélectionnez ou créez une vue administrateur (par exemple, `Look`).
4. Cliquez sur **Modifier** pour ouvrir ses paramètres.
5. Faites défiler pour trouver la nouvelle bascule **"Joomla Fields"**.
6. Activez cette option.

> **Remarque :** Cela ajoute l'intégration du champ personnalisé Joomla à la vue administrateur.
> Plusieurs vues d'administration peuvent prendre en charge cette intégration si nécessaire.

Cela garantit que les champs personnalisés seront disponibles pour la saisie de données dans le formulaire principal de cette vue.

---

<a id="3-compile-and-install-the-component"></a>
## 3. Compilez et installez le composant

[00:02:05](https://www.youtube.com/watch?v=n5RBmP0uNCM&t=00h02m05s)

Après avoir activé les champs Joomla :

1. **Compilez** votre composant.
2. **Installez** le sur votre site Joomla en utilisant le processus d'installation du compilateur JCB.

Une fois installé, accédez à votre composant dans le back-end Joomla.
Par exemple:

```
Components → Demo → Looks
```

Vous verrez maintenant deux nouveaux éléments de menu :

* **Regarde les champs**
* **Regarde les groupes de champs**

---

<a id="4-creating-fields-and-field-groups"></a>
## 4. Création de champs et de groupes de champs

[00:02:34](https://www.youtube.com/watch?v=n5RBmP0uNCM&t=00h02m34s)

1. Ouvrez **Groupes de champs Looks**.
2. Cliquez sur **Nouveau** → Entrez un **Titre**, par exemple `Really Easy` → Enregistrer et fermer.
3. Accédez à **Champs Looks** → Cliquez sur **Nouveau**.
4. Choisissez un **Type** (par exemple, `Text`).
5. Attribuez-le à votre groupe `Really Easy`.
6. Enregistrez et fermez.

Désormais, lors de la création d'un nouvel enregistrement **Look**, un **nouvel onglet** nommé `Really Easy` apparaîtra avec votre champ personnalisé visible pour la saisie.

Tu peux:

* Ajoutez plusieurs champs en les attribuant au même groupe.
* Ajoutez des groupes supplémentaires pour organiser les champs.

> **Exemple :**
>
> * Groupe de terrain : `Really Easy`
> * Champs : `Simple Field`, `More Fields`

---

<a id="5-adding-field-display-events-to-the-front-end"></a>
## 5. Ajout d'événements d'affichage de champ au front-end

[00:04:42](https://www.youtube.com/watch?v=n5RBmP0uNCM&t=00h04m42s)

Par défaut, les champs fonctionnent immédiatement dans le **back-end**, mais pour les afficher dans le **front-end**, vous devez utiliser les **événements du plug-in de contenu Joomla**.

JCB les fournit via **Dynamic Get Builder**.

<a id="steps"></a>
### Étapes :

1. Dans JCB, accédez à **GETS dynamiques**.
2. Sélectionnez **Obtenir l'élément** pour votre vue frontale (par exemple, `Looking`).
3. Sous **Événements de plug-in de contenu**, sélectionnez :

* `onContentAfterTitle`
   * `onContentBeforeDisplay`
   * `onContentAfterDisplay`
4. Enregistrez et fermez.

Ces événements contrôlent quand et comment les champs Joomla sont affichés.

---

<a id="6-compiling-to-inject-event-code"></a>
## 6. Compilation pour injecter le code d'événement

[00:07:30](https://www.youtube.com/watch?v=n5RBmP0uNCM&t=00h07m30s)

Après avoir activé les événements :

1. **Recompilez** le composant dans JCB.
2. **Inspectez** le code généré :

   ```
   components/com_demo/views/looking/view.html.php
   ```3. La fonction d'affichage comprend désormais :

* Chargement du répartiteur d'événements
   * Déclencheurs du plugin de contenu :

     * `onContentAfterTitle`
     * `onContentBeforeDisplay`
     * `onContentAfterDisplay`

Ces appels demandent à Joomla de récupérer et d'afficher tous les champs personnalisés attribués.

---

<a id="7-adjusting-the-context"></a>
## 7. Ajuster le contexte

[00:09:51](https://www.youtube.com/watch?v=n5RBmP0uNCM&t=00h09m51s)

Si le nom de votre vue administrateur diffère de votre vue de site (par exemple, `Look` vs `Looking`), vous devez ajuster le **Contexte**.

1. Accédez à **Vues du site**.
2. Ouvrez votre **vue frontale** (par exemple, `Looking`).
3. Localisez le nouveau champ **Contexte**.
4. Définissez le contexte pour qu'il corresponde à la vue administrateur (`Look`).
5. Enregistrez et fermez.
6. Recompilez.

Cela garantit que les données de champ liées à `com_demo.look` s'affichent correctement dans le frontal.

> **Conseil :**
> Les champs Joomla reposent sur des identifiants de contexte correspondants.
> Un mauvais alignement (par exemple, `look` vs `looking`) empêchera l'affichage des données de champ.

---

<a id="8-displaying-fields-in-your-template"></a>
## 8. Afficher les champs dans votre modèle

[00:16:42](https://www.youtube.com/watch?v=n5RBmP0uNCM&t=00h16m42s)

Pour afficher les valeurs des champs dans votre modèle :

1. Ouvrez le **fichier de modèle de vue de site** de votre composant :

   ```
   components/com_demo/views/looking/tmpl/default.php
   ```2. Utilisez des espaces réservés pour les événements, le cas échéant :

   ```php
   <?php echo $this->item->event->afterDisplayTitle; ?>
   <?php echo $this->item->event->beforeDisplayContent; ?>
   <?php echo $this->item->event->afterDisplayContent; ?>
   ```3. Ajustez le placement en fonction de l'endroit où vous souhaitez que les champs apparaissent (avant le titre, après le contenu, etc.).
4. Enregistrez, recompilez et testez sur le front-end.

---

<a id="9-testing-and-troubleshooting"></a>
## 9. Tests et dépannage

[00:20:08](https://www.youtube.com/watch?v=n5RBmP0uNCM&t=00h20m08s)

* Si les champs ne s'affichent pas :

* Confirmez les correspondances **Contexte**.
  * Assurez-vous que les **variables d'événement** correctes sont utilisées.
  * Vérifiez que les **événements GET dynamiques** sont sélectionnés et compilés.
* Vous pouvez repositionner la sortie du champ en modifiant le paramètre **Affichage automatique** :

* Avant l'affichage
  * Après le titre
  * Après affichage
  * Ne pas afficher automatiquement

> **Exemple d'ajustement :**
>
> * Déplacer "Simple Field" pour l'afficher après le contenu :
>
> * Ouvrez le champ dans Joomla → réglez "Affichage automatique" sur "Après affichage".

---

<a id="10-optional-hide-field-labels"></a>
## 10. Facultatif : Masquer les étiquettes des champs

[00:22:20](https://www.youtube.com/watch?v=n5RBmP0uNCM&t=00h22m20s)

Pour masquer une étiquette de champ dans l'affichage frontal :

1. Modifiez le champ dans Joomla.
2. Définissez **"Afficher l'étiquette" → "Masquer"**.
3. Enregistrez et actualisez.

Seule la valeur du champ apparaîtra sur la page.

---

<a id="11-final-notes"></a>
## 11. Notes finales

Cette intégration offre une prise en charge transparente des champs personnalisés Joomla dans les composants générés par JCB.
Vous pouvez désormais :

* Créez et gérez des **Groupes de champs** et des **Champs**.
* Utilisez **Dynamic GET Events** pour déclencher le rendu des champs.
* Contrôler le placement et la visibilité du champ.
* Étendez les fonctionnalités grâce aux **plugins de contenu** et au **code personnalisé**.

> **Astuce :** Cette configuration imite le comportement des champs d'articles natifs de Joomla, garantissant que vos composants JCB s'intègrent naturellement dans l'écosystème Joomla.

---

<a id="summary-workflow"></a>
### Flux de travail récapitulatif

| Étape | Actions | Zone |
| ---- | ---------------------------------- | ---------------- |
| 1 | Activer les champs Joomla dans la vue administrateur | Vue administrateur JCB |
| 2 | Compiler et installer | Compilateur JCB |
| 3 | Créer des groupes de champs et des champs | Back-end Joomla |
| 4 | Activer les événements du plug-in de contenu | JCB Dynamique GET |
| 5 | Ajuster le contexte | Vue du site JCB |
| 6 | Recompiler le composant | Compilateur JCB |
| 7 | Modifier le modèle pour afficher les champs | Modèle de site |
| 8 | Tester et ajuster l'affichage | Front-End Joomla |

---

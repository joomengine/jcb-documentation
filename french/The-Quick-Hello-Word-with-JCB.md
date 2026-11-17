> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="the-quick-hello-world-with-joomla-component-builder-jcb"></a>
# Le Quick Hello World avec Joomla Component Builder (JCB)

<a id="overview"></a>
## Aperçu

Ce didacticiel rapide montre comment **installer**, **importer**, **compiler** et **publier** un simple composant *Hello World* à l'aide de Joomla Component Builder (JCB).
Il s'agit d'une version simplifiée du didacticiel complet, vous guidant tout au long de la configuration et de l'exécution en quelques minutes seulement.

---

<a id="1-installing-jcb"></a>
## 1. Installation de JCB

**[00:00:00](https://www.youtube.com/watch?v=MEKs1c7LfO8&t=00h00m00s)**

Avant de créer un composant Joomla, assurez-vous que JCB est installé.

1. Dans votre administrateur Joomla, accédez à :
   **Extensions → Installer**
2. Recherchez **JCB (Joomla Component Builder)**.
3. Sélectionnez **Installer** pour démarrer l'installation.
   Lorsque vous y êtes invité, confirmez toutes les installations de dépendances.

**Conseil :**
Si JCB est déjà installé, vous pouvez le mettre à jour à partir du même menu pour vous assurer que vous disposez de la dernière version.

---

<a id="2-importing-the-hello-world-package"></a>
## 2. Importation du package Hello World

**[00:00:37](https://www.youtube.com/watch?v=MEKs1c7LfO8&t=00h00m37s)**

Une fois JCB installé, importez le plan prédéfini « Hello World » via le moteur de packaging.

1. Ouvrez **Components → Component Builder → Repositories** et enregistrez le
   Entrée `joomengine/repoindex` (organisation `joomengine`, référentiel `repoindex`, contenu cible
   `repositories`).
2. Cliquez sur **Init** dans la liste Repositories et initialisez le catalogue. Cela ajoute la démo
   référentiels à votre installation.
3. Accédez à **Composants → Générateur de composants → Composants**.
4. Appuyez sur **Init** dans la barre d'outils et sélectionnez le plan **Hello World for Joomla 5**.
5. Consultez le fichier README du référentiel et confirmez l'importation. JCB résout toutes les dépendances
   automatiquement.

Une fois le processus terminé, le composant apparaît dans votre liste de composants, prêt à être compilé.

---

<a id="3-compiling-the-hello-world-component"></a>
## 3. Compilation du composant Hello World

**[00:01:35](https://www.youtube.com/watch?v=MEKs1c7LfO8&t=00h01m35s)**

Maintenant que le package est importé, il est prêt à être compilé dans un composant Joomla.

1. Accédez à :
   **Composants → Générateur de composants → Compilateur**

2. Sélectionnez **Hello World** dans la liste.

3. Cliquez sur **Compiler**.
   Une fois le processus terminé, vous devriez voir un message de réussite.

4. Après la compilation, cliquez sur **Installer** pour l'installer directement dans Joomla.

---

<a id="4-testing-the-component-in-the-backend"></a>
## 4. Test du composant dans le backend

**[00:02:02](https://www.youtube.com/watch?v=MEKs1c7LfO8&t=00h02m02s)**

Après l'installation :

1. Accédez à :
   **Composants → Bonjour tout le monde**
2. Créez un nouvel enregistrement de message d'accueil en cliquant sur **Nouveau**.
3. Dans le champ de message d'accueil, saisissez :

   ```
   Hi James
   ```4. Cliquez sur **Enregistrer et fermer**.

Cela crée votre première entrée "Hello World" dans le backend Joomla.

---

<a id="5-displaying-the-greeting-on-the-frontend"></a>
## 5. Afficher le message d'accueil sur le frontend

**[00:02:37](https://www.youtube.com/watch?v=MEKs1c7LfO8&t=00h02m37s)**

Pour afficher votre message d'accueil :

1. Accédez à :
   **Menus → Menu principal → Ajouter un nouvel élément de menu**
2. Pour **Type d'élément de menu**, sélectionnez :
   **Bonjour tout le monde → Salutations**
3. Enregistrez et fermez l'élément de menu.

Visitez l’interface de votre site Web.
Si vous rencontrez une erreur « La page ne redirige pas correctement », cela est probablement dû aux **paramètres d'autorisation**.

---

<a id="6-adjusting-frontend-permissions"></a>
## 6. Ajuster les autorisations du frontend

**[00:03:02](https://www.youtube.com/watch?v=MEKs1c7LfO8&t=00h03m02s)**

Pour rendre le message d'accueil accessible au public :

1. Revenez au panneau Administrateur Joomla.
2. Accédez à :
   **Composants → Hello World → Options → Autorisations**
3. Dans la section **Site**, recherchez :

* **Salut**
   * **Autorisé**

Définissez-les sur **Public → Autorisé**.
Cliquez sur **Enregistrer et fermer**.

Actualisez maintenant votre page d'interface - votre message d'accueil ("Salut James") apparaîtra.
Cliquez dessus pour ouvrir et afficher le message de bienvenue.

---

<a id="7-configuring-edit-permissions-optional"></a>
## 7. Configuration des autorisations de modification (facultatif)

**[00:03:29](https://www.youtube.com/watch?v=MEKs1c7LfO8&t=00h03m29s)**

Si vous essayez de modifier un message d'accueil depuis le frontend et voyez *"Non autorisé à modifier"*, mettez à jour les autorisations :

1. Revenez à **Options → Autorisations** dans le composant Hello World.
2. Sous **Modifier**, définissez **Public → Autorisé** si vous le souhaitez (à des fins de test uniquement).
   En production, il est recommandé de limiter cette opération aux utilisateurs connectés.

---

<a id="8-verifying-functionality"></a>
## 8. Vérification de la fonctionnalité

À ce stade, votre composant Hello World est pleinement opérationnel :

* Les fonctions backend CRUD (Créer, Lire, Mettre à jour, Supprimer) fonctionnent.
* L'affichage frontal est actif.
* Les autorisations sont correctement configurées.

Vous avez installé, compilé et testé avec succès un composant Joomla à l'aide de JCB, le tout en quelques minutes.

---

<a id="key-takeaways"></a>
## Points clés à retenir

* **Les packages JCB** simplifient l'importation de composants préconfigurés.
* **La validation de la somme de contrôle** garantit l'authenticité du package.
* **Compilateur** automatise la génération et l'installation des composants Joomla.
* **Les autorisations** doivent être configurées pour l'accès frontal.

---

<a id="next-steps"></a>
## Prochaines étapes

À partir de là, vous pouvez commencer à personnaliser votre composant Hello World :

* Ajoutez plus de champs à la vue Message d'accueil (par exemple, *auteur*, *date*, *type de message*).
* Utilisez **Dynamic GET Builder** pour connecter d'autres composants ou filtrer les messages d'accueil de manière dynamique.
* Expérimentez avec les **vues administrateur et site** pour contrôler la mise en page et le flux de données.

---

**Conclusion :**
Le « Quick Hello World » est une première étape essentielle pour comprendre le flux de travail de JCB – de l'importation d'un package à son déploiement en direct.
Une fois ces étapes maîtrisées, vous êtes prêt à créer et personnaliser vos propres composants Joomla en toute confiance.

---

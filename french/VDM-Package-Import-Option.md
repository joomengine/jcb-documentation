> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="repository-index--demo-packages"></a>
# Index du référentiel et packages de démonstration

JCB ne télécharge plus les archives ZIP depuis l'onglet « Packages VDM ». Au lieu de cela, vous pouvez initialiser un
index du référentiel qui répertorie les composants de démonstration officiels et les bibliothèques d'assistance. Cette page explique comment
introduisez le catalogue dans votre installation, explorez la documentation incluse et importez le
les plans dont vous avez besoin.

---

<a id="1-load-the-repository-index"></a>
## 1. Charger l'index du référentiel

1. Accédez à **Composants → Générateur de composants → Dépôts**.
2. Cliquez sur **Nouveau** et créez une entrée pour l'index :
   * **Organisation :** `joomengine`
   * **Dépôt :** `repoindex`
   * **Lire la branche :** `master`
   * **Type :** `GitHub`
   * **Contenu cible :** `repositories`
   * **Accès :** `global`
3. Enregistrez l'enregistrement et revenez à la vue liste.
4. Appuyez sur **Init**, sélectionnez l'entrée d'index du dépôt et choisissez **Initialiser les référentiels sélectionnés**.

JCB clone l'index, crée des enregistrements locaux pour chaque référentiel répertorié et affiche leur README
fichiers directement dans l’interface. Vous avez désormais un accès instantané au catalogue de démonstration.

---

<a id="2-explore-the-included-demo-components"></a>
## 2. Explorez les composants de démonstration inclus

Après l'initialisation, vous verrez les référentiels pour :

* **Composant de démonstration Joomla 4**
* **Composant de démonstration Joomla 5**
* **Bonjour tout le monde pour Joomla 5**
* **Gestionnaire de recettes pour Joomla 5**
* **Portail E-Santé pour Joomla 5**

Chaque entrée comprend une documentation qui met en évidence les modèles utilisés dans le composant, tels que
relations multi-vues, types de champs personnalisés ou exemples de routage avancé.

---

<a id="3-import-a-demo-using-init"></a>
## 3. Importer une démo à l'aide d'Init

1. Ouvrez le type d'entité qui correspond au référentiel (par exemple **Composants** pour le composant de démonstration).
2. Sélectionnez **Init** dans la barre d'outils.
3. Choisissez l'entrée du référentiel que vous souhaitez importer et confirmez.
4. Consultez le fichier README pour comprendre les prérequis ou les dépendances facultatives.

JCB importe le plan, résout tous les types de champs, extraits ou superpuissances liés, et rend le
composant disponible dans votre installation. Compilez-le comme d'habitude pour générer un ZIP d'extension Joomla pour
tests locaux.

---

<a id="4-reset-to-pull-updates"></a>
## 4. Réinitialiser pour extraire les mises à jour

Lorsque le référentiel amont reçoit des améliorations :

1. Assurez-vous que seuls les référentiels auxquels vous faites confiance sont **publiés** pour le contenu cible pertinent.
2. Ouvrez l'entité et appuyez sur **Réinitialiser**.
3. JCB extrait le dernier commit et met à jour le plan, en gardant votre copie locale synchronisée.

Si plusieurs référentiels fournissent la même entité, faites-les glisser dans l'ordre souhaité ou temporairement
dépublier les alternatives avant de réinitialiser.

---

<a id="5-use-the-readme-as-documentation"></a>
## 5. Utilisez le README comme documentation

Le moteur d'empaquetage fait également office de visualiseur de documentation. Chaque fichier README du référentiel peut inclure :

* Présentation du composant ou de la bibliothèque
* Notes d'installation et de configuration
* Liens vers des didacticiels, des problèmes ou des exemples de données
* Directives de contribution

Lisez la documentation avant d'importer afin de comprendre comment le plan s'intègre dans votre projet.

---

<a id="6-next-steps"></a>
## 6. Prochaines étapes

* Importez des référentiels supplémentaires du catalogue (types de champs, extraits de code, pouvoirs) selon vos besoins.
* Forkez les référentiels pour personnaliser les démos ou proposer des améliorations.
* Contribuez à de nouveaux plans en suivant les
  [flux de publication de packages](./Add-your-own-JCB-packages-to-the-JCB-Communty-Directory.md).

L'index du référentiel maintient votre installation JCB approvisionnée en projets de démonstration maintenus qui reflètent
les dernières bonnes pratiques.
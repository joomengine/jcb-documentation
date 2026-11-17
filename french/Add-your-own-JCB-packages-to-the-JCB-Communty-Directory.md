> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="publish-your-jcb-packages-to-the-community-catalogue"></a>
# Publiez vos packages JCB dans le catalogue communautaire

Le moteur de packaging JCB moderne traite chaque plan comme un référentiel Git. Partager votre travail maintenant
signifie publier les entités (composants, types de champs, extraits de code, etc.) dans un référentiel et ouvrir un
pull request afin que le catalogue de la communauté puisse le répertorier. Ce guide vous explique comment préparer votre colis,
documentez-le et soumettez-le pour inclusion.

> 💡 **Rappel de terminologie :** Un *package JCB* est un plan stocké dans Git. Un *package Joomla* est le
> ZIP compilé que vous installez sur un site Joomla. Les instructions ci-dessous se concentrent sur les plans.

---

<a id="1-decide-what-youre-publishing"></a>
## 1. Décidez de ce que vous publiez

JCB regroupe les référentiels par **contenu cible**. Avant de créer un référentiel, décidez quelle entité vous
envie de partager :

| Contenu cible | Utilisation typique |
| --- | --- |
| `packages` | Plans de composants complets (vues, champs, mises en page, scripts) |
| `field_types` | Bibliothèques de types de champs réutilisables |
| `snippets` | Extraits HTML/CSS/JS pour les mises en page et les formulaires |
| `super_powers` et `joomla_powers` | Classes d'assistance et intégrations |
| `repositories` | Entrées du méta-catalogue (utilisées par les responsables) |

Des référentiels séparés permettent de gérer les dépendances. Si votre composant s'appuie sur des types de champs personnalisés,
publiez les types de champs dans leur propre référentiel et répertoriez-les en tant que dépendances dans votre fichier Lisez-moi.

---

<a id="2-fork-or-create-a-repository"></a>
## 2. Fork ou créer un référentiel

1. Si vous souhaitez contribuer au catalogue officiel, **fork** le référentiel JoomEngine concerné
   (par exemple `joomengine/packages`).
2. Pour les travaux spécifiques à l'organisation, créez un référentiel sous votre propre compte ou espace de noms d'entreprise.
3. Clonez le référentiel localement et ajoutez un README qui explique ce que fournit le plan, comment
   initialisez-le, ainsi que toutes les étapes de configuration.

JCB affiche le README dans l'interface, alors écrivez-le pour les utilisateurs finaux.

---

<a id="3-register-the-repository-in-jcb"></a>
## 3. Enregistrez le référentiel dans JCB

1. Accédez à **Composants → Générateur de composants → Dépôts**.
2. Cliquez sur **Nouveau** et remplissez :
   * **Organisation** et **Référentiel** (correspondant à la télécommande Git).
   * **Tapez** (GitHub, Gitea, etc.).
   * **Contenu cible** correspondant au tableau ci-dessus.
   * **Lire la branche** (par exemple `main` ou `master`).
   * **Écrivez une branche** si vous envisagez d'effectuer un push à partir de cette instance JCB.
   * **Accès** (`global`, `protected` ou `private`).
3. Enregistrez et appuyez sur **Init** pour lier le référentiel. JCB affichera le README et disponible
   des plans.

Si le référentiel est privé, ajoutez un jeton GitHub sous **Remplacer les paramètres globaux** ou configurez le
jeton à l’échelle du site dans les options de JCB.

---

<a id="4-prepare-the-blueprint-locally"></a>
## 4. Préparez le plan localement

Concevez ou mettez à jour votre entité dans JCB comme d'habitude. Lorsque vous êtes prêt à publier :

1. Assurez-vous que l'entité est liée au référentiel correct (utilisez **Init** si nécessaire).
2. Cliquez sur **Pousser**. JCB sérialise l'entité et la valide dans la branche du référentiel.
3. Examinez les modifications localement (`git status`, `git diff`) et validez avec un message clair.
4. Poussez le commit sur votre fork distant.

> 🔁 **Conseil :** Exécutez toujours **Réinitialiser** après que les collaborateurs ont fusionné les modifications afin que votre copie locale reste synchronisée
> avec l'historique du dépôt.

---

<a id="5-document-dependencies-and-usage"></a>
## 5. Dépendances et utilisation des documents

Étant donné que les référentiels servent également de documentation, incluez les éléments suivants dans votre README :

* Aperçu de ce que contient le package et quand l'utiliser.
* Dépendances sur d'autres référentiels (lien vers leurs entrées de catalogue).
* Étapes de configuration, exemples de données ou conseils de configuration.
* Notes de versionnage ou de migration pour les nouvelles versions.

Les packages bien documentés ont plus de chances d'être acceptés dans le catalogue communautaire.

---

<a id="6-submit-to-the-community-directory"></a>
## 6. Soumettre à l'annuaire de la communauté

Pour lister votre package aux côtés des démos officielles :

1. Ouvrez une pull request sur le référentiel en amont (par exemple `joomengine/packages`).
2. Décrivez ce que fournit le plan, comment il a été testé et les conditions préalables éventuelles.
3. Si nécessaire, ajoutez les métadonnées de votre référentiel au [`repoindex`](https://github.com/joomengine/repoindex)
   afin que d'autres utilisateurs puissent le découvrir via le workflow Init.
4. Surveillez les commentaires des responsables et mettez à jour votre PR si demandé.

Une fois fusionné, le catalogue répertoriera automatiquement votre package et les autres installations JCB verront
après avoir actualisé l'index du référentiel.

---

<a id="7-maintain-your-package"></a>
## 7. Entretenez votre colis

* Gardez le README et les métadonnées du package à jour avec chaque version.
* Balisez les versions de Git afin que les utilisateurs puissent épingler un état connu en cas de besoin.
* Répondre aux problèmes ou aux discussions soulevées par la communauté.
* Archivez les anciens référentiels s'ils ne sont plus pris en charge afin que les utilisateurs n'importent pas accidentellement des fichiers obsolètes.
  des plans.

La publication via le moteur d'empaquetage garantit que chaque plan est contrôlé en version, documenté et
et prêt pour le développement collaboratif.
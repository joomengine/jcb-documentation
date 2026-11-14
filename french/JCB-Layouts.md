> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="jcb-layouts"></a>
# Dispositions JCB

Les mises en page JCB sont des fichiers de mise en page Joomla que vous organisez, versionnez et réutilisez via l'interface Joomla Component Builder (JCB). Ils vous permettent de partager le même balisage entre plusieurs modèles, vues d'administration et vues de site sans vous répéter.

> 📚 Nouveau dans les remplacements de mise en page Joomla ? Commencez par [Configuration de la mise en page](./Layout-Setup.md) pour une présentation pas à pas au niveau du code, puis revenez ici pour maîtriser le flux de travail du référentiel qui maintient ces remplacements synchronisés entre les projets.

---

<a id="what-are-jcb-layouts"></a>
## Que sont les mises en page JCB ?

Les mises en page JCB sont des **fichiers de mise en page Joomla modulaires** gérés via le [JCB GUI](https://www.joomlacomponentbuilder.com).
Ils sont équivalents aux fichiers de remplacement de mise en page natifs de Joomla (`/layouts`) et suivent les mêmes principes de conception.

Avec JCB Layouts, vous pouvez définir des vues HTML+PHP réutilisables et personnalisables :

- Rendu depuis n'importe où dans votre composant (administrateur ou site)
- Encapsulé dans des blocs propres et basés sur des modèles
- Entièrement compatible avec l'espace de noms et remplaçable comme les mises en page natives de Joomla

Cela permet à vos composants de rester **plus propres, plus maintenables et SECS** (Ne vous répétez pas).

---

<a id="why-use-layouts-in-jcb"></a>
## Pourquoi utiliser les mises en page dans JCB ?

Les mises en page JCB vous aident à :

- Extrayez le balisage réutilisable des vues, des champs et des modules
- Maintenir la cohérence structurelle de votre composant
- Simplifiez les modifications en éditant un fichier au lieu de plusieurs
- Autoriser la prise en charge du remplacement via les modèles Joomla

Ils sont idéaux pour :

- Rendu des lignes de formulaire
- Sortie répétée (comme des éléments dans une boucle)
- Conditions et logique d'affichage dynamique

Associez ces avantages au didacticiel [Ajout de modèles et de mises en page à une vue de site](./Adding-Templates-and-Layouts-to-a-Site-View.md) pour voir comment les modèles, les mises en page et les Gets dynamiques s'articulent au moment de l'exécution.

---

<a id="how-do-you-manage-layouts-in-jcb"></a>
## Comment gérer les mises en page dans JCB ?

Toutes les mises en page sont contrôlées en version et gérées dans l'interface graphique de JCB sous l'onglet **Mise en page**. Le flux de travail reflète d'autres actifs sauvegardés dans le référentiel dans JCB :

1. Cliquez sur **Init** dans la zone Mises en page pour connecter le projet à un référentiel de mises en page.
2. Choisissez à partir de quel référentiel charger les mises en page (collections officielles, un team fork ou votre boutique personnelle).
3. Sélectionnez la ou les mises en page spécifiques que vous souhaitez importer.
4. Compilez ou prévisualisez votre composant : la mise en page est désormais disponible partout où vous appelez `JLayoutHelper::render()`.

Une fois importé, vous pouvez :

- **Réinitialiser** une mise en page pour la synchroniser avec la version en amont.
- **Poussez** vos mises en page personnalisées si vous avez un accès en écriture au référentiel.
- **Fork** le référentiel pour gérer votre propre collection de mises en page sans perdre les améliorations en amont.

Cela vous donne une manière structurée d'intégrer les mises à jour en amont tout en préservant les personnalisations de votre projet.

> 🛠️ **Conseil :** Traitez l'onglet Mises en page comme un contrôle de code source. Réinitialisez avant de compiler pour détecter les nouvelles modifications en amont et poussez une fois vos mises à jour testées. Pour les projets d’équipe, documentez la branche du référentiel vers laquelle pointe une mise en page afin que les collaborateurs restent alignés.

---

<a id="using-layouts-during-development"></a>
## Utilisation des mises en page pendant le développement

- Mises en page de référence à partir de modèles, de vues d'administration ou de code d'assistance à l'aide de `JLayoutHelper::render('namespace.layout', $displayData)`.
- Transmettez uniquement les données dont la mise en page a besoin ; `$displayData` est votre contrat entre l'appelant et le fichier de mise en page.
- Dispositions en chaîne lorsque vous avez besoin de sous-composants. Les appels imbriqués permettent de conserver un balisage complexe lisible tout en respectant la hiérarchie de remplacement de Joomla.
- Fiez-vous à la structure de répertoires de remplacement de Joomla (`templates/<template>/html/layouts/`) lorsque vous souhaitez que les créateurs de sites personnalisent votre sortie sans modifier le composant.

Si vous créez de nouvelles vues de site, combinez ce guide avec la [Présentation de l'architecture de vue de site](./Adding-Site-Views-to-a-Component.md) révisée . L'interaction entre les requêtes dynamiques, les modèles, les mises en page et les espaces réservés de code personnalisé permet de maintenir les composants volumineux.

---

<a id="index-of-jcb-layouts"></a>
## Index des implantations JCB

Lorsque vous importez des mises en page depuis un référentiel, JCB les enregistre dans l'onglet Mises en page. Utilisez cet espace pour conserver une référence rapide de ce que chaque mise en page est censée restituer et de son origine. Exemple de structure :

| Clé de mise en page | Objectif | Dépôt amont |
| --- | --- | --- |
| `sermonlist.item` | Balisage des cartes de liste de sermons partagé par les vues Prédicateur, Série et Catégorie | `vdm-io/layouts-sermons` |
| `forms.fieldset.row` | Rend les ensembles de champs Bootstrap pour les vues de modification de l'administrateur | `your-org/layouts-forms` |

> ✏️ **Personnalisez ce tableau par projet.** L'enregistrement de la portée de la mise en page à côté du nom du référentiel permet de décider plus facilement quand réinitialiser, bifurquer ou retirer une mise en page à mesure que votre composant évolue.

Pour obtenir des conseils de collaboration plus larges, consultez l'article [Proposed Collaborative Workflow in JCB](./Proposed-Collaborative-Workflow-in-JCB.md) une fois que votre catalogue de mises en page commence à s'étoffer.
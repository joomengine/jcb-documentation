> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="the-new-fields-area-in-joomla-component-builder"></a>
# La nouvelle zone de champs dans Joomla Component Builder

<a id="introduction"></a>
### Introduction

[00:00:08](https://www.youtube.com/watch?v=26x_Sc8jbp8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m08s)

Dans Joomla Component Builder (JCB), la **Zone de champ** joue un rôle essentiel dans la façon dont votre composant se comporte et interagit avec les données. Il définit une grande partie des fonctionnalités et de la logique de vos vues. Au fil du temps, ce domaine a subi d'importants changements pour améliorer la stabilité, la convivialité et l'efficacité.

La dernière mise à jour introduit une nouvelle présentation de sous-formulaire qui remplace l'ancienne méthode de définition XML, rendant la gestion des champs plus facile et plus sûre sans risquer de mauvaises configurations accidentelles.

---

<a id="1-how-the-field-area-used-to-work"></a>
## 1. Comment fonctionnait la zone de terrain

[00:00:46](https://www.youtube.com/watch?v=26x_Sc8jbp8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m46s)

Dans les versions antérieures de JCB, chaque champ utilisait une **zone de définition de champ XML**. Les développeurs pouvaient librement modifier ou omettre directement des éléments, ce qui donnait de la flexibilité mais provoquait également une instabilité : des modifications accidentelles ou des balises XML manquantes pouvaient interrompre la fonctionnalité.

Même si cette flexibilité était utile pour les utilisateurs avancés, elle posait des problèmes pour garantir des composants cohérents et sans erreur. Pour résoudre ce problème, l'équipe de JCB a restructuré le système pour le rendre plus robuste et plus convivial.

---

<a id="2-transition-to-the-sub-form-layout"></a>
## 2. Transition vers la mise en page du sous-formulaire

[00:01:55](https://www.youtube.com/watch?v=26x_Sc8jbp8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m55s)

À partir de la version **2.7.5**, la zone de définition du champ XML a été remplacée par une **interface de sous-formulaire structuré**. Cette mise à jour a introduit :

* Un **onglet Base de données** dédié à la gestion des valeurs de la base de données.
* Un **onglet Informations sur le terrain** avec des options clairement organisées.
* Une disposition cohérente à onglets qui regroupe logiquement les paramètres associés.

Lorsque vous ouvrez un champ comme *Alias*, le nouveau sous-formulaire affiche les valeurs de champ prédéfinies et permet d'ajouter de nouvelles propriétés qui ne sont pas déjà présentes.

**Exemple :**
Si vous souhaitez ajouter une nouvelle propriété telle que `size`, sélectionnez-la simplement dans la liste déroulante - JCB charge automatiquement sa description et sa valeur par défaut.

**Conseil :**
Même si les champs obligatoires peuvent techniquement rester vides, il est recommandé de toujours fournir des valeurs valides pour garantir des compilations propres.

---

<a id="3-improved-validation-and-compilation-behavior"></a>
## 3. Comportement de validation et de compilation amélioré

[00:03:31](https://www.youtube.com/watch?v=26x_Sc8jbp8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m31s)

Si un champ obligatoire est omis lors de la compilation, JCB le détecte et revient automatiquement à la valeur par défaut. Cependant, vous devez toujours confirmer que les valeurs de vos champs sont correctes avant de compiler.

Cette amélioration réduit les erreurs courantes liées au XML et rationalise le processus de création de composants stables et prêts pour la production.

---

<a id="4-new-implementation-for-custom-fields-and-users"></a>
## 4. Nouvelle implémentation pour les champs personnalisés et les utilisateurs

[00:05:00](https://www.youtube.com/watch?v=26x_Sc8jbp8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m00s)

Dans la version **2.7.6**, JCB a introduit une **nouvelle implémentation pour les champs personnalisés** et les **utilisateurs personnalisés**.

Lors de la création d'un nouveau champ personnalisé, JCB organise désormais automatiquement le code PHP associé (tel que `getOptions`) dans une zone de texte dédiée, ce qui le rend beaucoup plus facile à lire et à modifier.

Pour le type de champ **Utilisateur**, deux nouvelles méthodes sont clairement séparées :

* `getExclude`
* `getGroup`

Cela améliore la clarté et aide les développeurs à comprendre plus rapidement la logique sous-jacente.

---

<a id="5-extra-properties-enhanced-flexibility"></a>
## 5. Propriétés supplémentaires : flexibilité améliorée

[00:06:05](https://www.youtube.com/watch?v=26x_Sc8jbp8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m05s)

JCB prend désormais en charge les **propriétés de champ supplémentaires** qui étendent la personnalisation sans avoir besoin de modifier le code principal.

<a id="listclass-property"></a>
### Propriété `listclass`

Cette propriété vous permet d'appliquer des classes CSS personnalisées aux valeurs de champ dans les vues de liste.
Par exemple, vous pouvez ajouter une classe telle que `my-class-dean` pour styliser différemment un champ dans la vue liste des administrateurs.

**Mesures:**

1. Ouvrez le champ souhaité dans JCB.
2. Dans la section « Propriétés supplémentaires », sélectionnez **listclass**.
3. Entrez le nom de votre classe CSS (par exemple, `highlight-row`).

Cette propriété ajoute cette classe dynamiquement à la sortie HTML de la vue liste.

---

<a id="6-escape-option"></a>
## 6. Option d'évasion

[00:07:19](https://www.youtube.com/watch?v=26x_Sc8jbp8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m19s)

Par défaut, JCB échappe les valeurs des champs pour empêcher le rendu HTML indésirable. Toutefois, si vous souhaitez intentionnellement des éléments HTML (comme `<span>` ou `<div>`) dans votre sortie de champ, définissez **Escape** sur `false`.

**Exemple de cas d'utilisation :**
Lorsque vous souhaitez afficher du texte ou des icônes formatés dans une vue de liste sans qu'ils soient supprimés.

---

<a id="7-display-option"></a>
## 7. Option d'affichage

[00:08:06](https://www.youtube.com/watch?v=26x_Sc8jbp8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m06s)

L'**Option d'affichage** contrôle quand et où les champs apparaissent dans la configuration de votre composant.
Par exemple, les champs peuvent être configurés pour afficher :

* Dans la zone **Options des composants**.
* Dans les **panneaux de configuration des éléments de menu**.

Cela facilite la gestion du comportement des composants dans différentes zones d'interface.
Une documentation supplémentaire pour cette fonctionnalité est prévue dans les futures mises à jour.

---

<a id="8-validate-option"></a>
## 8. Valider l'option

[00:08:53](https://www.youtube.com/watch?v=26x_Sc8jbp8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m53s)

Tous les types de champs ne sont pas dotés d'une validation intégrée. L'**Option de validation** vous permet de définir une règle de validation pour n'importe quel champ.

Si le type de champ sélectionné prend déjà en charge la validation, il est préférable d'utiliser sa propriété native. Sinon, cette propriété supplémentaire garantit l'intégrité de vos données en appliquant une règle personnalisée.

---

<a id="9-field-restoration-and-default-management"></a>
## 9. Restauration des champs et gestion des défauts

[00:10:00](https://www.youtube.com/watch?v=26x_Sc8jbp8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m00s)

L'un des ajouts les plus conviviaux est la **fonctionnalité de restauration automatique**.
Si vous modifiez ou supprimez une propriété et décidez de la rétablir, JCB restaure automatiquement la valeur précédente ou par défaut.

Cela garantit que vous ne perdrez jamais votre travail par erreur, même lorsque vous expérimentez différents paramètres.

**Exemple de flux de travail :**

1. Ajoutez ou modifiez une propriété.
2. Changez d'avis et cliquez pour restaurer.
3. JCB rétablit instantanément la valeur d'origine.

---

<a id="10-summary-and-best-practices"></a>
## 10. Résumé et bonnes pratiques

[00:12:02](https://www.youtube.com/watch?v=26x_Sc8jbp8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m02s)

La nouvelle zone Champs de JCB simplifie le processus de création et de gestion des champs, le rendant plus intuitif et moins sujet aux erreurs.

**Principaux points à retenir :**

* L'édition XML n'est plus nécessaire - utilisez plutôt des sous-formulaires structurés.
* Les valeurs obligatoires sont auto-validées lors de la compilation.
* Le code PHP des champs personnalisés est clairement organisé.
* Des options supplémentaires (`listclass`, `escape`, `display`, `validate`) améliorent la flexibilité.
* Les propriétés des champs peuvent être rétablies en toute sécurité à tout moment.

Dans l'ensemble, cette amélioration rend la création de champs dans JCB plus rapide, plus sûre et beaucoup plus facile pour les développeurs débutants et avancés.

---

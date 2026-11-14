> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="custom-admin-views"></a>
# Vues d'administration personnalisées

<a id="concept-primer"></a>
## Introduction au concept

<a id="what-are-custom-admin-views"></a>
### Que sont les vues d'administration personnalisées ?

**Les vues d'administration personnalisées** vous offrent une liberté totale pour définir des interfaces d'administration sur mesure au sein de vos composants Joomla, sans vous limiter aux générateurs de vues par défaut de Joomla. Ils sont l'**équivalent côté administrateur des vues de site**, construits à l'aide de blocs de construction JCB familiers tels que **Templates**, **Layouts**, **Dynamic Gets** et **Custom Code**, avec des actifs **JavaScript ou CSS** facultatifs superposés en cas de besoin.

Utilisez des vues d'administration personnalisées pour créer :

- Tableaux de bord de données
- Zones d'import/export
- Générateurs de rapports
- Des outils administratifs ponctuels
- Vues d'édition multi-onglets

Cela transforme le back-end de Joomla en un **puissant canevas** pour toute interface que vous envisagez, entièrement alimenté par la même architecture JCB utilisée dans l'ensemble du front-end.

<a id="how-are-custom-admin-views-composed"></a>
### Comment les vues d'administration personnalisées sont-elles composées ?

Chaque vue d'administration personnalisée peut être une **Vue d'élément** (entité unique), une **Vue de liste** (plusieurs entités avec pagination) ou une **Vue hybride/utilitaire** pour les tableaux de bord, les opérations par lots ou les outils sur mesure. Assemblez-les en combinant :

- Un ou plusieurs **Dynamic Gets** pour récupérer et relier les données entre les tables
- **Formulaires**, **Filtres** ou **Barres d'outils** en option pour capturer les entrées
- **Modèles et mises en page** pour structurer la sortie
- **Blocs de code personnalisés** pour injecter de la logique à des points de compilation spécifiques
- **Bibliothèques JavaScript/CSS** facultatives pour des interactions plus riches

Le résultat est un contrôle total sur les données et la conception tout en bénéficiant du flux de travail piloté par le compilateur de JCB.

<a id="reset-fork-or-customise"></a>
### Réinitialiser, bifurquer ou personnaliser

Comme d'autres actifs alimentés par JCB, les vues d'administration personnalisées prennent en charge les flux de travail contrôlés par version :

- **Init** une vue d'administration personnalisée à partir de ce référentiel
- **Réinitialiser** pour synchroniser avec les dernières mises à jour
- **Poussez** vos propres versions améliorées
- **Fork** le dépôt pour personnaliser entièrement vos interfaces d'administration privées

Chaque vue d'administration personnalisée peut évoluer en fonction des besoins back-end de votre projet, et JCB garantit que vos modifications sont conservées en toute sécurité tout au long du cycle de vie de la compilation.

> La conception de l'interface d'administration ne doit jamais être une réflexion après coup. Avec les vues d'administration personnalisées, vous êtes propriétaire de l'expérience, de la logique à la mise en page, le tout dans Joomla Component Builder.

<a id="index-of-custom-admin-views"></a>
### Index des vues d'administration personnalisées

Utilisez la [_Sidebar](./_Sidebar.md) ou l'[index de documentation](./index.md) pour accéder directement aux didacticiels, aux procédures pas à pas et aux définitions de vues réutilisables qui démontrent le comportement des vues d'administration personnalisées dans des projets réels.

---

<a id="video-walkthrough-overview"></a>
## Présentation vidéo pas à pas

[00:00:00](https://www.youtube.com/watch?v=gtdQ1lwB9ds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(*Cliquez sur ces liens horaires pour voir la vidéo YouTube.*)

Les vues d'administration personnalisées dans **Joomla Component Builder (JCB)** sont des vues backend spécialisées qui vous permettent d'afficher des **mises en page, rapports, tableaux de bord ou analyses personnalisés** dans la zone d'administration de Joomla.

Alors que les **Vues de site** se concentrent sur la présentation frontale, les **Vues d'administration personnalisées** vous permettent de créer des interfaces d'administration hautement interactives, basées sur PHP et contrôlées par les autorisations.

> ⚠️ N'oubliez pas : les vues d'administration personnalisées ne remplacent **pas** les vues d'administration standard. Chaque composant a toujours besoin d'au moins une vue d'administration normale pour définir son schéma de données, sa table de base de données et sa pile CRUD générée. Les vues d'administration personnalisées s'appuient sur cette base pour fournir des tableaux de bord ou des flux de travail sur mesure.

Dans cet exemple, nous ferons référence au composant **Cost-Benefit Projection**, qui utilise des vues d'administration personnalisées pour visualiser les données sur l'état de santé de l'entreprise et l'impact des interventions.

---

<a id="example-cost-benefit-projection-component"></a>
## Exemple : composante de projection coûts-avantages

[00:00:33](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h00m33s)

Le composant Projection coûts-avantages est utilisé pour montrer aux entreprises les **avantages financiers de la lutte contre certaines maladies ou causes** au sein de leur personnel.

Il comporte deux vues d'administration personnalisées clés :

* **Résultats de l'entreprise**
* **Résultats combinés**

Ces vues affichent des données accessibles uniquement aux utilisateurs disposant d'autorisations spécifiques.

[00:01:04](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h01m04s)

Dans le panneau d'administration, sous **Entreprises**, chaque entrée d'entreprise comprend une icône pour ouvrir ses données de résultat.
De plus, il existe un bouton **"Résultats combinés"** qui apparaît dynamiquement - il est automatiquement créé par JCB.

[00:01:36](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h01m36s)

---

<a id="component-builder-custom-admin-view"></a>
## Vue d'administration personnalisée du générateur de composants

[00:01:55](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h01m55s)

Dans JCB, une **Vue d'administration personnalisée** représente une zone vide dans laquelle vous pouvez charger du **HTML, PHP et JavaScript personnalisés**.

Tout ce qui se trouve dans la zone de travail blanche est géré par vous, y compris le rendu du contenu, les contrôles des boutons et la visualisation des données.

[00:02:07](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h02m07s)

Vous pouvez ajouter un menu de barre latérale et lier cette vue à d'autres zones du composant, telles que des listes d'entreprises ou des tableaux de bord.

Chaque vue peut être liée à une société ou à un enregistrement spécifique. À partir de là, cliquez sur **Modifier** pour ouvrir l'enregistrement connecté pour modification.

[00:03:10](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h03m10s)

Si vous fermez la fenêtre d'édition, JCB vous ramène à la même page de résultats, garantissant ainsi une continuité fluide du flux de travail pour l'utilisateur.

[00:03:35](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h03m35s)

---

<a id="adding-a-custom-admin-view-in-jcb"></a>
## Ajout d'une vue d'administration personnalisée dans JCB

Pour créer une nouvelle vue d'administration personnalisée :

1. Ouvrez **Joomla Component Builder → Vues d'administration**.
2. Cliquez sur **Nouveau → Vue administrateur personnalisée**.
3. Saisissez le **Nom** (par exemple, `Company Results`).
4. Choisissez un **Emplacement du menu** si vous souhaitez qu'il soit visible dans une section spécifique du menu d'administration.
5. Ajoutez du **Code de mise en page personnalisé** dans la zone de l'éditeur (appels PHP, HTML ou modèle).
6. Liez éventuellement des **champs**, des **mises en page** ou des **fichiers modèles**.
7. Enregistrez la vue.

Une fois compilé, JCB génère automatiquement le contrôleur PHP et affiche les fichiers dans le dossier `admin/views/` du composant.

---

<a id="add-custom-button-sample"></a>
## Ajouter un exemple de bouton personnalisé

[00:04:12](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h04m12s)

Vous pouvez ajouter des **boutons de barre d'outils personnalisés** dans votre vue d'administration personnalisée. Ces boutons déclenchent des méthodes de contrôleur qui effectuent des actions spécifiques.

1. Dans votre vue d'administration personnalisée, faites défiler jusqu'à la section **Boutons personnalisés**.
2. Cliquez sur **Ajouter**.
3. Configurez :

* **Icône** - Choisissez parmi les icônes intégrées de Joomla.
   * **Nom** - Exemple : `Edit Company`.
   * **Méthode du contrôleur** - Exemple : `editcompany`.
   * **Type de cible** - Sélectionnez si le bouton s'applique à un **élément unique**, à une **liste** ou aux **les deux**.
4. Cliquez sur **Enregistrer**.

> **Remarque :** La configuration des boutons est enregistrée dans le formulaire JCB mais n'est pas encore implémentée dans la base de données ou dans la logique PHP jusqu'à ce que le composant soit compilé.

[00:04:52](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h04m52s)

---

<a id="adding-scripts-for-controller-methods"></a>
## Ajout de scripts pour les méthodes de contrôleur

[00:05:05](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h05m05s)

Chaque bouton que vous créez nécessite une **méthode de contrôleur** associée pour définir son comportement.

1. Dans le backend JCB, ouvrez votre composant et accédez à :
   **Vue d'administration personnalisée → Zone de script du contrôleur PHP.**
2. Ajoutez votre logique PHP pour chaque bouton personnalisé, par exemple :

```php
// Example controller method
public function gotocompanies()
{
    $this->setRedirect('index.php?option=com_costbenefitprojection&view=companies');
}
```

[00:05:16](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h05m16s)

Vous pouvez également inclure une logique de modèle associée en ajoutant du code dans la section **Model Script**.
Si aucun script de modèle n'est nécessaire, utilisez des espaces réservés pour les commentaires (`//`) pour supprimer les avertissements.

[00:05:47](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h05m47s)

La méthode `editcompany`, par exemple, suit la convention de Joomla pour ouvrir les éléments en toute sécurité, y compris la validation des jetons CSRF et les contrôles d'autorisation.

[00:06:13](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h06m13s)

---

<a id="area-for-custom-scripting"></a>
## Zone pour les scripts personnalisés

[00:06:17](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h06m17s)

JCB fournit des **zones d'insertion de code** spécifiques pour les vues d'administration personnalisées, où vous pouvez ajouter en toute sécurité des scripts personnalisés.

Si vous ne savez pas où un extrait de code particulier s'exécute :

1. Compilez votre composant.
2. Recherchez le texte de l'extrait dans les fichiers de composants générés.
3. Observez sa position dans le flux PHP (contrôleur, modèle ou vue).

Cela rend le débogage et la personnalisation simples.

---

<a id="combining-multiple-data-example"></a>
## Exemple de combinaison de plusieurs données

[00:06:58](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h06m58s)

Dans la vue **Résultats combinés**, plusieurs entrées de données d'entreprise peuvent être sélectionnées et agrégées.
Lorsque vous cliquez sur **Résultats combinés**, JCB fusionne les enregistrements sélectionnés et affiche une seule sortie structurée.

[00:07:16](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h07m16s)

La mise en page utilise une combinaison de HTML et PHP et peut inclure des modèles pour une conception réutilisable.

[00:07:41](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h07m41s)

> **Conseil :**
> Vous pouvez utiliser les **modèles et mises en page** de manière interchangeable dans **Site** et **Vues d'administration**.
> Cela garantit une conception cohérente et une réutilisation du code dans l'ensemble de votre composant.

[00:08:11](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h08m11s)

---

<a id="summary"></a>
## Résumé

Les vues d'administration personnalisées dans JCB vous permettent de :

* Créez des **interfaces backend complexes** avec du contenu dynamique.
* Intégrez des **scripts personnalisés et la logique du contrôleur**.
* Ajoutez des **boutons de barre d'outils interactifs**.
* Réutilisez les **mises en page et modèles** dans plusieurs vues.

Ils sont puissants pour afficher des données avancées, combiner des résultats ou créer des tableaux de bord spécialisés directement dans votre zone d'administration Joomla.

---

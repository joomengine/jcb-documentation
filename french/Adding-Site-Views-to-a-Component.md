> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="adding-site-views-to-a-component-in-joomla-component-builder-jcb"></a>
# Ajout de vues de site à un composant dans Joomla Component Builder (JCB)

Les vues du site dans JCB définissent ce que les utilisateurs voient sur le front-end de votre composant Joomla.
Ils utilisent les mêmes champs que vous concevez dans le back-end : consultez la présentation des [Champs JCB](./JCB-Fields.md) pour comprendre comment le schéma, la validation et les règles de rendu de chaque champ sont transférés vers l'interface publique.

<a id="site-view-fundamentals"></a>
## Principes fondamentaux de la vue du site

Les **Vues du site** sont la vue publique de votre composant Joomla : JCB génère pour vous le modèle, la vue et les fichiers de contrôleur natifs de Joomla pendant que vous décidez de la manière dont les informations apparaissent. Chaque vue combine :

- Un **Main Dynamic Get** qui détermine le mode de chargement des données (enregistrement unique ou listes).
- N'importe quel nombre de **Objets dynamiques personnalisés** pour fournir des ensembles de données supplémentaires.
- **Modèles** et **Mise en page** intégrés pour que vous puissiez organiser le balisage et réutiliser la logique de présentation.
- **Espaces réservés de code personnalisé** facultatifs où vous pouvez injecter une logique frontale réutilisable à partir d'extraits ou de référentiels.
- **Bibliothèques JavaScript et CSS** facultatives pour améliorer l'interaction ou le style.


Étant donné que chaque élément est modulaire, vous pouvez réinitialiser une vue de site à la référence maintenue chaque fois qu'un référentiel est mis à jour, ou l'intégrer dans votre propre référentiel lorsque vous avez besoin d'une personnalisation à long terme.

---

<a id="000000httpswwwyoutubecomwatchvzz_hjeyl8pst00h00m00s---accessing-component-settings"></a>
## [00:00:00](https://www.youtube.com/watch?v=zZ_HJeYL8ps&t=00h00m00s) - Accès aux paramètres des composants

1. **Connectez-vous à l'administrateur Joomla.**
   Ouvrez votre backend Joomla et connectez-vous en tant qu'administrateur.

2. **Accédez à Component Builder.**
   Dans le menu principal, accédez à **Composants → Générateur de composants → Composants**.

3. **Sélectionnez votre composant.**
   Ouvrez votre composant existant (par exemple, *Sermon Distributor*).

4. **Accédez à l'onglet Paramètres.**
   Dans votre composant, localisez l'onglet **Paramètres**.
   C'est ici que les **Vues d'administration** et les **Vues de site** sont gérées.

---

<a id="000025httpswwwyoutubecomwatchvzz_hjeyl8pst00h00m25s---understanding-views"></a>
## [00:00:25](https://www.youtube.com/watch?v=zZ_HJeYL8ps&t=00h00m25s) - Comprendre les vues

* **Vues d'administration :** Utilisées pour gérer les données et la configuration du backend.
* **Vues d'administration personnalisées :** Autoriser l'ajout de pages personnalisées dans la zone d'administration.
* **Vues du site :** Définissez la structure et les données présentées sur le front-end de votre site Joomla.

Pour ajouter ou gérer des vues de site :

* Accédez aux sections **Vues d'administration personnalisées** et **Vues du site**.
* Cliquez sur **"Ajouter une vue d'administration personnalisée"** si vous en avez besoin de nouvelles (Sermon Distributor, par exemple, n'en a pas).
* Passez à **Vues du site** pour configurer les vues de vos composants accessibles au public.

---

<a id="000111httpswwwyoutubecomwatchvzz_hjeyl8pst00h01m11s---fixing-the-site-views-selection-glitch"></a>
## [00:01:11](https://www.youtube.com/watch?v=zZ_HJeYL8ps&t=00h01m11s) - Correction du problème de sélection des vues du site

Vous remarquerez peut-être que certaines cases à cocher ou bascules de l'affichage du site apparaissent **non sélectionnées** même si vous les avez sélectionnées et enregistrées précédemment.

<a id="important"></a>
### Important

Il s'agit d'un **problème JavaScript Joomla** - pas d'un problème avec JCB.

**Comment gérer cela :**

1. Si les options de la vue du site semblent désélectionnées après l'enregistrement :

* Fermez l'éditeur Site View.
   * Rouvrez-le à nouveau.
2. Les sélections devraient maintenant apparaître correctement.
3. Évitez d'enregistrer lorsque les cases ne sont pas cochées - cela enregistrerait les valeurs `null` et entraînerait des résultats inattendus.

> **Conseil :** Le même problème peut occasionnellement se produire dans les vues d'administration. Vérifiez toujours avant de sauvegarder.

---

<a id="000221httpswwwyoutubecomwatchvzz_hjeyl8pst00h02m21s---exploring-site-view-options"></a>
## [00:02:21](https://www.youtube.com/watch?v=zZ_HJeYL8ps&t=00h02m21s) – Explorer les options d'affichage du site

Chaque vue du site dans JCB propose **quatre commutateurs à clé** :

| Options | Descriptif | Utilisation typique |
| :--------------- | :---------------------------------------------------------------- | :---------------------------------------------------------- |
| **Menu** | Ajoute cette vue du site en tant qu'élément de menu sélectionnable dans Joomla.          | Permet aux utilisateurs de lier la vue à partir du système de menus de Joomla.     |
| **Métadonnées** | Active les métadonnées (titre, description, mots-clés) pour cette page.    | Pour le référencement et l’affichage des métadonnées du navigateur.                        |
| **Vue par défaut** | Définit cette vue comme page de secours (par défaut) pour votre composant. | Utilisé lorsqu'aucune vue spécifique n'est demandée ou que l'accès est refusé. |
| **Accès** | Active le contrôle d’accès (autorisations et groupes).                  | Limite les personnes pouvant afficher des pages ou des données spécifiques.               |

Décomposons chaque option ci-dessous.

---

<a id="000246httpswwwyoutubecomwatchvzz_hjeyl8pst00h02m46s---menu-option"></a>
### [00:02:46](https://www.youtube.com/watch?v=zZ_HJeYL8ps&t=00h02m46s) - Option de menu

Lorsque **Menu = Oui**, JCB crée automatiquement une définition XML afin que Joomla reconnaisse la vue du site comme un type de menu.

**Effet :**
Après avoir compilé le composant :

1. Accédez à **Menus → Ajouter un nouvel élément de menu** dans Joomla.
2. Sous **Sélectionner le type d'élément de menu**, la vue de votre composant (par exemple, « Liste des sermons ») apparaîtra maintenant.
3. Le sélectionner reliera l’affichage frontal directement à cette vue du site.

> **Astuce :** Cela fait gagner du temps : vous n'avez pas besoin d'écrire manuellement du XML pour les types de menus Joomla.

---

<a id="000347httpswwwyoutubecomwatchvzz_hjeyl8pst00h03m47s---metadata-option"></a>
### [00:03:47](https://www.youtube.com/watch?v=zZ_HJeYL8ps&t=00h03m47s) - Option de métadonnées

Lorsque **Metadata = Yes**, JCB ajoute des scripts de gestion des métadonnées à votre vue générée.

**Pour que cela fonctionne correctement :**

1. Assurez-vous que votre modèle transmet les champs de métadonnées dans la vue.

* Généralement trouvé dans les baies `$this->item` ou `$this->items`.
2. Compilez votre composant.
3. Ouvrez le fichier généré :
   `/components/com_yourcomponent/views/viewname/view.html.php`
4. Vérifiez que les métadonnées sont chargées et attribuées correctement.

Si les données ne sont pas présentes, Joomla n'affichera pas les métadonnées même si le commutateur est activé.

> **Conseil :** Vérifiez toujours que le modèle renvoie des métadonnées pour vos éléments Site View.

---

<a id="000453httpswwwyoutubecomwatchvzz_hjeyl8pst00h04m53s---default-view-option"></a>
### [00:04:53](https://www.youtube.com/watch?v=zZ_HJeYL8ps&t=00h04m53s) - Option d'affichage par défaut

La **Vue par défaut** fait office de **page d'accueil** ou d'itinéraire de secours du composant.

**Directives :**

* Vous ne pouvez **avoir qu'une seule vue par défaut** par composant.
* Lorsque Joomla ne parvient pas à déterminer quelle vue charger, il redirige automatiquement vers celle-ci.
* Il est également utilisé comme solution de secours lorsqu'un utilisateur n'est pas autorisé à accéder à d'autres vues.

Exemple :
Si votre vue par défaut est **Prédicateurs** et qu'un utilisateur visite une vue restreinte « Sermon », il sera redirigé vers « Prédicateurs » avec un message.

> **Important :** Ne sélectionnez pas plusieurs vues par défaut. Un seul devrait être actif.

---

<a id="000537httpswwwyoutubecomwatchvzz_hjeyl8pst00h05m37s---access-option"></a>
### [00:05:37](https://www.youtube.com/watch?v=zZ_HJeYL8ps&t=00h05m37s) - Option d'accès

Le commutateur **Access** permet le contrôle des autorisations pour chaque vue de site.

**Objectif :**
Permet à JCB d'inclure les tables d'accès nécessaires pour que :

* Les utilisateurs ne voient que les vues pour lesquelles ils ont l'autorisation.
* Les niveaux d'accès de Joomla (Public, Enregistré, Spécial, etc.) sont respectés.

**Détails de mise en œuvre :**

* L'accès peut être géré aux niveaux **item** et **view**.
* Utilise des **groupes d'utilisateurs** et des **niveaux d'accès** pour contrôler qui peut voir quoi.
* Lorsque cette option est cochée, JCB garantit que les champs d'accès et la logique sont intégrés à votre composant.

> **Astuce :** Configurez toujours les niveaux d'accès dans Joomla après l'installation pour qu'ils correspondent à la logique de votre composant.

---

<a id="000632httpswwwyoutubecomwatchvzz_hjeyl8pst00h06m32s---final-step-compile-and-test"></a>
## [00:06:32](https://www.youtube.com/watch?v=zZ_HJeYL8ps&t=00h06m32s) - Dernière étape : compiler et tester

Une fois que vous avez configuré vos vues de site :

1. Cliquez sur **Enregistrer et fermer** dans JCB.
2. Accédez à **Component Builder → Compile** et compilez votre composant.
3. Installez ou mettez à jour le package de composants généré dans Joomla.
4. Ouvrez votre frontal Joomla et testez :

* Les liens du menu.
   * Présence de métadonnées.
   *Restrictions d'accès.
   * Redirection de vue par défaut.

> **Résultat :** Vos vues de site sont désormais actives, accessibles et correctement configurées.

---

<a id="keep-site-views-in-sync-across-projects"></a>
## Gardez les vues du site synchronisées entre les projets

Les vues du site sont expédiées à partir de référentiels organisés. Chaque fois qu'une définition en amont s'améliore :

1. **Sélectionnez** les vues du site que vous souhaitez actualiser dans JCB.
2. Cliquez sur **Réinitialiser** pour extraire la dernière version maintenue.
3. Recompilez votre composant pour que les fichiers MVC générés incluent les mises à jour.

Si vous devez diverger de manière permanente, **forkez le référentiel** qui gère la vue du site, ajustez-le à vos besoins et pointez JCB vers votre fork. Cela permet de contrôler la version de votre logique personnalisée tout en bénéficiant de la génération automatique de JCB.

---

<a id="summary"></a>
## Résumé

| Étape | Actions | Remarques |
| :--- | :------------------------------------------------------------ | :---------------------------------- |
| 1 | Ouvrez votre composant dans JCB.                     | Accédez à *Paramètres → Vues du site*.      |
| 2 | Corrigez les bascules non sélectionnées si nécessaire.               | Rouvrez avant de sauvegarder.               |
| 3 | Configurer le menu, les métadonnées, la vue par défaut, l'accès. | Chacun ajoute des fonctionnalités clés.        |
| 4 | Compilez votre composant.                         | Génère une structure XML et PHP.    |
| 5 | Testez dans le front-end Joomla.                       | Confirmez le menu, l'accès et les métadonnées. |

---

<a id="helpful-tips"></a>
## Conseils utiles

* Toujours **rouvrez l'éditeur Site View** avant d'enregistrer si les sélections semblent désactivées.
* Utilisez **Menu = Yes** pour exposer la vue au gestionnaire de menus de Joomla.
* Une seule **une vue par défaut** devrait être active.
* Utilisez **Access Control** à bon escient pour protéger les pages sensibles.
* Après des modifications majeures, **recompilez et réinstallez** le composant pour appliquer les mises à jour.

---

**Référence vidéo :**
*Regardez le tutoriel complet sur YouTube :*
[Ajout de vues de site à un composant - Joomla Component Builder](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)

---

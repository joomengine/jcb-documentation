> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="adding-none-database-fields-to-an-admin-view"></a>
# Ajout de champs de base de données Aucun à une vue administrateur

<a id="overview"></a>
### Aperçu

Joomla Component Builder (JCB) introduit une option de champ **"Aucun DB"** qui vous permet d'ajouter des champs à votre **Vue administrateur** sans les enregistrer dans la base de données. Cette amélioration permet des interfaces flexibles et pilotées par script dans lesquelles certains champs n'existent que pour la logique, l'interaction ou le calcul, sans modifier la structure de la base de données.

---

<a id="1-when-to-use-none-database-fields"></a>
## 1. Quand utiliser aucun champ de base de données

**[00:00:00](https://www.youtube.com/watch?v=6OTRDIgxgq0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)**

Cette nouvelle fonction JCB permet aux développeurs d'**ajouter un champ à une vue sans créer de colonne de base de données correspondante**. Ceci est particulièrement utile lorsque :

* Le champ **récupère ou manipule les données** d'une autre table.
* Vous souhaitez **modifier le comportement de la page de manière dynamique** en fonction de la sélection ou des conditions de l'utilisateur.
* Vous avez besoin d'un champ uniquement pour **combiner ou traiter plusieurs valeurs** avant de les enregistrer dans un seul champ de base de données.
* Le champ est utilisé pour les **données temporaires ou calculées**, et non pour le stockage persistant.

Par exemple, vous souhaiterez peut-être utiliser deux champs sur la page d'administration pour capturer différentes entrées, les combiner dans votre fonction `save` et stocker une seule valeur fusionnée dans la base de données.

---

<a id="2-how-it-works-in-practice"></a>
## 2. Comment ça marche en pratique

**[00:00:41](https://www.youtube.com/watch?v=6OTRDIgxgq0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m41s)**

Lorsque vous utilisez un **champ Aucun DB**, vous pouvez gérer ses données via :

* **Code PHP personnalisé** dans la méthode de sauvegarde de la vue administrateur.
* **Logique JavaScript** qui manipule le formulaire avant sa soumission.

Exemple de flux de travail :

1. Créez un champ `None DB` pour accepter une saisie temporaire.
2. Utilisez JavaScript pour collecter sa valeur lors de la soumission du formulaire.
3. Dans votre logique de sauvegarde PHP, fusionnez cette entrée avec la valeur d'un autre champ.
4. Stockez les données fusionnées dans un véritable champ de base de données.

Cela permet une **flexibilité totale** dans la manière dont les données du formulaire sont traitées et enregistrées.

---

<a id="3-implementation-example-hidden-behavior-and-external-tables"></a>
## 3. Exemple d'implémentation : comportement caché et tables externes

**[00:01:16](https://www.youtube.com/watch?v=6OTRDIgxgq0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m16s)**

Un autre cas d'utilisation courant est celui où les valeurs d'un champ sont utilisées pour **remplir ou mettre à jour une autre table**. Dans cette configuration :

* Le champ **Aucun DB** collecte les entrées de l'utilisateur.
* Lors de l'enregistrement, votre script écrit ces données dans une autre table.
* Après l'enregistrement, le formulaire peut **masquer ces champs** en fonction de conditions logiques ou de valeurs.

Cette méthode est idéale pour les **interactions multi-tables** ou la **logique d'affichage conditionnelle** dans les interfaces d'administration complexes.

---

<a id="4-integration-with-subforms"></a>
## 4. Intégration avec les sous-formulaires

**[00:01:34](https://www.youtube.com/watch?v=6OTRDIgxgq0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m34s)**

La fonctionnalité Aucun DB est également utile pour travailler avec des **sous-formulaires** ou des **types de champs de formulaire réutilisables**.

Par exemple:

* Vous disposez peut-être d'un sous-formulaire dont les données ne sont utilisées que pour le traitement lors de la sauvegarde.
* L'utilisation de **Aucun champ DB** garantit que ces champs temporaires ne sont pas écrits dans votre table principale.

Avant cette fonctionnalité, JCB supposait automatiquement que **chaque champ d'une vue administrateur** devait être stocké dans la base de données. Désormais, les développeurs peuvent créer des **structures de formulaire dynamiques et non persistantes**.

---

<a id="5-setting-up-the-none-db-field-option"></a>
## 5. Configuration de l'option de champ Aucun DB

**[00:02:24](https://www.youtube.com/watch?v=6OTRDIgxgq0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m24s)**

Dans la configuration de votre champ de vue d'administration JCB, localisez la nouvelle option **"Aucun DB"** à côté des paramètres habituels *"Afficher dans la liste"* et *"Par défaut"*.

| Paramètre | Descriptif |
| ----------------- | ---------------------------------------------------------------------------- |
| **Afficher dans la liste** | Détermine si le champ apparaît dans la vue de la liste des administrateurs.                      |
| **Par défaut (1/0)** | Contrôle la valeur par défaut de la base de données (auparavant la seule option).            |
| **Aucune base de données** | Marque le champ comme n'étant pas une base de données ; sa valeur ne sera pas stockée automatiquement. |

Cette **troisième option** vous permet de définir des champs qui sont utilisés uniquement dans des contextes logiques ou d'affichage.

---

<a id="6-example-conditional-validation-with-a-none-db-field"></a>
## 6. Exemple : Validation conditionnelle avec un champ de base de données Aucun

**[00:02:49](https://www.youtube.com/watch?v=6OTRDIgxgq0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m49s)**

Vous pouvez utiliser les champs **Aucun DB** pour la logique de validation interne.
Par exemple, le didacticiel utilise un champ nommé **"Non requis"**, qui est manipulé via JavaScript pour adapter dynamiquement la validation du formulaire.

* Le champ stocke les valeurs temporaires utilisées pour décider si d'autres champs sont obligatoires ou masqués.
* Ces valeurs n'ont jamais besoin d'être stockées de manière permanente, ce qui rend le `None DB` idéal.

**[00:03:18](https://www.youtube.com/watch?v=6OTRDIgxgq0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m18s)**
Lorsque vous activez **Aucun DB**, JCB affichera deux avis :

1. "Ce champ ne sera plus enregistré dans la base de données."
2. "Utilisez uniquement l'option Aucun DB si vous envisagez de cibler ce champ avec JavaScript ou PHP pour déplacer sa valeur dans un autre champ qui sera enregistré."

Ces avertissements aident à prévenir les abus.

---

<a id="7-what-happens-behind-the-scenes"></a>
## 7. Que se passe-t-il dans les coulisses

**[00:04:21](https://www.youtube.com/watch?v=6OTRDIgxgq0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m21s)**

Lorsqu'un champ est marqué comme **Aucun DB**, JCB :

* **L'exclut** des migrations de bases de données et de la création de schémas SQL.
* **Supprime** toute logique de sauvegarde liée au formulaire qui écrit dans la base de données.
* **Efface** les options de configuration incompatibles (comme les filtres, les index et les valeurs par défaut de la base de données).

Après l'enregistrement, la valeur du champ **existe uniquement en mémoire** (via les données POST du formulaire ou les scripts) et disparaît sauf si vous la gérez explicitement.

---

<a id="8-tip-using-automated-field-counters"></a>
## 8. Astuce : Utilisation de compteurs de champs automatisés

**[00:05:08](https://www.youtube.com/watch?v=6OTRDIgxgq0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m08s)**

JCB attribue automatiquement un **compteur de champs** lors de la gestion de plusieurs champs dans la logique de votre script. Chaque fois que vous ajoutez ou modifiez un champ, il met à jour et incrémente le compteur pour assurer la cohérence des scripts de formulaire et de l'indexation des champs.

---

<a id="9-summary"></a>
## 9. Résumé

Le type de champ **Aucun DB** offre aux développeurs un **plus grand contrôle** sur la logique des formulaires et la gestion des données au sein de JCB.
Il est préférable de l'utiliser pour :

* Champs logiques conditionnels.
* Valeurs calculées ou affichées uniquement.
* Transfert de données entre tables.
* Interactions ou sous-formulaires avancés de l'interface utilisateur.

Si votre cas d'utilisation n'implique pas ces scénarios, vous pouvez continuer en toute sécurité à utiliser les champs de base de données standard.

---

<a id="key-takeaways"></a>
### Points clés à retenir

* Utilisez `None DB` lorsque les données d'un champ ne doivent pas persister dans la base de données.
* Gérez toujours sa valeur manuellement en utilisant **JavaScript** ou **PHP personnalisé**.
* N'oubliez pas : ces champs sont **exclus** de la génération du schéma de base de données et doivent être **explicitement traités** lors de la sauvegarde.

---

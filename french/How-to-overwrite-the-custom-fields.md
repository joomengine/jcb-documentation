> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="how-to-overwrite-the-custom-fields"></a>
# Comment écraser les champs personnalisés

**Documentation du Générateur de composants Joomla (JCB)**
*(Basé sur le didacticiel « Comment écraser les champs personnalisés »)*

---

<a id="overview"></a>
## Aperçu

[00:00:00](https://www.youtube.com/watch?v=FHQfIhWHYyQ&t=00h00m00s)
Dans Joomla Component Builder (JCB), certains **champs par défaut** sont automatiquement ajoutés à chaque vue d'administration. Cependant, il existe des situations dans lesquelles vous souhaiterez peut-être **personnaliser ou repositionner ces champs par défaut**, par exemple en affichant les champs *Créé par* ou *Date de création* dans un autre onglet ou une autre vue de liste.

Ce guide explique comment écraser ces champs en toute sécurité, mettre à jour leur emplacement et maintenir la compatibilité avec le compilateur JCB.

---

<a id="1-understanding-default-fields"></a>
## 1. Comprendre les champs par défaut

[00:00:12](https://www.youtube.com/watch?v=FHQfIhWHYyQ&t=00h00m12s)
Lors de la création ou de la modification d'une vue administrateur, JCB inclut automatiquement un ensemble de champs par défaut :

* `id`
* `asset_id`
* `state`
* `access`
* `ordering`
* `created_by`
* `date_created`
* `modified_by`
* `date_modified`
* `checked_out`
* `checked_out_time`
* `version`
* `hits`
* `metakey`
* `metadescription`
* `metadata`

Ces champs existent dans chaque vue administrateur, même si vous ne les ajoutez pas explicitement.
Par défaut, **seuls les champs ID et État** apparaissent dans la vue Liste.

---

<a id="2-displaying-more-default-fields"></a>
## 2. Afficher plus de champs par défaut

[00:01:20](https://www.youtube.com/watch?v=FHQfIhWHYyQ&t=00h01m20s)
Dans certains cas, les clients peuvent demander des détails supplémentaires dans la liste ou modifier les vues (par exemple, *Date de création* ou *Créé par*). JCB vous permet d'**écraser ces champs par défaut** en les recréant manuellement.

<a id="example"></a>
### Exemple

[00:01:45](https://www.youtube.com/watch?v=FHQfIhWHYyQ&t=00h01m45s)

Dans la vue "Experts" :

* Les champs `id`, `state` et `ordering` sont affichés par défaut.
* La colonne de classement est affichée sous forme d'icônes haut/bas plutôt que de valeurs numériques.

Si vous souhaitez afficher plus de champs, comme *Créé par* ou *Date de création*, vous pouvez écraser ceux par défaut en créant de nouveaux champs avec **les mêmes noms**.

---

<a id="3-overwriting-default-fields"></a>
## 3. Écrasement des champs par défaut

[00:02:23](https://www.youtube.com/watch?v=FHQfIhWHYyQ&t=00h02m23s)
Pour remplacer un champ par défaut :

1. Créez un nouveau champ dans votre **Vue administrateur**.
2. Utilisez le **exactement le même nom de champ** que celui utilisé par JCB.
   Exemples de noms :

* `created_by`
   * `created_date`
3. Définissez son **type**, son **étiquette** et sa **description** en fonction de votre conception.

<a id="example---created-by-field"></a>
### Exemple - Champ "Créé par"

[00:02:57](https://www.youtube.com/watch?v=FHQfIhWHYyQ&t=00h02m57s)

*Type de champ : `user`
* Nom : `created_by`
* Libellé : *Créé par*
* Description : *L'utilisateur qui a créé cet enregistrement*

<a id="example---created-date-field"></a>
### Exemple - Champ "Date de création"

*Type de champ : `calendar`
* Nom : `created_date`
* Libellé : *Date de création*
* Description : *La date à laquelle cet enregistrement a été créé*

> **Conseil :**
> Faites toujours correspondre exactement les noms de champs. JCB identifie les écrasements en comparant les noms : s'ils diffèrent, vos modifications ne prendront pas effet.

---

<a id="4-reviewing-the-compiled-code"></a>
## 4. Révision du code compilé

[00:03:46](https://www.youtube.com/watch?v=FHQfIhWHYyQ&t=00h03m46s)
Pour confirmer comment JCB compile vos champs écrasés :

1. Ouvrez le **dossier administrateur** de votre composant.
2. Accédez à `models/forms/`.
3. Recherchez le formulaire XML correspondant à votre vue administrateur (par exemple, `joborder.xml`).
4. Ouvrez-le et faites défiler pour localiser vos définitions de champs.

Vous verrez les définitions de champs par défaut et écrasées au format XML.
Ce sont les valeurs que JCB utilise lors de la construction de votre composant.

> **Important :**
> Ne **pas** renommer les nœuds XML des champs par défaut directement dans les fichiers compilés.
> JCB s'appuie sur le nom du champ pour détecter les écrasements. Leur modification peut rompre ce lien.

---

<a id="5-adding-overwritten-fields-in-jcb"></a>
## 5. Ajout de champs écrasés dans JCB

[00:05:06](https://www.youtube.com/watch?v=FHQfIhWHYyQ&t=00h05m06s)
Une fois que vous avez créé les champs personnalisés dans votre vue administrateur, vous devez **les ajouter à la liste des champs** et attribuer leurs positions.

1. Accédez à **Vues administrateur → [Votre vue] → onglet Champs**.
2. Cliquez sur **Ajouter un champ** et sélectionnez ceux nouvellement créés (par exemple, `created_date`, `created_by`).
3. Assignez-les pour qu'ils apparaissent dans un **onglet** spécifique et déterminez s'ils doivent s'afficher dans des vues de liste ou de formulaire.

---

<a id="6-managing-field-placement-in-tabs"></a>
## 6. Gestion du placement des champs dans les onglets

[00:05:41](https://www.youtube.com/watch?v=FHQfIhWHYyQ&t=00h05m41s)
JCB organise les champs du formulaire d'édition en **onglets** numérotés.
Chaque onglet correspond à un regroupement logique d'éléments de formulaire.

* Le **15e onglet** est réservé aux champs liés au système (emplacement par défaut pour "Créé par", "Modifié par", etc.).
* Vous pouvez réattribuer le numéro d'onglet pour afficher ces champs ailleurs.

<a id="example-1"></a>
### Exemple

[00:06:14](https://www.youtube.com/watch?v=FHQfIhWHYyQ&t=00h06m14s)

* Définissez `Tab Number = 3` pour déplacer *Créé par* vers le troisième onglet du formulaire d'édition.
* Enregistrez et compilez le composant.
* Après l'installation, le champ *Créé par* apparaîtra désormais dans le troisième onglet.

Pour le restaurer dans l'onglet système par défaut :

* Changer `Tab Number = 15`
* Enregistrez, compilez et réinstallez votre composant.

> **Remarque :**
> En choisissant l'onglet 15, JCB place le champ dans sa section "Publication" par défaut.
> Tout autre numéro d'onglet remplace cet emplacement.

---

<a id="7-compiling-and-testing-the-component"></a>
## 7. Compilation et test du composant

[00:08:03](https://www.youtube.com/watch?v=FHQfIhWHYyQ&t=00h08m03s)
Après avoir effectué toutes les modifications :

1. **Enregistrez** la configuration de votre vue.
2. **Compilez** le composant à l'aide du compilateur JCB.
3. **Installez-le ou mettez-le à jour** dans Joomla.
4. **Actualisez** votre vue administrateur pour vérifier le nouveau placement du champ.

[00:08:49](https://www.youtube.com/watch?v=FHQfIhWHYyQ&t=00h08m49s)
Vous verrez maintenant que :

* Les champs apparaissent là où vous les avez placés.
* Les valeurs par défaut écrasées (par exemple, *Créé par* et *Date de création*) fonctionnent normalement.
* Leurs instances par défaut sont supprimées, évitant ainsi la duplication.

---

<a id="key-takeaways"></a>
## Points clés à retenir

* JCB inclut automatiquement les champs système par défaut dans chaque vue.
* Vous pouvez **écraser** ces champs en toute sécurité en créant des versions personnalisées portant les mêmes noms.
* Utilisez le **numéro d'onglet** pour contrôler le placement.
* Toujours **compiler et tester** votre composant après l'écrasement.
* Ne **pas** modifier directement le XML compilé - effectuez les modifications dans JCB.

---

<a id="summary"></a>
## Résumé

L'écrasement des champs par défaut dans Joomla Component Builder offre une flexibilité dans la manière dont les informations sont affichées dans les vues backend de votre composant. Que vous ayez besoin de repositionner des champs, d'afficher des métadonnées supplémentaires ou de personnaliser leurs étiquettes, suivre cette méthode structurée garantit que vos modifications persisteront lors des futures compilations et mises à jour.

---

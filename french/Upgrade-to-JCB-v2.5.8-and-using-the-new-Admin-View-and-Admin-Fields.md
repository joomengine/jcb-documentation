> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="upgrading-to-jcb-v258-and-using-the-new-admin-view-and-admin-fields"></a>
# **Mise à niveau vers JCB v2.5.8 et utilisation de la nouvelle vue administrateur et des nouveaux champs d'administration**

**Référence du didacticiel vidéo :** [Regarder sur YouTube](https://www.youtube.com/watch?v=YaycQcsMpOs&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)

---

<a id="overview"></a>
## **Aperçu**

Avec la sortie de **JCB v2.5.8**, Joomla Component Builder (JCB) a introduit une mise à jour majeure remplaçant l'ancien **système de champs répétables** par la nouvelle **disposition des champs de sous-formulaire** dans la vue administrateur et les champs d'administration.
Cette mise à niveau améliore les performances, simplifie la gestion des données et s'aligne sur les normes Joomla 4.

Ce document explique le processus de transition, les changements à prévoir et comment utiliser efficacement la nouvelle vue d'administration basée sur un sous-formulaire.

---

<a id="1-removal-of-repeatable-fields"></a>
## **1. Suppression des champs répétables**

[00:00:00](https://www.youtube.com/watch?v=YaycQcsMpOs&t=00h00m00s)

Dans les versions précédentes de JCB, les champs répétables étaient utilisés pour gérer plusieurs ensembles de données associées dans les vues d'administration, les boutons personnalisés et les conditions. Joomla a déprécié ces champs en raison de limitations structurelles et de problèmes de performances.

Dans JCB 2.5.8 :

* Toutes les structures de champs répétables sont remplacées par des **Champs de sous-formulaire**.
* Le changement améliore le stockage des données, la fiabilité et la compatibilité future.

**Conseil :** Les champs répétables modaux contextuels ont disparu. Les sous-formulaires fournissent désormais une édition en ligne et une structure de données plus stable.

---

<a id="2-migration-of-the-admin-view-to-subform-layout"></a>
## **2. Migration de la vue Admin vers la mise en page de sous-formulaire**

[00:01:59](https://www.youtube.com/watch?v=YaycQcsMpOs&t=00h01m59s)

La zone entière de la vue Admin a été convertie pour utiliser la disposition du sous-formulaire.
Cela comprend :

* Autorisations
* Champs
*Conditions
* Vues liées
* Boutons personnalisés
* Connexions MySQL (Ajouter des tables)

Chacune de ces structures utilisait auparavant des structures répétables. Ils sont désormais entièrement intégrés au format Subform, éliminant le besoin de fenêtres contextuelles modales.

---

<a id="3-field-organization-and-new-tabs"></a>
## **3. Organisation du terrain et nouveaux onglets**

[00:03:13](https://www.youtube.com/watch?v=YaycQcsMpOs&t=00h03m13s)

L'organisation du terrain dans la vue Admin a été améliorée :

* Les boutons **Champs** et **Conditions** se trouvent désormais sous un **onglet Champs** unifié.
* Un nouvel **onglet Paramètres**, renommé **Détails**, contient d'autres éléments répétables précédents.

Ces ajustements rendent l’interface plus propre et mieux organisée. La mise à niveau gère tout cela automatiquement, sans aucune saisie manuelle requise.

---

<a id="4-automatic-conversion-scripts"></a>
## **4. Scripts de conversion automatique**

[00:04:19](https://www.youtube.com/watch?v=YaycQcsMpOs&t=00h04m19s)

JCB 2.5.8 inclut des scripts automatisés qui convertissent toutes les anciennes données de champs répétables dans la nouvelle structure de sous-formulaire.
Ces scripts sont disponibles sur GitHub sous la **branche staging**.

Le processus de conversion est géré par la fonction **`convertRepeatable`**, qui :

* Recherche des champs tels que `ajax`, `custom_button` et `addtables`.
* Convertit les anciennes données JSON en tableaux compatibles avec les sous-formulaires.
* Met à jour les entrées de la base de données en conséquence.

Cela garantit une migration transparente sans intervention de l’utilisateur.

---

<a id="5-model-updates-for-conversion"></a>
## **5. Mises à jour du modèle pour la conversion**

[00:06:30](https://www.youtube.com/watch?v=YaycQcsMpOs&t=00h06m30s)

Pour garantir que chaque champ est correctement converti, des mises à jour ont été apportées aux modèles suivants :

* `admin_field_conditions.php`
* `admin_view.php`

Dans la méthode `getItem()` de ces modèles :

1. Le système vérifie si les zones ont été converties.
2. Sinon, il les convertit lors du chargement.
3. Une fois convertis, ils sont marqués afin que la conversion ne se reproduise pas.

Ces modifications de modèle garantissent que la mise à niveau ne provoque pas de conflits et que le processus se termine automatiquement.

---

<a id="6-compiler-adaptation"></a>
## **6. Adaptation du compilateur**

[00:09:09](https://www.youtube.com/watch?v=YaycQcsMpOs&t=00h09m09s)

Le compilateur JCB a été mis à jour pour utiliser la nouvelle structure de données Subform.
Même si vous n'ouvrez manuellement aucune vue d'administration avant la compilation, le compilateur vérifiera et convertira automatiquement les données si nécessaire. Cela garantit que les composants se compilent correctement en utilisant le dernier format de champ.

---

<a id="7-installing-the-upgrade-to-v258"></a>
## **7. Installation de la mise à niveau vers la v2.5.8**

[00:11:50](https://www.youtube.com/watch?v=YaycQcsMpOs&t=00h11m50s)

Pour installer la mise à niveau :

1. Téléchargez **JCB v2.5.8** depuis GitHub ou votre source locale.
2. Accédez à **Extensions → Gérer → Installer** dans Joomla.
3. Téléchargez et installez le nouveau package JCB.
4. Attendez la fin du processus.

Après l'installation, JCB commencera automatiquement à mettre à jour ses structures de données internes.
Une fois terminé, ouvrez n'importe quelle vue d'administration et actualisez pour confirmer que les nouveaux onglets et mises en page de sous-formulaire sont visibles.

---

<a id="8-new-field-and-conditions-view"></a>
## **8. Nouvelle vue des champs et des conditions**

[00:12:55](https://www.youtube.com/watch?v=YaycQcsMpOs&t=00h12m55s)

Les vues Champ et Conditions ont été repensées pour utiliser la disposition Sous-formulaire.
Toutes les données ont été mises à jour et stockées dans les valeurs du sous-formulaire.

Les améliorations des performances sont notables, mais le chargement des ensembles de données volumineux peut encore prendre plus de temps.
Il est recommandé d'éviter plus de **50 champs d'administration par vue**, car chaque ligne de champ peut contenir jusqu'à 13 sous-champs.

---

<a id="9-editing-fields-and-conditions"></a>
## **9. Modification des champs et des conditions**

[00:14:15](https://www.youtube.com/watch?v=YaycQcsMpOs&t=00h14m15s)

L'édition est désormais plus directe :

* Utilisez les boutons **Modifier les champs liés** ou **Modifier les conditions des champs**.
* Enregistrez votre travail avant de continuer.
* Apportez des modifications et enregistrez ou fermez la fenêtre une fois terminé.

Seuls les champs liés à la vue Admin actuelle sont chargés, ce qui rend l'édition plus rapide et plus ciblée.

---

<a id="10-creating-new-fields"></a>
## **10. Création de nouveaux champs**

[00:15:42](https://www.youtube.com/watch?v=YaycQcsMpOs&t=00h15m42s)

Pour créer un nouveau champ :

1. Ouvrez **Champs d'administration**.
2. Cliquez sur **Créer** ou **Créer des champs d'administration pour cette vue d'administration**.
3. Confirmez l'enregistrement, puis cliquez sur l'icône plus (+) pour ajouter un champ.
4. Enregistrez et fermez lorsque vous avez terminé.

La création d'un champ l'ajoute à la liste des champs disponibles. Vous pouvez ensuite le lier à n’importe quelle vue administrateur.

Il existe également des boutons de raccourci pour un accès rapide aux **Champs d'administration** et aux **Conditions** directement à partir de la liste Vue d'administration.

---

<a id="11-creating-a-new-admin-view"></a>
## **11. Création d'une nouvelle vue administrateur**

[00:17:35](https://www.youtube.com/watch?v=YaycQcsMpOs&t=00h17m35s)

Lors de la création d'une nouvelle vue administrateur :

1. Remplissez les champs suivants :

* Nom d'enregistrement unique
   * Liste du nom de l'enregistrement
   * Brève description
   * Nom du système
2. Enregistrez une fois pour générer un identifiant pour la vue.
3. Ouvrez **Champs et conditions** pour créer et lier des champs.

Il est nécessaire d'enregistrer une fois avant de pouvoir joindre des champs, car la vue administrateur doit avoir un identifiant attribué.

---

<a id="12-summary-of-key-changes"></a>
## **12. Résumé des changements clés**

| Changement | Descriptif |
| ---------------------------------- | ----------------------------------------------- |
| Champs répétables → Champs de sous-formulaire | Mise à niveau vers une structure de données moderne et fiable. |
| Nouvelle présentation d'administration | Onglets pour les champs, les paramètres et les conditions.     |
| Migration automatique | Les scripts et le compilateur gèrent la conversion des données.   |
| Améliorations des performances | Temps de chargement plus rapides, meilleure évolutivité.         |
| Compatibilité Joomla 4 | Les sous-formulaires s'alignent sur les standards de base de Joomla 4.   |

---

<a id="13-conclusion"></a>
## **13. Conclusion**

La mise à niveau vers **JCB 2.5.8** marque une étape importante dans l'amélioration des performances, de la fiabilité et de la compatibilité.
En adoptant pleinement Subform Fields, JCB devient plus stable et prêt pour l'avenir pour Joomla 4 et au-delà.

---

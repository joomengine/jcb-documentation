> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="major-release-of-joomla-component-builder-jcb-v260"></a>
# **Version majeure de Joomla Component Builder (JCB) v2.6.0**

<a id="overview"></a>
## Aperçu

**JCB v2.6.0** marque une mise à niveau significative qui modernise la façon dont les composants sont structurés et gérés. Le changement le plus notable est la **suppression complète de tous les champs répétables** dans la zone des composants Joomla. Cette amélioration garantit une meilleure gestion des données, des performances et une compatibilité avec Joomla 4 et au-delà.

Cette documentation explique les principales modifications, fournit des conseils de mise à niveau et clarifie le fonctionnement du nouveau système pour maintenir la compatibilité ascendante tout en offrant une architecture plus robuste.

---

<a id="1-removal-of-repeatable-fields"></a>
## **1. Suppression des champs répétables**

[00:00:00](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h00m00s)

Les champs répétables étaient autrefois largement utilisés dans la zone de composants de JCB pour gérer des collections de valeurs associées. Cependant, ces champs ont désormais été **entièrement remplacés** par des **champs de sous-formulaire** et des tables dédiées.

<a id="why-the-change-was-necessary"></a>
### Pourquoi le changement était nécessaire

[00:00:43](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h00m43s)

Auparavant, les champs répétables utilisaient JavaScript pour combiner plusieurs valeurs en une seule chaîne à des fins de stockage. Bien qu'efficace, cette approche présentait des inconvénients :

* Il stockait les données sous forme de chaîne unique, limitant la normalisation de la base de données.
* La validation était moins précise que celle des sous-formulaires structurés.
* Joomla 4 a officiellement rendu obsolète les champs répétables, nécessitant une nouvelle solution.

<a id="new-approach"></a>
### Nouvelle approche

[00:01:13](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h01m13s)

La nouvelle structure **SubForm** :

* Crée des **tables dédiées** pour des ensembles de données précédemment répétables.
* Améliore la **validation des données** et l'**intégrité**.
* Réduit le **poids de chargement des pages** en traitant des données complexes via des structures relationnelles.

Ce changement a nécessité l'ajout d'environ **neuf nouvelles tables de base de données** pour prendre en charge la nouvelle architecture.

---

<a id="2-impact-scope---only-the-component-area"></a>
## **2. Portée de l'impact - Uniquement la zone du composant**

[00:02:03](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h02m03s)

La restructuration affecte principalement la **Zone des composants Joomla**. Cependant, comme JCB est très dynamique et interconnecté, l’impact s’étend à plusieurs autres domaines qui dépendent de ces structures de données. Le processus de mise à niveau garantit la compatibilité sur l’ensemble du système.

---

<a id="3-compiler-and-package-importexport-upgrades"></a>
## **3. Mises à niveau du compilateur et de l'importation/exportation de packages**

[00:02:20](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h02m20s)

Les systèmes **Compiler** et **Package Import/Export** ont été mis à niveau pour s'aligner sur le nouveau modèle de données SubForm. Toutes les actions d'import/export gèrent désormais les données de manière plus fiable.

**Les résultats des tests** montrent une transition fluide avec une intervention minimale de l'utilisateur nécessaire. Les utilisateurs effectuant une mise à niveau à partir d'anciennes versions ne devraient subir aucune perte ni corruption de données.

---

<a id="4-clear-browser-cache-and-memory"></a>
## **4. Effacer le cache et la mémoire du navigateur**

[00:02:47](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h02m47s)

Après la mise à niveau :

* **Effacez le cache et la mémoire de votre navigateur**.
  Le code JavaScript résiduel de l'ancien système de champs répétables peut entrer en conflit avec les nouveaux scripts.
* Effacez l'**historique du navigateur** spécifique à votre domaine JCB si vous préférez ne pas effacer tout l'historique.

Cela garantit que les nouveaux scripts se chargent correctement, évitant ainsi tout problème d'interface utilisateur ou de fonctionnalité.

---

<a id="5-dynamic-get-builder-conflicts"></a>
## **5. Conflits dynamiques avec le générateur GET**

[00:03:29](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h03m29s)

Certains utilisateurs peuvent rencontrer des problèmes temporaires avec la **zone GET dynamique**, qui récupère les données de manière dynamique à partir des vues d'administration.

Si cette fonctionnalité ne fonctionne pas comme prévu :

1. Effacez la **mémoire du navigateur**.
2. Rechargez la page et réessayez.
   La plupart des problèmes sont dus à des conflits JavaScript mis en cache et non à des bugs du système.

---

<a id="6-upgrading-via-joomlas-management-area"></a>
## **6. Mise à niveau via la zone de gestion de Joomla**

[00:05:13](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h05m13s)

Pour effectuer la mise à niveau :

1. Accédez à **Composants → Générateur de composants Joomla → Mises à jour**.
2. Confirmez que la mise à jour **v2.6.0** est disponible.
3. Cliquez sur **Mettre à jour**.
4. Une fois terminé, retournez à JCB et vérifiez qu'il affiche **"à jour."**

Aucune étape de migration manuelle n'est nécessaire : le processus de mise à niveau gère automatiquement les conversions.

---

<a id="7-editing-components-after-upgrade"></a>
## **7. Modification des composants après la mise à niveau**

[00:06:09](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h06m09s)

Bien que la disposition de la zone d'édition de composants reste familière, les modèles d'interaction ont changé.

<a id="key-ui-updates"></a>
### Mises à jour clés de l'interface utilisateur

* **Les éditeurs modaux** (utilisés pour les mises à jour, les vues, etc.) sont désormais remplacés par des **vues dédiées**.
* Lors de la modification des mises à jour, des vues d'administration ou des vues de site, JCB les ouvrira en vues pleine page pour un meilleur contrôle.
* Vous serez invité à enregistrer toutes les modifications avant de changer de vue.

Cela améliore la stabilité et la précision de l’édition dans plusieurs domaines.

---

<a id="8-contributors-and-component-files"></a>
## **8. Contributeurs et fichiers de composants**

[00:07:00](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h07m00s)

* **Contributeurs** : désormais modifiables directement dans la page principale du composant.
* **Fichiers et dossiers de composants** :
  Ceux-ci ont été déplacés vers une **table commune**, améliorant les performances et simplifiant la gestion des fichiers.
  Utilisez le bouton « Modifier les fichiers/dossiers du composant » pour gérer directement ces ressources.

---

<a id="9-admin-views---new-tab"></a>
## **9. Vues d'administration - Nouvel onglet**

[00:07:42](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h07m42s)

Les **Vues d'administration** ont désormais leur **propre onglet dédié** et peuvent être modifiées directement à partir du composant.

Des boutons tels que :

* **Modifier les vues d'administration des composants**
* **Vue d'administration liée - Modifier**

vous permettent d'accéder et de modifier instantanément les vues d'administration sans revenir à la liste principale des composants.

Lors des mises à niveau, JCB vérifie automatiquement dans chaque vue les anciens formats de champ et les convertit vers la nouvelle présentation de sous-formulaire. Si une vue n'a pas été ouverte ou compilée depuis la mise à niveau, vous pouvez déclencher ce processus manuellement :

> Allez dans **Compilateur → Compiler le composant**
> JCB analysera à nouveau tous les champs et appliquera les conversions de format nécessaires.

---

<a id="10-new-feature---translation-checker"></a>
## **10. Nouvelle fonctionnalité - Vérificateur de traduction**

[00:09:19](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h09m19s)

Un **Vérificateur de traduction** (Système d'avertissement) a été introduit pour faciliter la gestion des composants multilingues.

<a id="how-it-works"></a>
### Comment ça marche

* Compte le nombre total de chaînes de langue dans votre composant.
* Indique combien sont traduits pour chaque vue :

* Vue administrateur
  * Vue du système d'administration
  * Vue du site
* Affiche la progression de l'achèvement pour chaque langue.

Cet outil s'active uniquement lorsque **les langues sont configurées** et que le composant a été compilé **au moins une fois**.

---

<a id="11-translation-and-backup-configuration"></a>
## **11. Configuration de traduction et de sauvegarde**

[00:10:48](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h10m48s)

Si vous recevez un message concernant le **dossier de sauvegarde**, cela signifie probablement que les répertoires **Sauvegarde** et **Temporaire** sont identiques.
Il ne s'agit **pas d'une erreur**, mais d'une **mauvaise configuration**.
Pour le réparer :

1. Accédez aux **Options → Chemins des dossiers** de JCB.
2. Définissez un chemin distinct pour le **Dossier de sauvegarde**.

---

<a id="12-adjusting-translation-requirements"></a>
## **12. Ajustement des exigences de traduction**

[00:11:39](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h11m39s)

Vous pouvez définir le **seuil de pourcentage** pour l'achèvement de la traduction avant que JCB ne signale les traductions manquantes :

* Par défaut : **50 %**
* Pour ajuster : accédez à **Options → Traductions → Exigence d'achèvement**

Cela permet aux équipes de contrôler quand une traduction est considérée comme suffisamment complète.

---

<a id="13-final-notes-and-best-practices"></a>
## **13. Notes finales et meilleures pratiques**

[00:12:18](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h12m18s)

* Effacez toujours la mémoire du navigateur après la mise à niveau.
* Si vous rencontrez des problèmes, **signalez-les sur GitHub** avec les détails de votre navigateur et de la version JCB.
* Depuis la version 2.6.0, les **Champs répétables ont été entièrement remplacés par des sous-formulaires**, rendant JCB plus compatible, efficace et évolutif.

<a id="productivity-enhancements"></a>
### Améliorations de la productivité

[00:13:19](https://www.youtube.com/watch?v=MQrLBYhvGyA&t=00h13m19s)
Vous pouvez désormais :

* Accédez directement aux **zones découplées** (par exemple, vues d'administration, tableaux de bord) via des boutons de raccourci.
* Modifiez les structures de base sans naviguer dans la zone principale des composants.

---

<a id="summary"></a>
## **Résumé**

| Zone | Changement | Avantage |
| -------------------- | ---------------------- | ------------------------------------------------ |
| Champs répétables | Remplacé par des sous-formulaires | Meilleure structure des données et compatibilité Joomla 4 |
| Compilateur | Mis à jour | Gestion fluide de la nouvelle architecture |
| GET dynamique | Raffiné | Moins de conflits avec les vues d'administration |
| Vérificateur de traduction | Nouvelle fonctionnalité | Suivre et gérer les progrès linguistiques |
| Vues d'administration | Séparé dans son propre onglet | Accès plus facile et édition directe |
| Contributeurs & Fichiers | Nouvelle table commune | Gestion simplifiée et optimisée |

---

<a id="upgrade-complete"></a>
### **Mise à niveau terminée**

Votre installation Joomla Component Builder devrait désormais fonctionner avec **SubForms**, des performances optimisées et de nouveaux outils de gestion de traduction.
Si tous les champs et relations semblent corrects, votre mise à niveau vers **JCB v2.6.0** a réussi.

---

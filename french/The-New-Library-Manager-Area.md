> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="managing-libraries-dynamically-in-jcb"></a>
# Gestion dynamique des bibliothèques dans JCB

[00:00:00](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

Ce didacticiel explique la nouvelle zone **Library Manager** de Joomla Component Builder (JCB), qui introduit une manière dynamique, flexible et centralisée de gérer les bibliothèques JavaScript et CSS telles que Bootstrap, UiKit et FooTable. L'implémentation améliorée simplifie la façon dont les bibliothèques sont ajoutées et liées aux composants et aux vues.

---

<a id="1-understanding-libraries-in-jcb"></a>
## 1. Comprendre les bibliothèques dans JCB

Les bibliothèques sont des frameworks ou des outils externes qui améliorent vos composants Joomla.
Auparavant, JCB prenait en charge trois bibliothèques prédéfinies (**UiKit**, **FooTable** et **No Library**) qui pouvaient être basculées via les options « Ajouter UiKit » et « Ajouter FooTable » dans les paramètres du composant.

Désormais, avec **Library Manager**, les bibliothèques sont gérées de manière dynamique et liées directement à des **vues** spécifiques, ce qui permet une plus grande flexibilité et une réutilisation entre les composants.

---

<a id="2-how-it-used-to-work"></a>
## 2. Comment ça fonctionnait

[00:00:53](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m53s)

Dans les versions antérieures, les bibliothèques étaient ajoutées globalement dans les paramètres des composants.
Par exemple, les développeurs pourraient choisir d'inclure UiKit ou FooTable globalement et spécifier les versions préférées.

Cependant, cette méthode était limitée. L'ajout d'une nouvelle bibliothèque nécessitait la création d'un dossier dans :

```
administrator/components/com_componentbuilder/custom/
```

Vous placerez ensuite manuellement les fichiers de bibliothèque (par exemple, Bootstrap) dans un dossier personnalisé et actualiserez la configuration du composant. Ces fichiers ont ensuite été copiés dans le répertoire multimédia lors de la compilation.

Cette approche a fonctionné mais a nécessité une configuration manuelle et des efforts dupliqués pour chaque composant.

---

<a id="3-introducing-the-dynamic-library-feature"></a>
## 3. Présentation de la fonctionnalité de bibliothèque dynamique

[00:01:34](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m34s)

La nouvelle option **Dynamique** modifie la façon dont les bibliothèques sont gérées.
Au lieu d'attribuer globalement des bibliothèques à tous les composants, vous pouvez désormais lier les bibliothèques directement à des **vues spécifiques**.

En définissant une bibliothèque sur *Dynamique*, l'inclusion globale est désactivée et JCB détermine automatiquement quelles bibliothèques sont requises en fonction des vues liées au composant.

---

<a id="4-the-library-manager-interface"></a>
## 4. L'interface du gestionnaire de bibliothèque

[00:05:43](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m43s)

Ouvrez la section **Bibliothèques** dans JCB.
Vous trouverez plusieurs bibliothèques prédéfinies :

* **Amorçage 4**
* **UiKit 2**
* **UiKit 3**
* **Tableau de bas de page 2**
* **Tableau de bas de page 3**
* **Pas de bibliothèque**

Ces bibliothèques de base ne doivent pas voir leurs *noms* ou *types* modifiés, mais leur **comportement** et leurs sources de fichiers peuvent être configurés.

---

<a id="5-configuring-library-behavior"></a>
## 5. Configuration du comportement de la bibliothèque

[00:06:44](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m44s)

Chaque bibliothèque dispose de **comportements de fichiers** configurables qui contrôlent la manière dont ses éléments sont ajoutés :

* **Toujours ajouter** - incluez toujours ces fichiers.
* **Local (Get)** - téléchargez et incluez les fichiers localement pendant la compilation.
* **Conditions** - inclut les fichiers uniquement lorsque des conditions spécifiques sont remplies (en cours de développement).
* **Script personnalisé** - écrivez votre propre logique PHP pour inclure des fichiers de manière dynamique.
* **Ne pas ajouter** - exclut complètement les fichiers.

Vous pouvez basculer entre les liens CDN et les fichiers locaux en modifiant le champ **Type** de « Lien » à « Local ».
Lors de la compilation, JCB télécharge et intègre automatiquement les fichiers nécessaires.

---

<a id="6-adding-files-and-folders-to-libraries"></a>
## 6. Ajout de fichiers et de dossiers aux bibliothèques

[00:07:32](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m32s)

Les fichiers peuvent être ajoutés à partir de la même zone **Fichiers et dossiers personnalisés** que celle utilisée dans les anciennes versions de JCB, mais celle-ci est désormais gérée **par bibliothèque** au lieu de par composant.
Une fois configurés, ces fichiers sont automatiquement inclus dans toutes les vues liées à cette bibliothèque, garantissant ainsi la cohérence et un gain de temps.

---

<a id="7-using-configuration-fields-and-conditions"></a>
## 7. Utilisation des champs et des conditions de configuration

[00:09:17](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m17s)

Des conditions sont en cours d'élaboration, mais leur objectif est de permettre l'inclusion sélective de fichiers basés sur des **champs de configuration des composants**.

Tu peux:

1. Créez des champs de configuration personnalisés dans JCB.
2. Liez-les à une bibliothèque à l'aide de « Library Config ».
3. Utilisez ces champs pour basculer dynamiquement entre des fichiers spécifiques pendant l'exécution.

Par exemple, un champ radio « Utiliser Bootstrap » pourrait déterminer si des scripts Bootstrap sont ajoutés à la page.

---

<a id="8-writing-custom-scripts"></a>
## 8. Écrire des scripts personnalisés

[00:12:10](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m10s)

Le comportement **Custom Script** vous permet de définir comment et quand les fichiers de bibliothèque sont chargés à l'aide de PHP.
Par exemple, vous pouvez remplacer les noms de composants de manière dynamique ou ajuster les chemins de fichiers lors de la compilation.

Lorsque JCB compile le composant, il détecte automatiquement les types de fichiers `.css` et `.js` et les place dans les répertoires appropriés.

Cela donne aux développeurs un contrôle total pour écrire des inclusions logiques et étendre les fonctionnalités de la bibliothèque au-delà des liaisons statiques.

---

<a id="9-linking-libraries-to-views"></a>
## 9. Lier les bibliothèques aux vues

[00:14:50](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m50s)

Pour utiliser une bibliothèque dans votre composant :

1. Accédez à **Vues du site**.
2. Ouvrez une vue spécifique (par exemple, « Looks »).
3. Sélectionnez une bibliothèque telle que **Bootstrap v4** dans la liste déroulante Bibliothèque.

Une fois sélectionnés, JCB filtre les **Snippets** disponibles pour correspondre à cette bibliothèque.
Cela garantit que seuls les extraits pertinents (comme les alertes Bootstrap) sont disponibles pour l'insertion.

---

<a id="10-installing-library-snippets"></a>
## 10. Installation d'extraits de bibliothèque

[00:15:19](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m19s)

Vous pouvez importer des extraits de code pour chaque bibliothèque directement depuis les référentiels communautaires :

1. Cliquez sur **Init** dans la barre d'outils Extraits.
2. Choisissez le référentiel et la bibliothèque à partir desquels vous souhaitez extraire (par exemple, Bootstrap v4 dans le catalogue de la communauté).
3. Sélectionnez des extraits individuels ou utilisez les outils de sélection groupée pour importer tout ce qui est nouveau ou mis à jour.

Les extraits installés apparaîtront alors sous la liste des extraits de cette bibliothèque, prêts à être utilisés dans vos vues.

---

<a id="11-creating-library-bundles"></a>
## 11. Création de bundles de bibliothèques

[00:18:04](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h18m04s)

Lorsque vous devez utiliser plusieurs bibliothèques ensemble (par exemple, UiKit 2 et UiKit 3), créez un **Bundle** :

1. Cliquez sur **Nouveau** dans le gestionnaire de bibliothèque.
2. Choisissez **Bundle** comme type.
3. Sélectionnez les bibliothèques à inclure (par exemple, UiKit 2 et UiKit 3).
4. Ajoutez toute configuration personnalisée ou tout script selon vos besoins.
5. Enregistrez le paquet.

Cela permet à un seul bundle de charger plusieurs bibliothèques de manière conditionnelle ou simultanée, en fonction de la logique de votre script.

---

<a id="12-using-custom-script-behavior-with-bundles"></a>
## 12. Utilisation du comportement de script personnalisé avec des bundles

[00:21:19](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h21m19s)

Dans un bundle, vous pouvez écrire une logique basée sur PHP à l'aide des paramètres de composant pour déterminer quels fichiers de bibliothèque sont chargés.
Ces paramètres sont accessibles via `$this->params` dans le code PHP.
Vous pouvez vérifier les valeurs des paramètres et inclure des fichiers de manière conditionnelle en fonction des champs de configuration.

Cela permet des scénarios complexes, tels que le basculement entre les versions d'UiKit ou le chargement de Bootstrap uniquement sous certaines options de composants.

---

<a id="13-compiling-components-with-linked-libraries"></a>
## 13. Compilation de composants avec des bibliothèques liées

[00:27:02](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h27m02s)

Lorsque vous compilez votre composant, JCB automatiquement :

* Télécharge tous les fichiers marqués comme **Local (Get)**.
* Insère correctement les chemins de fichiers dans le code de votre composant.
* Ajoute des références de bibliothèque aux vues et mises en page qui ont été liées.

Vous pouvez vérifier la sortie en vérifiant le répertoire `/media/com_yourcomponent/` compilé.

---

<a id="14-linking-libraries-to-views-templates-and-layouts"></a>
## 14. Lier les bibliothèques aux vues, aux modèles et aux mises en page

[00:28:15](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h28m15s)

Pour garantir qu'une bibliothèque est disponible dans un contexte spécifique, vous devez la lier explicitement à celui-ci :

* **Vue du site**
* **Vue d'administration personnalisée**
* **Modèle**
* **Mise en page**

Chaque vue ou mise en page peut être associée à plusieurs bibliothèques, voire à un ensemble, en fonction de vos exigences de conception.

---

<a id="15-compatibility-with-older-implementations"></a>
## 15. Compatibilité avec les anciennes implémentations

[00:29:01](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h29m01s)

L'ancienne implémentation de bibliothèque dans **Libs & Helpers** fonctionne toujours pour une compatibilité ascendante.
Si vous définissez un composant sur « Ajouter UiKit 2 et 3 » ou « Ajouter FooTable 2 », JCB continue de les gérer globalement.
Toutefois, la méthode **Dynamique** est recommandée pour les nouveaux composants, car elle vous offre un contrôle plus précis et une meilleure évolutivité.

---

<a id="16-conclusion"></a>
## 16. Conclusion

[00:30:19](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h30m19s)

Le **Library Manager** de JCB offre un moyen robuste et modulaire de gérer les bibliothèques externes.
Vous pouvez désormais :

* Liez les bibliothèques directement aux vues.
* Définir des comportements ou des conditions personnalisés.
* Créez des paquets réutilisables.
* Importez et partagez des extraits via la communauté.

Ce système dynamique réduit la duplication, simplifie la maintenance et améliore la flexibilité du développement de composants Joomla.

---

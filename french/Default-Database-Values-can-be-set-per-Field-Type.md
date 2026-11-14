> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="default-database-values-can-be-set-per-field-type"></a>
# Les valeurs de base de données par défaut peuvent être définies par type de champ

Ce guide explique comment utiliser la nouvelle fonctionnalité Joomla Component Builder (JCB) qui vous permet de définir des **valeurs de base de données par défaut** pour des types de champs spécifiques. Cette amélioration rationalise le développement de composants en appliquant automatiquement les paramètres de base de données couramment utilisés chaque fois que vous créez un nouveau champ du même type.

---

<a id="overview"></a>
## Aperçu

Lors de la création de champs dans JCB, les développeurs réutilisent souvent des configurations de base de données similaires pour les mêmes types de champs (par exemple, `VARCHAR(255)` pour les champs de texte ou `INT(11)` pour les nombres). Auparavant, ces valeurs devaient être définies manuellement pour chaque nouveau champ, ce qui pouvait s'avérer répétitif et prendre beaucoup de temps.

Pour résoudre ce problème, JCB vous permet désormais de définir des **valeurs de base de données par défaut par type de champ**. Une fois définies, ces valeurs par défaut sont automatiquement renseignées chaque fois que vous sélectionnez ce type de champ lors de la création du champ.

> **Remarque :** Cette fonctionnalité n'est **pas active par défaut**. Vous devez définir manuellement les valeurs par défaut pour chaque type de champ que vous souhaitez normaliser.

---

<a id="step-by-step-guide"></a>
## Guide étape par étape

<a id="1-creating-a-field"></a>
### 1. Créer un champ

[00:00:16](https://www.youtube.com/watch?v=wGFqV63KzeA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m16s)

1. Dans votre interface Joomla Component Builder, accédez à **Champs** et cliquez sur **Nouveau**.
2. Choisissez le **Type de champ** souhaité - par exemple, `Text` ou `List`.
3. Configurez les **propriétés** comme d'habitude :

* Définir l'étiquette
   * Définir les options (le cas échéant)
   * Supprimez tous les paramètres inutilisés

Normalement, vous définiriez désormais les **Valeurs de la base de données** manuellement à chaque fois. Avec cette nouvelle amélioration, cette étape peut désormais être automatisée.

---

<a id="2-understanding-the-default-database-values"></a>
### 2. Comprendre les valeurs par défaut de la base de données

[00:00:43](https://www.youtube.com/watch?v=wGFqV63KzeA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m43s)

Même si vous utilisiez la même structure de base de données pour un type de champ donné, JCB exigeait auparavant la saisie de ces paramètres pour chaque nouveau champ. La nouvelle fonctionnalité vous permet de définir une **valeur par défaut unique** qui sera automatiquement renseignée pour ce type de champ.

Cela permet de standardiser votre schéma de base de données sur plusieurs champs et composants, tout en réduisant les travaux de configuration répétitifs.

---

<a id="3-enabling-and-setting-default-database-values"></a>
### 3. Activation et définition des valeurs de base de données par défaut

[00:01:20](https://www.youtube.com/watch?v=wGFqV63KzeA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m20s)

Pour configurer les valeurs par défaut :

1. Ouvrez la zone **Types de champs** dans JCB.
2. Sélectionnez le type de champ que vous souhaitez modifier, par exemple `Number`.
3. Dans la section **Valeurs de la base de données**, entrez votre configuration préférée.

**Exemple :**
Pour un champ "Numéro" :

```text
Type: INT
Length: 11
Null: No
Default: 0
```

Cliquez sur **Enregistrer** pour stocker votre configuration.

Désormais, chaque fois que vous créez un nouveau champ de type « Numéro », ces valeurs de base de données apparaîtront automatiquement.

---

<a id="4-testing-the-defaults"></a>
### 4. Test des valeurs par défaut

[00:01:49](https://www.youtube.com/watch?v=wGFqV63KzeA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m49s)

Pour vérifier que vos paramètres par défaut fonctionnent :

1. Créez un **nouveau champ**.
2. Sélectionnez le type de champ que vous avez configuré (par exemple, `Number`).
3. Observez que les valeurs de la base de données sont automatiquement remplies avec vos valeurs par défaut.

Vous pouvez toujours les modifier pour des cas particuliers, mais la configuration de base est déjà en place, ce qui permet de gagner du temps et d'assurer la cohérence.

---

<a id="5-applying-defaults-to-other-field-types"></a>
### 5. Application des valeurs par défaut à d'autres types de champs

[00:02:28](https://www.youtube.com/watch?v=wGFqV63KzeA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m28s)

Vous pouvez répéter la même configuration pour d'autres types de champs. Par exemple:

| Type de champ | Type de base de données typique | Exemple par défaut |
| ------------- | ------------------------------------ | --------------- |
| **Téléphone** | `VARCHAR` | `VARCHAR(64)` |
| **Texte** | `VARCHAR` | `VARCHAR(255)` |
| **Entier** | `INT` | `INT(11)` |
| **Date** | `DATETIME` | `NULL` |

En définissant ces normes une seule fois, votre processus de création de champs devient beaucoup plus efficace et cohérent.

---

<a id="6-example-workflow"></a>
### 6. Exemple de flux de travail

[00:02:54](https://www.youtube.com/watch?v=wGFqV63KzeA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m54s)

Prenons les exemples `Telephone` et `Text` :

* Pour **Téléphone**, définissez le type de base de données sur `VARCHAR(64)`.
* Pour **Texte**, définissez le type de base de données sur `VARCHAR(255)`.

Une fois enregistrées, ces configurations s'appliquent automatiquement à chaque fois que vous créez de nouveaux champs de ces types.

---

<a id="tips-and-best-practices"></a>
## Conseils et bonnes pratiques

* **Gardez la cohérence :** Définissez des valeurs par défaut standard et raisonnables qui reflètent la façon dont vous utilisez généralement chaque type de champ.
* **Utilisez les conventions de dénomination :** Faites correspondre les types de bases de données aux attentes des champs Joomla (par exemple, `INT` pour les valeurs numériques, `VARCHAR` pour le texte court).
* **Vérifiez avant d'enregistrer :** Les valeurs par défaut s'appliquent globalement par type de champ - vérifiez votre configuration avant d'enregistrer.
* **Remplacer si nécessaire :** Vous pouvez toujours personnaliser les valeurs de la base de données dans des champs individuels lorsque des exceptions surviennent.

---

<a id="conclusion"></a>
## Conclusion

[00:03:13](https://www.youtube.com/watch?v=wGFqV63KzeA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m13s)

Cette fonctionnalité facilite le maintien d'un **flux de travail cohérent et efficace** lors de la conception de composants dans Joomla Component Builder. La définition de **valeurs de base de données par défaut par type de champ** élimine les tâches de configuration répétitives et garantit que les structures de votre base de données restent uniformes sur tous les composants.

En prenant quelques minutes pour configurer vos types de champs les plus utilisés, vous pouvez accélérer considérablement le développement de composants dans JCB.

---

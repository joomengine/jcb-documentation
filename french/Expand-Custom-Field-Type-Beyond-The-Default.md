> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="expand-custom-field-type-beyond-the-default"></a>
# Développez le type de champ personnalisé au-delà de la valeur par défaut

> *Tutoriel de documentation horodatée basé sur JCB*
> *Référence vidéo : [YouTube Tutorial - Expand Custom Field Type Beyond the Default](https://www.youtube.com/watch?v=Mu9H0zgH9Lw)*

---

<a id="1-introduction"></a>
## 1. Introduction

**[00:00:00](https://www.youtube.com/watch?v=Mu9H0zgH9Lw&t=0s)**
Ce didacticiel présente une nouvelle option intéressante disponible dans **Joomla Component Builder (JCB) version 2.9.3 (bêta)**.
Il vous permet d'étendre les **types de champs personnalisés** directement dans JCB - **sans modifier les fichiers principaux de Joomla**.

Auparavant, l'extension des types de champs de Joomla nécessitait des modifications manuelles du répertoire `/libraries/joomla/form/fields`. Avec cette mise à jour, vous pouvez créer de nouveaux types de champs en utilisant uniquement l'interface JCB.

---

<a id="2-understanding-jcbs-field-type-system"></a>
## 2. Comprendre le système de type de champ de JCB

**[00:00:36 → 00:02:15]**
Dans JCB, la liste **Field Type** inclut tous les types de champs principaux de Joomla.
Parmi ceux-ci se trouve le type de champ **Personnalisé** - une option flexible et dynamique capable d'étendre :

* `List`
* `Radio`
* `Checkbox`

Le type de champ **Personnalisé** sert de base à la création de nouveaux types de champs spécialisés.

Avec la version 2.9.3, JCB ajoute la possibilité d'**étendre le champ personnalisé lui-même**, permettant une personnalisation plus approfondie *sans modifier le noyau.*

---

<a id="3-joomla-field-file-structure"></a>
## 3. Structure des fichiers de champs Joomla

**[00:02:48 → 00:04:59]**
Pour comprendre comment cela fonctionne, regardez les définitions de champs de Joomla :

```
administrator/
└── components/
    └── libraries/
        └── joomla/
            └── form/
                └── fields/
```

Chaque fichier de ce dossier (comme `list.php`, `radio.php`, etc.) étend un champ de formulaire Joomla de base (par exemple `JFormFieldList`, `JFormFieldRadio`).

Vous pouvez afficher des méthodes telles que `getLabel()` et `getInput()` dans ces classes.
Auparavant, en étendre un signifiait éditer ces fichiers directement. JCB vous permet désormais de **répliquer et d'étendre** ces champs en toute sécurité dans le générateur.

---

<a id="4-field-types-vs-fields"></a>
## 4. Types de champs et champs

**[00:05:33 → 00:06:07]**

> 🔹 **Type de champ** - La structure ou le modèle d'un champ (par exemple, liste, radio, personnalisé).
> 🔹 **Field** - Une instance utilisée dans votre composant qui est construite sur un type de champ.

Cette distinction est essentielle lors de la personnalisation. Vous modifierez ou étendrez les *types de champs*, mais le résultat sera visible dans vos *champs* réels au sein des composants.

---

<a id="5-creating-a-new-custom-field-type"></a>
## 5. Création d'un nouveau type de champ personnalisé

**[00:07:13 → 00:09:35]**

<a id="step-1---open-the-custom-field-type"></a>
### Étape 1 - Ouvrez le type de champ personnalisé

Chez JCB :

* Accédez à **Composant → Types de champs**
* Ouvrez le type de champ **Personnalisé**.

<a id="step-2---define-the-name-with-"></a>
### Étape 2 - Définissez le "Nom" avec `@`

Donnez à votre champ un nom unique en utilisant un symbole **`@`**.
Voici comment JCB identifie les types de champs personnalisés qui en étendent d'autres :

```
list@mine
```

L'emplacement de `@` peut être n'importe où dans le nom (début, milieu ou fin).

> **Remarque :** Sans le `@`, JCB le traitera comme un type de champ standard et non comme une extension personnalisée.

<a id="step-3---keep-required-properties"></a>
### Étape 3 - Conserver les propriétés requises

Vous devez conserver les valeurs clés :

* **Type** - Doit rester unique (par exemple, `mylist`)
* **Extends** - Définit le type de champ Joomla dont il hérite (`list`, `radio`, etc.)
* **Étiquette**, **Nom** et **Description** peuvent être personnalisés.

Évitez d'utiliser directement des noms de types réservés comme `list` ou `radio` - ils existent déjà.

---

<a id="6-php-field-array-and-dynamic-code-segments"></a>
## 6. Tableau de champs PHP et segments de code dynamique

**[00:11:04 → 00:13:50]**
Chaque ligne de l'**éditeur PHP de type de champ personnalisé** représente une ligne de code.

JCB fournit jusqu'à **16 espaces réservés de segments de code PHP** (`typephp`, `typephp_a`, `typephp_b`, … `typephp_x`).
Ces segments vous permettent d'injecter PHP dans différentes parties logiques de votre classe de champ - par exemple :

* `typephp` → section PHP par défaut
* `typephp_a` → logique secondaire
* `typephp_b` → méthode ou bloc alternatif

Cette flexibilité permet d'insérer du code dans plusieurs parties de votre classe de champ (par exemple, `getInput`, `getOptions`, `addOptions`).

---

<a id="7-example-extending-list-field-type"></a>
## 7. Exemple : Extension du type de champ `List`

**[00:14:17 → 00:22:46]**

Pour illustrer cela, le didacticiel crée un champ appelé **`list@mine`**, étendant le champ Liste de Joomla.

<a id="step-by-step"></a>
### Étape par étape :

1. Ajoutez de nouvelles lignes de code PHP pour définir une méthode telle que `getOptions()`.
2. Utilisez les identifiants **Type PHP** (`typephp_1`, `typephp_2`, etc.) pour chaque ligne.
3. Incluez des commentaires et des espaces réservés logiques pour plus de lisibilité.
4. Enregistrez le type de champ sous un nouveau nom (par exemple, **Mon champ de liste personnalisé**).

> **Conseil :** Lors de la création de types de champs réutilisables, conservez l'implémentation générique. Évitez de coder en dur les valeurs spécifiques au projet.

---

<a id="8-reusing-custom-field-types"></a>
## 8. Réutilisation des types de champs personnalisés

**[00:22:10 → 00:24:52]**
Une fois créé, votre nouveau type de champ peut être réutilisé sur plusieurs composants.
Assurer:

* C'est **Réglable** (coché)
* Non **Obligatoire** sauf si nécessaire
  Ensuite, **Enregistrez et fermez** pour finaliser le nouveau type de champ personnalisé.

---

<a id="9-adding-a-field-using-the-custom-type"></a>
## 9. Ajout d'un champ à l'aide du type personnalisé

**[00:24:52 → 00:27:17]**

1. Accédez à **Champs → Nouveau champ**
2. Sélectionnez votre nouveau type de champ (`list@mine`)
3. JCB charge automatiquement les paramètres associés et le modèle de code.
4. Ajustez le type de colonne de base de données (par exemple, `VARCHAR`) en fonction des données attendues.
5. Ajoutez à une vue administrateur (par exemple, *Vue administrateur de démonstration*) et attribuez sa position.

Ensuite, **Compilez** votre composant.

---

<a id="10-how-jcb-compiles-custom-field-types"></a>
## 10. Comment JCB compile les types de champs personnalisés

**[00:27:50 → 00:29:54]**

Lors de la compilation, JCB appelle la fonction
`setCustomFieldTypeFile()` dans le compilateur.

Cette fonction :

* Collecte tous les espaces réservés (comme `{component}`, `{table}`, `{view}`)
* Les remplace par les valeurs d'exécution réelles
* Fusionne les segments de code PHP dans un fichier généré
* Le produit dans le cadre de votre composant compilé

---

<a id="11-testing-the-new-field"></a>
## 11. Tester le nouveau champ

**[00:29:54 → 00:31:01]**
Après l'installation :

* Accédez à votre composant dans le backend de Joomla.
* Créez un nouvel élément dans la vue où vous avez placé le champ personnalisé.
  Si vous voyez votre nouvelle structure d'étiquette et de champ, la compilation a réussi.
  Si du HTML ou des options sont manquants, assurez-vous que votre code PHP renvoie une sortie HTML ou un tableau d'options approprié.

---

<a id="12-improving-and-expanding-your-field"></a>
## 12. Améliorer et élargir votre domaine

**[00:31:01 → 00:33:53]**
Vous pouvez affiner votre champ en :

* Ajout de lignes de code PHP supplémentaires pour plus de lisibilité.
* Renvoi de tableaux HTML structurés ou d'options.
* Test dynamique des espaces réservés (`{component}`, `{table}`, `{id}`, etc.).

Exemple présenté : ajout de **Option 1** et **Option 2** simples à la sortie du champ pour démontrer que `getOptions()` renvoie des valeurs dynamiques.

> Astuce : conservez toujours `extends` défini (par exemple, `list`) - cela détermine l'héritage.

---

<a id="13-placeholder-replacement-system"></a>
## 13. Système de remplacement d'espace réservé

**[00:37:21 → 00:41:22]**
Les espaces réservés (par exemple, `#component#`, `#table#`, `{id}`, `{text}`) sont remplacés dynamiquement lors de la compilation.
Ils sont définis dans le **replace array** du compilateur et correspondent aux définitions de **table**, **component** et **field** dans JCB.

Vous pouvez afficher ou vider ce tableau de remplacement pour inspecter les espaces réservés disponibles.

---

<a id="14-final-notes"></a>
## 14. Notes finales

**[00:42:04 → 00:42:44]**

* Ajoutez toujours un `@` dans le nom de votre champ pour vous assurer que JCB le reconnaît comme personnalisé.
* Vous pouvez commencer par dupliquer le **champ personnalisé par défaut**, le renommer et le développer à partir de là.
* Ne modifiez jamais directement le noyau `/libraries/joomla/form/fields` de Joomla.
* JCB générera en toute sécurité de nouveaux fichiers de champs PHP sous votre composant lors de la compilation.

---

<a id="summary"></a>
## Résumé

| Concepts | Descriptif |
| -------------------- | ---------------------------------------------------- |
| **Version requise** | JCB 2.9.3 bêta ou version ultérieure |
| **Objectif** | Créez des types de champs personnalisés étendus sans modifications principales |
| **Champs de base** | Liste, Radio, Case à cocher (ou tout type de champ Joomla) |
| **Identifiant** | Doit contenir `@` (par exemple, `list@mine`) |
| **Rôle du compilateur** | Remplace les espaces réservés et crée des fichiers de champ de manière dynamique |
| **Réutilisable** | Oui - peut être utilisé sur plusieurs composants |
| **Meilleures pratiques** | Conserver le champ générique et bien commenté pour pouvoir le réutiliser |

---

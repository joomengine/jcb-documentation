> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="manage-a-components-global-config-option-field-in-relation-with-menu-params"></a>
# Gérer le champ d'option de configuration globale d'un composant en relation avec les paramètres de menu

<a id="overview"></a>
## Aperçu

Ce tutoriel explique comment **gérer les champs d'options de configuration globales** dans votre composant Joomla Component Builder (JCB) et comment ces mêmes champs peuvent être liés aux **paramètres de menu** pour des vues de site spécifiques.

Vous apprendrez :

* Comment les options globales sont liées aux options d'affichage du menu.
* Comment contrôler l'endroit où certains champs apparaissent - soit dans **Global Config**, **Menu Params** ou **les deux**.
* Comment utiliser la propriété `display` dans JCB pour attribuer dynamiquement la visibilité des champs.

---

<a id="1-understanding-global-configuration-options"></a>
## 1. Comprendre les options de configuration globales

**[00:00:18](https://www.youtube.com/watch?v=dhVVQP4KS3Q&t=00h00m18s)**

Dans Joomla, les **Options de configuration globales** définissent les comportements par défaut de votre composant. Ceux-ci peuvent ensuite être remplacés par des **paramètres de menu** pour des éléments de menu individuels.

> Par exemple, vous souhaiterez peut-être qu'un paramètre apparaisse :
>
> * Uniquement dans la zone *Configuration globale* de votre composant.
> * Uniquement dans les paramètres d'un *élément de menu*.
> * Ou dans *les deux*.

JCB vous permet d'obtenir facilement cette distinction à l'aide d'une propriété `display`.

---

<a id="2-reviewing-existing-configuration-fields"></a>
## 2. Examen des champs de configuration existants

**[00:01:43](https://www.youtube.com/watch?v=dhVVQP4KS3Q&t=00h01m43s)**

Ouvrez votre composant dans JCB (par exemple, **Member Manager**) et localisez la zone **Global Config Fields**.

1. Accédez à votre composant dans **Composants** → **Member Manager**.
2. Observez les champs de configuration existants - ils sont utilisés à la fois dans les options de configuration et de menu du composant.
3. S'il n'en existe pas, cliquez sur **➕ (Ajouter un nouveau champ)** pour commencer.

Vous remarquerez que le comportement de chaque champ est largement déterminé par ses **propriétés supplémentaires**, que nous examinerons ensuite.

---

<a id="3-understanding-the-display-property"></a>
## 3. Comprendre la propriété `display`

**[00:04:31](https://www.youtube.com/watch?v=dhVVQP4KS3Q&t=00h04m31s)**

Chaque champ du Field Manager de JCB comporte une section *Propriétés supplémentaires*.
Une propriété clé est **`display`**, qui détermine où le champ apparaît :

| Valeur de la propriété | Le champ apparaît dans |
| ---------- | ---------------------------------- |
| *(vide)* | Configuration globale et paramètres de menu |
| `menu` | Paramètres de menu uniquement |
| `config` | Configuration globale uniquement |

> **Conseil :**
> Laisser `display` vide équivaut au comportement hérité : le champ apparaît dans les contextes Global et Menu.

Exemple:

```text
display = menu
```

Ce paramètre garantit que le champ est visible **uniquement** dans les paramètres du menu.

---

<a id="4-demonstration-field-visibility-control"></a>
## 4. Démonstration : Contrôle de la visibilité sur le terrain

**[00:05:10](https://www.youtube.com/watch?v=dhVVQP4KS3Q&t=00h05m10s)**

Lorsque la valeur `display` est définie sur **menu**, le champ n'apparaîtra **pas** dans la zone de configuration globale, mais **apparaîtra** sous les paramètres de menu d'une vue de site.

Si tu:

* Allez dans **Global Config** → votre composant → onglet *membres* → le champ ne sera pas visible.
* Allez dans **Menus** → *Ajouter un élément de menu* → sélectionnez la vue correspondante → le champ **est** visible.

Cela confirme le placement correct du champ.

---

<a id="5-creating-a-new-field-for-both-global-config-and-menu-params"></a>
## 5. Création d'un nouveau champ pour la configuration globale et les paramètres de menu

**[00:07:08](https://www.youtube.com/watch?v=dhVVQP4KS3Q&t=00h07m08s)**

Ajoutons un nouveau champ appelé **"Afficher le titre"**.

<a id="steps"></a>
### Étapes :

1. Accédez à **JCB → Champs → Nouveau**.
2. Définir :

* **Nom :** `show_title`
   * **Étiquette :** `Show Title`
   * **Type :** `Radio`
   * **Description :** "Sélectionnez si le titre doit être affiché."
   * **Options :** Oui / Non
   * **Par défaut :** `1` (Oui)
3. Laissez **`display`** vide pour le faire apparaître dans les zones de configuration et de menu.
4. Enregistrez le champ.

Ensuite, ajoutez ce champ à la **Global Config** de votre composant.

<a id="add-field-to-config-tab"></a>
### Ajouter un champ à l'onglet de configuration :

1. Ouvrez votre composant (par exemple, *Member Manager*).
2. Cliquez sur le bouton **Configuration globale (+)**.
3. Créez un onglet portant le même nom que la **vue du site** cible (par exemple, `cpanel`).
4. Ajoutez votre nouveau champ `show_title` à cet onglet.
5. Enregistrez et fermez.

Compilez et installez le composant pour appliquer les modifications.

---

<a id="6-verifying-the-field-in-joomla"></a>
## 6. Vérifier le champ dans Joomla

**[00:08:37](https://www.youtube.com/watch?v=dhVVQP4KS3Q&t=00h08m37s)**

Après l'installation :

* Ouvrez **Système → Configuration globale → Gestionnaire de membres**
  Vous verrez un onglet **Cpanel** avec le nouveau champ **Afficher le titre (Oui/Non)**.
* Créez ou modifiez un **élément de menu** lié à la vue du site de ce composant.
  Sous l'onglet **Member Manager**, le champ **Afficher le titre** apparaît également, comprenant une option pour *"Utiliser Global"*.

> Cela permet aux éléments de menu Joomla d'**hériter ou de remplacer** la valeur globale du composant.

---

<a id="7-restricting-a-field-to-global-config-only"></a>
## 7. Restreindre un champ à la configuration globale uniquement

**[00:09:33](https://www.youtube.com/watch?v=dhVVQP4KS3Q&t=00h09m33s)**

Pour faire apparaître un champ **uniquement dans Global Config** :

1. Modifiez le champ dans JCB → **Fields Manager**.
2. Sous *Propriétés supplémentaires*, définissez :

   ```text
   display = config
   ```3. Enregistrez, compilez et réinstallez le composant.

<a id="verify"></a>
### Vérifier:

* Le champ **disparaît** des paramètres des éléments de menu.
* Il **reste visible** dans la zone de configuration globale du composant.

---

<a id="8-restricting-a-field-to-menu-params-only"></a>
## 8. Restreindre un champ aux paramètres de menu uniquement

**[00:10:30](https://www.youtube.com/watch?v=dhVVQP4KS3Q&t=00h10m30s)**

Pour déplacer le champ exclusivement vers la **zone de menu** :

1. Modifiez à nouveau le même champ.
2. Définir :

   ```text
   display = menu
   ```3. Enregistrez, compilez et réinstallez.

Maintenant:

* Le champ est **uniquement visible dans Menu Params**.
* Il est **caché** sur l'écran Global Config.

> **Remarque :**
> Dans JCB version 2.9.15 et versions ultérieures, ce comportement a été corrigé pour supprimer correctement la référence "Global" lorsque le champ est uniquement menu.

---

<a id="9-field-naming--site-view-alignment"></a>
## 9. Dénomination des champs et alignement de la vue du site

**[00:12:02](https://www.youtube.com/watch?v=dhVVQP4KS3Q&t=00h12m02s)**

Lors de l'attribution de champs aux onglets de configuration, le **nom de l'onglet doit correspondre** au **nom de la vue du site**.

Pour trouver ça :

1. Accédez à **Vues du site** dans JCB.
2. Ouvrez la vue du site souhaitée (par exemple, `cpanel` ou `members`).
3. Utilisez la valeur **Nom** (et non le titre) comme **nom de l'onglet**.

Cela garantit que les paramètres de menu se connectent correctement à l’onglet d’affichage du site correspondant.

---

<a id="10-scope-and-behavior-notes"></a>
## 10. Notes sur la portée et le comportement

**[00:12:52](https://www.youtube.com/watch?v=dhVVQP4KS3Q&t=00h12m52s)**

* La propriété `display` s'applique uniquement aux **champs de configuration** qui appartiennent à un onglet correspondant à une vue de site.
* Cela n'affecte **pas** les **vues d'administrateur** ou les champs normaux des formulaires backend.
* Lorsqu'un champ est utilisé sur plusieurs composants, son comportement `display` reste cohérent dans chacun.

---

<a id="11-wrapping-up"></a>
## 11. Conclusion

**[00:14:18](https://www.youtube.com/watch?v=dhVVQP4KS3Q&t=00h14m18s)**

Vous avez maintenant appris à :

* Créer et configurer des champs globaux dans JCB.
* Contrôlez leur affichage entre Global Config et Menu Params à l'aide de la propriété `display`.
* Attribuez correctement les champs aux onglets qui correspondent aux noms de vue de votre site.

Si vous rencontrez des problèmes ou avez des demandes de fonctionnalités :

* Visitez le [Forum JCB](https://github.com/orgs/joomengine/discussions)
* Ou ouvrez un ticket sur [GitHub](https://github.com/vdm-io/Joomla-Component-Builder/issues)

---

<a id="summary-table"></a>
### **Tableau récapitulatif**

| Objectif | Paramètres `display` | Visible dans |
| ------------------ | ----------------- | ------------- |
| Les deux Global + Menu | *(vide)* | Les deux |
| Configuration globale uniquement | `config` | Configuration globale |
| Paramètres de menu uniquement | `menu` | Options des menus |

---

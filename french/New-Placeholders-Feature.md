> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="new-placeholders-feature-in-joomla-component-builder"></a>
# Nouvelle fonctionnalité d'espaces réservés dans le générateur de composants Joomla

---

<a id="introduction"></a>
## Introduction

*(Horodatage : [00:00:00](https://www.youtube.com/watch?v=USVLYu4ZLCc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m26s))*

Dans **JCB version 2.9.14**, une nouvelle fonctionnalité a été introduite : **Espaces réservés globaux et au niveau des composants**.
Cette fonctionnalité vous permet de définir et de réutiliser des espaces réservés de manière dynamique dans vos composants, améliorant ainsi la flexibilité, la réutilisabilité et la maintenabilité de votre code Joomla généré.

Avant de plonger dans la nouvelle fonctionnalité, il est important de comprendre le système d'espaces réservés existant de JCB.

---

<a id="existing-core-placeholders"></a>
## Espaces réservés existants (de base)

<a id="1-component-level-placeholders"></a>
### 1. Espaces réservés au niveau des composants

*(Horodatage : [00:00:26](https://www.youtube.com/watch?v=USVLYu4ZLCc&t=00h00m26s))*

JCB inclut déjà un ensemble d'**espaces réservés par défaut** que vous pouvez utiliser dans tout le système.
Les exemples incluent :

* `[[[component]]]` - Nom du composant en minuscules
* `[[[Component]]]` - Première lettre majuscule
* `[[[COMPONENT]]]` - Majuscules
* `###component###` - Enveloppé dans des hachages
* `<<<component>>>` - Enveloppé dans des équerres

Ces espaces réservés sont automatiquement remplacés lors de la compilation par le nom du composant correspondant au format correct.

---

<a id="2-view-level-placeholders"></a>
### 2. Espaces réservés au niveau de la vue

*(Horodatage : [00:02:02](https://www.youtube.com/watch?v=USVLYu4ZLCc&t=00h02m02s))*

De même, les **vues** ont leur propre ensemble d'espaces réservés. Selon l'endroit où ils sont utilisés (administrateur ou site), ils varient légèrement.

Les formes courantes incluent :

* `[[[view]]]`, `[[[View]]]`, `[[[VIEW]]]`
* `###view###`
* `[[[views]]]` - pour les vues de liste (pluriel)

**Note:**

* Dans le backend (zone d'administration), les espaces réservés tels que `view` et `views` correspondent aux vues **list** et **edit**.
* Dans la zone du site, les espaces réservés de vue commencent par un **S** minuscule ou majuscule (par exemple, `[[[SView]]]`), représentant le contexte du site.

---

<a id="introduction-of-custom-placeholders"></a>
## Introduction des espaces réservés personnalisés

*(Horodatage : [00:04:36](https://www.youtube.com/watch?v=USVLYu4ZLCc&t=00h04m36s))*

Le nouveau **Placeholder Manager** de JCB vous permet de définir **vos propres espaces réservés** dans l'interface graphique, offrant ainsi aux développeurs la même flexibilité que les extraits de code personnalisés, mais pour les **chaînes de texte** au lieu du code.

Contrairement au code personnalisé :

* Les espaces réservés n'utilisent **pas** d'éditeur de style IDE.
* Ils effectuent un **remplacement de chaîne sur place** lors de la compilation.
* Ils peuvent être appliqués globalement ou remplacés par composant.

---

<a id="using-the-placeholder-manager"></a>
## Utilisation du gestionnaire d'espaces réservés

*(Horodatage : [00:05:03](https://www.youtube.com/watch?v=USVLYu4ZLCc&t=00h05m03s))*

<a id="accessing-the-manager"></a>
### Accéder au gestionnaire

1. Dans JCB, accédez à **Placeholders** dans le menu d'administration.
2. Vous verrez une liste des espaces réservés existants. Si vous avez importé des composants, certains sont peut-être déjà définis ; sinon, la liste sera vide.

<a id="creating-a-new-placeholder"></a>
### Création d'un nouvel espace réservé

*(Horodatage : [00:05:29](https://www.youtube.com/watch?v=USVLYu4ZLCc&t=00h05m29s))*

1. Cliquez sur **Nouveau** pour créer un nouvel espace réservé.

2. Saisissez un **nom** - JCB le mettra automatiquement entre triples crochets, par exemple :

   ```
   [[[MyPlaceholder]]]
   ```

3. Dans le champ **Valeur**, saisissez la chaîne ou la variable que vous souhaitez remplacer.

* La valeur peut inclure :

* Signes dollar (`$`)
     * Supports (`[ ]`), croisillons (`{ }`)
     * Toute chaîne d'une seule ligne
   *Exemple :

     ```
     $myVariableName
     ```

4. JCB recherche automatiquement tous les composants pour détecter si cet espace réservé est déjà utilisé.

5. Cliquez sur **Enregistrer et fermer** pour finaliser.

> **Conseil :**
> Si la valeur de votre espace réservé provoque des erreurs (par exemple, en raison de caractères spéciaux), signalez-le sur GitHub : les espaces réservés sont conçus pour gérer presque tous les modèles de chaînes valides.

---

<a id="using-custom-placeholders-in-components"></a>
## Utilisation d'espaces réservés personnalisés dans les composants

*(Horodatage : [00:08:26](https://www.youtube.com/watch?v=USVLYu4ZLCc&t=00h08m26s))*

Une fois qu'un espace réservé est créé, il peut être inséré dans plusieurs zones : classes d'assistance, extraits de code personnalisés ou méthodes GET dynamiques.

<a id="example-adding-a-placeholder-to-a-helper-class"></a>
### Exemple : Ajout d'un espace réservé à une classe d'assistance

1. Ouvrez un composant (par exemple, `Anthropometry`).
2. Ajoutez votre espace réservé à la **Classe d'assistance**.

   ```php
   [[[AnyWord]]]
   ```3. Enregistrez et fermez.

Vous pouvez réutiliser le même espace réservé dans un autre composant (par exemple, `MedicalAid`).

Cela permet à la logique partagée ou aux extraits de code de s'ajuster dynamiquement en fonction des remplacements au niveau des composants.

---

<a id="advanced-example-combining-with-custom-code"></a>
## Exemple avancé : combinaison avec du code personnalisé

*(Horodatage : [00:09:17](https://www.youtube.com/watch?v=USVLYu4ZLCc&t=00h09m17s))*

Envisagez un **extrait de code personnalisé** réutilisable, comme une animation de chargeur JavaScript (`Little Dot Trick`).
Si plusieurs composants utilisent ce même extrait mais nécessitent un texte ou un comportement légèrement différent, vous pouvez y insérer des espaces réservés :

```javascript
console.log("[[[AnyWord]]]");
```

Ensuite, pour chaque composant :

* Remplacez l'espace réservé dans **Composant → Espaces réservés** :

*Pour un composant : `[[[AnyWord]]] = "not like the other"`
  *Pour un autre : `[[[AnyWord]]] = "default string"`

Lors de la compilation, JCB les remplace dynamiquement, garantissant ainsi des variations spécifiques aux composants sans dupliquer le code.

---

<a id="compiling-and-verifying"></a>
## Compilation et vérification

*(Horodatage : [00:12:43](https://www.youtube.com/watch?v=USVLYu4ZLCc&t=00h12m43s))*

Après avoir défini des espaces réservés :

1. Compilez vos composants (par exemple, `Anthropometry`, `Medical Aid`).
2. Installez-les sur votre site Joomla.
3. Ouvrez la **classe d'assistance** compilée ou l'**extrait de code personnalisé** dans l'EDI.
4. Vérifiez que les espaces réservés ont été remplacés par les valeurs correctes au niveau du composant ou globales.

Exemple:

* Dans `AnthropometryHelper`, `[[[AnyWord]]]` → "pas comme les autres"
* Dans `MedicalAidHelper`, `[[[AnyWord]]]` → chaîne globale

Cela confirme le succès du remplacement contextuel.

---

<a id="key-benefits-of-the-placeholder-system"></a>
## Avantages clés du système d'espace réservé

*(Horodatage : [00:15:09](https://www.youtube.com/watch?v=USVLYu4ZLCc&t=00h15m09s))*

* **Réutilisabilité dynamique** - Écrivez un extrait de code ou une logique de chaîne, réutilisez-le sur des composants présentant des différences contextuelles uniques.
* **Maintenance simplifiée** - Centralisez les mises à jour ; une définition d'espace réservé est mise à jour partout où elle est utilisée.
* **Remplacements au niveau des composants** - Comportement différent pour le même espace réservé entre les composants.
* **Intégration transparente** - Fonctionne dans les assistants, le code personnalisé, le GET dynamique ou toute zone de texte JCB.
* **Compatibilité multi-composants** - Parfait pour les grands projets avec des composants interdépendants (par exemple, l'exemple de projet principal "Coral").

---

<a id="conclusion"></a>
## Conclusion

*(Horodatage : [00:16:48](https://www.youtube.com/watch?v=USVLYu4ZLCc&t=00h16m48s))*

La **Nouvelle fonctionnalité Placeholder** représente une avancée majeure dans l'évolution de JCB.
Il permet aux développeurs de :

* Écrivez du code plus propre et plus maintenable,
* Réutilisez efficacement les extraits de code entre les composants, et
* Ajustez dynamiquement les valeurs de texte ou de code en fonction du contexte.

À mesure que JCB continue d'évoluer, les espaces réservés joueront un rôle clé dans l'amélioration de l'interopérabilité des composants et de la productivité des développeurs.

---

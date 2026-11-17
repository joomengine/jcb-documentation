> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="join-fields-in-the-admin-list-view-with-field-relations"></a>
# Rejoindre les champs dans la vue Liste d'administration avec les relations avec les champs

<a id="introduction"></a>
## Introduction

[00:00:00](https://www.youtube.com/watch?v=hh4IIPmYIY8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

La version **2.8** de Joomla Component Builder (JCB) a introduit une nouvelle fonctionnalité puissante : **Field Relations** pour joindre des champs directement dans **Admin List View**.
Cela vous permet de **combiner plusieurs valeurs de champ dans une seule colonne d'affichage** tout en conservant la possibilité de **filtrer et de rechercher** à l'aide de ces mêmes champs.

> Si vous avez utilisé des **scripts personnalisés** dans vos vues de liste de composants avant la mise à niveau, notez que la nouvelle structure de build peut affecter l'emplacement de votre code personnalisé. Après la mise à niveau, examinez et réinsérez tous les extraits de code personnalisés si nécessaire.

---

<a id="what-the-feature-does"></a>
## Que fait la fonctionnalité

[00:01:27](https://www.youtube.com/watch?v=hh4IIPmYIY8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m27s)

La fonctionnalité **Admin Field Relations** vous permet de **joindre plusieurs valeurs de champ** dans une seule colonne d'affichage combinée.
Par exemple, vous pouvez combiner un **nom de prédicateur**, un **e-mail** et un **site Web** dans une seule entrée de liste qui affiche le champ ayant une valeur - tout en conservant intactes les fonctionnalités de filtrage et de liaison.

<a id="example-scenario"></a>
### Exemple de scénario

En utilisant le composant *Sermon Distributor*, vous souhaiterez peut-être que votre liste de prédicateurs affiche :

* **Nom**
* **E-mail (si présent)**, ou
* **Site Web (si pas d'e-mail)**

Le tout dans une seule colonne à côté du nom du prédicateur.

---

<a id="creating-an-admin-field-relation"></a>
## Création d'une relation de champ d'administration

[00:02:35](https://www.youtube.com/watch?v=hh4IIPmYIY8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m35s)

1. Ouvrez **Component Builder → Vues d'administration**.
2. Choisissez votre vue d'administration cible (par exemple, *Preachers*).
3. Faites défiler jusqu'à la zone **Champs**.
4. En bas, cliquez sur **"Créer des relations de champs d'administration pour cette vue d'administration"**.
5. Vous serez redirigé vers le **Générateur de relations avec les champs d'administration**.

Ici, vous pouvez définir comment les champs doivent être joints et dans quel domaine la relation agira.

---

<a id="understanding-the-area-column"></a>
## Comprendre la colonne "Zone"

[00:03:43](https://www.youtube.com/watch?v=hh4IIPmYIY8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m43s)

Le paramètre **Area** détermine où votre logique de relation s'applique :

* **Modèle (avant la modélisation) :** modifiez les données avant que JCB ne les traite.
* **Modèle (après modélisation) :** modifie les données après que JCB les a structurées.
* **Afficher :** modifiez ou combinez la sortie HTML générée.

Si vous devez modifier des valeurs brutes (par exemple, du texte brut ou des chiffres), utilisez **Modèle**.
Si vous souhaitez manipuler le rendu du HTML, utilisez **View**.

---

<a id="example-targeting-the-model-area"></a>
## Exemple : Ciblage de la zone du modèle

[00:06:52](https://www.youtube.com/watch?v=hh4IIPmYIY8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m52s)

1. Dans **Admin Field Relations Builder**, choisissez votre champ **Nom**.
2. Ajoutez **E-mail** et **Site Web** comme champs joints.
3. Définissez **Zone** sur **Modèle**.
4. Choisissez **Type de joint : concaténation**.
5. Sous **Colle**, spécifiez ce qui sépare les valeurs (par exemple, virgule, flèche ou espace).

Une fois compilée, la sortie jointe apparaît dans la vue liste comme ceci :

```
John Doe, johndoe@example.com
```

Vous pouvez personnaliser la colle ou utiliser la logique PHP pour un comportement dynamique.

---

<a id="using-php-code-in-relations"></a>
## Utilisation du code PHP dans les relations

[00:09:32](https://www.youtube.com/watch?v=hh4IIPmYIY8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m32s)

Vous pouvez remplacer l'option de colle par du **code PHP personnalisé** en sélectionnant le type **"Code"**.
JCB utilise les ID de champ entre accolades `{}` pour référencer les champs (par exemple, `{1222}` pour le courrier électronique, `{280}` pour le site Web).

Exemple d'extrait PHP :

```php
if (!empty($item->{1222})) {
    $details = $item->{1222};
} elseif (!empty($item->{280})) {
    $details = $item->{280};
} else {
    $details = '';
}
```

> **Conseil :** Une fois que vous avez confirmé quels ID de champ correspondent à quelles valeurs, supprimez les commentaires générés par JCB pour un résultat plus propre.

Vous pouvez utiliser n'importe quelle logique PHP valide ou même appeler des fonctions pour un comportement avancé.

---

<a id="limitation-one-target-per-list-field"></a>
## Limitation : une cible par champ de liste

[00:13:28](https://www.youtube.com/watch?v=hh4IIPmYIY8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m28s)

Chaque champ de liste ne peut être ciblé qu'une seule fois dans les relations de champ.
Si vous essayez d'utiliser le même champ plusieurs fois, une seule relation s'appliquera.

---

<a id="testing-the-output"></a>
## Test de la sortie

[00:14:44](https://www.youtube.com/watch?v=hh4IIPmYIY8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m44s)

Après avoir compilé et installé votre composant :

* Les enregistrements avec un e-mail affichent l'**email**.
* Les enregistrements sans e-mail affichent le **site Web**.
* Les enregistrements sans aucun des deux affichent une entrée vide.

---

<a id="targeting-the-view-area"></a>
## Ciblage de la zone de visualisation

[00:15:53](https://www.youtube.com/watch?v=hh4IIPmYIY8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m53s)

Lorsque **Area** est défini sur **View**, vous rejoignez les **blocs de code HTML** créés par JCB pour chaque champ, et non les valeurs brutes de la base de données.

Exemples d'espaces réservés :

```
[field=199]
[field=1222]
[field=280]
```

Ces espaces réservés représentent des blocs HTML complets pour chaque champ (y compris les liens, les autorisations et le formatage).
Vous pouvez les combiner, supprimer les commentaires inutiles et même insérer des balises HTML ou PHP selon vos besoins.

---

<a id="example-concatenation-in-view-area"></a>
## Exemple : Concaténation dans la zone d'affichage

[00:18:32](https://www.youtube.com/watch?v=hh4IIPmYIY8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h18m32s)

1. Utilisez le type de joint **Concaténation**.
2. Définissez la colle sur `<br/>` pour séparer chaque valeur sur une nouvelle ligne.
3. Compilez et installez.

Maintenant, votre vue de liste affiche :

```
Leonard Ravenhill
leonard@example.com
ravenhill.org
```

Le HTML de chaque champ (liens, autorisations, etc.) est conservé.

---

<a id="advanced-demonstration-combining-linked-fields"></a>
## Démonstration avancée : combinaison de champs liés

[00:22:15](https://www.youtube.com/watch?v=hh4IIPmYIY8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h22m15s)

Vous pouvez rejoindre les **champs de table associés** (comme Preacher et Sermon) tout en gardant les deux liens actifs.

Mesures:

1. Dans la **Vue d'administration des sermons**, ouvrez **Champs**.
2. Supprimez *Preacher* de « Afficher dans la vue Liste » mais conservez-le comme **Filtre** et **Lien**.
3. Accédez à **Relations sur le terrain → Nouvelle relation**.
4. Choisissez :

* **Champ de liste :** Nom
   * **Rejoindre le champ :** Prédicateur
   * **Zone :** Vue
   * **Colle :** Espace
5. Compilez et installez.

La vue liste affiche maintenant :

```
Ten Shekels and a Shirt  Paris Reidhead
```

Les deux valeurs restent cliquables, renvoyant à leurs vues respectives.

---

<a id="how-it-works-in-the-code"></a>
## Comment ça marche dans le code

[00:26:16](https://www.youtube.com/watch?v=hh4IIPmYIY8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h26m16s)

Dans le modèle :

```php
$query->select($db->quoteName('a.name'));
$query->select($db->quoteName('preacher.name', 'preacher_name'));
```

Dans la vue :

```php
<?php echo $this->escape($item->preacher_name); ?>
```

JCB gère automatiquement :

* Jointures de tables
* Vérifications d'autorisation
* Génération de liens
* Échappement et rendu corrects

---

<a id="best-practices-and-tips"></a>
## Bonnes pratiques et conseils

* **Testez toujours** vos champs joints après la compilation et l'installation.
* **Utilisez la zone "Affichage"** lorsque vous souhaitez conserver le HTML et les liens.
* **Utilisez la zone "Modèle"** pour manipuler les valeurs brutes ou ajouter une logique PHP.
* **Ne réutilisez pas un champ cible** plus d'une fois par vue.
* **Gardez une trace des identifiants de champ** lors de l'écriture de code personnalisé.
* **Utilisez les problèmes GitHub de JCB** pour signaler des comportements inattendus.

---

<a id="summary"></a>
## Résumé

Cette fonctionnalité simplifie ce qui nécessitait auparavant une manipulation PHP personnalisée.
Désormais, vous pouvez facilement **rejoindre plusieurs champs dans les vues de liste d'administration** à l'aide de l'interface graphique de JCB tout en gardant un contrôle total sur le filtrage, la liaison et la logique d'affichage.

Il s'agit d'une amélioration majeure de la qualité de vie pour les développeurs créant des composants Joomla avancés avec des vues de liste dynamiques, lisibles et puissantes.

---

> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="dynamic-router-implementation-explained"></a>
# Implémentation du routeur dynamique expliquée

**Référence vidéo :** [Mise en œuvre du routeur dynamique expliquée sur YouTube](https://www.youtube.com/watch?v=hYycPLbaMos)
---

<a id="overview"></a>
## Aperçu

Dans ce didacticiel, nous explorons la **nouvelle implémentation de routeur dynamique** de JCB, une amélioration du système conçue pour réduire la complexité et améliorer la façon dont les URL sont créées pour les vues de votre site Joomla. Cette mise à jour résout principalement les problèmes liés aux **processus d'analyse et de création du routeur**, en particulier pour les composants qui utilisent **Dynamic Gets** dans leurs **Vues de site**.

---

<a id="1-understanding-router-complexity"></a>
## 1. Comprendre la complexité du routeur

**[00:00:00 → 00:00:49]**

Lorsqu'un composant Joomla Component Builder inclut des **Vues de site** (vues frontales), ces vues utilisent généralement **Dynamic Gets** pour récupérer des données.
Le routeur utilise ensuite ces données, combinées avec le nom de la vue, pour construire des **URL conviviales pour les moteurs de recherche (SEF)**.

Par exemple:

```
index.php?option=com_sermondistributor&view=preacher&id=12
```

peut devenir :

```
/sermondistributor/preacher/john-doe
```

JCB génère automatiquement un fichier `router.php` pour chaque composant, tentant de « deviner » les relations nécessaires à l'analyse et à la création d'URL. Bien que souvent correct, il peut émettre des hypothèses incorrectes lorsque les requêtes dynamiques deviennent complexes.

---

<a id="2-the-router-file-and-its-methods"></a>
## 2. Le fichier du routeur et ses méthodes

**[00:01:26 → 00:02:08]**

Après avoir compilé votre composant, accédez à :

```
/components/com_sermondistributor/router.php
```

Ce fichier contient deux méthodes clés dans une classe de routeur :

* `build($query)` - Convertit les paramètres d'URL en segments SEF.
* `parse($segments)` - Interprète les segments SEF en variables de requête.

Dans `parse()`, une instruction `switch` évalue le premier segment, représentant généralement le **nom de la vue**.

Exemple:

```php
switch ($segments[0]) {
    case 'preacher':
        $vars['view'] = 'preacher';
        break;
    case 'preachers':
        $vars['view'] = 'preachers';
        break;
}
```

---

<a id="3-understanding-default-router-behavior"></a>
## 3. Comprendre le comportement du routeur par défaut

**[00:02:33 → 00:03:44]**

La **Vue Liste (`preachers`)** récupère les données directement de la base de données sans nécessiter de saisie d'URL.
Par conséquent, le routeur n’a besoin que de :

```php
$vars['view'] = 'preachers';
```

Le reste du code généré automatiquement (pour les identifiants, les alias, etc.) est redondant et peut être supprimé en toute sécurité.

Toutefois, pour la **Vue unique (`preacher`)**, le routeur peut mal interpréter les relations Dynamic Get, par exemple en extrayant incorrectement les données de la table `sermon` au lieu de la table `preacher`.

---

<a id="4-identifying-and-correcting-router-errors"></a>
## 4. Identifier et corriger les erreurs du routeur

**[00:04:09 → 00:06:25]**

Dans la requête du modèle `preacher`, JCB crée par erreur une logique faisant référence à la table `sermon` alors qu'il devrait faire référence à la table `preacher`.
Le correctif implique de modifier la valeur que le routeur vérifie lors de l'analyse :

**Incorrect:**

```php
$getVar('sermon', $id);
```

**Correct:**

```php
$getVar('preacher', $id);
```

Vous pouvez vérifier ce que fait `getVar()` au bas de `router.php` : il est responsable de la récupération et de la validation dynamique des valeurs d'URL.

Le même ajustement s'applique à d'autres vues de sites mal identifiées, telles que les **Catégories** et les **Séries**.

---

<a id="5-implementing-fixes-via-dynamic-gets"></a>
## 5. Implémentation de correctifs via Dynamic Gets

**[00:07:14 → 00:08:48]**

Plutôt que de modifier manuellement le code du routeur, JCB vous permet désormais d'injecter dynamiquement des correctifs directement depuis l'**interface Dynamic Get**.

<a id="steps"></a>
### Étapes :

1. Ouvrez **Dynamic Gets** dans JCB.
2. Sélectionnez la **Vue du site** associée (par exemple, `Preacher`, `Series`, `Category`).
3. Sous chacun d'eux, localisez l'**onglet Script personnalisé**.
4. Activez **"Ajouter PHP (méthode d'analyse) dans le routeur"**.
5. Ajustez les espaces réservés selon vos besoins.

Cette fonctionnalité vous permet de remplacer et de cibler des vues spécifiques sans réécrire l'intégralité du routeur.

---

<a id="6-working-with-custom-placeholders"></a>
## 6. Travailler avec des espaces réservés personnalisés

**[00:10:06 → 00:11:32]**

Lors de l'activation de l'option « Ajouter PHP (méthode d'analyse) », JCB injecte un extrait de code par défaut qui inclut des **espaces réservés** :

Exemple:

```php
case '[sview]':
    $vars['view'] = '[sview]';
    $vars['id']   = $this->getVar('[sview]', $segments[1]);
    break;
```

* `[sview]` se résout automatiquement en **Nom de la vue du site**.
* Cela rend le routeur dynamique sur plusieurs vues de site.
* Si l'URL inclut plusieurs variables, les espaces réservés peuvent toutes les gérer de manière dynamique.

**Conseil :** Assurez-vous toujours que votre valeur `[sview]` correspond au nom réel de votre vue de site afin d'éviter tout routage incompatible.

---

<a id="7-adjusting-specific-site-views"></a>
## 7. Ajustement des vues spécifiques du site

**[00:11:56 → 00:13:59]**

Vous devrez appliquer cette logique de routeur personnalisée pour les vues de site suivantes :

* **Sermon (ID de série)** - Corrigez "sermon" → "série".
* **Sermon (ID du prédicateur)** - Assurez-vous que les deux valeurs correspondent (`preacher`).
* **Catégorie** - Ajoutez `true` à l'appel `getVar` pour l'identifier comme recherche de catégorie.

Exemple pour la catégorie :

```php
$vars['id'] = $this->getVar('category', $segments[1], true);
```

Cela garantit que JCB vérifie correctement la table `#__categories` au lieu de la table de données principale.

---

<a id="8-compiling-and-verifying-the-changes"></a>
## 8. Compilation et vérification des modifications

**[00:14:21 → 00:14:49]**

Après avoir enregistré et fermé vos modifications Dynamic Get :

1. Recompilez votre composant dans JCB.
2. Installez-le ou mettez-le à jour sur votre site Joomla.
3. Rouvrez `router.php` pour vérifier les modifications :

   ```php
   case 'preacher':
       $vars['id'] = $this->getVar('preacher', $segments[1]);
       break;
   case 'category':
       $vars['id'] = $this->getVar('category', $segments[1], true);
       break;
   case 'series':
       $vars['id'] = $this->getVar('series', $segments[1]);
       break;
   ```

Si le code correspond à votre logique souhaitée, votre routeur gère désormais correctement les URL SEF.

---

<a id="9-future-improvements-and-collaboration"></a>
## 9. Améliorations futures et collaboration

**[00:15:16 → Fin]**

Cette implémentation représente la **première phase** des améliorations du routeur de JCB.
Les futures mises à jour visent à rendre la logique de devinette dynamique plus intelligente.

Les développeurs sont encouragés à contribuer via le **dépôt GitHub** de JCB pour affiner ces méthodes de routage.

---

<a id="summary"></a>
## Résumé

| Problème | Parce que | Solutions |
| ----------------------------------- | ---------------------------------------------------------- | ------------------------------------------------ |
| Mappage incorrect des variables du routeur | JCB s'est trompé Dynamic Get relations | Remplacer par la méthode d'analyse personnalisée dans Dynamic Get |
| Code de routeur redondant dans les vues de liste | Les valeurs par défaut générées ne sont pas nécessaires | Supprimer la logique `id` redondante |
| Vue des catégories non reconnue | Le routeur n'a pas détecté le contexte de catégorie | Utiliser `getVar('category', $id, true)` |
| Génération d'URL SEF incohérente | Incompatibilité des espaces réservés | Utilisez les espaces réservés `[sview]` pour plus de cohérence |

---

<a id="final-notes"></a>
## Notes finales

* Utilisez **Dynamic Get → Custom Script → Add PHP (parse Method)** pour réparer les routeurs de manière dynamique.
* Évitez de modifier manuellement `router.php`, sauf si nécessaire.
* Toujours recompiler et réinstaller pour appliquer les modifications.
* Restez à jour avec les nouvelles versions de JCB pour une logique de routage plus intelligente.

---

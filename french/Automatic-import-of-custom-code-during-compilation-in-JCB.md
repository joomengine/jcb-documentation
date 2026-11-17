> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="automatic-import-of-custom-code-during-compilation-in-jcb"></a>
# Importation automatique du code personnalisé lors de la compilation dans JCB

[00:00:00](https://www.youtube.com/watch?v=DFMfIl-VkSk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(_Cliquez sur ces liens horaires pour voir la vidéo Youtube_)

---

<a id="1-introduction-to-custom-code"></a>
## 1. Introduction au code personnalisé

**[00:00:00](https://www.youtube.com/watch?v=DFMfIl-VkSk&t=00h00m00s)**

La fonctionnalité **Code personnalisé** de Joomla Component Builder (JCB) est un ajout puissant qui permet aux développeurs d'intégrer de manière transparente leur code écrit manuellement dans le flux de travail des composants. Cette fonctionnalité fonctionne parallèlement au système **Dynamic Get** et garantit que toutes les modifications personnalisées ajoutées aux composants compilés sont automatiquement suivies, stockées et réappliquées lors des compilations ultérieures.

Vous aurez rarement besoin de modifier ces entrées de code personnalisé directement dans l'interface utilisateur de JCB. Au lieu de cela, la plupart des modifications ont lieu dans votre **éditeur de code** préféré (par exemple, VS Code, PHPStorm, Sublime Text).

---

<a id="2-purpose-of-the-custom-code-feature"></a>
## 2. Objectif de la fonctionnalité de code personnalisé

**[00:00:39](https://www.youtube.com/watch?v=DFMfIl-VkSk&t=00h00m39s)**

Cette fonctionnalité est destinée aux développeurs qui préfèrent coder directement dans leur éditeur. Le flux de travail typique ressemble à ceci :

1. **Créez** un composant à l'aide de JCB.
2. **Compilez-le et installez-le** sur le même site Joomla.
3. **Modifiez ou ajoutez du code** manuellement dans les fichiers compilés.
4. Sur la **compilation** suivante, JCB automatiquement :

* Extrait ce code nouveau ou modifié.
   * Le stocke dans la section **Code personnalisé**.
   * Le réinsère au bon emplacement dans le composant.

Ce système vous évite de perdre vos modifications lors de la recompilation.

> **Remarque :** La fonctionnalité est toujours en **bêta** et les utilisateurs sont encouragés à fournir des commentaires pour l'affiner.
> **[00:01:45](https://www.youtube.com/watch?v=DFMfIl-VkSk&t=00h01m45s)**

---

<a id="3-editing-code-in-your-editor"></a>
## 3. Modification du code dans votre éditeur

**[00:02:28](https://www.youtube.com/watch?v=DFMfIl-VkSk&t=00h02m28s)**

Pour tester la fonctionnalité :

1. Ouvrez le répertoire racine de votre site Joomla dans un éditeur de code.
2. Accédez à `administrator/components/com_demo` (en supposant que vous utilisez le **Composant de démonstration**).
3. Ouvrez un fichier PHP principal tel que `index.php`.
4. Ajoutez quelques scripts ou commentaires personnalisés simples.

Cette modification sera détectée ultérieurement par JCB lors de la compilation.

---

<a id="4-custom-code-conventions"></a>
## 4. Conventions du code personnalisé

**[00:03:04](https://www.youtube.com/watch?v=DFMfIl-VkSk&t=00h03m04s)**

Le code personnalisé utilise des balises d'espace réservé spécifiques que JCB peut reconnaître et gérer. Ces espaces réservés marquent le début et la fin de votre code.

<a id="a-insertion-tags"></a>
### un. Balises d'insertion

Pour **insérer** un nouveau code :

```php
/***[INSERT<>$$$$]***/
// Your custom PHP code here
/***[/INSERT<>$$$$]***/
```

Pour les blocs HTML, enveloppez les mêmes marqueurs avec des commentaires HTML :

```html
<!--***[INSERT<>$$$$]***-->
<!-- Your custom markup here -->
<!--***[/INSERT<>$$$$]***-->
```

<a id="b-replacement-tags"></a>
### b. Balises de remplacement

Pour **remplacer** le code existant :

```php
/***[REPLACE<>$$$$]***/
// Your replacement PHP code here
/***[/REPLACE<>$$$$]***/
```

<a id="c-after-compilation"></a>
### c. Après la compilation

Une fois compilés, JCB met à jour ces espaces réservés :

* Cela remplace `[INSERT<>$$$$]` par `[INSERTED<>$$$$23]`, où `23` est le **ID de code personnalisé** dans JCB.
* **Ne modifiez pas ce numéro.** Il est essentiel pour les futures compilations.

> **Conseil :**
> Si vous modifiez ultérieurement votre code, ajoutez à nouveau les parenthèses en losange `<>` pour indiquer que JCB doit mettre à jour la version stockée.

Pour une comparaison côte à côte de l'injection manuelle d'extraits de code et de l'automatisation du hachage, consultez la [Présentation des codes personnalisés JCB](./JCB-Custom-Codes.md).

---

<a id="5-limitations-of-custom-code"></a>
## 5. Limites du code personnalisé

**[00:05:30](https://www.youtube.com/watch?v=DFMfIl-VkSk&t=00h05m30s)**

Il existe quelques limitations importantes lors de l'utilisation de balises de code personnalisées :

* **Espacement :** Les blocs de code personnalisé doivent être espacés d'au moins **6 à 8 lignes**.
* **Fingerprinting :** JCB crée une **fingerprint** (instantané contextuel) de quelques lignes avant et après votre insertion. Si ce contexte change trop, JCB ne reconnaîtra pas où réinsérer le code.
* Si l'empreinte digitale change, JCB :

* Ignorer la réinsertion et afficher un **avertissement** lors de la compilation.
  * Insérez le code comme **échappé**, l'empêchant de casser votre composant.

> Ce système d'empreintes digitales évite les écrasements accidentels et garantit une fusion automatisée stable.

---

<a id="6-demonstration---replace-example"></a>
## 6. Démonstration - Exemple de remplacement

**[00:08:00](https://www.youtube.com/watch?v=DFMfIl-VkSk&t=00h08m00s)**

1. Ouvrez le fichier principal du **composant de démonstration**.
2. Ajoutez vos balises de remplacement :

   ```php
   /***[REPLACE<>$$$$]***/
   echo 'hi, it worked!';
   /***[/REPLACE<>$$$$]***/
   ```3. Enregistrez votre fichier et recompilez le composant dans JCB.

Après la compilation, vérifiez l'onglet **Code personnalisé** dans JCB :

* Vous verrez votre entrée répertoriée avec son **chemin** et ses **hachages d'empreintes digitales**.
* L'interface affiche les empreintes digitales **start** et **end** pour les remplacements.

---

<a id="7-verifying-replacement-in-the-editor"></a>
## 7. Vérification du remplacement dans l'éditeur

**[00:10:03](https://www.youtube.com/watch?v=DFMfIl-VkSk&t=00h10m03s)**

Une fois que vous avez réinstallé le composant compilé :

* Le code apparaîtra correctement inséré et étiqueté comme **remplacé**.
* Un numéro d'identification (par exemple, `23`) sera ajouté pour le suivre dans le système.
* Si vous modifiez ce code ultérieurement, n'oubliez pas de rajouter les symboles `<>` avant de recompiler.

---

<a id="8-demonstration---insert-example"></a>
## 8. Démonstration - Insérer un exemple

**[00:11:32](https://www.youtube.com/watch?v=DFMfIl-VkSk&t=00h11m32s)**

Suivez ces étapes pour tester les **insertions** :

1. Dans votre éditeur, déplacez au moins **8 lignes** sous toute balise existante.
2. Ajoutez un bloc d'insertion :

   ```php
   /***[INSERT<>$$$$]***/
   echo 'New insert block added!';
   /***[/INSERT<>$$$$]***/
   ```3. Enregistrez et compilez à nouveau votre composant.

Avant de réinstaller, ouvrez l'onglet **Code personnalisé** dans JCB :

* Vous devriez voir la nouvelle insertion répertoriée.
* Seul le **hachage de début** est requis pour les insertions (pas de hachage de fin).

Après l'installation, votre code apparaîtra avec le statut `INSERTED` et un identifiant unique.

---

<a id="9-updating-custom-code"></a>
## 9. Mise à jour du code personnalisé

**[00:14:34](https://www.youtube.com/watch?v=DFMfIl-VkSk&t=00h14m34s)**

Pour mettre à jour le code inséré ou remplacé :

1. Modifiez votre code dans l'éditeur.
2. Ajoutez les symboles de diamant `<>` à la balise.
3. Enregistrez le fichier.
4. Recompilez et réinstallez votre composant.

JCB détectera automatiquement le changement et mettra à jour sa version stockée dans la base de données.

---

<a id="10-handling-fingerprint-warnings"></a>
## 10. Gestion des avertissements d'empreintes digitales

**[00:15:18](https://www.youtube.com/watch?v=DFMfIl-VkSk&t=00h15m18s)**

Si le code entourant votre insertion ou votre remplacement change :

*JCB peut ne pas trouver l'empreinte digitale originale.
* Le système **insérera le code échappé** (désactivé), afin de ne pas casser votre composant.
* Cela garantit que votre code ajouté manuellement ne sera jamais perdu ou égaré.

Pour les remplacements, ce processus est plus complexe car le code remplacé peut ne pas être supprimé automatiquement. Consultez toujours les avertissements dans la sortie du compilateur.

---

<a id="11-distribution-settings"></a>
## 11. Paramètres de distribution

**[00:16:21](https://www.youtube.com/watch?v=DFMfIl-VkSk&t=00h16m21s)**

Lorsque votre composant est prêt pour la **distribution** :

1. Dans JCB, passez le composant en **"Mode production."**
2. Lors de la prochaine compilation, JCB :

* Supprimez toutes les balises d'espace réservé.
   * Exclure les marqueurs de gestion de code personnalisés.

Cela garantit que votre composant distribué est propre et prêt à être déployé.

---

<a id="12-summary"></a>
## 12. Résumé

| Feature                    | Descriptif |
| -------------------------- | ------------------------------------------------------------------- |
| **Automatic Extraction**   | JCB lit et stocke vos scripts personnalisés lors de la compilation.            |
| **Automatic Reinsertion**  | Une fois recompilés, vos scripts sont rajoutés aux bons endroits. |
| **Insert & Replace Tags**  | Utilisez `INSERT` pour le nouveau code, `REPLACE` pour le code existant.             |
| **Fingerprint Protection** | Protège vos modifications manuelles en validant le contexte du code.            |
| **Production Switch**      | Removes tags for public release.                                    |

---

<a id="13-key-takeaways"></a>
## 13. Points clés à retenir

* Espacez toujours les blocs de code personnalisé d'au moins 8 lignes.
* Ne modifiez jamais l'ID généré automatiquement après la compilation.
* Utilisez les supports en diamant `<>` lorsque vous souhaitez que JCB détecte une mise à jour.
* Testez votre code personnalisé avec un **composant de démonstration** avant utilisation en production.
* Surveillez l'onglet **Code personnalisé** pour tous les scripts extraits et gérés.

---

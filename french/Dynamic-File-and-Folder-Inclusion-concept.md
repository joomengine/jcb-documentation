> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="joomla-component-builder---dynamic-file-and-folder-inclusion"></a>
# Joomla Component Builder - Inclusion dynamique de fichiers et de dossiers

<a id="tutorial-reference"></a>
### Référence du didacticiel

**Vidéo :** "Concept d'inclusion dynamique de fichiers et de dossiers"
---

<a id="1-introduction-to-dynamic-inclusion"></a>
## 1. Introduction à l'inclusion dynamique

**[00:00:00 → 00:01:17]**

Joomla Component Builder introduit un **système d'inclusion dynamique de fichiers et de dossiers** qui permet aux développeurs d'inclure des fichiers ou des dossiers externes, locaux ou distants, directement dans leur package de composants.

Cette fonctionnalité améliore l'automatisation et la flexibilité lors du développement de composants Joomla complexes qui reposent sur des ressources partagées ou externes.

<a id="key-concept"></a>
### Concept clé

Vous pouvez désormais :

* Incluez des **fichiers ou dossiers externes** (même en dehors du répertoire racine de Joomla).
* Récupérez et intégrez des **fichiers distants** (comme depuis GitHub ou un autre site Web) directement dans votre composant.
* Gérez les extraits de code de manière dynamique avec **EXTERNALCODE**.

---

<a id="2-accessing-the-advanced-tab-for-dynamic-files"></a>
## 2. Accès à l'onglet Avancé pour les fichiers dynamiques

**[00:02:03 → 00:02:35]**

Accédez à la zone **"Fichiers et dossiers"** dans JCB.
Un nouvel **onglet "Avancé"** a été ajouté pour compléter l'**onglet de base** existant.

<a id="what-it-does"></a>
### Ce qu'il fait

* Permet à JCB de **récupérer des fichiers de n'importe où dans votre système** et de les ajouter à votre package de composants.
* Prend en charge les **fichiers en dehors du répertoire racine de Joomla**, à condition que PHP dispose des autorisations de lecture nécessaires.

> **Astuce :** Normalement, vous n'aurez besoin que des fichiers contenus dans le répertoire de vos composants Joomla.
> Utilisez l'inclusion externe uniquement lorsque votre flux de travail nécessite spécifiquement des dépendances externes.

---

<a id="3-adding-files-and-folders"></a>
## 3. Ajout de fichiers et de dossiers

**[00:02:53 → 00:04:21]**

Vous pouvez configurer JCB pour regrouper des fichiers ou dossiers personnalisés non générés avec votre composant. Cela signifie que vous pouvez conserver ces fichiers à leur place pendant le développement et demander à JCB de les inclure automatiquement lors de la compilation.

<a id="path-settings"></a>
### Paramètres du chemin

* **Utilisez des constantes** dans les chemins de fichiers (par exemple, `_VDM_PATH_`).
* Ne **pas** mettre les constantes entre guillemets.
* Le compilateur de JCB interprète automatiquement ces constantes correctement.

Exemple (à l'intérieur de JCB) :

```
VDM_PATH.'/libraries/vdm_io'
```

Devient résolu dynamiquement par le compilateur sans syntaxe supplémentaire.

---

<a id="4-defining-the-target-path-and-zip-relation"></a>
## 4. Définir le chemin cible et la relation ZIP

**[00:04:29 → 00:05:39]**

Lors de la configuration de l'inclusion de fichiers ou de dossiers :

1. **Définissez le chemin cible** dans la structure ZIP de votre composant.
   Exemple : `libraries/vdm_io`
2. Cela permet à JCB d'inclure des dossiers non standard (comme des bibliothèques) dans le package de composants.
3. Lors de l'installation, ces dossiers sont automatiquement copiés à leur emplacement approprié.

> **Exemple de cas d'utilisation :**
> Incluez les fichiers de bibliothèque gérés par Composer directement dans votre composant JCB sans emballage séparé.

---

<a id="5-automatic-installation-scripts-for-non-standard-folders"></a>
## 5. Scripts d'installation automatique pour les dossiers non standard

**[00:05:53 → 00:07:59]**

Si JCB détecte que votre chemin cible se trouve **en dehors** des répertoires habituels Admin, Media ou Site, il ajoute une fonction de script d'installation spéciale (`setDynamicF0ld3rs`) pour gérer correctement ces dossiers.

<a id="script-behavior"></a>
### Comportement des scripts

* Déplace les dossiers spécifiés vers la bonne destination lors de l'installation ou des mises à jour.
* Ignore les dossiers Admin, Media et Site (ceux-ci sont gérés nativement par Joomla).
* Gère tous les autres emplacements de manière dynamique.

> **Attention :**
> Cette fonctionnalité est puissante mais potentiellement dangereuse.
> Vous pourriez involontairement écraser des fichiers n'importe où dans l'installation de Joomla.
> **À utiliser avec prudence** et uniquement lorsque vous contrôlez l'environnement de déploiement.

---

<a id="6-security-reminder"></a>
## 6. Rappel de sécurité

**[00:09:13]**

Soyez prudent lorsque vous importez des plans à partir de référentiels que vous ne contrôlez pas.

> **Remarque :**
> L'inclusion dynamique peut théoriquement déplacer des fichiers n'importe où sur votre système.
> Consultez le fichier README du référentiel, l'historique des sources et les responsables avant d'exécuter **Init** ou **Reset**.
> Liez uniquement les référentiels publiés auxquels vous faites confiance.

---

<a id="7-using-externalcode-snippets"></a>
## 7. Utilisation des extraits `EXTERNALCODE`

**[00:09:49 → 00:12:38]**

Le mot-clé `EXTERNALCODE` permet à JCB de récupérer et d'intégrer dynamiquement des **extraits de code externes** dans votre composant au moment de la compilation.

<a id="how-it-works"></a>
### Comment ça marche

* Peut référencer des **chemins de fichiers locaux** ou des **URL distantes** (par exemple, des liens de fichiers bruts GitHub).
* Utile pour inclure du code partagé dans les référentiels Git ou des extraits d'équipe.
* JCB crée et suit automatiquement une **signature de hachage** du code pour la détection des modifications.

<a id="example"></a>
#### Exemple:

```
EXTERNALCODE:https://gist.githubusercontent.com/username/raw/fancydate.txt
```

Cet extrait récupère le contenu brut du fichier et l'intègre dans votre assistant de composant ou votre zone de classe.

> **Remarque :**
> Actuellement, EXTERNALCODE ne prend **pas en charge les constantes** dans les chemins : utilisez des chemins absolus ou des URL complètes.

---

<a id="8-compilation-and-hash-validation"></a>
## 8. Compilation et validation de hachage

**[00:13:19 → 00:15:11]**

Lors de la compilation d'un composant avec EXTERNALCODE :

* JCB récupère la ressource externe.
* Il affiche un **message confirmant** que le code externe a été ajouté.
* Un **hash** est généré pour surveiller les changements dans les futures compilations.

Si l'extrait change :

* JCB affiche un **avertissement** sous "Avertissements" après la recompilation.
* Vous êtes invité à vérifier que le changement de code est légitime.

---

<a id="9-post-compilation-validation"></a>
## 9. Validation post-compilation

**[00:16:16 → 00:18:49]**

Après compilation :

1. Vérifiez que le code externe inclus apparaît correctement dans vos fichiers de composants (par exemple, dans le répertoire `helpers`).
2. Si un changement est détecté dans une compilation ultérieure, vérifiez le code mis à jour pour en vérifier la sécurité et l'exactitude.
3. Confirmez que toutes les modifications sont attendues (par exemple, à partir de votre source GitHub).

---

<a id="10-handling-external-code-updates-safely"></a>
## 10. Gérer les mises à jour de code externe en toute sécurité

**[00:17:20 → 00:19:16]**

Si un extrait externe change :

* JCB vous avertira automatiquement lors de la compilation.
* Vérifiez le fichier concerné pour confirmer que seules les mises à jour attendues ont été effectuées.
* JCB garantit également que tout code malveillant injecté est échappé sous forme de chaîne, empêchant ainsi son exécution directe.

> **Meilleure pratique :**
> Vérifiez toujours le **message de changement de hachage** après chaque compilation impliquant des extraits externes.

---

<a id="11-final-thoughts"></a>
## 11. Réflexions finales

**[00:20:15 → 00:20:54]**

Les fonctionnalités **Inclusion dynamique de fichiers et de dossiers** et **EXTERNALCODE** sont des outils avancés conçus pour les développeurs Joomla professionnels qui souhaitent :

* Bases de code modulaires et réutilisables.
* Inclusion automatisée de bibliothèques ou de scripts partagés.
* Un moyen robuste de collaborer via GitHub tout en préservant l'intégrité des composants.

Cependant, une grande flexibilité implique de grandes responsabilités :

* Validez toujours l’intégrité de la source.
* Publiez uniquement des référentiels pour les collaborateurs en qui vous avez confiance et documentez clairement leur comportement.
* Gardez les chemins d'inclusion et les autorisations étroitement contrôlés.

---

<a id="summary-of-key-features"></a>
## Résumé des principales fonctionnalités

| Fonctionnalité | Objectif | Niveau de risque | Utilisation recommandée |
| ---------------------------- | ------------------------------------------------------------- | ---------- | ------------------------------------------------ |
| **Inclusion de fichiers dynamiques** | Ajoutez des fichiers externes ou internes dans votre composant.           | Moyen | Lors de l'inclusion de bibliothèques statiques ou de fichiers d'assistance. |
| **Inclusion de dossiers dynamiques** | Déplacez les dossiers externes dans les répertoires Joomla lors de l'installation. | Élevé | À utiliser uniquement si vous connaissez parfaitement les chemins d'accès aux fichiers.           |
| **CODE EXTERNE** | Récupérez des extraits de code externes à partir de GitHub ou d'URL.             | Moyen | Idéal pour les fonctions d'assistance contrôlées par la version.   |
| **Vérification du hachage du compilateur** | Détecte les modifications non autorisées ou inattendues.                   | Faible | Lisez toujours les messages d’avertissement.                  |

---

<a id="helpful-tips"></a>
## Conseils utiles

* Utilisez les **constantes JCB** pour les chemins dynamiques afin de garantir la portabilité entre les environnements.
* Conservez les inclusions externes **contrôlées en version** via GitHub.
* Périodiquement **recompilez et vérifiez les hachages** pour maintenir l'intégrité des composants.
* N'utilisez jamais EXTERNALCODE provenant de sources non vérifiées ou publiques.

---

> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="cli-command-suite"></a>
# Suite de commandes CLI

> Discussion source : [CLI Command Suite · joomengine · Discussion #1013](https://github.com/orgs/joomengine/discussions/1013)

La CLI Joomla Component Builder (JCB) introduit une interface de ligne de commande complète de niveau production qui vous permet de gérer, synchroniser, compiler, installer et distribuer les actifs JCB sans utiliser l'interface graphique.

Cette couche CLI n’est pas un wrapper ou un raccourci : c’est une interface de premier ordre vers les systèmes et référentiels internes de JCB.

---

<a id="design-goals-of-the-jcb-cli"></a>
## Objectifs de conception de la CLI JCB

La CLI a été conçue pour :

- Permettre l'automatisation complète des flux de travail JCB
- Prise en charge des référentiels distants en tant que citoyens de première classe
- Autoriser l'utilisation sans tête (CI/CD, serveurs, conteneurs)
- Fournir un comportement déterministe et scriptable
- Mettre en miroir (et dans certains cas étendre) la fonctionnalité de l'interface graphique
- Maintenir un contrôle explicite (rien ne se passe implicitement)

---

<a id="how-to-access-the-cli"></a>
## Comment accéder à la CLI

Depuis votre répertoire racine Joomla :

```bash
php cli/joomla.php
```

Ceci répertorie toutes les commandes CLI Joomla disponibles, y compris le groupe de commandes Component Builder.

Pour voir l'aide pour n'importe quelle commande :

```bash
php cli/joomla.php <command> -h
```

---

<a id="cli-command-naming-structure"></a>
## Structure de dénomination des commandes CLI

Toutes les commandes JCB CLI suivent cette structure :

```text
componentbuilder:<action>:<area>
```

<a id="actions"></a>
### Actions

- `compile`
- `get`
- `init`
- `pull`
- `push`
- `reset`

<a id="areas"></a>
### Zones

Les zones représentent les types d'entités gérées par JCB, tels que :

- `joomla_component`
- `joomla_module`
- `joomla_plugin`
- `power`
- `field`
- `fieldtype`
- `layout`
- `template`
- `snippet`
- `library`
- `repository`
- `admin_view`
- `site_view`
- `custom_code`
- `dynamic_get`
- `validation_rule`
- `class_extends`
- `class_method`
- `class_property`
- `placeholder`
- `joomla_power`
- …et d'autres

Le comportement d'une action est cohérent dans tous les domaines : seule l'entité cible change.

---

<a id="the-action-model-how-the-cli-thinks"></a>
## Le modèle d'action (comment pense la CLI)

La CLI est intentionnellement axée sur l’action et non sur l’état.

Chaque action a une signification spécifique.

---

<a id="get--synchronize-existing-items"></a>
## `get` – Synchroniser les éléments existants

<a id="purpose"></a>
### But

Synchronisez les éléments qui existent déjà localement avec leurs référentiels distants.

<a id="command-example"></a>
### Exemple de commande

```bash
php cli/joomla.php componentbuilder:get:joomla_component
```

<a id="what-get-does"></a>
### Que fait `get`

- Récupère les mises à jour des référentiels distants
- Synchronise les métadonnées et le contenu
- Ne force pas l'écrasement
- N'initialise pas les éléments manquants

<a id="inputs"></a>
### Entrées

```text
--items / -i       CSV, newline-separated, or JSON list
--items-file       Path to file containing items
```

<a id="key-behavior"></a>
### Comportement des clés

- Les éléments ne doivent pas nécessairement être des GUID
- Les alias peuvent être résolus en interne (lorsqu'ils sont pris en charge)
- Conçu pour une synchronisation sécurisée

<a id="when-to-use-get"></a>
### Quand utiliser `get`

- Mise à jour des actifs locaux existants
- Garder l'état local synchronisé
- Rafraîchissement non destructif

---

<a id="init--initialize-from-a-remote-repository"></a>
## `init` – Initialiser à partir d'un référentiel distant

<a id="purpose-1"></a>
### But

Initialisez et synchronisez les éléments qui n'existent pas encore localement.

<a id="command-example-1"></a>
### Exemple de commande

```bash
php cli/joomla.php componentbuilder:init:joomla_component
```

<a id="what-init-does"></a>
### Que fait `init`

- Extrait les éléments d'un référentiel distant
- Crée un état de suivi local
- Écrase éventuellement les éléments existants
- Peut résoudre les alias en GUID

<a id="additional-inputs"></a>
### Entrées supplémentaires

```text
--repo / -r        Repository JSON object
--repo-file        Path to repository definition
--force / -f       Force overwrite
--resolve          Resolve non-GUID identifiers
```

<a id="when-to-use-init"></a>
### Quand utiliser `init`

- Première configuration
- Clonage d'actifs d'un autre projet
- Amorcer un environnement local

---

<a id="pull--force-remote-state-locally"></a>
## `pull` – Forcer l'état distant localement

<a id="purpose-2"></a>
### But

Synchronisez de force l’état local à distance, en écrasant les modifications locales.

<a id="key-characteristics"></a>
### Caractéristiques clés

- Destructeur pour les changements locaux
- Favorise toujours la source distante
- Destiné au recouvrement ou à l'exécution

<a id="when-to-use-pull"></a>
### Quand utiliser `pull`

- Réinitialisation de la divergence locale
- Application de l'état distant canonique
- Environnements CI

---

<a id="push--publish-to-a-remote-repository"></a>
## `push` – Publier sur un référentiel distant

<a id="purpose-3"></a>
### But

Poussez les éléments locaux et leurs dépendances vers un référentiel de packages distant.

<a id="command-example-2"></a>
### Exemple de commande

```bash
php cli/joomla.php componentbuilder:push:joomla_component
```

<a id="what-push-does"></a>
### Que fait `push`

- Télécharge des éléments vers un référentiel
- Résout automatiquement les dépendances
- Bloque jusqu'à ce que l'opération soit terminée
- Nécessite des GUID valides

<a id="important-notes"></a>
### Remarques importantes

- Les dépendances sont détectées automatiquement
- Les poussées partielles ne sont pas autorisées
- Destiné à la publication et au partage

---

<a id="reset--reset-local-tracking-state"></a>
## `reset` – Réinitialiser l'état du suivi local

<a id="purpose-4"></a>
### But

Réinitialisez le suivi interne de JCB pour des articles spécifiques.

<a id="what-reset-means"></a>
### Que signifie la réinitialisation

- Efface les métadonnées de synchronisation locale
- Ne supprime pas l'élément
- Force la réinitialisation sur le prochain `init`/`pull`

<a id="safety-guarantees"></a>
### Garanties de sécurité

- Nécessite une liste d'éléments explicite
- Ne fonctionnera pas avec une entrée vide
- Ne peut pas être exécuté accidentellement

---

<a id="compiler-command-most-powerful-command"></a>
## Commande du compilateur (commande la plus puissante)

<a id="command"></a>
### Commande

```text
componentbuilder:compile:component
```

Cette commande expose le compilateur JCB complet via CLI.

<a id="what-the-compiler-cli-can-do"></a>
### Ce que la CLI du compilateur peut faire

- Compiler un ou plusieurs composants
- Extraire automatiquement les composants manquants
- Injecter des pouvoirs
- Appliquer les règles du référentiel
- Réduire la sortie
- Insérer des espaces réservés
- Cibler plusieurs versions de Joomla
- Installer automatiquement les extensions compilées
- Intégration aux serveurs de sauvegarde et de vente

---

<a id="component-selection"></a>
## Sélection des composants

Au moins une entrée de composant est requise :

```text
--component / -c
--components
--components-file
```

Tous les formats prennent en charge :

- CSV
- Valeurs séparées par une nouvelle ligne
- Tableaux JSON
- sténographie `@/path/to/file`

---

<a id="options-bundle-system"></a>
## Système de bundle d'options

Le compilateur prend en charge un ensemble d'options :

```text
--options / -o
```

Cela permet :

- Objets JSON
- Fichiers externes
- Configuration fusionnée
- Les indicateurs CLI remplacent les valeurs des fichiers

Cela rend le compilateur idéal pour :

- Pipelines CI
- Constructions reproductibles
- Configuration partagée

---

<a id="auto-install--i"></a>
## Installation automatique (`-i`)

```text
-i, --install
```

Lorsqu'il est activé :

- Les extensions compilées sont automatiquement installées
- Fonctionne pour les composants, modules et plugins
- Nécessite un environnement Joomla valide

---

<a id="powers-integration"></a>
## Intégration des pouvoirs

```text
-p, --powers
--powers-repository
```

Contrôles :

- Si les pouvoirs sont injectés
- Si les référentiels Power sont synchronisés
- Si les remplacements de puissance sont appliqués

Cela s'intègre directement au système de remplacement de puissance documenté séparément.

---

<a id="target-joomla-version"></a>
## Version cible de Joomla

```text
-j, --joomla-version
```

Valeurs autorisées :

- `3`
- `4`
- `5`
- `6`

Celui-ci contrôle :

- Structure de l'espace de noms
- Compatibilité API
- Comportement de sortie

---

<a id="environment-variable-support"></a>
## Prise en charge des variables d'environnement

Chaque option majeure prend en charge les solutions de secours des variables d'environnement, notamment :

```text
JCB_COMPILE_COMPONENT
JCB_COMPILE_COMPONENTS
JCB_COMPILER_OPTIONS
JCB_COMPILE_INSTALL
JCB_JOOMLA_VERSION
JCB_POWERS
JCB_MINIFY
...
```

Cela permet :

- Exécution sans tête
- Utilisation de Docker
- Intégration CI/CD
- Isolement secret

---

<a id="verbosity-and-output-control"></a>
## Verbosité et contrôle de sortie

```text
-v    Normal output
-vv   Verbose
-vvv  Debug
-q    Quiet
```

La sortie utilise les styles de la console Symfony et respecte les paramètres ANSI.

---

<a id="how-all-areas-fit-together"></a>
## Comment tous les domaines s'articulent

Chaque zone (champs, mises en page, pouvoirs, extraits de code, etc.) utilise :

- La même logique d'action
- Les mêmes modèles d'entrée
- La même mécanique de référentiel

Une fois que vous comprenez un domaine, vous les comprenez tous.

---

<a id="mental-model-summary"></a>
## Résumé du modèle mental

Considérez la CLI JCB comme :

- Un gestionnaire d'actifs prenant en charge le référentiel
- Un frontend du compilateur
- Un outil de déploiement
- Un moteur de synchronisation

Le tout piloté par des commandes explicites, jamais par un état caché.

---

<a id="beta-status--testing"></a>
## Statut et tests bêta

La CLI est actuellement en version bêta.

Domaines d’intervention connus :

- Utilisation de la mémoire dans les grands projets
- Travaux de compilation de longue durée
- Graphiques de dépendance aux cas extrêmes

C'est pourquoi les tests et les commentaires sont essentiels.

---

<a id="final-notes"></a>
## Notes finales

Cette CLI est conçue pour évoluer :

- De développeurs solo
- Aux équipes
- Vers des pipelines automatisés

Si vous préférez les interfaces graphiques, vous pouvez continuer à les utiliser.
Si vous préférez les terminaux, JCB y est désormais pleinement à l'aise.
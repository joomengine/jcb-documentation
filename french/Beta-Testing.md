> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="getting-started-as-a-joomla-component-builder-beta-tester"></a>
## Premiers pas en tant que testeur bêta de Joomla Component Builder

<a id="overview"></a>
### Aperçu

Pour contribuer à améliorer la stabilité et les performances de Joomla Component Builder (JCB), le projet a besoin de testeurs plus fidèles. Les bêta-testeurs téléchargeront, installeront et testeront les nouvelles versions bêta de JCB, puis signaleront tout problème rencontré. Ce document vous guidera tout au long du processus pour devenir bêta-testeur JCB.

<a id="steps-to-become-a-jcb-beta-tester"></a>
### Étapes pour devenir un bêta-testeur JCB

1. Rejoignez le canal des versions/mises à jour de JCB : https://t.me/jcb_updates
2. Surveillez les versions bêta du dépôt bêta et téléchargez-les.
3. Installez la version bêta téléchargée sur un site Web Joomla vierge.
4. Effectuez une série de tâches et testez les nouvelles fonctionnalités ou modifications.
5. Signalez tous les problèmes que vous rencontrez sur Gitea : https://git.vdm.dev/joomla/Component-Builder/issues et marquez-les avec la balise Beta.
6. Recherchez tous les problèmes ouverts marqués avec la version bêta avant de commencer vos tests.

<a id="how-to-test"></a>
### Comment tester

1. Téléchargez la dernière version de https://git.vdm.dev/joomla-beta/pkg-component-builder/archive/master.zip
2. Installez et testez localement
3. Signalez les problèmes via un ticket à https://git.vdm.dev/joomla/Component-Builder/issues

<a id="change-logs"></a>
### Journaux des modifications

Vous pouvez trouver les journaux des modifications pour chaque version aux emplacements suivants :

- Journal des modifications non officiel de la chaîne bêta : https://git.vdm.dev/joomla-beta/com-componentbuilder/src/branch/master/CHANGELOG.md
- Journal officiel des modifications de la chaîne stable : https://git.vdm.dev/joomla/Component-Builder/src/branch/staging/CHANGELOG.md

Consultez les journaux de modifications et l’historique des validations pour comprendre quelles fonctionnalités/fonctions/domaines ont été mis à jour et nécessitent des tests.

<a id="additional-tips-and-detailed-steps"></a>
### Conseils supplémentaires et étapes détaillées

1. **Comprendre les modifications :** Gardez un œil sur les journaux de modifications dans le canal bêta (https://git.vdm.dev/joomla-beta/com-componentbuilder/src/branch/master/CHANGELOG.md) et le canal stable (https://git.vdm.dev/joomla/Component-Builder/src/branch/staging/CHANGELOG.md). Cela peut vous aider à identifier les domaines qui nécessitent des tests. Consultez également l’historique des validations pour mieux comprendre les modifications apportées, même si cela peut être écrasant pour les non-programmeurs.

2. **Compilation des composants :** Pendant le processus de test, assurez-vous de compiler vos composants dans un référentiel git. Cela vous permettra de voir ce qui a changé et d’identifier les problèmes. Prenez l'habitude de compiler et de télécharger des composants sur git après chaque mise à jour.

3. **Familiarisez-vous avec la fonctionnalité « Pouvoirs » de JCB :** Il s'agit d'un aspect avancé de la plateforme qui peut améliorer considérablement vos capacités de programmation PHP. Au fur et à mesure que le projet évolue, davantage de fonctionnalités seront introduites via Powers, il est donc crucial de comprendre cet aspect pour des tests efficaces.

4. **Participez activement au canal des mises à jour JCB :** Rejoignez le canal des mises à jour JCB (https://t.me/jcb_updates) et restez au courant des dernières versions bêta. Engagez-vous avec la communauté, partagez vos expériences et fournissez de précieux commentaires pour aider à améliorer le projet.

5. **Utilisation du composant de vérification des versions :** JCB dispose d'un composant de vérification des versions (https://git.vdm.dev/joomla/com_release_checking) qui peut être utilisé pour marquer et fournir des commentaires sur les fonctionnalités testées. Ce composant peut être installé sur un système Joomla lié à Gitea et accessible via votre compte Gitea. Utilisez cet outil pour rationaliser le processus de test et le rendre plus efficace.

6. **Collaborez avec d'autres testeurs :** Coordonnez-vous avec d'autres bêta-testeurs et partagez vos expériences de test. Créez une liste des domaines qui doivent être vérifiés pour chaque version et répartissez les tâches entre les testeurs. Cela garantira un processus de test complet et aidera à identifier les problèmes potentiels plus efficacement.

7. **Signaler des problèmes :** Si vous rencontrez des problèmes lors des tests, signalez-les à https://git.vdm.dev/joomla/Component-Builder/issues.. Assurez-vous de marquer le problème avec la balise « Bêta » et vérifiez les problèmes existants avec la même balise avant d'en soumettre un nouveau. Cela évitera les rapports de problèmes en double et aidera l'équipe de développement à prioriser ses tâches.

Ce guide suppose que Git est installé sur votre système. Si ce n'est pas le cas, veuillez suivre les instructions officielles pour installer Git : [https://git-scm.com/book/en/v2/Getting-Started-Installing-Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

<a id="how-to-test-the-compiler-in-the-octojoom-setuphttpsgitvdmdevoctoleooctojoom"></a>
## Comment tester le compilateur (dans la [configuration Octojoom](https://git.vdm.dev/octoleo/octojoom)) :

<a id="step-1-initialize-a-git-repository-in-your-components-target-folder-on-your-production-instance"></a>
### Étape 1 : Initialisez un référentiel Git dans le dossier cible de votre composant (sur votre instance de production)

1. Ouvrez votre interface de ligne de commande ou votre terminal.

2. Accédez au dossier cible de votre composant :

```
cd /path/to/your/component/target/folder
```

3. Initialisez un dépôt Git :

```
git init
```

<a id="step-2-commit-your-components-initial-state"></a>
### Étape 2 : validez l'état initial de votre composant

1. Ajoutez tous les fichiers du dossier cible à la zone de préparation :

```
git add .
```

2. Validez les fichiers avec un message significatif :

```
git commit -m "Initial commit of my component"
```

<a id="step-3-copy-the-target-folder-and-set-up-the-beta-jcb-instance"></a>
### Étape 3 : copiez le dossier cible et configurez l'instance bêta JCB

1. Copiez le dossier cible vers un nouvel emplacement que vous pourrez supprimer lorsque vous avez terminé :

```
cp -R /path/to/your/component/target/folder /path/to/new/target/folder
```

2. Configurez votre nouvelle installation vierge de la version bêta de JCB pour cibler ce nouveau dossier.

3. Initialisez vos référentiels dans l'instance bêta et utilisez **Init**/**Reset** pour extraire le
   plan de composant à partir du contrôle de source.

<a id="step-4-compile-your-component-with-the-beta-jcb-instance"></a>
### Étape 4 : Compilez votre composant avec l'instance bêta JCB

1. Compilez votre composant.

<a id="step-5-review-changes-made-by-the-beta-jcb-instance"></a>
### Étape 5 : Examiner les modifications apportées par l'instance bêta JCB

1. Dans l'interface de ligne de commande ou le terminal, accédez au nouveau dossier cible :

```
cd /path/to/new/target/folder
```

2. Vérifiez l'état du dépôt Git :

```
git status
```

3. S'il y a des modifications, ajoutez-les à la zone de préparation :

```
git add .
```

4. Validez les modifications avec un message indiquant qu'elles ont été apportées par l'instance bêta de JCB :

```
git commit -m "Changes made by beta JCB instance"
```

5. Pour voir les différences entre l'instance JCB stable et l'instance JCB bêta, utilisez la commande `git diff` :

```
git diff HEAD~1
```

Cette commande affichera les différences entre le commit actuel (HEAD) et le commit précédent (HEAD~1).

6. Examinez les différences et notez toutes les modifications qui semblent interrompre votre composant Joomla ou qui ne sont plus identiques à votre instance JCB stable.

<a id="step-6-report-any-issues"></a>
### Étape 6 : Signaler tout problème

Si vous rencontrez des problèmes, signalez-les au projet JCB en ouvrant un nouveau problème et en le marquant avec la balise Beta : [https://git.vdm.dev/joomla/Component-Builder/issues](https://git.vdm.dev/joomla/Component-Builder/issues)

> N'oubliez pas que des tests approfondis sont essentiels à la réussite du projet. Plus nous avons de testeurs actifs et engagés, plus JCB peut évoluer et s'améliorer efficacement.
> Bon test !
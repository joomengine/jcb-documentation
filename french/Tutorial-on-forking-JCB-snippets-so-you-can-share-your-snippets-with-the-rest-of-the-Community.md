> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="forking-jcb-snippets-to-share-with-the-community"></a>
# Forking d'extraits JCB à partager avec la communauté

[Regardez le didacticiel complet sur YouTube](https://www.youtube.com/watch?v=0hgHeQVTLOk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)

Ce guide explique comment **fork**, **configurer** et **contribuer** des extraits de communauté JCB via GitHub à l'aide de la version actualisée.
Flux de travail **Snippet Manager**. La zone des extraits de code utilise désormais les mêmes outils **Reset → Init → Push** qui alimentent JCPackages.
peut extraire des mises à jour, travailler localement et apporter des modifications sans quitter l'interface JCB.

---

<a id="overview"></a>
## Aperçu

Une fois familiarisé avec le Snippet Manager, vous pouvez :

1. Forkez le référentiel global d'extraits pour disposer de votre propre télécommande.
2. Utilisez **Reset** et **Init** pour préparer et extraire des extraits directement dans JCB.
3. Améliorez ou créez des extraits de code dans l'application.
4. Utilisez **Push** pour renvoyer votre travail à GitHub et ouvrez une pull request.

Le référentiel communautaire se trouve sur [github.com/joomengine/snippets](https://github.com/joomengine/snippets). Tout le monde peut tirer
à partir de cette télécommande, et les contributions sont partagées avec la communauté au sens large via des pull request.

---

<a id="step-1-fork-the-jcb-snippets-repository"></a>
## Étape 1. Forkez le référentiel d'extraits JCB

Vous aurez besoin d'un **compte GitHub** et d'une compréhension de base de Git.

1. Visitez [github.com/joomengine/snippets](https://github.com/joomengine/snippets).
2. Cliquez sur **Fork** (en haut à droite).
3. Choisissez votre compte personnel ou votre organisation comme destination du fork.
4. GitHub copiera le référentiel dans votre compte. L'URL de votre fork ressemblera à
   `https://github.com/<your-user>/snippets`.

Vous disposez désormais d'un référentiel accessible en écriture vers lequel vous pouvez accéder depuis JCB.

---

<a id="step-2-configure-your-fork-inside-jcb"></a>
## Étape 2. Configurez votre fourche dans JCB

Le Snippet Manager conserve une liste de référentiels, tout comme la zone JCPackages.

1. Ouvrez **Composants → Générateur de composants Joomla → Extraits**.
2. Cliquez sur **Réinitialiser** dans la barre d'outils pour ouvrir la boîte de dialogue de configuration du référentiel.
3. Ajoutez un nouveau référentiel (ou modifiez une entrée existante) avec :
   * **Nom** – Toute étiquette qui vous aide à identifier la télécommande (par exemple « My Fork »).
   * **URL distante** – L'URL HTTPS ou SSH de votre fork (`https://github.com/<your-user>/snippets.git`).
   * **Branche** – Généralement `main`, sauf si vous avez créé une branche par défaut différente.
4. Confirmez la boîte de dialogue. JCB prépare une copie de travail locale de ce référentiel sur votre système de fichiers.

Une fois la réinitialisation terminée, vous pouvez basculer entre les télécommandes à tout moment en ouvrant le sélecteur de référentiel et en choisissant l'entrée que vous souhaitez.
ajouté.

---

<a id="step-3-initialize-snippets-from-a-repository"></a>
## Étape 3. Initialiser les extraits d'un référentiel

1. Une fois votre référentiel sélectionné, cliquez sur **Init**.
2. Choisissez la télécommande à partir de laquelle vous souhaitez charger (communauté en amont ou votre fork).
3. JCB récupère les dernières métadonnées et répertorie tous les extraits disponibles regroupés par bibliothèque et type.
4. Cochez les extraits que vous souhaitez récupérer et confirmez.

JCB clone ou met à jour automatiquement le référentiel Git sous-jacent et ajoute les extraits sélectionnés à votre catalogue local. Vous pouvez
répétez **Init** chaque fois que vous souhaitez récupérer des extraits supplémentaires ou actualiser la copie locale d'un extrait.

---

<a id="step-4-add-or-improve-snippets-in-jcb"></a>
## Étape 4. Ajouter ou améliorer des extraits de code dans JCB

Travaillez directement dans le Snippet Manager :

* Créez de nouveaux extraits avec des descriptions claires, des notes d'utilisation et des affectations précises de bibliothèque/type.
* Mettez à jour les extraits de code existants tout en gardant la **Bibliothèque**, le **Type** et le **Nom** cohérents afin que JCB les suive en tant que mises à jour.
  de nouvelles entrées.
* Assurez-vous que les détails de votre contributeur sont définis sous **Options globales → Onglet Entreprise** afin que JCB marque correctement vos modifications.

Chaque modification est écrite dans la copie de travail Git locale, ce qui vous permet d'examiner les différences avant de les appliquer.

---

<a id="step-5-push-changes-back-to-github"></a>
## Étape 5. Transférer les modifications vers GitHub

1. Sélectionnez les extraits que vous souhaitez publier.
2. Cliquez sur **Pousser**.
3. Fournissez un message de validation court et descriptif résumant votre travail si vous y êtes invité.
4. JCB prépare les extraits de code sélectionnés, les valide dans le référentiel local et transmet la validation vers le serveur distant que vous avez configuré.

Si vous utilisez un fork personnel, le push met à jour votre référentiel instantanément. Les membres de l'équipe ou l'automatisation peuvent apporter ces modifications
à partir de la même télécommande.

---

<a id="step-6-open-a-pull-request"></a>
## Étape 6. Ouvrir une Pull Request

Pour partager vos améliorations avec la communauté mondiale :

1. Visitez votre fork sur GitHub après avoir poussé. Vous verrez une bannière vous invitant à **Comparer et tirer la demande**.
2. Examinez la comparaison pour vous assurer qu'elle contient uniquement les modifications d'extrait de code prévues.
3. Décrivez pourquoi la mise à jour est utile et faites référence à tout problème ou discussion connexe.
4. Soumettez la demande d'extraction à `joomengine/snippets`.

Les responsables du projet examineront votre contribution, vous proposeront des commentaires si nécessaire et la fusionneront afin que tout le monde puisse en bénéficier.

---

<a id="best-practices--recommendations"></a>
## Meilleures pratiques et recommandations

* Effectuez toujours des modifications via JCB afin que les métadonnées restent correctes.
* Conservez les champs **Bibliothèque**, **Type** et **Nom de l'extrait** stables, sauf si vous déplacez intentionnellement un extrait de code.
* Utilisez des messages de validation clairs chaque fois que vous appuyez.
* Extrayez régulièrement le référentiel en amont (via **Init**) pour rester aligné sur les mises à jour de la communauté.
* Si vous gérez des extraits de code internes, ajoutez une entrée de référentiel distincte afin de pouvoir basculer entre les catalogues privés et communautaires.

En suivant ce flux de travail, vous pouvez collaborer en toute confiance sur des extraits, réutiliser les contributions de la communauté et conserver vos propres projets.
en synchronisation avec le catalogue mondial.
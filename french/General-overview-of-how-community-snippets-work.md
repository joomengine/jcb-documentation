> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="general-overview-of-how-community-snippets-work-in-joomla-component-builder"></a>
# Présentation générale du fonctionnement des extraits de communauté dans le générateur de composants Joomla

Ce guide explique comment le **système Community Snippets** fonctionne dans **Joomla Component Builder (JCB)**. La zone d'extraits de code remaniée suit désormais le même flux de travail **Réinitialiser → Init → Push** qui alimente les packages JCB, ce qui facilite la **sauvegarde, l'extraction et le partage** d'extraits directement dans l'interface JCB.

> **Tutoriel vidéo :** [Regarder sur YouTube](https://www.youtube.com/watch?v=qr4I1jeCp7I&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)

---

<a id="1-introduction-the-new-community-snippet-concept"></a>
## 1. Introduction : le nouveau concept d'extrait de communauté

[00:00:00](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h00m00s)

Le **Snippet Manager** de JCB prend désormais en charge les contributions de la communauté.
À l'origine, les extraits de code n'étaient que des ressources locales que vous pouviez réutiliser dans :

* Vues d'administration personnalisées
* Vues du site
* Modèles
* Mises en page

Désormais, grâce à la fonctionnalité communautaire, vous pouvez partager et importer des extraits de code à partir de référentiels Git dédiés. JCB est livré avec une référence
référentiel que toute la communauté peut utiliser, mais vous pouvez également pointer le Snippet Manager vers vos propres référentiels internes lorsque
nécessaire.

---

<a id="2-the-new-snippet-area"></a>
## 2. La nouvelle zone d'extraits

[00:00:50](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h00m50s)

L'interface des extraits de code affiche :

* **Type** d'extrait (par exemple, commun, mise en page)
* **Nom** de l'extrait
* **Bibliothèque** à laquelle il appartient (par exemple, *UiKit v2*)

La sélection d'un extrait affiche :

* Le **type**, la **bibliothèque** et le **nom** de l'extrait
* Un **lien** vers la documentation externe de la bibliothèque (si disponible)

Cela permet d’identifier et de réutiliser efficacement les extraits pendant le développement.

---

<a id="3-local-vs-community-snippets"></a>
## 3. Extraits locaux et communautaires

[00:01:29](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h01m29s)

Deux types d'extraits existent désormais :

* **Extraits locaux** - Créés et stockés sur votre propre système.
* **Extraits de communauté** - Partagés via le référentiel public d'extraits de code JCB.

Vous pouvez désormais **contribuer** vos extraits ou **importer** ceux partagés par d'autres.

---

<a id="4-contributing-snippets-and-contributor-details"></a>
## 4. Extraits de contribution et détails des contributeurs

[00:01:56](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h01m56s)

Chaque extrait comprend des **informations sur le contributeur** :

* Nom
* Courriel
* Site Web

Lorsque vous créez un nouvel extrait, JCB remplit automatiquement les détails de votre contributeur (définis dans **Options globales → Onglet Entreprise**).

Vous ne pouvez pas modifier les détails des contributeurs des extraits existants : ceux-ci sont corrigés pour maintenir l'intégrité du crédit.

> **Conseil :** Si les noms des contributeurs sont manquants, mettez à jour votre base de données des contributeurs sous *Snippets → Zone des contributeurs*.

---

<a id="5-matching-snippet-metadata"></a>
## 5. Correspondance des métadonnées d'extrait de code

[00:03:58](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h03m58s)

Assurez-vous que vos extraits de code sont **mappés de la même manière** que ceux de la communauté :

* **Nom**
* **Tapez**
* **Bibliothèque**

Ces trois champs forment l'**identifiant unique**.
Si vous les renommez ou les modifiez, JCB traite votre extrait comme *nouveau* au lieu de *mis à jour*.

---

<a id="6-the-git-based-snippet-workflow-reset--init--push"></a>
## 6. Le workflow d'extraits de code basé sur Git (Réinitialiser → Init → Push)

Le Snippet Manager reflète désormais le même workflow centré sur Git utilisé par **JCPackages**. Chaque extrait vit dans un Git
référentiel, ce qui signifie que vous pouvez conserver un historique parfait des versions, créer des branches et collaborer de manière familière. La barre d'outils propose
trois actions clés :

1. **Réinitialiser** – Garantit que le référentiel d'extraits de code configuré est préparé localement. Utilisez-le si vous avez besoin de recréer un environnement de travail propre
   copiez ou sauvegardez l'emplacement du référentiel avant d'extraire les mises à jour.
2. **Init** – Récupère les dernières métadonnées du référentiel distant, vous montre tout ce qui est disponible et vous permet
   sélectionnez les extraits à importer ou à mettre à jour. C'est ici que vous « extrayez » des extraits de code dans votre instance JCB.
3. **Push** – Renvoie toutes les modifications locales au référentiel distant. Combinez cela avec un référentiel forké si vous le souhaitez
   contribuer aux mises à jour de la communauté.

Étant donné que les extraits de code suivent désormais le même cycle de vie du référentiel que les packages, vous pouvez sauvegarder votre travail en toute confiance, rester synchronisé avec
la communauté et automatisez la collaboration à l’aide de flux Git standard.

---

<a id="7-initializing-snippets-from-the-community-repository"></a>
## 7. Initialisation des extraits du référentiel communautaire

Pour intégrer des extraits de communauté dans votre projet :

1. Ouvrez la vue **Snippets** et cliquez sur **Init** dans la barre d'outils.
2. Choisissez le référentiel à partir duquel vous souhaitez extraire. Par défaut, vous pouvez pointer JCB vers le référentiel communautaire hébergé sur
   [github.com/joomengine/snippets](https://github.com/joomengine/snippets). Vous pouvez également configurer votre propre télécommande Git si vous
   voulez un catalogue privé.
3. Après avoir sélectionné le référentiel, JCB répertorie tous les extraits disponibles avec leur type, bibliothèque, contributeur et
   descriptif. Chaque entrée est contrôlée en version, vous savez donc exactement ce que vous importez.
4. Cochez les extraits souhaités et validez. JCB les initialise localement et ils deviennent immédiatement disponibles dans Custom
   Vues d'administration, vues de site, mises en page et modèles.

Une fois un extrait initialisé, vous pouvez le réinitialiser à tout moment pour qu'il corresponde à la version stockée dans le référentiel. JCB gère le Git
opérations pour vous, en gardant tout cohérent entre votre projet et le référentiel source.

---

<a id="8-working-with-local-changes-and-backups"></a>
## 8. Travailler avec les modifications et les sauvegardes locales

Étant donné que le référentiel d'extraits de code est un clone Git normal, chaque modification que vous apportez est suivie. Tu peux:

* Examinez les extraits modifiés avant de les renvoyer sur une télécommande.
* Créez des branches si vous avez besoin d'expérimenter de nouvelles idées avant de les partager avec une équipe.
* Utilisez **Réinitialiser** pour revenir à l'état propre du référentiel à tout moment, vous assurant ainsi de toujours disposer d'une base de référence sûre.

Cette approche vous permet de traiter les extraits de code comme n'importe quel autre élément de code source : idéal pour les équipes qui souhaitent des sauvegardes prévisibles ou
intégration avec les pipelines CI.

---

<a id="9-sharing-snippets-back-to-git"></a>
## 9. Partager des extraits avec Git

Lorsque vous êtes satisfait de vos améliorations locales :

1. Assurez-vous que les détails de votre contributeur sont renseignés sous **Options globales → Onglet Entreprise** afin que les métadonnées restent exactes.
2. Cliquez sur **Push** dans le gestionnaire d'extraits de code. JCB prépare et valide les extraits sélectionnés, puis les transmet au serveur configuré.
   à distance.
3. Si vous travaillez sur votre propre référentiel, le push se termine immédiatement et vos coéquipiers peuvent extraire les mises à jour.
4. Pour contribuer au catalogue mondial, créez le référentiel communautaire à l'adresse
   [github.com/joomengine/snippets](https://github.com/joomengine/snippets), définissez votre fourche comme télécommande à l'intérieur de JCB, appuyez sur le bouton
   modifications et ouvrez une pull request depuis votre fork vers le référentiel en amont. Cela reflète le flux de travail standard de GitHub
   de nombreux développeurs l'utilisent déjà.

Tous les extraits du référentiel sont des fichiers en texte brut stockés sous contrôle de version, donc examen des demandes d'extraction et collaboration
avec les autres, c'est simple.

---

<a id="10-helper-resources"></a>
## 10. Ressources d'aide

Pour obtenir de l'aide avec Git ou le workflow de contribution :

* [Démarrage rapide Git (Udemy)](https://www.udemy.com/git-quick-start/)
* [Tutoriels d'extraits JCB (YouTube)](https://www.youtube.com)
* [Problèmes du référentiel d'extraits de communauté](https://github.com/joomengine/snippets/issues)

Ces ressources vous aident à apprendre le contrôle de version, le forking et les demandes d'extraction.

---

<a id="11-snippet-details-and-contributor-recognition"></a>
## 11. Détails de l'extrait et reconnaissance des contributeurs

[00:10:57](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h10m57s)

Chaque extrait comprend :

* **Description**
* **Exemple d'utilisation**
* **Aperçu du code**
* **Informations sur le contributeur**

<a id="blame-view"></a>
### Vue des reproches

[00:11:12](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h11m12s)
Affiche qui a modifié chaque partie de l'extrait.
Les modifications mineures sont affichées ici au lieu de remplacer le contributeur principal.

Les contributeurs peuvent lier leurs profils ou sites Web pour gagner en visibilité au sein de la communauté JCB.

---

<a id="12-snippet-usage-in-jcb"></a>
## 12. Utilisation d'extraits de code dans JCB

[00:12:52](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h12m52s)

Des extraits peuvent être insérés dans :

* **Vues d'administration personnalisées**
* **Vues du site**
* **Modèles**
* **Mise en page**

Après avoir importé de nouveaux extraits, ils apparaissent au bas de votre liste locale et incluent automatiquement les détails du contributeur.

---

<a id="13-dynamic-contributor-fields"></a>
## 13. Champs de contributeurs dynamiques

[00:13:38](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h13m38s)

Si les informations du contributeur sont manquantes, JCB utilise automatiquement les **informations mondiales de votre entreprise**.

Lorsque vous créez un nouvel extrait :

1. JCB vérifie si un extrait avec les mêmes *Nom*, *Type* et *Bibliothèque* existe.
2. Sinon, il attribue vos coordonnées en tant que contributeur.
3. Si oui, il conserve les données du contributeur d'origine.

---

<a id="14-sharing-updated-snippets"></a>
## 14. Partage d'extraits mis à jour

[00:15:48](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h15m48s)

Lorsque vous avez créé ou amélioré des extraits :

1. Sélectionnez-les dans la liste.
2. Cliquez sur **Partager des extraits** pour générer un package partageable.
3. Suivez les tutoriels sur **forking** et **pull request** pour les soumettre à la communauté.

---

<a id="15-summary"></a>
## 15. Résumé

Le Community Snippet System améliore la collaboration au sein de JCB en permettant :

* **Contribution** de nouveaux extraits
* **Synchronisation** avec les mises à jour de la communauté
* **Reconnaissance** des contributeurs
* **Partage transparent** via l'intégration GitHub

En maintenant et en contribuant aux extraits de code, les développeurs améliorent collectivement l'écosystème JCB.

---

> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="joomla-component-builder---beginner-friendly-guide"></a>
# Joomla Component Builder - Guide convivial pour les débutants

Ce guide fournit un aperçu pratique et convivial pour les débutants sur la façon d'utiliser **Joomla Component Builder (JCB)**, basé sur le didacticiel *Introduction à Joomla Component Builder*.
Il explique le flux de travail, les outils et les meilleures pratiques essentiels, avec des détails précis et à jour reflétant la dernière interface utilisateur et le comportement de JCB.

---

<a id="1-prerequisites--mindset"></a>
## 1) Prérequis et état d'esprit

[00:00:18](https://www.youtube.com/watch?v=9evJkBTnKxE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m18s)

JCB est conçu pour les développeurs familiarisés avec **PHP** et le **framework Joomla MVC**.

* **Connaissance PHP :** Le constructeur automatise une grande partie de la génération de code mais s'attend à ce que vous puissiez comprendre et modifier PHP.
* **Apprendre l'API de Joomla :** Explorez la structure principale de Joomla (modèles, vues, contrôleurs) pour comprendre comment les composants générés par JCB s'intègrent. Ouvrez le répertoire Joomla `/components`, parcourez ses dossiers et inspectez la structure des composants principaux.
* **À l'aide d'un IDE (par exemple, NetBeans) :** Vous pouvez accéder aux définitions de fonctions (comme `getLayout`) pour suivre la façon dont Joomla gère le rendu.

*Astuce :* Si vous débutez avec PHP ou Joomla MVC, envisagez les cours de développement en ligne avant de plonger plus profondément.

---

<a id="2-local-development-environment"></a>
## 2) Environnement de développement local

[00:04:17](https://www.youtube.com/watch?v=9evJkBTnKxE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m17s)

Vous devez **créer et tester les composants hors ligne** dans un environnement sandbox local.

<a id="recommended-setup"></a>
### Configuration recommandée

* **Système d'exploitation :** Ubuntu ou une autre distribution Linux.
* **Pile :** PHP, MySQL/MariaDB et Joomla installés localement.
* **Outils de débogage :** Ajoutez des outils comme Xdebug pour inspecter et déboguer efficacement votre code.

Le développement local vous permet de travailler hors ligne, de déboguer facilement et d'éviter les problèmes liés au serveur.

*Suggestion de ressources :* Le cours *"Opérationnel avec Linux pour les développeurs PHP avec Jon Peck"* (Lynda.com) est un excellent point de départ pour configurer votre environnement.

---

<a id="3-security-and-offline-preference"></a>
## 3) Sécurité et préférence hors ligne

[00:07:51](https://www.youtube.com/watch?v=9evJkBTnKxE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m51s)

Bien que JCB puisse fonctionner sur un serveur en direct, il est préférable de l'utiliser **hors ligne**.

Lors de la compilation, JCB place temporairement votre build dans le répertoire Joomla `/tmp`.
S'ils sont hébergés en ligne, cela pourrait exposer publiquement vos packages compilés.

Pour rester en sécurité :

* Développez-vous toujours localement lorsque cela est possible.
* Si vous devez travailler en ligne, supprimez les versions temporaires immédiatement après la compilation.
* Limitez les autorisations du serveur pour protéger les répertoires sensibles.

---

<a id="4-understanding-the-purpose-of-jcb"></a>
## 4) Comprendre le but de JCB

[00:03:55](https://www.youtube.com/watch?v=9evJkBTnKxE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m55s)

Le **Joomla Component Builder** a été créé pour **accélérer le développement** en automatisant la génération répétitive de code pour les composants Joomla.

It:

* Suit de près les **conventions Joomla**.
* Vous permet de **personnaliser librement le code généré**.
* Prend en charge les **interfaces d'administration et de site complexes** en utilisant la structure MVC standard.

Vous êtes encouragé à suggérer des améliorations ou à partager de meilleures méthodes de mise en œuvre avec la communauté des développeurs.

---

<a id="5-creating-your-first-component"></a>
## 5) Création de votre premier composant

[00:05:43](https://www.youtube.com/watch?v=9evJkBTnKxE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m43s)

Une fois JCB installé sur votre site Joomla local :

1. Accédez à **Composants → Générateur de composants → Composants → Nouveau**.
2. Saisissez :

* **Nom :** Le nom lisible de votre composant.
   * **Option :** Généralement au format `com_example`.
   * **Description :** Bref aperçu de l'objectif.
   * **Version :** Votre numéro de version actuelle.
3. Enregistrez le nouveau composant.

Vous disposez désormais des bases de votre extension personnalisée.

> 📘 Vous souhaitez un rappel sur ce que contrôle le composant ? Consultez [Composants Joomla dans JCB](./Joomla-Components.md) pour voir comment les vues, les assistants, les actifs et les métadonnées d'empaquetage convergent tous au sein de cette définition unique.

---

<a id="6-adding-admin-views-and-fields"></a>
## 6) Ajout de vues et de champs d'administration

[00:06:07](https://www.youtube.com/watch?v=9evJkBTnKxE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m07s)

Les vues d'administration définissent la **structure backend** et déterminent la façon dont les données sont gérées.

<a id="steps-to-add-an-admin-view"></a>
### Étapes pour ajouter une vue administrateur :

1. Accédez à **Vues administrateur → Nouveau**.
2. Choisissez entre :

* **Vue de l'élément** (enregistrement unique)
   * **Vue en liste** (plusieurs enregistrements)
3. Liez la vue à une **table de base de données** (JCB génère automatiquement cette table).
4. Configurez l'ACL (autorisations), les options de la barre d'outils et la prise en charge des catégories/balises.

<a id="adding-fields"></a>
### Ajout de champs :

* Accédez à **Champs → Nouveau**.
* Définir le type de champ (texte, liste, média, répétable, etc.).
* Attribuez le champ à la vue d'administration appropriée.
* Configurez les règles de validation, les valeurs par défaut et les filtres.

Les champs peuvent être réutilisés dans les vues, les plugins et les modules.

---

<a id="7-building-frontend-site-views"></a>
## 7) Création de vues frontales (site)

[00:07:24](https://www.youtube.com/watch?v=9evJkBTnKxE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m24s)

Les vues frontend ou « site » définissent ce que les visiteurs voient sur votre site Web.

<a id="steps"></a>
### Étapes :

1. Accédez à **Vues du site → Nouveau**.
2. Choisissez entre les types d'affichage **Liste** ou **Élément**.
3. Connectez la vue du site à sa table correspondante ou Dynamic GET.
4. Définissez des modèles et des mises en page pour contrôler la façon dont les données sont affichées.

Les modèles permettent une personnalisation au niveau de la page, tandis que les mises en page définissent des sections d'affichage plus petites.

---

<a id="8-using-dynamic-gets"></a>
## 8) Utilisation des GET dynamiques

[00:08:14](https://www.youtube.com/watch?v=9evJkBTnKxE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m14s)

**Les GET dynamiques** sont le **générateur de requêtes visuel** de JCB, vous permettant de créer des requêtes de base de données avancées sans SQL manuel.

Utilisez un GET dynamique lorsque :

* Vous devez récupérer les données de plusieurs tables.
* Vous souhaitez appliquer des filtres, des jointures ou un classement visuel.

<a id="to-create-a-dynamic-get"></a>
### Pour créer un GET dynamique :

1. Accédez à ** GET dynamiques → Nouveau **.
2. Sélectionnez une **table de base**.
3. Ajoutez des **jointures**, des **champs** et des **filtres**.
4. Enregistrez-le et associez-le à une **Vue du site** ou une **Vue du rapport d'administration**.

Cette fonctionnalité permet de garder votre logique organisée et réutilisable sur plusieurs mises en page.

---

<a id="9-compiling-and-installing-the-component"></a>
## 9) Compilation et installation du composant

[00:08:51](https://www.youtube.com/watch?v=9evJkBTnKxE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m51s)

Après avoir défini les vues, les champs et les modèles, il est temps de créer votre composant installable.

<a id="compile-steps"></a>
### Étapes de compilation :

1. Dans la **Liste des composants**, cliquez sur **Compiler**.
2. Choisissez :

* **Mode test (exécution à sec) :** Générez du code sans installation.
   * **Construction normale :** Créez un fichier ZIP installable.
3. Après une construction réussie :

* Vous pouvez **installer directement** depuis la vue du compilateur de JCB, ou
   * Téléchargez le ZIP via les **Extensions → Installer** de Joomla.

Vérifiez que :

* Les vues backend se chargent correctement sous **Composants → Votre composant**.
* Les éléments du menu du site sont liés aux vues frontales comme prévu.

---

<a id="10-contributing-and-feature-requests"></a>
## 10) Demandes de contribution et de fonctionnalités

[00:09:50](https://www.youtube.com/watch?v=9evJkBTnKxE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m50s)

Le développeur encourage la collaboration pour assurer l'amélioration continue de JCB.

Si vous rencontrez des problèmes ou avez des suggestions de fonctionnalités :

* Signalez-les publiquement sur GitHub dans la section **Problèmes**.
* Démarrez ici de nouvelles **demandes de fonctionnalités**.
* Pour les développements sponsorisés ou les demandes prioritaires, vous pouvez contacter directement le responsable.

S'engager publiquement garantit que les discussions et les résolutions profitent à tout le monde.

---

<a id="11-supporting-the-project"></a>
## 11) Accompagner le projet

[00:08:51](https://www.youtube.com/watch?v=9evJkBTnKxE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m51s)

JCB étant gratuit, il est demandé aux utilisateurs **de ne pas diffuser les vidéos de formation** sans autorisation.
Si vous trouvez de la valeur dans l'outil et qu'il vous fait gagner du temps, envisagez de contribuer financièrement pour aider à financer le développement continu.

Votre soutien contribue à soutenir les améliorations pour l'ensemble de la communauté des développeurs Joomla.

---

<a id="12-summary---complete-workflow"></a>
## 12) Résumé – Flux de travail complet

[00:11:09](https://www.youtube.com/watch?v=9evJkBTnKxE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m09s)

1. **Configurez** un environnement Joomla local.
2. **Installer** le générateur de composants Joomla.
3. **Créez** votre composant (configuration de base).
4. **Ajouter** des vues et des champs d'administration.
5. **Créer** des vues et des modèles de site.
6. **Utilisez les GET dynamiques** pour les requêtes complexes.
7. **Compiler et tester** en mode Dry Run.
8. **Installer** et vérifier la fonctionnalité.
9. **Affiner et itérer** jusqu'à ce qu'il soit stable.
10. **Contribuer** à la communauté JCB.

---

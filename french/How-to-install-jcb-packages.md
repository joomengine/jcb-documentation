> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="import-jcb-packages-with-the-repository-engine"></a>
# Importer des packages JCB avec le moteur de référentiel

La génération Joomla 4+ de Joomla Component Builder (JCB) remplace l'ancien importateur ZIP par un
Moteur d'empaquetage soutenu par Git. Au lieu de télécharger des archives cryptées, vous connectez JCB à un
référentiel, parcourez les entités packagées et extrayez le plan dont vous avez besoin. Ce guide parcourt
configurer le catalogue, importer des plans et contrôler quels référentiels sont autorisés à
mettez à jour votre installation.

> 🔄 **Rappel :** Un package JCB est un plan qui vit à l'intérieur de JCB. Ce n'est *pas* le Joomla
> extension ZIP que vous installez sur un site. Utilisez le moteur de packaging lorsque vous souhaitez partager ou réutiliser
> les définitions de la base de données des composants, champs, extraits de code, pouvoirs et autres entités.

---

<a id="1-prepare-the-repository-catalogue"></a>
## 1. Préparer le catalogue du référentiel

Le moteur de packaging lit les référentiels Git enregistrés dans **Components → Component Builder →
Dépôts**. Pour charger le catalogue officiel :

1. Cliquez sur **Nouveau** et créez une entrée avec :
   * **Organisation :** `joomengine`
   * **Dépôt :** `repoindex`
   * **Lire la branche :** `master`
   * **Type :** `GitHub`
   * **Contenu cible :** `repositories`
   * **Accès :** `global`
2. Enregistrez le référentiel et revenez à la vue liste.
3. Appuyez sur **Init** dans la barre d'outils, sélectionnez l'entrée d'index du dépôt et choisissez
   **Initialiser les référentiels sélectionnés**.

JCB clone le catalogue et crée des enregistrements locaux pour chaque référentiel référencé. Chaque référentiel
inclut la documentation Markdown qui explique ce que le package fournit.

---

<a id="2-link-the-repositories-you-need"></a>
## 2. Liez les référentiels dont vous avez besoin

Chaque entité packagable (composants, types de champs, extraits de code, super pouvoirs, etc.) possède un bouton **Init**.
Utilisez-le pour lier l'entité à un ou plusieurs référentiels :

1. Accédez à la liste des entités (par exemple **Composants**) et ouvrez un élément.
2. Cliquez sur **Init** dans la barre d'outils.
3. Choisissez les référentiels qui correspondent au contenu cible de l'entité.
4. Confirmez pour les lier à votre installation.

Une fois lié, le référentiel apparaît dans la barre latérale de l'entité avec des métadonnées, du contenu Lisez-moi et une liste
des plans disponibles.

---

<a id="3-import-blueprints-with-init--reset"></a>
## 3. Importer des plans avec Init & Reset

* **Init** importe un plan pour la première fois. Sélectionnez l'élément souhaité dans la liste des référentiels
  et confirmez. JCB crée l'entité localement et résout automatiquement toutes les dépendances
  (par exemple, types de champs, extraits de code ou super pouvoirs référencés par le package).
* **Reset** resynchronise l'entité locale avec le référentiel. Utilisez-le pour extraire les modifications en amont après un
  le collaborateur envoie une mise à jour. JCB respecte l’ordre du référentiel – déplacez les sources préférées vers le
  top et dépublier les référentiels que vous souhaitez ignorer.

Étant donné que les référentiels sont prioritaires, vous pouvez conserver plusieurs dépôts en amont disponibles. Publier uniquement le
référentiels auxquels vous faites confiance avant d’exécuter Reset pour éviter les remplacements accidentels.

---

<a id="4-review-the-repository-documentation"></a>
## 4. Consultez la documentation du référentiel

Chaque référentiel comprend un fichier readme Markdown que JCB affiche à côté des contrôles d'entité. Utilisez-le pour :

* Comprenez la portée du plan avant de l'importer.
* Lisez les notes de mise à niveau ou de migration fournies par l'auteur du package.
* Suivez les liens vers les problèmes GitHub, les demandes d'extraction ou les exemples de sites.

Considérez le fichier Lisez-moi comme la documentation faisant autorité pour ce package. Si quelque chose n'est pas clair, ouvrez
une discussion ou un problème dans le référentiel source.

---

<a id="5-configure-github-tokens-for-private-imports"></a>
## 5. Configurer les jetons GitHub pour les importations privées

Les référentiels publics peuvent être lus de manière anonyme, mais en poussant les modifications ou en les important depuis le privé
les référentiels nécessitent une authentification.

1. Générez un jeton d'accès personnel GitHub avec la portée `repo`.
2. Ajoutez-le globalement sous *Components → Component Builder → Options → GitHub* **ou** modifiez un
   entrée du référentiel et activez **Remplacer les paramètres globaux** pour stocker un jeton par référentiel.
3. Pour les serveurs Git auto-hébergés, fournissez les informations d'identification correspondantes dans les paramètres du référentiel.

Les jetons sont stockés cryptés dans Joomla. Faites-les pivoter périodiquement en fonction des besoins de votre organisation.
politiques de sécurité.

---

<a id="6-troubleshooting-imports"></a>
## 6. Dépannage des importations

| Symptôme | Que vérifier |
| --- | --- |
| La liste des référentiels est vide | Confirmez que l'index du référentiel a été initialisé et que l'entrée du référentiel est **publiée**. |
| La réinitialisation extrait la mauvaise version | Réorganisez les référentiels pour le contenu cible ou annulez temporairement la publication de ceux dont vous ne souhaitez pas. |
| Le push est désactivé | L'entrée du référentiel nécessite une **branche d'écriture** et des informations d'identification valides. N'oubliez pas que les push affectent **tous** les référentiels publiés pour ce contenu cible. |
| Dépendances manquantes | Importez les référentiels associés (par exemple, les types de champs ou les extraits de code) et assurez-vous qu'ils sont publiés avant d'exécuter Réinitialiser. |

---

<a id="7-next-steps"></a>
## 7. Prochaines étapes

* Explorez la [Présentation du moteur d'emballage JCB](./JCB-Packaging-Engine.md) pour une analyse approfondie de
  cibler les canaux de contenu et les flux de travail collaboratifs.
* Lisez la documentation spécifique au référentiel pour savoir comment chaque plan doit être utilisé.
* Lorsque vous êtes prêt à partager votre propre travail, suivez les
  [guide de publication de packages](./Add-your-own-JCB-packages-to-the-JCB-Communty-Directory.md) pour
  connectez vos référentiels et renvoyez les mises à jour vers Git.

En s'appuyant sur des référentiels plutôt que sur des fichiers ZIP ad hoc, les équipes peuvent conserver tous les plans JCB.
synchronisé, révisable et contrôlé par version.
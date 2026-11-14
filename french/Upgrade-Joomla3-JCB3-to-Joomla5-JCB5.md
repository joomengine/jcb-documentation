> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="upgrading-joomla-3--jcb-3-sites-to-joomla-5--jcb-5"></a>
# Mise à niveau des sites Joomla 3 + JCB 3 vers Joomla 5 + JCB 5

La mise à niveau de projets de longue durée de Joomla 3 et Joomla Component Builder (JCB) 3.x vers la pile moderne Joomla 5 et JCB 5.x nécessite une approche progressive. Ce guide consolide les anciennes vidéos de migration JCB 2.5.8/2.6.0 avec le chemin de mise à niveau actuel de Joomla 5 afin que vous puissiez déplacer en toute confiance les sites de production sans perdre de données ni de code personnalisé.

Le processus est divisé en préparation, conversion, mises à niveau principales et validation post-mise à niveau. Suivez les listes de contrôle dans l'ordre : chaque étape suppose que la précédente a été complétée et vérifiée.

---

<a id="1-review-the-upgrade-scope-and-prerequisites"></a>
## 1. Examinez la portée et les conditions préalables de la mise à niveau

Avant de changer quoi que ce soit, comprenez ce qui va bouger et ce qui restera derrière.

* JCB 5.x ne prend plus en charge Joomla 3. Votre site doit atterrir sur Joomla 5 (ou 6 lors de sa sortie) pour les mises à jour en cours.
* Les champs répétables dans JCB 3 doivent être convertis en sous-formulaires et tableaux dédiés. Cela a été introduit pour la première fois dans les versions JCB 2.5.8/2.6.0 et reste une condition préalable pour les versions modernes.
* Assurez-vous d'avoir un accès administrateur à Joomla, des informations d'identification SSH/FTP et un accès à la base de données pour les sauvegardes.

> **Liste de contrôle**
> 1. Auditez les extensions installées et notez tous les packages Joomla 3 uniquement.
> 2. Confirmez la disponibilité de PHP 8.1+ – le minimum pour Joomla 5.
> 3. Planifiez une fenêtre de maintenance qui couvre les sauvegardes de base de données, les sauvegardes de fichiers et le temps de validation.

---

<a id="2-back-up-and-stage-the-joomla-3-site"></a>
## 2. Sauvegardez et mettez en scène le site Joomla 3

Travaillez toujours à partir d’une copie de production. Utilisez votre solution de sauvegarde préférée ou exportez manuellement la base de données (`mysqldump` ou phpMyAdmin) et archivez la racine Web. Restaurez la sauvegarde sur un serveur intermédiaire qui correspond à votre version PHP cible.

Une fois la mise en scène en ligne :

1. Désactivez les tâches cron et les intégrations tierces susceptibles de modifier les données lors de la mise à niveau.
2. Activez la journalisation de débogage de Joomla pour capturer les avis de dépréciation et les erreurs SQL.
3. Documentez tout remplacement de modèle ou tout code personnalisé écrit manuellement : ils peuvent nécessiter des ajustements après la mise à niveau.

---

<a id="3-convert-repeatable-fields-to-subforms-in-jcb-3"></a>
## 3. Convertir les champs répétables en sous-formulaires dans JCB 3

Les installations JCB 3 les plus anciennes reposent toujours sur des champs répétables. Avant de mettre à niveau JCB lui-même, parcourez votre schéma de composant et convertissez chaque champ répétable vers la nouvelle présentation de sous-formulaire :

1. Mettez à jour le site intermédiaire avec le dernier package JCB 3 disponible pour les utilisateurs de Joomla 3.
2. Dans JCB, ouvrez chaque vue d'administration contenant des champs répétables. Utilisez les outils de conversion introduits dans JCB 2.5.8/2.6.0 pour migrer ces champs vers des sous-formulaires. Les scripts créent des tables de base de données dédiées et ajustent automatiquement le XML de la vue administrateur.
3. Recompilez le composant et installez-le sur le site intermédiaire pour vérifier les vues converties.
4. Vérifiez les configurations Dynamic GET : nettoyez les jointures et les filtres signalés par les scripts de migration.

Ne continuez pas tant que chaque composant n'a pas été compilé avec succès sans avertissements de champ répétables.

---

<a id="4-prepare-the-codebase-for-joomla-4-and-5"></a>
## 4. Préparez la base de code pour Joomla 4 et 5

Joomla ne prend en charge que les mises à niveau majeures incrémentielles. Parcourez les versions dans l'ordre :

1. Mettez à niveau Joomla 3 vers la dernière version 3.10 et résolvez tous les avertissements sur la page de vérification préalable à la mise à jour.
2. Installez Joomla 4 sur la scène à l'aide du programme de mise à jour intégré. Réappliquez les remplacements de votre modèle et confirmez que le site se charge comme prévu.
3. Une fois Joomla 4 stable, exécutez la mise à niveau de Joomla 5. Vérifiez que toutes les extensions, y compris JCB, s'affichent comme étant compatibles.

Tout au long de ce processus, videz le cache de Joomla et celui de votre navigateur entre les étapes pour éviter que des ressources obsolètes ne masquent les problèmes.

---

<a id="5-install-jcb-5x-and-update-your-components"></a>
## 5. Installez JCB 5.x et mettez à jour vos composants

Une fois Joomla 5 lancé :

1. Installez le dernier package JCB 5 via le gestionnaire d'extensions Joomla.
2. Exécutez la vérification de la mise à jour de la base de données JCB pour vous assurer que toutes les modifications de schéma sont appliquées.
3. Ouvrez chaque composant dans JCB pour déclencher la nouvelle présentation d'administration. Examiner les onglets, les sous-formulaires et les paramètres de traduction : JCB 5 réorganise ces zones par rapport à JCB 3.
4. Recompilez vos composants et installez les packages générés sur le site intermédiaire. Faites attention aux journaux du compilateur pour les références de code obsolètes.

Si vous gérez des référentiels personnalisés ou des extraits partagés, synchronisez-les afin que les nouvelles définitions de champs et les modifications de bibliothèque se propagent à tous les projets.

---

<a id="6-validate-multilingual-and-translation-settings"></a>
## 6. Valider les paramètres multilingues et de traduction

JCB 5 est livré avec un vérificateur de traduction intégré et une prise en charge améliorée des packages linguistiques. Après recompilation :

1. Ouvrez le vérificateur de traduction dans JCB et assurez-vous que vos composants répondent au pourcentage d'achèvement requis.
2. Vérifiez que les chaînes de langue s'affichent correctement dans le backend et le frontend.
3. Mettez à jour les remplacements de langue ou les fichiers de traduction si les clés ont changé lors de la mise à niveau.

---

<a id="7-final-verification-and-production-rollout"></a>
## 7. Vérification finale et mise en production

Avant de passer en direct :

1. Exécutez le correctif de base de données de Joomla et effacez les caches.
2. Testez les workflows front-end et back-end, y compris les listes dynamiques pilotées par GET, les onglets d'administration personnalisés et les déclencheurs de code personnalisés.
3. Confirmez que les autorisations utilisateur, les éléments de menu et les modules se comportent comme prévu.
4. Effectuez une nouvelle sauvegarde du site intermédiaire mis à niveau, puis répétez le processus en production.

Documentez tout nettoyage manuel ou ajustement du code afin que le reste de l'équipe sache comment maintenir la nouvelle pile.

---

<a id="8-troubleshooting-tips"></a>
## 8. Conseils de dépannage

* **Conflits GET dynamiques** – Ré-enregistrez chaque GET après la mise à niveau afin que JCB réécrive ses jointures avec les nouveaux assistants de schéma.
* **Erreurs du compilateur** – Effacez le répertoire `/tmp` et reconstruisez. Si les problèmes persistent, réinstallez le dernier package JCB pour actualiser les modèles du compilateur.
* **Avertissements du vérificateur de traduction** – Ajustez le pourcentage d'achèvement requis ou terminez les chaînes manquantes avant l'expédition.
* **Problèmes de mise en page de la vue administrateur** – Réappliquez les scripts de conversion de sous-formulaire ; les champs qui ont été ignorés la première fois peuvent toujours être migrés manuellement.

Si vous rencontrez des problèmes qui ne sont pas abordés ici, capturez les journaux d'erreurs et consultez le forum de discussion JoomEngine pour obtenir des conseils de la communauté.
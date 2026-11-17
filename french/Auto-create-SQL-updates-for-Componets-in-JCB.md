> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="auto-create-sql-updates-for-components-in-jcb"></a>
# Créer automatiquement des mises à jour SQL pour les composants dans JCB

Ce didacticiel présente la fonctionnalité **Auto SQL Update Generation** dans **Joomla Component Builder (JCB)** : une amélioration majeure qui crée automatiquement des scripts de mise à jour SQL lorsque de nouvelles tables ou champs sont ajoutés à un composant.

**Source vidéo :** [Regarder sur YouTube](https://www.youtube.com/watch?v=bRPJTRat158&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)

---

<a id="1-understanding-how-jcb-manages-tables"></a>
## 1. Comprendre comment JCB gère les tables

[00:00:00](https://www.youtube.com/watch?v=bRPJTRat158&t=00h00m00s)

Chaque composant de Joomla est construit autour d'un **ensemble de vues**, et chaque vue est liée à une **table de base de données**.
Lorsque vous installez un composant, JCB crée automatiquement les tables nécessaires pour ces vues. C'est pourquoi lorsque vous créez ou modifiez des éléments dans le backend du composant, les données sont correctement stockées et récupérées de la base de données.

---

<a id="2-table-creation-during-installation"></a>
## 2. Création de table pendant l'installation

[00:00:38](https://www.youtube.com/watch?v=bRPJTRat158&t=00h00m38s)

Lorsque vous installez un composant généré par JCB, le système :

* Construit des tables de base de données pour chaque vue.
* Met en place des structures de champs pour le stockage des données.
* Enregistre le composant afin que Joomla le reconnaisse et interagisse correctement avec lui.

Si vous modifiez ultérieurement le composant (par exemple, en ajoutant de nouvelles tables ou de nouveaux champs), vous deviez généralement inclure les **scripts de mise à jour SQL** manuellement. Cela garantit que le schéma de base de données est correctement mis à jour lors de la réinstallation ou des mises à niveau.

---

<a id="3-the-old-method---manual-sql-updates"></a>
## 3. L'ancienne méthode - Mises à jour SQL manuelles

[00:01:47](https://www.youtube.com/watch?v=bRPJTRat158&t=00h01m47s)

Auparavant, JCB exigeait des développeurs qu'ils :

1. Ouvrez l'onglet **Mises à jour de version**.
2. Ajoutez manuellement de nouvelles **instructions SQL** (par exemple, `CREATE TABLE`, `ALTER TABLE`).
3. Incrémentez manuellement la version du composant.

Lors de l'installation, JCB a vérifié la différence de version et exécuté toutes les mises à jour SQL en attente.
Bien qu'efficace, ce processus était **long et sujet aux erreurs**.

---

<a id="4-introducing-auto-sql-generation"></a>
## 4. Présentation de la génération automatique SQL

[00:02:35](https://www.youtube.com/watch?v=bRPJTRat158&t=00h02m35s)

Grâce à cette nouvelle fonctionnalité, **JCB détecte et génère automatiquement des scripts de mise à jour SQL** lorsque :

* Une nouvelle **vue** (et donc une nouvelle table) est ajoutée.
* Un nouveau **champ** est ajouté à une table existante.

Passons en revue un exemple pratique.

---

<a id="5-adding-a-new-view"></a>
## 5. Ajout d'une nouvelle vue

[00:03:14](https://www.youtube.com/watch?v=bRPJTRat158&t=00h03m14s)

<a id="steps"></a>
### Étapes :

1. Ouvrez votre composant dans JCB.
2. Ajoutez une nouvelle **Vue administrateur** appelée **"Documents d'aide"**.
3. Ajustez les valeurs par défaut (définissez son ordre, son étiquette, etc.).
4. Cliquez sur **Enregistrer**.

Une fois enregistré, cela définit automatiquement une nouvelle table de base de données pour la vue.

Suivant:

* Accédez à **Compiler → Sélectionnez à nouveau votre composant → Compiler**.
* Le système détectera les changements structurels et **incrémentera automatiquement le numéro de version** (par exemple, de `1.4.1` à `1.4.2`).

---

<a id="6-behind-the-scenes-auto-version-increment"></a>
## 6. Dans les coulisses : incrémentation automatique de la version

[00:03:51](https://www.youtube.com/watch?v=bRPJTRat158&t=00h03m51s)

Lors de la compilation, JCB :

* Vérifie l'**historique des modifications du composant**.
* Identifie les mises à jour structurelles (nouvelles tables ou champs).
* Génère automatiquement le SQL requis pour ces modifications.
* Incrémente la **version du composant** en conséquence.

Une fois le nouveau composant installé, la nouvelle vue « Documents d'aide » apparaît et son tableau correspondant est entièrement fonctionnel.
L'onglet **Mises à jour de version** confirme que :

* La version `1.4.1` a ajouté la nouvelle table.
* La version `1.4.2` a été automatiquement créée et liée au script de mise à jour SQL généré.

Cela réduit la gestion manuelle de SQL et garantit l'intégrité de la base de données lors des mises à niveau.

---

<a id="7-adding-a-new-field-to-an-existing-view"></a>
## 7. Ajout d'un nouveau champ à une vue existante

[00:05:44](https://www.youtube.com/watch?v=bRPJTRat158&t=00h05m44s)

JCB peut également générer automatiquement des mises à jour lors de la modification de tables existantes.

<a id="example"></a>
### Exemple:

1. Ouvrez la **Vue Prédicateur**.
2. Ajoutez un nouveau champ, par exemple :
   **Nom :** `Image`
   **Tapez :** `media` (téléchargement d'images sélectionnable).
3. Cliquez sur **Enregistrer et fermer**.
4. Recompilez le composant.

Lors de la compilation, JCB détecte l'ajout d'un nouveau champ, met automatiquement à jour le schéma et incrémente à nouveau le numéro de version.

---

<a id="8-component-history-and-update-tracking"></a>
## 8. Historique des composants et suivi des mises à jour

[00:07:23](https://www.youtube.com/watch?v=bRPJTRat158&t=00h07m23s)

Pour garantir le bon fonctionnement des mises à jour SQL automatiques, JCB a besoin d'un **historique des composants**.

<a id="important-notes"></a>
### Remarques importantes :

* Les nouveaux composants enregistrent automatiquement l'historique lorsque vous enregistrez chaque vue et chaque champ.
* Les composants importés ou de démonstration **peuvent manquer d'historique**.
  → Dans ce cas, ouvrez chaque vue et **cliquez sur "Enregistrer"** pour initialiser le suivi de l'historique.

L'historique permet à JCB de comparer les versions actuelles et précédentes, afin de savoir quelles modifications SQL générer.

---

<a id="9-verifying-auto-sql-update-functionality"></a>
## 9. Vérification de la fonctionnalité de mise à jour automatique de SQL

[00:08:14](https://www.youtube.com/watch?v=bRPJTRat158&t=00h08m14s)

Après recompilation et réinstallation :

* La version s'incrémente à nouveau (par exemple, jusqu'à `1.4.3`).
* De nouvelles instructions SQL sont ajoutées automatiquement :

* Pour le tableau **Documents d'aide**.
  * Pour le nouveau champ **Image** dans la table Preacher.

Vous pouvez le confirmer dans la section **Mises à jour de version** :

* Les numéros de version sont incrémentés correctement.
* Les scripts SQL correspondants sont présents pour chaque modification.

---

<a id="10-summary--best-practices"></a>
## 10. Résumé et meilleures pratiques

[00:09:55](https://www.youtube.com/watch?v=bRPJTRat158&t=00h09m55s)

La fonctionnalité **Auto SQL Update** simplifie l'évolution des composants JCB en :

* Suivi automatique des modifications de schéma.
* Génération de scripts de mise à jour SQL précis.
* Gestion des incréments de version de manière transparente.

<a id="recommended-workflow"></a>
### Flux de travail recommandé :

1. **Enregistrez toujours chaque vue et chaque champ** avant de compiler.
2. **Recompiler** après tout changement structurel.
3. **Vérifiez l'onglet "Mises à jour de version"** pour vérifier les modifications SQL.
4. **Testez l'installation** pour vous assurer que les nouveaux champs et tables fonctionnent.

---

<a id="11-conclusion"></a>
## 11. Conclusion

Cette automatisation rend JCB encore plus puissant : capable d'**écrire vos mises à jour SQL pour vous**.
Cela permet de gagner du temps, d'éviter les erreurs et de garantir que vos composants restent cohérents et évolutifs.

> "La génération automatique de SQL fait de JCB l'un des outils de développement Joomla les plus avancés - gérant l'évolution des bases de données de manière dynamique et intelligente."

---

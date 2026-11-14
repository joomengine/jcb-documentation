> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="export--import-fully-mapped-components-via-the-packaging-engine"></a>
# Exporter et importer des composants entièrement mappés via le moteur de packaging

Le moteur de packaging basé sur Git introduit avec Joomla 4 transforme la façon dont JCB partage l'ensemble des composants
des plans. Au lieu de télécharger des archives ZIP cryptées, vous transférez vos composants vers un référentiel
et laissez les autres installations les extraire via **Init** et **Reset**. Cette page explique comment le
Le moteur sérialise chaque entité associée, comment publier ces exportations et comment les importer sur un
nouveau site.

---

<a id="1-what-the-packaging-engine-captures"></a>
## 1. Ce que le moteur de packaging capture

Lorsque vous poussez un composant, JCB collecte tout ce qui est nécessaire pour le recréer ailleurs :

* Composants et paramètres
* Vues d'administrateur, vues de site et vues d'administrateur personnalisées
* Champs, types de champs, règles de validation et relations d'requête dynamiques
* Mises en page, modèles, extraits de code et chaînes de langue
* Superpouvoirs, pouvoirs Joomla et toute dépendance référencée par le composant

Le résultat est un **plan entièrement mappé** qui reflète la structure stockée dans votre base de données Joomla.

---

<a id="2-prepare-a-repository"></a>
## 2. Préparez un référentiel

1. Enregistrez un référentiel sous **Composants → Générateur de composants → Référentiels**.
2. Définissez **Target Content** sur `packages` pour les composants complets et définissez les branches de lecture/écriture.
3. Fournissez une authentification (jeton GitHub ou autres informations d'identification) si le référentiel l'exige.
4. Appuyez sur **Init** pour que JCB lie le référentiel et affiche son README.

Pour les projets d'équipe, créez d'abord le référentiel du catalogue officiel, puis ajoutez votre fork à JCB avec un
écrire une branche.

---

<a id="3-export-by-pushing-the-component"></a>
## 3. Exporter en poussant le composant

1. Ouvrez le composant dans JCB.
2. Confirmez qu'il est lié au référentiel via la barre latérale.
3. Cliquez sur **Pousser**.
4. JCB sérialise le composant et chaque entité associée dans la branche du référentiel.
5. Utilisez votre client Git pour examiner les modifications, validez avec un message descriptif et transférez-les vers le
   origine lointaine.

Étant donné que l’exportation est stockée dans Git, vous obtenez un historique complet, des différences et une révision des demandes d’extraction.

---

<a id="4-import-on-another-installation"></a>
## 4. Importer sur une autre installation

1. Sur le site cible, enregistrez le même référentiel et appuyez sur **Init**.
2. Accédez à **Composants**, cliquez sur **Init** et sélectionnez le composant dans la liste des référentiels.
3. JCB crée le composant localement, résout les dépendances et met automatiquement à jour les ID.
4. Si le composant existe déjà, utilisez **Réinitialiser** pour extraire les dernières modifications au lieu d'importer un
   dupliquer.

Vous pouvez répéter le processus pour les référentiels associés (types de champs, extraits de code, super pouvoirs) pour garantir
toutes les dépendances sont disponibles avant de compiler le composant.

---

<a id="5-manage-versions-and-branches"></a>
## 5. Gérer les versions et les branches

* Utilisez les branches Git pour organiser des travaux expérimentaux avant de fusionner avec la branche principale d'emballage.
* Baliser les versions afin que d'autres installations puissent cibler une version spécifique lors de l'importation.
* Documentez les étapes de mise à niveau dans le référentiel README – JCB le restitue avec les boutons Init/Reset.

---

<a id="6-troubleshooting"></a>
## 6. Dépannage

| Problème | Résolution |
| --- | --- |
| Le composant n'apparaît pas dans la liste Init | Assurez-vous que l'entrée du référentiel est **publiée**, que le contenu cible correct (`packages`) est sélectionné et que la branche de lecture contient le plan exporté. |
| Dépendances manquantes après l'importation | Publiez des référentiels pour les types de champs, les extraits de code ou les super pouvoirs référencés par le composant, puis exécutez à nouveau **Reset**. |
| La poussée échoue | Vérifiez que le référentiel dispose d'une branche d'écriture, que les informations d'identification sont configurées et que vous disposez des autorisations d'écriture. |
| Écrasements inattendus | Réorganisez ou annulez temporairement la publication des référentiels qui ne doivent pas mettre à jour le composant avant d'exécuter **Reset**. |

---

<a id="7-compile--deploy"></a>
## 7. Compiler et déployer

Après l'importation, compilez le composant pour générer le ZIP installable par Joomla. Le moteur d'emballage
maintient votre plan synchronisé pendant que le compilateur produit l'artefact d'exécution pour votre Joomla
site.

Les exportations contrôlées par version facilitent la maintenance des sauvegardes, la collaboration entre plusieurs
installations et auditer chaque modification introduite dans un composant.
> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="jcb-joomla-modules"></a>
# Modules JCB Joomla

Joomla Component Builder (JCB) peut compiler des modules à part entière aux côtés de vos composants. Utilisez cette introduction pour comprendre comment ils s'intègrent dans votre flux de travail de construction, quelles fonctionnalités ils héritent de Joomla et comment JCB les maintient en version avec le reste de votre projet.

---

<a id="what-are-joomla-modules"></a>
## Que sont les modules Joomla ?

Les **Modules Joomla** intégrés à JCB sont des blocs d'affichage autonomes qui s'intègrent directement dans votre composant et restituent le contenu dans des positions de module prédéfinies dans Joomla.

Chaque module est compilé avec le composant auquel il est lié. Les modules sont couramment utilisés pour :

- Liste des éléments ou des statistiques sur le frontend
- Panneaux ou notifications du tableau de bord d'administration
- Widgets d'interface utilisateur dynamiques et rendu de contenu structuré

Modules pris en charge par JCB :

- Champs (pour les paramètres configurables par l'administrateur)
- Code personnalisé (logique partagée ou extraits)
- Script personnalisé (logique PHP rendue dans la sortie du module)
- Compilation prenant en compte les composants
- Ciblage des versions Joomla (3.x / 4.x / 5.x)

Ils suivent la structure du module natif de Joomla et s'installent dans le cadre du composant.

---

<a id="why-are-modules-useful-in-jcb"></a>
## Pourquoi les modules sont-ils utiles dans JCB ?

Les modules offrent des fonctionnalités réutilisables et positionnables sur votre site Joomla :

- Fournir des vues dynamiques compactes liées aux données des composants
- Accepter les paramètres basés sur le champ pour piloter le comportement du module
- Inclure une logique PHP ou un code personnalisé intégré
- Conçu pour être léger et rapide à charger
- Compilé automatiquement avec leur composant lié

Traitez les modules comme des widgets d'interface utilisateur portables. Parce qu'ils résident à l'intérieur de la définition du composant, ils héritent de sa gestion des versions, de ses canaux de mise à jour et de son flux de travail de distribution.

---

<a id="versioning-and-sharing"></a>
## Versionnement et partage

Lorsque vous devez mettre à jour les modules Joomla dans n'importe quel projet JCB :

1. Sélectionnez les modules à mettre à jour.
2. Cliquez sur **Réinitialiser** pour extraire la dernière version du référentiel source, ou sur **Fork** pour la personnaliser tout en gardant les modifications en amont accessibles.
3. Recompilez votre composant afin que les modules actualisés soient livrés dans le prochain package installable.

Cela garantit la maintenabilité tout en permettant une personnalisation complète.

> Les modules JCB sont étroitement intégrés à vos composants, ce qui facilite le déploiement de widgets dynamiques, de panneaux d'état et d'une logique d'affichage réutilisable sur votre site Joomla.

---

<a id="where-modules-fit-in-the-workflow"></a>
## Où les modules s'intègrent dans le flux de travail

- **Planifiez les modules à côté des vues :** définissez les données des composants qui doivent apparaître dans les positions des modules et les champs de configuration dont les administrateurs ont besoin.
- **Réutilisez la logique partagée :** référencez des blocs de code personnalisé ou des méthodes d'assistance afin que les modules reflètent le comportement des vues de site associées.
- **Ciblez la bonne version de Joomla :** alignez les paramètres du module avec les cibles de version du composant pour éviter toute dérive de compatibilité.
- **Conseils sur le placement des documents :** notez les positions de modules recommandées dans le fichier README ou le journal des modifications de votre composant afin que les responsables de la mise en œuvre sachent où les publier.

---

<a id="index-of-joomla-module-resources"></a>
## Index des ressources du module Joomla

Utilisez ces entrées lorsque vous développez votre bibliothèque de modules :

- _Bientôt disponible :_ les procédures pas à pas des modules individuels seront répertoriées ici au fur et à mesure qu'elles seront transcrites et éditées.
- [Composants Joomla dans JCB](./Joomla-Components.md) – montre comment les modules sont livrés avec le reste de l'ensemble de composants.
- [JCB Packaging Engine](./JCB-Packaging-Engine.md) – explique comment les modules sont regroupés dans le package installable lors de la compilation.

Consultez régulièrement le référentiel pour trouver de nouveaux exemples de modules que vous pouvez réinitialiser ou intégrer à vos projets.
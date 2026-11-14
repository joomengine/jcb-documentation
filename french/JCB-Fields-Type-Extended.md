> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="jcb-fields-type-extended"></a>
# Type de champs JCB étendu

*(Basé sur le tutoriel : "JCB Custom Fields Type Extended")*  
*(Cliquez sur les liens d'horodatage pour ouvrir les segments YouTube correspondants.)*

---

<a id="introduction"></a>
## Introduction

[00:00:00](https://www.youtube.com/watch?v=91iIAuHZj38&t=00h00m00s)  
Ce didacticiel fournit une présentation détaillée du fonctionnement des **Types de champs personnalisés** dans Joomla Component Builder (JCB). Alors que les didacticiels précédents présentaient les concepts de base des champs, cette explication mise à jour reflète les améliorations apportées aux versions les plus récentes de JCB, à la fois dans la conception de l'interface et dans le comportement du compilateur.

Les champs personnalisés font partie des types de champs les plus flexibles et les plus puissants de JCB, vous permettant de connecter des données entre des tables, de créer des relations dynamiques et même d'ajouter des actions de bouton personnalisées qui interagissent directement avec d'autres vues.

---

<a id="understanding-custom-fields"></a>
## Comprendre les champs personnalisés

<a id="what-are-custom-fields"></a>
### Que sont les champs personnalisés ?

[00:01:31](https://www.youtube.com/watch?v=91iIAuHZj38&t=00h01m31s)  
Les champs personnalisés vous permettent de **connecter une table à une autre** - en reliant les données entre les vues. Ils peuvent établir des relations un-à-un ou un-à-plusieurs et générer des listes dynamiques qui extraient les données d'autres tables.

Ce ne sont pas seulement des listes déroulantes ; ils peuvent devenir l’épine dorsale de structures composantes interdépendantes. En raison de leur flexibilité, les champs personnalisés sont souvent utilisés pour la liaison d'entités, les options de sélection dynamique ou les types de champs interactifs.

---

<a id="joomla-concept-of-custom-fields"></a>
## Concept Joomla de champs personnalisés

[00:02:24](https://www.youtube.com/watch?v=91iIAuHZj38&t=00h02m24s)  
Les champs personnalisés sont ancrés dans le système de champs de Joomla. Dans le dossier **`models/fields/`** de votre composant, chaque type de champ correspond à un fichier PHP définissant son comportement.

Lorsque JCB compile votre composant, il crée automatiquement ces fichiers - par exemple, `preachers.php` - et s'assure que le formulaire XML les référence via la directive `<addfieldpath>`.

```xml
<addfieldpath path="administrator/components/com_example/models/fields" />

---

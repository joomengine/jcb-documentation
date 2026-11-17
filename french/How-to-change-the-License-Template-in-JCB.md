> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="how-to-change-the-license-template-in-joomla-component-builder-jcb"></a>
# Comment modifier le modèle de licence dans Joomla Component Builder (JCB)

Ce guide explique comment modifier, créer et appliquer un modèle de licence personnalisé dans **Joomla Component Builder (JCB)**. Il est idéal pour les développeurs qui ont personnalisé des composants existants (tels que Sermon Distributor) et souhaitent gérer correctement le texte de licence dans les fichiers compilés.

---

<a id="introduction"></a>
## Introduction

[00:00:00](https://www.youtube.com/watch?v=AveBf6YZzmo&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

Lorsque vous avez modifié de manière significative l'un des composants de démonstration de JCB (environ 40 % ou plus), il convient de mettre à jour son **modèle de licence**.
Cela détermine le texte de licence qui apparaît dans les en-têtes des fichiers générés par votre composant.

Le modèle de licence est géré dans le système de compilation JCB et peut être facilement personnalisé avec votre propre fichier `.txt`.

---

<a id="step-1---locate-the-license-template-files"></a>
## Étape 1 - Localisez les fichiers de modèle de licence

[00:00:34](https://www.youtube.com/watch?v=AveBf6YZzmo&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m34s)

Tous les modèles de licence disponibles sont stockés dans :

```
administrator/components/com_componentbuilder/compiler/
```

Ce dossier contient plusieurs fichiers modèles `.txt`.
Chaque fichier définit un format de licence différent que JCB peut appliquer à vos fichiers de composants.

Vous pouvez ajouter votre propre fichier `.txt` ici et le sélectionner comme modèle de licence dans JCB.

---

<a id="step-2---viewing-the-available-templates"></a>
## Étape 2 - Affichage des modèles disponibles

[00:00:57](https://www.youtube.com/watch?v=AveBf6YZzmo&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m57s)

Dans le dossier `compiler`, vous trouverez généralement environ cinq modèles `.txt`. Évitez d'utiliser les modèles `.html`, car ils ne conviennent pas à une utilisation sous licence.

Choisissez un fichier `.txt` comme modèle actuel ou créez-en un nouveau basé sur un fichier existant.

---

<a id="step-3---editing-an-existing-template"></a>
## Étape 3 - Modification d'un modèle existant

[00:01:50](https://www.youtube.com/watch?v=AveBf6YZzmo&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m50s)

Vous pouvez modifier directement un modèle par défaut ; cependant, cela n'est **pas recommandé** car vos modifications seront écrasées lors d'une mise à jour JCB.

Plutôt:

1. Ouvrez le fichier de licence par défaut dans le dossier du compilateur.
2. Modifiez-le si nécessaire - par exemple, supprimez des lignes ou ajustez les crédits.
3. **Laissez les espaces réservés suivants intacts :**

   * `@copyright`
   * `@license`

Ces espaces réservés sont remplacés dynamiquement lors de la compilation par les valeurs de la configuration de votre composant (auteur, version, licence, etc.).

> **Conseil :** Modifiez uniquement ce qui est unique à votre projet. La base de code globale reste partagée entre JCB et Joomla, vos droits d'auteur s'appliquent donc principalement à vos modifications.

---

<a id="step-4---understanding-placeholder-variables"></a>
## Étape 4 - Comprendre les variables d'espace réservé

[00:05:00](https://www.youtube.com/watch?v=AveBf6YZzmo&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m00s)

Le compilateur de JCB prend en charge de nombreuses **variables d'espace réservé** qui peuvent être insérées dans votre modèle de licence.
Ceux-ci se trouvent dans la section « infusion » du compilateur auxiliaire.

Les espaces réservés courants incluent :

| Espace réservé | Descriptif |
| ----------------------------------------- | ------------------------------- |
| `COMPANYNAME` | Nom de votre entreprise |
| `CREATIONDATE` | Date de création originale |
| `BUILDDATE` | Date de compilation du composant |
| `AUTHOR`, `AUTHOREMAIL`, `AUTHORWEBSITE` | Informations pour les développeurs |
| `COPYRIGHT` | Avis de droit d'auteur |
| `LICENSE` | Nom et texte de la licence |
| `VERSION`, `ACTUALVERSION` | Numéros de version des composants |
| `COMPONENT_NAMES` | Liste des noms de composants |
| `SHORT_DESCRIPTION`, `DESCRIPTION` | Descriptions des composants |

> ⚙️ **Remarque :** Évitez d'utiliser des espaces réservés destinés aux scripts (par exemple, des scripts d'assistance personnalisés).
> Ils ne conviennent pas au texte de licence et interrompront le formatage.

---

<a id="step-5---saving-a-new-template-recommended-method"></a>
## Étape 5 - Enregistrement d'un nouveau modèle (méthode recommandée)

[00:07:03](https://www.youtube.com/watch?v=AveBf6YZzmo&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m03s)

Pour conserver vos modifications lors des mises à jour :

1. Ouvrez votre fichier de licence `.txt` préféré.
2. Sélectionnez **"Enregistrer sous…"** et renommez-le (par exemple, `default_q.txt`).
3. Enregistrez le nouveau fichier dans le même répertoire `compiler`.

Revenez à JCB, actualisez la configuration du composant et votre nouveau modèle de licence apparaîtra comme une option dans la liste déroulante « Modèle de licence ».

Lorsque vous le sélectionnez et recompilez votre composant, JCB utilisera votre nouveau modèle de licence dans tous les fichiers.

---

<a id="step-6---verify-the-license-update"></a>
## Étape 6 - Vérifiez la mise à jour de la licence

[00:08:03](https://www.youtube.com/watch?v=AveBf6YZzmo&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m03s)

Après recompilation :

1. Ouvrez l'un des fichiers générés par votre composant (par exemple, à partir du composant Sermon Distributor).
2. Faites défiler jusqu'à l'en-tête du fichier.
3. Confirmez que le texte de la licence reflète désormais votre nouveau modèle.

JCB remplace automatiquement le contenu de la licence lors de la compilation, en appliquant votre nouveau modèle à chaque fichier.

---

<a id="step-7---final-notes-and-good-practices"></a>
## Étape 7 – Notes finales et bonnes pratiques

[00:09:02](https://www.youtube.com/watch?v=AveBf6YZzmo&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m02s)

* **Échappement et déséchappement :** Assurez-vous que l'échappement est correct dans le texte de votre modèle pour éviter les problèmes de formatage du code.
* **Conservez les balises de droit d'auteur et de licence :** Celles-ci aident les utilisateurs et les développeurs à comprendre comment votre composant peut être utilisé.
* **Compatibilité Open Source :**
  Bien que vous ayez la liberté de personnaliser, n'oubliez pas que JCB et Joomla sont des projets open source. Certaines pièces ne peuvent pas légalement faire l'objet d'une nouvelle licence en tant que propriété.

> **Meilleure pratique :** Maintenez toujours la transparence sur les parties de votre composant qui constituent votre travail original et celles qui sont dérivées du code open source.

---

<a id="summary"></a>
## Résumé

Changer le modèle de licence dans Joomla Component Builder vous permet de :

* Personnalisez les en-têtes de licence pour vos composants.
* Ajoutez votre propre marque ou formulation.
* Protégez les mises à jour en les enregistrant sous un nouveau nom de fichier.

Avec une édition minutieuse et en respectant les variables d'espace réservé, vous pouvez personnaliser votre modèle de licence sans perturber les futures mises à jour de JCB.

---

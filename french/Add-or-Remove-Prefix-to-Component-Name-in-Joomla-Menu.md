> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="add-or-remove-prefix-to-component-name-in-joomla-menu"></a>
# Ajouter ou supprimer un préfixe au nom du composant dans le menu Joomla

Ce tutoriel explique la nouvelle fonctionnalité Joomla Component Builder (JCB) qui permet aux développeurs d'**ajouter ou de supprimer un préfixe** du nom du composant affiché dans le menu Joomla. Cette personnalisation vous aide à marquer ou à distinguer visuellement vos entrées de composants dans l'interface d'administration Joomla.

---

<a id="1-understanding-the-menu-prefix"></a>
## 1. Comprendre le préfixe du menu

[00:00:00](https://www.youtube.com/watch?v=vwZyhKp_L38&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

Dans les versions antérieures de JCB, les composants incluaient automatiquement un symbole de préfixe (comme une petite flèche) avant leur nom dans le menu d'administration de Joomla. Par exemple, votre composant peut apparaître comme :

```
Component Builder
```

Avec la nouvelle fonctionnalité, vous pouvez désormais **personnaliser ou supprimer entièrement ce préfixe**.

---

<a id="2-accessing-the-global-configuration"></a>
## 2. Accéder à la configuration globale

[00:00:26](https://www.youtube.com/watch?v=vwZyhKp_L38&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m26s)

1. Dans JCB, ouvrez votre composant.
2. Accédez à l'onglet **Global** dans la configuration du composant.
3. Recherchez le paramètre **Ajouter un préfixe de menu**.

Ici, vous pouvez :

* Définissez **"Non"** pour supprimer complètement le préfixe.
* Entrez une chaîne ou un symbole **préfixe personnalisé**.
* Laissez le champ tel quel pour utiliser la **flèche par défaut (>)**.

> **Conseil :** Vous n'avez pas besoin d'ajouter manuellement un espace après le préfixe : JCB en inclut automatiquement un.

---

<a id="3-using-html-character-entities-for-symbols"></a>
## 3. Utilisation d'entités de caractères HTML pour les symboles

[00:00:56](https://www.youtube.com/watch?v=vwZyhKp_L38&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m56s)

Étant donné que le préfixe est stocké dans un fichier XML, tous les caractères spéciaux ou non standard doivent être représentés sous forme d'**entités de caractères HTML**.

Par exemple:

* `&#9658;` → ►
* `&#10003;` → ✓
* `&#8857;` → ⊙

Vous pouvez trouver une liste complète des entités HTML ici :
[Référence des entités de caractères HTML (w3schools.com)](https://www.w3schools.com/html/html_entities.asp)

Vous pouvez également utiliser le **nom de votre entreprise** ou un court **préfixe de texte** au lieu d'un symbole. Par exemple:

```
JCB MyComponent
```

---

<a id="4-example-changing-the-prefix-symbol"></a>
## 4. Exemple : Changer le symbole du préfixe

[00:01:36](https://www.youtube.com/watch?v=vwZyhKp_L38&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m36s)

Pour démontrer, changeons le préfixe en un petit symbole circulaire :

1. Copiez l'entité HTML :

   ```
   &#8857;
   ```2. Collez-le dans le champ **Ajouter un préfixe de menu**.
3. Cliquez sur **Enregistrer et fermer**.
4. Compilez l'un de vos composants de démonstration.
5. Installez le package compilé dans Joomla.

**Résultat :**
Le nom du composant dans le menu Joomla apparaît désormais comme :

```
⊙ Demo
```

---

<a id="5-removing-the-prefix-entirely"></a>
## 5. Supprimer complètement le préfixe

[00:02:45](https://www.youtube.com/watch?v=vwZyhKp_L38&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m45s)

Si vous préférez un nom de menu clair sans aucun préfixe :

1. Définissez **Ajouter un préfixe de menu** sur **Non**.
2. Enregistrez vos paramètres.
3. Recompilez et installez votre composant.

Désormais, le composant apparaîtra simplement comme :

```
Demo
```

---

<a id="6-summary"></a>
## 6. Résumé

| Actions | Paramètre | Résultat |
| ----------------- | -------------------- | ----------------------------------------------------------------- |
| Ajouter un symbole personnalisé | `&#8857;` ou similaire | Affiche un préfixe personnalisé avant le nom du composant |
| Supprimer le préfixe | Réglé sur **Non** | Affiche uniquement le nom du composant |
| Utiliser le nom de l'entreprise | par ex. `MyCo` | Ajoute la marque avant le nom du composant |

---

<a id="helpful-tips"></a>
### Conseils utiles

* Utilisez toujours des **entités HTML valides** pour les symboles afin d'éviter les erreurs XML lors de la compilation.
* Vous pouvez modifier ce paramètre à tout moment sans affecter les autres parties de votre composant.
* Recompilez et réinstallez le composant après chaque modification pour voir les mises à jour dans le menu Joomla.

---

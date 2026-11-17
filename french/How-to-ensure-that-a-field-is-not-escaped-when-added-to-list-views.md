> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="how-to-ensure-that-a-field-is-not-escaped-when-added-to-list-views"></a>
# Comment s'assurer qu'un champ n'est pas échappé lorsqu'il est ajouté aux vues de liste

[Regarder le didacticiel](https://www.youtube.com/watch?v=bfl0l3AoLKU&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)

---

<a id="overview"></a>
## Aperçu

Parfois, lorsque vous travaillez avec des **Vues de liste** dans **Joomla Component Builder (JCB)**, vous souhaiterez peut-être ajouter un **style personnalisé** ou un **formatage HTML** directement dans une sortie de champ.
Cependant, par défaut, JCB **échappe à toutes les valeurs de champ** pour des raisons de sécurité, ce qui signifie que le HTML est rendu sous forme de texte brut.

Ce guide montre comment désactiver en toute sécurité l'échappement de champs pour des champs spécifiques, vous permettant d'inclure une sortie HTML telle que des étiquettes colorées ou des dates stylisées dans vos vues de liste.

---

<a id="1-understanding-field-escaping"></a>
## 1. Comprendre l'échappement de champ

[00:00:06](https://www.youtube.com/watch?v=bfl0l3AoLKU&t=00h00m06s)

Par défaut, Joomla **échappe** automatiquement les valeurs des champs dans les vues de liste pour empêcher l'injection de code malveillant (XSS).
Lorsque vous souhaitez afficher un **style basé sur HTML** (par exemple, `<span class="danger">Overdue</span>`), cet échappement empêche le rendu HTML correct.

Si vous remarquez que votre contenu stylisé apparaît sous forme de texte plutôt que de HTML, l'échappement est probablement activé dans ce champ.

---

<a id="2-example-scenario-adding-extra-styling-to-fields"></a>
## 2. Exemple de scénario : ajout d'un style supplémentaire aux champs

[00:00:31](https://www.youtube.com/watch?v=bfl0l3AoLKU&t=00h00m31s)

Dans ce didacticiel, la **Vue administrative des ordres de travail** est utilisée à titre d'exemple.
Dans la méthode `getItems()` (avant correction de traduction et décryptage), un extrait PHP est ajouté pour appliquer un style basé sur la couleur en fonction de valeurs sensibles au temps.

Cependant, ce n'est **pas l'emplacement idéal** pour modifier les données pour le rendu HTML, car l'échappement se produira toujours plus tard dans la compilation.

---

<a id="3-working-with-configuration-values"></a>
## 3. Travailler avec les valeurs de configuration

[00:00:58](https://www.youtube.com/watch?v=bfl0l3AoLKU&t=00h00m58s)

La configuration implique des **champs de configuration** qui définissent les seuils de temps « avertissement » et « danger » (par exemple, *3 semaines* et *1 semaine*).
Ces valeurs de configuration sont utilisées dans une logique qui détermine quand l'affichage d'un champ doit changer visuellement - par exemple, changer la date d'une tâche en rouge en cas de retard.

Cette logique implique généralement :

* Récupération de la date actuelle.
* En le comparant aux seuils de temps configurés.
* Ajout des noms de classe CSS correspondants comme `"warning"` ou `"danger"`.

---

<a id="4-looping-through-data-and-applying-styling"></a>
## 4. Parcourir les données et appliquer un style

[00:01:44](https://www.youtube.com/watch?v=bfl0l3AoLKU&t=00h01m44s)

Ensuite, parcourez l’ensemble de données et déterminez quels enregistrements doivent être marqués visuellement.
Par exemple, vous pourriez :

* Ajoutez une classe rouge pour les travaux en retard.
* Ajouter une classe jaune pour les échéances à venir.

Le code utilise une **méthode de classe d'assistance** appelée `fancyDate()` pour formater les dates SQL (par exemple, `2025-04-02`) dans des formats lisibles comme « 2 avril 2025 ».

Cependant, une fois le composant compilé et chargé, les balises HTML appliquées par cette méthode sont **échappées** et affichées sous forme de texte brut (par exemple, `&lt;span class="danger"&gt;Overdue&lt;/span&gt;`).

Cela se produit car la **méthode d'échappement Joomla** (`htmlspecialchars()`) s'exécute par défaut sur toutes les sorties des champs de liste.

---

<a id="5-preventing-html-escaping"></a>
## 5. Empêcher l'échappement HTML

[00:03:27](https://www.youtube.com/watch?v=bfl0l3AoLKU&t=00h03m27s)

Pour autoriser la sortie HTML dans votre vue liste :

1. Ouvrez la **vue backend de votre composant** dans JCB.

* Accédez à **Vues administrateur → Champs**.
   * Localisez le champ pertinent (par exemple, `job_status`).

2. Modifiez le champ et faites défiler jusqu'à la **zone de configuration avancée**.

3. Dans la **section code**, ajoutez l'attribut :

```php
escape="false"
```

4. Enregistrez vos modifications.

[00:04:09](https://www.youtube.com/watch?v=bfl0l3AoLKU&t=00h04m09s)

Lors de la compilation, JCB demandera désormais à Joomla de ne pas échapper à la sortie de ce champ, permettant ainsi à votre code HTML de s'afficher correctement.

---

<a id="6-recompiling-the-component"></a>
## 6. Recompiler le composant

[00:04:37](https://www.youtube.com/watch?v=bfl0l3AoLKU&t=00h04m37s)

Après avoir ajouté l'attribut `escape="false"` :

1. Recompilez votre composant dans JCB.
2. Installez ou mettez à jour le ZIP généré sur votre site Joomla.
3. Actualisez votre vue de liste pour voir l'affichage HTML formaté.

Vous devriez maintenant voir un résultat visuel approprié - par exemple, des dates surlignées en rouge ou des étiquettes d'avertissement affichant leurs styles prévus.

---

<a id="7-key-takeaways"></a>
## 7. Points clés à retenir

[00:05:15](https://www.youtube.com/watch?v=bfl0l3AoLKU&t=00h05m15s)

* Joomla échappe aux sorties de champ par défaut pour améliorer la sécurité.
* Pour afficher le HTML en toute sécurité, définissez `escape="false"` sur ce champ spécifique dans JCB.
* Ce paramètre indique à Joomla! d'afficher la valeur du champ *telle quelle*, sans l'exécuter via le filtre d'échappement.
* Utilisez cette fonctionnalité de manière sélective, en vous assurant que seul le contenu fiable généré par le système est affiché sans échappement.

---

<a id="tips-for-safe-use"></a>
## Conseils pour une utilisation en toute sécurité

* **Évitez les saisies utilisateur sans échappement.** Désactivez l'échappement uniquement pour les champs dont le contenu est contrôlé par le système (par exemple, généré par programme ou à partir de sources fiables).
* **Utilisez des classes d'assistance** comme `fancyDate()` pour formater et nettoyer les données avant la sortie.
* **Testez minutieusement** pour confirmer que votre HTML s'affiche correctement et n'introduit pas de problèmes de mise en page.

---

<a id="conclusion"></a>
## Conclusion

Vous avez maintenant appris comment faire en sorte qu'un champ Joomla Component Builder affiche la sortie HTML directement dans la vue liste en désactivant l'échappement.
Cette technique est utile pour les indicateurs visuels tels que les statuts colorés, les badges ou d'autres représentations de données stylisées au sein de votre interface d'administration Joomla.

---

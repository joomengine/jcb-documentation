> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="component-scripts"></a>
# **Scripts de composants**

[Regardez la vidéo sur YouTube](https://www.youtube.com/watch?v=xY9TWQrF8AQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(*Cliquez sur n'importe quel horodatage ci-dessous pour accéder à ce moment dans la vidéo.*)

---

<a id="overview"></a>
## **Aperçu**

Dans ce didacticiel, nous explorons l'**onglet Scripts** dans **Joomla Component Builder (JCB)**.
Cette section permet aux développeurs d'ajouter des **scripts globaux personnalisés** à leurs composants, notamment des méthodes d'assistance, des bibliothèques CSS, JavaScript, des dumps MySQL et l'intégration des données du tableau de bord.

Ces options vous permettent d'étendre les fonctionnalités de votre composant **sans modifier la logique principale de JCB**, permettant ainsi un meilleur contrôle et une meilleure maintenabilité.

---

<a id="1-the-scripts-tab-overview"></a>
## **1. Présentation de l'onglet Scripts**

[00:00:00](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h00m00s)

L'**onglet Scripts** de JCB vous permet d'intégrer des scripts personnalisés dans votre composant dans une portée **globale ou par vue**.
Ici, vous pouvez :

* Ajouter des méthodes d'assistance PHP.
* Chargez les bibliothèques CSS et JavaScript (comme UIKit ou FooTable).
* Incluez les événements CSS ou admin globaux.
* Ajoutez des dumps MySQL.
* Créez des méthodes de tableau de bord pour remplir dynamiquement les données backend.

Cet onglet est destiné principalement aux développeurs qui souhaitent injecter de la logique directement dans le composant.

---

<a id="2-create-user-helper-method"></a>
## **2. Créer une méthode d'assistance utilisateur**

[00:00:47](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h00m47s)

La **méthode d'assistance utilisateur** vous permet d'écrire des **fonctions PHP personnalisées** qui étendent les fonctionnalités de votre composant.

> **Remarque :**
> Cette fonctionnalité s'adresse aux développeurs à l'aise avec PHP.
> JCB ne générera pas de logique automatiquement - vous devrez la scripter.

<a id="example-creating-a-user-automatically"></a>
### **Exemple : Création automatique d'un utilisateur**

[00:01:29](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h01m29s)

En utilisant l'**outil de projection coûts-avantages** comme exemple :

* Dans la vue d'administration "Entreprise", lors de l'ajout d'une nouvelle entreprise, si un utilisateur n'est pas sélectionné mais qu'un email est renseigné, le composant peut **créer automatiquement un utilisateur Joomla**.
* La méthode d'assistance définit comment cet utilisateur est créé et lié.

Ce comportement est déclenché dans la méthode `postSaveHook()` du contrôleur.

---

<a id="locating-the-postsavehook"></a>
### **Localisation du PostSaveHook**

[00:02:38](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h02m38s)

Dans la vue administrateur du composant :

1. Accédez à **Vue Administrateur → onglet PHP**.
2. Localisez la méthode `postSaveHook`.
3. C'est ici que vous pouvez exécuter une logique personnalisée après la sauvegarde d'un enregistrement.

Au sein de la méthode :

```php
if (!$userExists) {
    $userId = [[[Component]]]Helper::create_user($validData);
}
```

* L'espace réservé `[[[Component]]]` sera remplacé par le nom de code de votre composant.
* La méthode d'assistance `create_user` est définie dans la classe d'assistance de votre composant.

---

<a id="helper-class-implementation"></a>
### **Implémentation de la classe d'assistance**

[00:04:13](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h04m13s)

Dans la classe d'assistance (par exemple, `costbenefitprojectionHelper`), créez votre fonction d'assistance :

```php
public static function create_user($validData)
{
    // Generate password if none provided
    if (empty($validData['password'])) {
        $validData['password'] = self::randomString();
    }

    // Create Joomla user
    $user = new JUser;
    if (!$user->bind($validData)) {
        return false;
    }

    $user->save();
    return $user->id;
}
```

Cette méthode :

* Génère un mot de passe s'il n'en existe pas.
* Crée et enregistre l'utilisateur Joomla.
* Renvoie l'ID du nouvel utilisateur.

[00:06:41](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h06m41s)

Après enregistrement, l'identifiant est stocké dans le dossier de l'entreprise, reliant automatiquement l'utilisateur et l'entreprise.

---

<a id="3-add-uikit-and-footable-libraries"></a>
## **3. Ajouter les bibliothèques UIKit et FooTable**

[00:07:01](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h07m01s)

Vous pouvez activer les frameworks CSS/JS populaires avec une bascule :

* **UIKit** : ajoute automatiquement des composants d'interface utilisateur réactifs.
* **FooTable** : Active les tableaux dynamiques.

Ces bibliothèques sont automatiquement incluses dans votre dossier multimédia et liées dans votre composant.

> **Conseil :**
> Vous n'avez pas besoin de les mettre manuellement en file d'attente - JCB gère cela de manière dynamique.

---

<a id="4-add-global-css-for-the-admin-backend"></a>
## **4. Ajouter du CSS global pour le backend d'administration**

[00:07:32](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h07m32s)

Si vous souhaitez personnaliser globalement votre interface d'administration :

* Ajoutez votre CSS dans cette section.
* Cela s'appliquera à **toutes les vues d'administration** de votre composant.

Exemple:

```css
.icon-48-dashboard {
    color: #4CAF50;
}
```

---

<a id="5-add-custom-php-helper-admin-class"></a>
## **5. Ajouter une classe d'administration d'assistance PHP personnalisée**

[00:07:46](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h07m46s)

Ce champ vous permet d'injecter du code PHP personnalisé dans votre **classe Helper_Admin**, tel que :

* Utilitaires d'administration personnalisés
* Déclencheurs d'événements
* Fonctions d'assistance pour les scripts backend

---

<a id="6-add-global-admin-event"></a>
## **6. Ajouter un événement d'administration global**

[00:08:03](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h08m03s)

Le commutateur **Global Admin Event** vous permet d'ajouter des fonctions qui s'exécutent **à chaque chargement de page backend**.

Lorsqu'il est activé :

* JCB déclenche une fonction d'événement global prédéfinie.
* Vous pouvez y placer n'importe quelle tâche d'administration répétitive.

Exemple:

```php
public static function loadDropboxAjax($doc)
{
    $script = "console.log('Dropbox Ajax Loaded');";
    $doc->addScriptDeclaration($script);
}
```

Cela injectera le script globalement dans les vues backend.

[00:10:59](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h10m59s)

Ceci est idéal pour les tâches d'automatisation telles que la synchronisation des données, la vérification des mises à jour de Dropbox ou le chargement dynamique d'actifs.

---

<a id="7-add-custom-php-helper-site-view"></a>
## **7. Ajouter une vue de site d'assistance PHP personnalisée**

[00:11:44](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h11m44s)

Les assistants frontaux diffèrent de ceux des administrateurs pour la **sécurité et le contrôle d'accès**.
Vous pouvez ajouter des méthodes d'assistance spécifiques au front-end, garantissant que seule la logique sécurisée s'exécute publiquement.

Exemple d'utilisation :

* Synchronisation des données utilisateur.
* Exécution des mises à jour Ajax en toute sécurité sur le front-end.

---

<a id="8-add-mysql-dump"></a>
## **8. Ajouter un vidage MySQL**

[00:13:49](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h13m49s)

Vous pouvez importer des **fichiers de vidage SQL** ici plutôt que par vue.
Ceci est utile pour :

* Tableaux de préchargement.
* Ajout de données par défaut lors de l'installation.

> **Remarque :**
> Évitez d'ajouter deux fois le même SQL ; JCB fusionne toutes les sauvegardes en un seul fichier d'installation.

---

<a id="9-dashboard-methods"></a>
## **9. Méthodes du tableau de bord**

[00:14:23](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h14m23s)

**Méthodes de tableau de bord** vous permettent d'afficher des données dynamiques directement sur le tableau de bord backend du composant - aucune vue supplémentaire n'est nécessaire.

Exemple : Afficher les statistiques d'utilisation.

```php
public function getUsageData()
{
    // Custom data logic
    return $this->calculateUsage();
}
```

Convention:

* Les méthodes commençant par `get` deviennent automatiquement disponibles sous le nom `$this->usagedata`.
* Le préfixe "get" est supprimé et la partie restante est mise en minuscules.

So `getUsageData()` → `$this->usagedata`.

Vous pouvez le référencer en HTML comme :

```php
<?php if ($this->usagedata): ?>
  <table>
    <!-- display data -->
  </table>
<?php endif; ?>
```

---

<a id="10-adding-data-to-a-page"></a>
## **10. Ajouter des données à une page**

[00:18:06](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h18m06s)

Vous pouvez utiliser des méthodes de tableau de bord pour préparer et transmettre des données à la vue :

* Renvoie des tableaux ou des objets.
* Parcourez-les dans des modèles HTML.

Alternativement, vous pouvez utiliser du PHP simple ou même simplement du HTML pour les éléments statiques du tableau de bord, tels que :

* Notes du développeur.
* Flux RSS.
* Informations sur les composants.

[00:20:34](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h20m34s)

Exemple:

```php
<?php echo $this->rssfeed; ?>
```

---

<a id="conclusion"></a>
## **Conclusion**

[00:21:27](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h21m27s)

L'**onglet Scripts** offre aux développeurs avancés un cadre flexible pour :

* Ajoutez une logique au-delà du code généré automatiquement.
* Étendre les assistants et les contrôleurs.
* Chargez des données dynamiques et un style.
* Automatisez les tâches via des événements mondiaux.

S'il est utilisé à bon escient, il transforme JCB en un **puissant cadre d'application rapide** capable de gérer de manière transparente une logique personnalisée sophistiquée au sein de Joomla.

---

<a id="summary-of-key-script-areas"></a>
### **Résumé des domaines clés du script**

| Fonctionnalité | Objectif |
| ------------------ | ------------------------------------ |
| Aide utilisateur | Automatisez les actions liées aux utilisateurs |
| UIKit/FooTable | Ajouter des bibliothèques d'interface utilisateur frontale |
| CSS global | Styliser toutes les pages d'administration |
| Assistant Administrateur/Site | Étendre la logique pour le backend ou le frontend |
| Événement d'administration globale | Exécuter des scripts sur les pages backend |
| Décharge MySQL | Charger les données par défaut |
| Méthodes du tableau de bord | Afficher les données dynamiques dans le panneau d'administration |

---

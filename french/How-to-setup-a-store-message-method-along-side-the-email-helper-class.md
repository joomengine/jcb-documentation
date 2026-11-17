> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="how-to-set-up-a-store-message-method-alongside-the-email-helper-class"></a>
# Comment configurer une méthode de message de magasin en plus de la classe d'assistance par courrier électronique

[00:00:00](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(*Cliquez sur les horodatages pour afficher les sections correspondantes dans la vidéo.*)

---

<a id="1-overview"></a>
## 1. Aperçu

Dans Joomla Component Builder (JCB), la **Email Helper Class** permet aux développeurs d'envoyer des e-mails personnalisés à partir de leurs composants. Cependant, il existe des scénarios dans lesquels vous souhaiterez peut-être **stocker le message envoyé** à des fins de tenue d'enregistrements ou de flux de travail avancés.

Ce tutoriel montre comment :

* Étendez la classe Email Helper pour inclure une **méthode de stockage de messages**.
* Configurez votre composant pour enregistrer et gérer les messages sortants.

---

<a id="2-understanding-the-email-helper-class"></a>
## 2. Comprendre la classe Email Helper

[00:00:24](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m24s)

La **Classe d'assistance de messagerie** est automatiquement placée dans le dossier d'assistance backend de votre composant.
Son chemin suit ce schéma :

```
administrator/components/com_[component_name]/helpers/email.php
```

Par exemple, si votre composant s'appelle **Jobtracking**, la classe d'assistance est :

```
administrator/components/com_jobtracking/helpers/email.php
```

Pour appeler l'assistant de messagerie dans votre **script personnalisé**, utilisez la syntaxe à trois crochets :

```php
[[[component]]]email.send($data);
```

[00:00:59](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m59s)
Cette syntaxe demande à JCB de localiser et d'exécuter la classe d'assistance de messagerie de manière dynamique lors de la compilation de votre composant.

---

<a id="3-the-send-method-and-its-role"></a>
## 3. La méthode "Send" et son rôle

[00:01:17](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m17s)

Dans la **Email Helper Class**, il existe une méthode `send()` qui gère le processus d'envoi d'un e-mail.
Lorsque l'e-mail est envoyé avec succès, le résultat est stocké dans une variable telle que `$sendEmail`.

[00:01:47](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m47s)
À la fin de cette méthode, JCB vous permet d'appeler une autre méthode d'assistance - **si elle existe ** - pour effectuer des actions supplémentaires après l'envoi de l'e-mail (comme la journalisation ou le stockage).

Cette vérification s'effectue à l'aide de :

```php
if (method_exists('JobtrackingHelper', 'storeMessage'))
```

Cela garantit que la méthode `storeMessage()` n'est appelée que si elle a été explicitement définie dans **Admin Helper** de votre composant.

---

<a id="4-adding-the-storemessage-method"></a>
## 4. Ajout de la méthode `storeMessage()`

[00:02:19](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m19s)

<a id="step-1-access-the-admin-helper-in-jcb"></a>
### Étape 1 : Accédez à l'assistant d'administration dans JCB

1. Ouvrez **Joomla Component Builder**.
2. Accédez à votre composant.
3. Accédez à **"Libs & Helpers"** dans le menu de gauche.
4. Faites défiler jusqu'à **Ajouter PHP (admin_helper)**.

[00:02:47](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m47s)

<a id="step-2-create-the-storemessage-function"></a>
### Étape 2 : Créer la fonction `storeMessage()`

Ajoutez la fonction suivante dans la zone **Admin Helper** :

```php
public static function storeMessage($subject = null, $body = null, $recipient = null, $headers = null, $attachments = null)
{
    // Example: Save email data to a custom database table or log file
}
```

<a id="step-3-understand-parameter-defaults"></a>
### Étape 3 : Comprendre les valeurs par défaut des paramètres

[00:03:19](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m19s)

Chaque paramètre de la signature de fonction a une **valeur par défaut de `= null`**, garantissant que la méthode s'exécute même si certains arguments ne sont pas transmis.

Les paramètres typiques incluent :

* `$subject` - La ligne d'objet de l'e-mail envoyé.
* `$body` - Le contenu du corps du message.
* `$recipient` - L'adresse e-mail du destinataire.
* `$headers` - En-têtes facultatifs utilisés dans l'e-mail.
* `$attachments` - Tous les fichiers joints.

Dans la plupart des cas, vous n'avez besoin de gérer que les **quatre premières valeurs**.

---

<a id="5-integrating-the-method-into-email-helper"></a>
## 5. Intégration de la méthode dans Email Helper

[00:04:17](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m17s)

La méthode `send()` d'Email Helper vérifie l'existence de `storeMessage()` et, si elle est trouvée, transmet les variables pertinentes :

```php
if (method_exists('JobtrackingHelper', 'storeMessage')) {
    JobtrackingHelper::storeMessage($subject, $body, $recipient, $headers, $attachments);
}
```

[00:04:52](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m52s)
Si la méthode **n'existe pas**, elle ignore simplement cette partie et renvoie le résultat `$sendEmail`.
S'il **existe**, il exécute la méthode `storeMessage()`, vous permettant de gérer ou d'enregistrer les données de courrier électronique de manière dynamique.

---

<a id="6-using-user-information-with-getvar"></a>
## 6. Utilisation des informations utilisateur avec `getVar()`

[00:05:09](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m09s)

Pour associer les messages stockés à des utilisateurs Joomla spécifiques :

* Utilisez la méthode `getVar()` de la **Classe utilisateur**.
* Faites correspondre le destinataire de l'e-mail à l'enregistrement de l'utilisateur et récupérez l'ID utilisateur.

Exemple:

```php
$userId = JFactory::getUser()->getVar('id', 'email', $recipient);
```

Une fois que vous disposez du `$userId`, vous pouvez lier le message stocké à cet enregistrement utilisateur dans votre base de données.

---

<a id="7-storing-the-message"></a>
## 7. Stockage du message

[00:05:38](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m38s)

Vous pouvez désormais :

* Stockez les messages dans une **table de base de données personnalisée** (par exemple, `#__jobtracking_messages`).
* Incluez des champs tels que :

* Identifiant du message
  *Identifiant utilisateur
  * Sujet
  * Corps
  *Date d'envoi
  * Statut (par exemple, succès/échec)

La méthode `storeMessage()` vous donne un contrôle total pour :

* Enregistrez les journaux de courrier électronique.
* Gérer les résultats de livraison.
* Étendez les fonctionnalités des composants au-delà du simple envoi.

---

<a id="8-summary-and-best-practices"></a>
## 8. Résumé et meilleures pratiques

* Toujours **définissez `storeMessage()`** dans votre assistant d'administration si vous prévoyez de suivre ou de stocker des e-mails.
* Utilisez **les valeurs des paramètres par défaut (`= null`)** pour éviter les erreurs d'exécution.
* Utilisez le contrôle `method_exists()` pour garantir une exécution sûre.
* Combinez cette approche avec les méthodes natives de **logging ou de stockage de base de données** de Joomla pour plus de fiabilité.
* Gardez votre code modulaire - évitez de placer la logique directement dans Email Helper.

---

<a id="9-practical-use-case"></a>
## 9. Cas d'utilisation pratique

Un cas d'utilisation typique pourrait être un **système de notification** automatisé :

* Lorsqu'une action de l'utilisateur déclenche un e-mail (par exemple, mise à jour d'une tâche ou soumission d'un formulaire),
* Le message est envoyé à l'aide de l'Email Helper,
* Puis stocké via `storeMessage()` pour un suivi d'audit ou un examen ultérieur.

---

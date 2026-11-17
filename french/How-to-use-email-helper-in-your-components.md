> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="how-to-use-the-email-helper-in-your-components"></a>
# Comment utiliser l'assistant de messagerie dans vos composants

**Référence du didacticiel :** [Vidéo - Comment utiliser Email Helper dans vos composants](https://www.youtube.com/watch?v=tp6mMUTOF2Y)

<a id="1-introduction-to-the-email-helper-class"></a>
## 1. Introduction à la classe Email Helper

[00:00:00](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h00m00s)

La **Classe d'assistance de courrier électronique** dans Joomla Component Builder (JCB) est une classe réutilisable située dans la section **Helpers** d'un composant. Il permet aux développeurs d'envoyer facilement des e-mails depuis n'importe quelle partie de leur composant.

* Le fichier d'assistance est généralement nommé `email.php`.
* Il étend la classe d'assistance abstraite de JCB.
* Il utilise le courrier intégré de Joomla (`JMail`) pour préparer et envoyer des messages.

**Comment ça marche :**
Lorsqu'un e-mail est envoyé, l'assistant crée une instance du mailer de Joomla, charge les variables nécessaires et envoie le message avec la configuration appropriée.

---

<a id="2-setting-up-the-email-helper-class"></a>
## 2. Configuration de la classe d'assistance par courrier électronique

[00:01:02](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h01m02s)

1. Depuis votre **Component Builder Dashboard**, ouvrez votre composant (par exemple, Learning Manager).
2. Accédez à **Libs & Helpers** dans la section d'édition.
3. Tournez **Ajouter un assistant de messagerie** sur **Oui**.

> **Remarque :**
> L'activation de cette option ajoute la classe Email Helper à votre composant, mais elle n'implémente pas automatiquement la fonctionnalité de messagerie. Vous devrez toujours configurer les paramètres et les champs associés.

---

<a id="3-adding-mail-configuration-fields-in-component-settings"></a>
## 3. Ajout de champs de configuration de messagerie dans les paramètres du composant

[00:01:47](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h01m47s)

Pour personnaliser les paramètres de messagerie de votre composant, vous devez ajouter des **champs de configuration personnalisés**.

1. Accédez aux **Paramètres** > **Zone de configuration** de votre composant.
2. Cliquez sur **Ajouter un champ de configuration**.
3. Faites défiler vers le bas pour trouver la section **Configuration de la messagerie**.
4. Recréez les champs liés au courrier similaires à ceux de la configuration globale de Joomla (trouvé dans `configuration.xml`).

Ceux-ci incluent :

* Type de courrier (`mailer`)
* Du nom
* Depuis un e-mail
* Adresse de réponse
* Hôte SMTP, port, nom d'utilisateur, mot de passe, etc.
* Champs DKIM (facultatif mais recommandé)

> **Conseil :**
> Vous pouvez consulter le fichier de configuration par défaut de Joomla pour faire correspondre correctement les noms de champs. L'attribut "name" est l'identifiant de clé utilisé dans le code.

---

<a id="4-understanding-field-names-in-code"></a>
## 4. Comprendre les noms de champs dans le code

[00:02:45](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h02m45s)

Chaque champ de configuration comprend :

* **Nom** - utilisé dans le code (par exemple, `mailer`, `smtp_host`)
* **Étiquette** - visible dans l'interface utilisateur
* **Description** - explique l'objectif du champ

Lorsque vous écrivez du code, assurez-vous que le **nom du champ** correspond exactement à ce qui est déclaré dans le XML de votre composant.

---

<a id="5-configuring-the-component-mailer-options"></a>
## 5. Configuration des options du composant Mailer

[00:03:35](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h03m35s)

Dans l'onglet **Options** de votre composant, vous trouverez une section **Configuration du courrier**.
Ici, vous pouvez :

* Activer/désactiver le mailing via le **Mailer Switch** (`On` ou `Off`)
* Remplacer les paramètres de messagerie globaux de Joomla (si vous le souhaitez)
* Définir la configuration DKIM pour l'authentification par courrier électronique

Si vous choisissez **Global**, le composant utilisera les paramètres de messagerie par défaut de Joomla.

---

<a id="6-joomla-global-mail-settings"></a>
## 6. Paramètres de messagerie globale de Joomla

[00:04:10](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h04m10s)

Si vous n'avez pas configuré les champs de messagerie de votre composant, JCB utilisera **Configuration globale Joomla → Serveur → Paramètres de messagerie**.

Ceux-ci incluent :

* Type de courrier mondial
* De l'adresse et du nom
* Paramètres SMTP
*Configuration DKIM

Tout composant sans sa propre configuration de messagerie reviendra à ces paramètres à l'échelle de Joomla.

---

<a id="7-component-level-email-overrides"></a>
## 7. Remplacements d'e-mails au niveau des composants

[00:05:08](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h05m08s)

Lorsque l'option **Global** est désactivée**, votre composant peut définir ses propres paramètres de messagerie (identifiants SMTP, type de courrier, etc.).
Ceci est particulièrement utile si votre composant doit envoyer des e-mails via un autre serveur de messagerie.

---

<a id="8-dkim-configuration-and-encryption"></a>
## 8. Configuration et cryptage DKIM

[00:05:40](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h05m40s)

DKIM (DomainKeys Identified Mail) ajoute une authentification à vos e-mails, réduisant ainsi le risque de spam.

Pour utiliser DKIM :

1. Activez **Utiliser DKIM** dans votre configuration de messagerie.
2. Fournissez :

* Clé privée
   * Clé publique
   * Sélecteur
   * Domaine

Si DKIM est défini sur « Oui » mais que des valeurs sont manquantes, il ne sera pas appliqué.

> **Recommandation :**
> Consultez la documentation `JMail` DKIM de Joomla pour plus de détails sur la mise en œuvre avancée.

---

<a id="9-how-the-helper-works-in-code"></a>
## 9. Comment fonctionne l'assistant dans le code

[00:07:15](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h07m15s)

Dans votre code d'assistance, le mailer est obtenu à partir de la configuration du composant.
Si `mailer` est défini sur **global**, la configuration de Joomla est utilisée. Sinon, les paramètres personnalisés du composant s'appliquent.

La méthode **`send()`** gère :

* Configuration du destinataire
* Contenu du sujet et du corps
* Configuration du courrier
* Gestion et journalisation des erreurs

> **Conseil sur les performances :**
> Bien que capable d'envoyer plusieurs e-mails à la fois, tenez toujours compte des limites de votre serveur pour éviter les problèmes de spam.

---

<a id="10-handling-dkim-and-mailer-in-code"></a>
## 10. Gestion de DKIM et Mailer dans le code

[00:08:40](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h08m40s)

Les valeurs DKIM sont injectées dans l'instance `$mailer` avant l'envoi.
JCB utilise la classe étendue `JMailer` de Joomla, vous permettant de configurer les options de messagerie avancées en toute sécurité.

---

<a id="11-error-checking-and-message-storage"></a>
## 11. Vérification des erreurs et stockage des messages

[00:09:12](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h09m12s)

L'assistant inclut une gestion intégrée des erreurs.
Si l'envoi échoue, il vérifie si l'assistant de votre composant (`componentnamehelper.php`) dispose d'une méthode **`storeMessage()`**.

Cette méthode personnalisée :

* Enregistre ou stocke les messages envoyés via votre composant.
* Peut également enregistrer des messages réussis pour l'accès des utilisateurs.

**Exemple de signature :**

```php
storeMessage($recipient, $subject, $body, $type = 'email')
```

Cela permet aux utilisateurs de visualiser ultérieurement les messages qui leur sont envoyés, créant ainsi une piste d'audit complète au sein de votre composant.

---

<a id="12-implementing-the-email-helper-in-a-component"></a>
## 12. Implémentation de l'assistant de messagerie dans un composant

[00:11:39](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h11m39s)

**Exemple :**
Dans le **Système de suivi des tâches**, des e-mails sont envoyés lorsqu'une **Commande de travail** est créée.

1. Activez **Ajouter un assistant de messagerie** dans les paramètres de votre composant.
2. Dans votre **Vue administrateur**, ajoutez un bouton **Envoyer un e-mail** (par exemple, dans le formulaire de commande de travail).
3. Le bouton déclenche la tâche `sendEmail`.

Lorsque l'utilisateur clique sur le bouton :

* Le composant envoie l'e-mail au client (par exemple, `testing@vdm.io`).
* Un message de confirmation apparaît dans le coin supérieur droit.

---

<a id="13-code-level-implementation-example"></a>
## 13. Exemple d'implémentation au niveau du code

[00:13:40](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h13m40s)

La vue d'administration ** Ordre de travail ** inclut une fonction JavaScript qui appelle une tâche de contrôleur PHP :

<a id="frontend-javascript"></a>
### JavaScript frontal

```javascript
function sendEmail() {
    Joomla.request({
        url: 'index.php?option=com_joborder&task=sendEmail',
        method: 'POST',
        data: { email: recipientEmail },
        onSuccess: function(response) {
            Joomla.renderMessages({ success: [response.message] });
        }
    });
}
```

<a id="controller-php"></a>
### Contrôleur (PHP)

```php
public function sendEmail()
{
    $model = $this->getModel('Ajax');
    $result = $model->sendEmail($this->input);
    echo json_encode($result);
    JFactory::getApplication()->close();
}
```

<a id="model-method"></a>
### Méthode modèle

```php
public function sendEmail($input)
{
    $mail = Helper::get('email');
    $result = $mail->send($to, $subject, $body, true);
    return $result ? ['success' => true] : ['error' => 'Failed to send email'];
}
```

Ce flux :

1. JS déclenche la requête Ajax.
2. Le contrôleur gère la tâche `sendEmail`.
3. Le modèle utilise **Email Helper** pour envoyer du courrier.

---

<a id="14-final-notes"></a>
## 14. Notes finales

[00:17:43](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h17m43s)

La **Email Helper Class** simplifie l'envoi de courrier au sein de votre composant tout en conservant la flexibilité et la cohérence avec les standards Joomla.

**Avantages:**

* Logique de messagerie centralisée
* Prise en charge configurable DKIM et SMTP
* Intégration transparente avec Joomla Global Config
* Journalisation extensible et stockage des messages

---

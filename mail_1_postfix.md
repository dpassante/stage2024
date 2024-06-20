### Travaux Pratiques: Mise en Place d'un Serveur Mail et Envoi de Mails avec Postfix

**Objectif:** Ce TP vise à vous initier au fonctionnement des serveurs mail en configurant un serveur mail simple avec Postfix sur une machine virtuelle Linux, et à pratiquer l'envoi et la réception de mails, y compris l'envoi d'un email réel à votre propre boîte mail.

**Durée estimée:** 1 à 2 heures

**Prérequis:**
- Accès à une machine virtuelle Linux (Ubuntu de préférence).
- Droits de superutilisateur sur la machine.

**Instructions détaillées:**

1. **Installation de Postfix:**
   - Connectez-vous à votre machine virtuelle Linux.
   - Mettez à jour les paquets existants :
     ```
     sudo apt update
     sudo apt upgrade
     ```
   - Installez Postfix en exécutant :
     ```
     sudo apt install postfix
     ```
   - Pendant l'installation, sélectionnez "Site Internet" pour le type de configuration mail.
   - Pour le nom de mail, utilisez le nom de domaine de votre VM ou, si vous n'en avez pas, utilisez le nom d'hôte de la VM.

2. **Configuration de Postfix:**
   - Éditez le fichier de configuration de Postfix :
     ```
     sudo nano /etc/postfix/main.cf
     ```
   - Assurez-vous que les lignes suivantes sont configurées avec les bonnes valeurs (remplacez `yourdomain.com` par votre domaine ou nom d'hôte) :
     ```
     myhostname = yourdomain.com
     mydestination = $myhostname, localhost.$mydomain, $mydomain
     mynetworks = 127.0.0.0/8
     ```
   - Redémarrez Postfix pour appliquer les changements :
     ```
     sudo systemctl restart postfix
     ```

3. **Test d'envoi de mail en local:**
   - Envoyez un email de test à l'utilisateur local (remplacez `username` par votre nom d'utilisateur sur la VM) :
     ```
     echo "Test email body" | mail -s "Test Email Subject" username@localhost
     ```
   - Vérifiez que le mail a été reçu :
     ```
     mail
     ```

4. **Configuration pour envoyer des mails à l'extérieur:**
   - Pour envoyer des emails à des adresses externes, vous aurez besoin de configurer Postfix pour utiliser un serveur SMTP comme relais. Si vous avez un compte Gmail, vous pouvez utiliser le SMTP de Gmail.
   - Éditez à nouveau `/etc/postfix/main.cf` et ajoutez :
     ```
     relayhost = [smtp.gmail.com]:587
     smtp_use_tls = yes
     smtp_sasl_auth_enable = yes
     smtp_sasl_security_options = noanonymous
     smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
     smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
     ```
   - Créez le fichier `sasl_passwd` dans `/etc/postfix/` et ajoutez votre nom d'utilisateur et mot de passe Gmail :
     ```
     sudo nano /etc/postfix/sasl_passwd
     [smtp.gmail.com]:587 username@gmail.com:password
     ```
   - Sécurisez et mettez à jour les tables de Postfix :
     ```
     sudo postmap /etc/postfix/sasl_passwd
     sudo chmod 600 /etc/postfix/sasl_passwd
     sudo systemctl restart postfix
     ```

5. **Envoyer un email réel:**
   - Envoyez un email à votre propre adresse email externe pour tester :
     ```
     echo "Ceci est un test d'envoi d'email via Postfix" | mail -s "Test Postfix" your-email@example.com
     ```
   - Vérifiez votre boîte de réception pour voir si vous avez reçu l'email.

**Résultat attendu:**
- Vous avez configuré un serveur mail simple sur une machine virtuelle Linux.
- Vous avez pratiqué l'envoi et la réception de mails en local.
- Vous avez configuré Postfix pour envoyer des emails à l'extérieur et testé en envoyant un email à votre propre adresse.

**Pour aller plus loin:**
- Explorez la configuration de la sécurité avec SPF, DKIM et DMARC pour améliorer la fiabilité de votre serveur mail.
- Essayez d'installer et de configurer un client mail graphique comme Thunderbird pour gérer les mails sur votre serveur.

Ce TP vous offre une introduction pratique à la configuration et à la gestion d'un serveur mail avec Postfix. Vous êtes maintenant mieux préparé pour gérer des configurations de serveur mail plus complexes et sécurisées. Bon apprentissage!

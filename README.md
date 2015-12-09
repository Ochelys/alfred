# Alfred

![Alfred](https://raw.githubusercontent.com/Ochelys/alfred/master/alfred.jpg)

## À propos

Alfred est un des serveurs d'applications d'[Ochelys](http://www.ochelys.com/).  
Il nous met à disposition quelques outils sympas encapsulés dans des conteneurs. Merci [Docker](https://www.docker.com/) ♥

## Applications

Alfred est un mec sympa et te met à disposition les applications ci-dessous.

_Si tu veux ajouter ton application préférée, tu peux créer une issue ou, encore mieux, nous faire une PR._

* Docker
* [Exim](http://www.exim.org/)

### Base de données

* [MySQL](https://registry.hub.docker.com/_/mysql/)

### Moteur de recherche

* [Elasticsearch](https://hub.docker.com/_/elasticsearch/)

### Serveur HTTP

* [Nginx](http://nginx.org/)

### Outils

* Htop
* Tmux
* Vim
* Backup-manager

### Supervision & Sécurité

* Logwatch
* Apticron
* Fail2ban

## Pré-requis

* [Ansible](http://docs.ansible.com/) (>= 1.8)

## En local

Dans le cas où tu voudrais un Alfred (rien qu'à toi) en local, on a tout prévu.

### Pré-requis

* [Vagrant](http://www.vagrantup.com/) (>= 1.7)
* [VirtualBox](https://www.virtualbox.org/) (>= 4.3)

### Installation du serveur

```sh
$ vagrant up
```

## Sur un serveur de production

Tu veux tout ça sur ton serveur de production mais tu ne sais pas comment faire ?  
Très simple. Un fichier de configuration, une ligne de commande et on en parle plus.

### Configuration

Ce fichier de configuration va te servir à surcharger les variables par défaut du playbook.

Tu peux nommer ce fichier `hosts.prod`, par exemple, et le sauvegarder dans ton petit endroit secret.

```ini
[alfred]
alfred.ma-super-entreprise.com

[alfred:vars]
mysql_root_password=change-me
apticron_email_to=alertes-technique@ma-super-entreprise.com
apticron_email_from=root@alfred.ma-super-entreprise.com
logwatch_email_to=alertes-technique@ma-super-entreprise.com
logwatch_email_from=root@alfred.ma-super-entreprise.com
alfred_hostname=alfred.ma-super-entreprise.com
alfred_hostname_local=alfred
backup_dir=/backups/alfred
backup_email_to=alertes-technique@ma-super-entreprise.com
fail2ban_email_to=alertes-technique@ma-super-entreprise.com
smtp_domain=ma-super-entreprise.com
```

### Provisonnement du serveur

Tu peux commencer à créer manuellement, sur ton serveur, un utilisateur sudoer qui sera utilisé par Ansible pour se connecter et effectuer le provisionnement.  
Alors, certes, je te vois venir. Ce n'est pas obligatoire et tu vas me dire que tu peux utiliser le compte `root`. Oui, mais non. Pour une question de sécurité, il est préférable de [désactiver la connexion au compte root via SSH](http://www.howtogeek.com/howto/linux/security-tip-disable-root-ssh-login-on-linux/).

```sh
$ ansible-playbook --inventory-file=/path/to/hosts.prod --user=chucknorris --sudo --ask-sudo-pass playbook.yml
```

## Contribution & Remerciements

Sens-toi libre de forker et de t'approprier le projet.  
Si tu souhaites nous faire une [pull request](https://help.github.com/articles/using-pull-requests/) pour corriger un truc qui te choque ou soumettre une application, tu es le bienvenu. Fais le sans pression.

Tu utilises ce playbook et tu en es content ? N'hésite pas à nous faire un bisous sur [Twitter](https://twitter.com/ochelys). On aime bien les bières aussi :beers:

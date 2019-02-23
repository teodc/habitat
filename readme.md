# Habitat

Habitat is a virtual PHP development environment.

It uses Vagrant, VirtualBox and Ansible to provide a complete PHP environment easy to configure and provision.

## Requirements

* SSH
* NFS
* Git
* VirtualBox (\^5.2)
* Vagrant (\^2.2)
* Ansible (\^2.7)

## Included software

* Ubuntu 18.04
* Git
* PHP 7.3
* Nginx
* MySQL 8.0
* Sqlite3
* Composer
* Node.js _(with Maildev, Webpack, Yarn)_
* Redis
* Memcached
* Beanstalkd
* Elasticsearch 6 _(with Java 11)_
* Supervisor _(with configuration Maildev)_

## Setup

From your project's root directory:

```
git clone https://github.com/teodc/habitat.git habitat
```

Configure your virtual machine:

```
cp habitat/Vagrantfile.dist Vagrantfile
vim Vagrantfile
```

Edit your Ansible inventory:

```
cp habitat/hosts.dist habitat/hosts
vim habitat/hosts
```

Edit your Ansible playbook:

```
cp habitat/playbook.yml.dist habitat/playbook.yml
vim habitat/playbook.yml
```

Configure your software stack:

```
cp habitat/vars/habitat.yml.dist habitat/vars/habitat.yml
vim habitat/vars/habitat.yml
```

Finally, simply run:

```
vagrant up
```

## Usage

### Connecting Via SSH

You can SSH into your virtual machine with the `vagrant ssh` command from your project directory.

### Catching Emails

By default, Habitat dispenses Maildev as mail-catcher.

To use it, be sure Supervisor is running the `maildev` configuration and go to this URL: `http://<ip_of_your_vm>:1080`

---

__Important:__

* Don't forget to ignore the `Vagrantfile` file & the `/habitat` folder from your project's version control.
* Don't forget to edit the host machine's `/etc/hosts` file if you want to access your app via its URL.
* You might need to install the Vagrant plugin `vagrant-vbguest` on the host machine. (`$ vagrant plugin install vagrant-vbguest`)

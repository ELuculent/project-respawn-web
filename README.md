# Project Respawn Development Site

## General Information
Project Respawn is a community project to return Halo's community to its roots before it were 
divided into communities that never interact. We seek to reunite everyone and create a central
place to share ideas, look for players, and generally interact with everyone in the Halo 
community about anything Halo, including mods, fan-projects, and official games. 

  
---

## How to contribute
The project website is being built on the full-stack framework [Laravel](https://laravel.com/),
using the [Composer Package Manager](https://getcomposer.org/) for PHP and the 
[Lararvel Homestead](https://laravel.com/docs/6.x/homestead) package as a web server (requires 
[Vagrant](https://www.vagrantup.com/)). These are requirements for contributing and will be 
used throughout the whole project. Along with this, it is recommended that you 
install [NodeJS](https://noedjs.org) as well.

### Requirements
- Laravel - https://laravel.com/
- Vagrant - https://www.vagrantup.com/
- NodeJS  - https://noedjs.org
- Virtualbox, VMWare, or another virtual machine provider - https://www.virtualbox.org
- Git Bash - https://git-scm.com/downloads 

### Setting up the workspace  

To begin, clone the repository to a drive
```bash
$ git clone https://github.com/ELuculent/project-respawn-web _project-respawn
$ cd _project-respawn
```

and download the Homestead Vagrant box.
```bash
$ vagrant box add laravel/homestead
```

Use Composer and NPM to install any dependencies
```bash
$ composer install
$ npm install
```

And install Homestead using
```bash
# Linux
$ php vendor/bin/homestead make

# Windows
$ vendor\\bin\\homestead.bat make
```

then customise the `Homestead.yaml` file
```yaml
ip: 192.168.10.10
memory: 2048
cpus: 2
provider: virtualbox
authorize: /path/to/public_key
keys:
    - /path/to/private_key
folders:
    -
        map: '/path/to/_project-respawn'
        to: /home/vagrant/code
sites:
    -
        map: homestead.test
        to: /home/vagrant/code/public
databases:
    - homestead
features:
    -
        mariadb: false
    -
        ohmyzsh: false
    -
        webdriver: false
name: '-project-respawn'
hostname: '-project-respawn'
```
and add the following line to the `/etc/hosts` or `C:/Windows/System32/drivers/etc/hosts` file.
```
192.168.10.10 homestead.test
```

Finally, run `vagrant up` to launch the virtual machine, the website will be hosted on a 
private IP address, `192.168.10.10` by default, with the domain name `homestead.test`.

### Committing Changes
When committing changes to this repository, make a new branch and start a pull request. Please
provide as much details as possible to ensure we know what you have changed. You can commit 
changes via the following

```bash
$ git pull
$ git add /resources/*
```

# Appendix - Scripts
These are setup scripts for people that don't like reading words with their READMEs
## Linux
```bash
# Linux Command Line

git clone https://github.com/ELuculent/project-respawn-web _project-respawn
cd _project-respawn
vagrant box add laravel/homestead
composer install
npm install
php vendor/bin/homestead make
```
## Windows
```bash
# Windows Command Line
git clone https://github.com/ELuculent/project-respawn-web _project-respawn
cd _project-respawn
vagrant box add laravel/homestead
composer install
npm install
vendor\\bin\\homestead.bat make
```

## After Setup
```bash
vagrant up
```

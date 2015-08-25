A few playbooks I use to create Vagrant VMs for development and live servers
running Django on Ubuntu 14.04

Playbooks
=========

jenkins-dev.yml
  Creates and Manages a Vagrant VM for running Jenkins CI server for use,
  in this case, to run tests against Django projects with a Postgres 
  database

Examples
========

The examples folder contains some example server configurations and Vagrant files.
In most cases, provided you have the prerequisites installed
(Python, Ansible, Vagrant) you
should be able to run ``vagrant up`` from within the individual example directories.

  
Roles
=====

A selection of roles used to create development and production servers.
Some roles are created by myself while others are from Ansible Galaxy and
clearly indicated as such. Originally I started mostly with roles of my
own creation, but over time have migrated to roles from Ansible
Galaxy as I've discovered good ones.

email-sendgrid
  Installs exim4 and configures to route emails via SendGrid service. When
  email_redirect_address is set to a non empty string, all outgoing 
  emails are redirected to that address. Useful when running development VMs
  ::
    email_redirect_address: me@example.com
    email_service_user: sendgriduser
    email_service_passwd: sendgridpasswd

os-packages
  Upgrade packages, install common packages and specified extra packages.
  ::
    extra_os_packages: [sloccount]
  
ANXS.postgresql
  Popular Postgres role from Ansible Galaxy. For details and to source your own 
  up-to-date copy: https://galaxy.ansible.com/list#/roles/512
  
python3-ubuntu-repository
  Installs Python 3 from the Ubuntu (14.04) repository
  :: 
    python_global_packages: [virtualenvwrapper]
  
geerlingguy.jenkins
  A jenkins role from Ansible Galaxy. For details and to source your own 
  up-to-date copy: https://galaxy.ansible.com/list#/roles/440
  
geerlingguy.java
  A dependency required by the geerlingguy.jenkins role from Ansible Galaxy. 
  For details and to source your own up-to-date copy: 
  https://galaxy.ansible.com/list#/roles/439
  
cron
  Manage cron entries for users.
  ::
    cron_entries:
      -
        user: root
        name: jenkins_backup
        minute: '*'
        hour: '10,13,17'
        day: '*'
        month: '*'
        weekday: '*'
        job: 'cp -R /var/lib/jenkins /vagrant'

secure-ssh
  Secure SSH on productions servers.

jdauphant.nginx
  An nginx role for Ansible Galaxy. For details and to source your own
  up-to-date copy: https://galaxy.ansible.com/list#/roles/466

jcsaaddupuy.supervisord_config
  A supervisord role for Ansible Galaxy. For details and to source your own
  up-to-date copy: https://galaxy.ansible.com/list#/roles/3090

devel-extras
  Performs a number of tasks specific to development. These include:

  * Adding some useful development aliases.
  * Adding a cron task to backup the project database every 20 minutes.

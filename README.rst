A few playbooks I use to create Vagrant VMs for development and live servers
running Ubuntu

Playbooks
=========

jenkins-dev.yml
  Creates and Manages a Vagrant VM for running Jenkins CI server for use,
  in this case, to run tests against Django projects with a Postgres 
  database
  
Roles
=====

email-sendgrid
  Installs exim4 and configures to route emails via SendGrid service. On
  Vagrant VMs, it also redirects all outgoing emails to the address provided
  in the variable email_redirect_address.

ANXS.postgresql
  Popular Postgres role from Ansible Galaxy. For details and to source your own 
  up-to-date copy: https://galaxy.ansible.com/list#/roles/512
  
python3-ubuntu-repository
  Install Python 3 from the Ubuntu repository
  :: 
    python_install: []
  

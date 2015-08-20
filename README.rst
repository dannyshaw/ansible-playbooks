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
  Installs exim4 and configures to route emails via SendGrid service. When
  email_redirect_address is set to a non empty string, all outgoing 
  emails are redirected to that address. Useful when running local VMs
  ::
    email_redirect_address: me@example.com
    email_service_user: sendgriduser
    email_service_passwd: sendgridpasswd


ANXS.postgresql
  Popular Postgres role from Ansible Galaxy. For details and to source your own 
  up-to-date copy: https://galaxy.ansible.com/list#/roles/512
  
python3-ubuntu-repository
  Installs Python 3 from the Ubuntu repository
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

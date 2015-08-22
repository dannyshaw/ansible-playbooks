Creates a Vagrant VM with an install of Jenkins suitable for testing
Python and Django projects.

It installs the Jenkins plugins that you are most likely to need
when starting out with Python/Django continuous integration. These
include git, violations (code quality), cobertura (coverage) and
sloccount (lines of code)

Prerequisites
=============

* Vagrant install
* A Python 2.7 virtual environment with Ansible installed

Steps to Run
============

* Review and change any settings in ``ansible-settings.yml``. Those
  to address are:

  - Email settings for SendGrid

  - Postgres database settings. These are the database details of your Django
    project database. Eventually you'll need one set of database settings for
    each project that the Jenkins server tests against.

* Run ``vagrant up``

* On your Vagrant host, go to http://localhost:8888/ and you should
  see the Jenkins home page

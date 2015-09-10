Creates a Vagrant VM with an install of Jenkins suitable for testing
Python and Django projects.

It installs the Jenkins plugins that you are most likely to need
when starting out with Python/Django continuous integration. These
include git, violations (code quality), cobertura (coverage) and
sloccount (lines of code)

Prerequisites
=============
On you local machine, you'll need:

* VirtualBox
* Vagrant
* A Python 2.7 virtual environment with Ansible installed

Steps to Run
============

Note: This has only been tested on a Ubuntu 14.04 host.

* Review and change any settings in ``ansible-settings.yml``. Those
  to address are:

  - Email settings for SendGrid

  - Test Postgres database settings (the defaults will work for you though).
    This is the postgres role that tests will use to create databases
    during test execution.

* Run ``vagrant up``

* On your Vagrant host, go to http://localhost:8888/ and you should
  see the Jenkins home page

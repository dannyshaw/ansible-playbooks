A few playbooks I use to create Vagrant VMs for development and live servers

Roles
=====

email-sendgrid
  Installs exim4 and configures to route emails via SendGrid service. On
  Vagrant VMs, it also redirects all outgoing emails to the address provided
  in the variable email_redirect_address.

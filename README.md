Role Name
=========

Install a Apache2 server

Requirements
------------

- Ubuntu 16.04lts, 18.04lts
- Certificates

Role Variables
--------------

Look at the defaults/main.yml for further information.

Dependencies
------------

Look at role app-cert-selfsigned for creating selfsigned certificates.

Example Playbook
----------------

    - hosts: nl-bel-lt05
      become: true

      vars:
        # -- custom settings: srv-apache2 --
        ap_serveradmin             : '{{ cert_email }}'
        ap_servername              : '{{ cert_orgname }}'
        ap_serveralias             : '{{ ansible_hostname }}.{{ ap_servername }}'
        ap_sslcertificatefile      : '/opt/ansible/system/ssl/certs/nl-bel-lt05/certificate-selfsigned.crt' 
        ap_sslcertificatekeyfile   : '/opt/ansible/system/ssl/private/nl-bel-lt05/private-selfsigned.key'
        ap_sslcertificatechainfile : '/opt/ansible/system/ssl/certs/nl-bel-lt05/certificate-selfsigned.crt'

      roles:
        - srv-apache2

License
-------

GPLv3

Author Information
------------------

Luc Rutten

lrutten@bitfinity.nl

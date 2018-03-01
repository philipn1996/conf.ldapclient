# conf.ldapclient
Ansible-Role to configure fedora/centos-systems to act as ldap-clients using sssd.

The role installs needed packages, templates sssd.conf, openldap/ldap.conf and nsswitch.conf, modifies pam.d/system-auth and pam.d/password-auth using ansibles built-in pamd-module and enables the services.
# Variables:
- ldap_server: list of ldap-servers to query
- ldap_search_base: ldap_search_base
- cert_dest: where to store the tls-certificate of the ldap-server
- cert_src: where to get this certificate from


# Example-Playbook
```
- name: ldap-client
  hosts: clients
  vars:
    ldap_server: [ "ldaps://ldap1.mydomain.com","ldaps://ldap3.mydomain.com"]
    ldap_search_base: "dc=mydomain,dc=com"
    cert_src: "files/ldap_all.cert"
    cert_dest: "/etc/openldap/all.cert"
  roles: [{ role: 'conf.ldapclient'}]
```

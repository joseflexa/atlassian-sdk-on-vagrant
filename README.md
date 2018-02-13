# atlassian-sdk-on-vagrant
Vagrant and Ansible support files for doing Atlassian SDK development.

This requires Vagrant, Ansible and Virtual Box

Run it by doing:
```bash
vagrant up
vagrant provision
vagrant ssh
```
See help with command: vagrant help

Vagrant automatically shares the directory where this file is hosted as /vagrant. So you can connect to the machine you created and list the shared files by doing:

```bash
vagrant ssh
ls /vagrant
```
Maven may have issues to authorize maven.atlassian.com, so you will need to import the certificate into java keystore:
```bash
openssl s_client -connect maven.atlassian.com:443 < /dev/null | sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' > public.crt
keytool -import -alias maven.atlassian.com -keystore /etc/ssl/certs/java/cacerts -file ./public.crt
```
You can verify if the certificate was imported correctly by using https://github.com/MichalHecko/SSLPoke
```bash
java -Djavax.net.ssl.trustStore=/usr/lib/jvm/java-8-openjdk-amd64/jre/lib/security/cacerts SSLPoke maven.atlassian.com 443
```

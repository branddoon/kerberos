# How to create kerberos client | UBUNTU

### 1. Install krb5 user

export DEBIAN_FRONTEND=noninteractive && sudo apt-get install -y krb5-user

### 2. Modify /etc/krb5.conf, pointing kerberos server


### 3. Get a ticket from kerberos server

kinit -kt /tmp/admin.user.keytab admin

### 4. Check details with klist command | EXAMPLE
Ticket cache: FILE:/tmp/krb5cc_1000
Default principal: admin@KAFKA.SECURE

Valid starting     Expires            Service principal
12/27/25 15:29:52  12/28/25 15:29:52  krbtgt/KAFKA.SECURE@KAFKA.SECURE


### Aditional | Check keytab
klist -kte /tmp/admin.user.keytab
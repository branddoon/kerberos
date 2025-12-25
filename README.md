# How to create kerberos(KDC) | CENTOS

### 1. Create kerberos server 

- sudo yum install -y krb5-server

### 2. Modify /var/kerberos/krb5kdc/kdc.conf 

### 3. Modify /var/kerberos/krb5kdc/kadm5.acl

### 4. Modify /etc/krb5.conf

### 5. Create Kerberos database

- sudo /usr/sbin/kdb5_util create -s -r KAFKA.SECURE -P this-is-unsecure

### 6. Create principal

- sudo kadmin.local -q "add_principal -pw this-is-unsecure admin/admin"

### 7. Restart and status 

- sudo systemctl restart krb5kdc
- sudo systemctl status krb5kdc
- sudo systemctl restart kadmin
- sudo systemctl status kadmin
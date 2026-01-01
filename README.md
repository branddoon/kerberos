# How to create kerberos(KDC) | CENTOS

### 1. Create kerberos server 

sudo yum install -y krb5-server

### 2. Modify /var/kerberos/krb5kdc/kdc.conf 

### 3. Modify /var/kerberos/krb5kdc/kadm5.acl

### 4. Modify /etc/krb5.conf

### 5. Create Kerberos database

sudo /usr/sbin/kdb5_util create -s -r KAFKA.SECURE -P this-is-unsecure

### 6. Create principal

sudo kadmin.local -q "add_principal -pw this-is-unsecure admin/admin"

### 7. Restart and status 

sudo systemctl restart krb5kdc
sudo systemctl status krb5kdc
sudo systemctl restart kadmin
sudo systemctl status kadmin

### 8. Creating principals
sudo kadmin.local -q "add_principal -randkey reader@KAFKA.SECURE"

sudo kadmin.local -q "add_principal -randkey writer@KAFKA.SECURE"

sudo kadmin.local -q "add_principal -randkey admin@KAFKA.SECURE"

sudo kadmin.local -q "add_principal -randkey kafka/127.0.0.1@KAFKA.SECURE"

sudo kadmin.local -q "add_principal -randkey kafka/172.26.25.56@KAFKA.SECURE"

sudo kadmin.local -q "addprinc -randkey kafka/localhost@KAFKA.SECURE"

### 9.Creating keytabs

sudo kadmin.local -q "xst -kt /tmp/admin.user.keytab admin@KAFKA.SECURE"

sudo kadmin.local -q "xst -kt /tmp/reader.user.keytab reader@KAFKA.SECURE"

sudo kadmin.local -q "xst -kt /tmp/writer.user.keytab writer@KAFKA.SECURE"

sudo kadmin.local -q "xst -kt /tmp/kafka.user.keytab kafka/172.26.25.56@KAFKA.SECURE"

sudo kadmin.local -q "xst -kt /tmp/kafka.user.keytab kafka/localhost@KAFKA.SECURE"


### 10. Adjusting permissions in keytab files

sudo chmod a+r /tmp/*.keytab

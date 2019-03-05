JobRec
==================================

Configuration
---------------
```sh
#SFTP server 1
sftp.host.1=192.168.99.100
sftp.port.1=2222
sftp.user.1=foo
sftp.download.path.1=/app/staging/in/cib/FILEBKUP/
sftp.upload.path.1=/pmhftp/PMH/Report/
sftp.ssh.keyfile.1=nopp
sftp.ssh.passphrase.1=

#SFTP server 2
sftp.host.2=192.168.99.101
sftp.port.2=2222
sftp.user.2=appuser
sftp.download.path.2=/app/staging/in/cib/FILEBKUP/
sftp.upload.path.2=/pmhftp/PMH/Report/
sftp.ssh.keyfile.2=rsa
sftp.ssh.passphrase.2=

#File
file.name.prefix=Recon_
file.name.dateformat=yyyyMMdd
file.share.path=payhshare/Finacle/ONS_LOGS/TMB_LOGS/

#Log4j
log.config.file=log4j.properties

#Database
#Database
db.oracle.url=jdbc:oracle:thin:@192.168.99.102:1521:xe
db.oracle.user=C##testsc
db.oracle.pass=qwerty
#query
db.select=select * from cpyckv where to_date(sysdate,'DD/MM/YYYY') = to_date(upload_date,'DD/MM/YYYY')

#MAIL SERVER
mail.transport.protocol=smtp
mail.smtp.auth=true
mail.smtp.starttls.enable=true
mail.smtp.host=smtp.live.com
mail.smtp.port=25

#debug
mail.debug=true

#auth
mail.user=
mail.pass=

#content
mail.sender=
mail.to=
mail.cc=
mail.bcc=
mail.dateformat=dd-MM-yyyy
mail.subject=[FILE REC] - as of #dd-MM-yyyy from PAYMENTHUB
mail.message.html.file=body_message.html
```

Usage command
---------------
```sh
java -Dconfig.file=${config.properties} -jar ${PaymentHub.jar} ${mode}
```
  Use -Dconfig.file=${config.properties} to get your config
	
  Use -jar ${CFR.jar} to get your jarfile to run



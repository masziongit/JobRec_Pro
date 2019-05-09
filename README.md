JobRec
==================================

Configuration
---------------
```sh
#SFTP server
sftp.host=192.168.99.100
sftp.port=2222
sftp.user=foo

sftp.upload.path=/pmhftp/PMH/Report/
sftp.ssh.keyfile=nopp
sftp.ssh.passphrase=

#File
<<<<<<< HEAD
file.backup.path=/app/staging/in/cib/FILEBKUP/
=======
file.backup.path=t1/app/staging/in/cib/FILEBKUP/
>>>>>>> Sign off
file.name.prefix=Recon_
file.name.dateformat=yyyyMMdd
file.share.path=payhshare/Finacle/ONS_LOGS/TMB_LOGS/

#Log4j
log.config.file=log4j.properties

#Database
db.oracle.url=jdbc:oracle:thin:@192.168.99.102:1521:xe
db.oracle.user=C##testsc
<<<<<<< HEAD
db.oracle.pass=qwerty
#query
db.select=select * from cpyckv where to_date(sysdate,'DD/MM/YYYY') = to_date(upload_date,'DD/MM/YYYY')
=======
db.oracle.pass=EPsnmHHUky3UqPkPxXbSxw==
#query
db.select=select * from cpyckv where 1=1 and ROWNUM <= 100
  #and TRUNC(upload_date) = TRUNC(SYSDATE)
>>>>>>> Sign off

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
<<<<<<< HEAD
```sh
java -Dconfig.file=${config.properties} -jar ${PaymentHub.jar} ${mode}
=======
Encrypt password
```sh
java -cp JobRec.jar main.AESCrypt ${password}
```
Run program
```sh
java -Dconfig.file=${config.properties} -jar ${JobRec.jar} ${mode}
>>>>>>> Sign off
```
  Usage command
  	java -Dconfig.file=${config.properties} -jar ${JobRec.jar} ${part}
  	Use -Dconfig.file=${config.properties} to get your config
  	Use -jar ${JobRec.jar} to get your jarfile to run
  	Use ${part} to get part of program (get|compare)



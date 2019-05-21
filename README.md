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
file.backup.path=t1/app/staging/in/cib/FILEBKUP/
file.name.prefix=Recon_
file.name.dateformat=yyyyMMdd
file.share.path=payhshare/Finacle/ONS_LOGS/TMB_LOGS/

#Log4j
log.config.file=log4j.properties

#Database
db.oracle.url=jdbc:oracle:thin:@192.168.99.102:1521:xe
db.oracle.user=C##testsc
db.oracle.pass=EPsnmHHUky3UqPkPxXbSxw==
#query
db.select=select * from cpyckv where 1=1 and ROWNUM <= 100
  #and TRUNC(upload_date) = TRUNC(SYSDATE)

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

#Add content in Email
db.select.batch=SELECT fhd.in_out_file_name, bat.bat_status, TO_CHAR(bat.rcre_time,'YYYY-MM-DD HH24:MI:SS') trandate, TO_CHAR(SYSDATE,'YYYY-MM-DD HH24:MI:SS') curdate, ABS(( SYSDATE - bat.rcre_time) * 24 * 60 ) AS difference_in_minutes FROM cbatrec bat LEFT JOIN py_fhd fhd ON ( bat.batch_id = fhd.hdr_srl_num ) WHERE bat.bat_status = 'DP' AND trunc(bat.rcre_time) = trunc(SYSDATE) AND fhd.file_hdr_srl_num IS NOT NULL AND ABS(( ( SYSDATE - bat.rcre_time) * 24 * 60 )) > 15 ORDER BY bat.rcre_time DESC
db.count.msd=select count(*) as count from py_msd where batch_hdr_srl_num in ( select hdr_srl_num from py_fhd where in_out_file_name in (?) and file_hdr_srl_num is not null)
db.count.ed=select count(*) as count from py_ed where batch_header_srl_num in (  select hdr_srl_num from py_fhd  where in_out_file_name in (?) and file_hdr_srl_num is not null)
db.count.ctx=select count(*) as count from ctxnrec where fp_batch_ref_num in (                select fp_bat_ref_num from cbatrec where batch_id in (                select hdr_srl_num from py_fhd                where in_out_file_name in (?) and file_hdr_srl_num is not null))


```

Usage command
---------------
Encrypt password
```sh
java -cp ActProduct.jar gen.AESCrypt ${password}
```
Run program
```sh
java -Dconfig.file=${config.properties} -jar ${JobRec.jar} ${mode}
```
  Usage command
  	java -Dconfig.file=${config.properties} -jar ${JobRec.jar} ${part}
  	Use -Dconfig.file=${config.properties} to get your config
  	Use -jar ${JobRec.jar} to get your jarfile to run
  	Use ${part} to get part of program (get|compare)



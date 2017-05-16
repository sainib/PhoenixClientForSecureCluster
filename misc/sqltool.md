Try the following suggestions for Squirrel, but some of the steps could be valid for DBVisualizer also): 
```
------------------------------------------------ 
3. Set up JCE. 
Download JCE jars and copy into %JAVA_HOME%\jre\lib\security 

4. Edit DBVisualizer SQL start up script (*.bat) to add -Djavax.security.auth.useSubjectCredsOnly=false in java execution line (for example just before or after -Xmx256m) 
If krb5.ini location is not a default location, also add -Djava.security.krb5.conf="C:\Some\Path\To\krb5.ini 

To debug in case of some error, add " -Dsun.security.krb5.debug=true" 
================================================== 

The other suggestion is taken from the Phoenix JDBC setup: 
https://community.hortonworks.com/articles/19016/connect-to-phoenix-hbase-using-dbvisualizer.html 
------------------------------------------------ 
a. add following files to DBVisualizer resources directory. 
hdfs-site.xml 
hbase-site.xml 
core-site.xml 

b. Copy krb5.conf file to local workstation. 

c. Create a jaas file with following entry (Changed from zookeeper to hive2) 
Client { 
com.sun.security.auth.module.Krb5LoginModule required useTicketCache=true renewTicket=true 
serviceName="hive2";}; 

Modify dbvisgui.bat file to add following parameters for launching DBVisualizer 
-Djava.security.auth.login.config="<path-to-jaas-file>" -Djava.security.krb5.conf="<path-to-krb5-file>" 

d. Connection string for cached keytab will be 
jdbc:hive2:<hiveserver2 host>:<hiveserver2 port>:<path-to-jaas file> 
================================================== 
```

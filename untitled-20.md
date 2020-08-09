---
description: 17/7/2020
---

# Oozie - automate/schedule the working flow of Hadoop \(de\) - 17/07/2020

## Getting the files ready

### 1. create\_table.hql

I am going to use the script from "Hive - Relational database - Importing data + read all " to create a new table via Hive.

```text
CREATE TABLE gamesale(
  name STRING,
  platform STRING,
  year_of_Release STRING,
  genre STRING,
  publisher STRING,
  nA_sales STRING,
  eU_sales STRING,
  jP_Sales STRING,
  other_Sales STRING,
  global_Sales STRING,
  critic_Score STRING, 
  critic_Count STRING,
  user_Score STRING,
  user_Count STRING,
  developer STRING,
  rating STRING)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY '\t'
STORED AS TEXTFILE;



LOAD DATA LOCAL INPATH '/tmp/Video_Games_Sales_as_at_22_Dec_2016_adjusted.tsv'
OVERWRITE INTO TABLE gamesalesss;
```

### 2. workflow.xml

This is the instructions given to Oozie to execute the working process. The format is XML and the syntax is quite self-explanatory.

```markup
<?xml version="1.0" encoding="UTF-8"?>                                                                                                                
<workflow-app xmlns="uri:oozie:workflow:0.2" name="game-sales">                                                                                       
        <start to="hive-node"/>                                                                                                                       
        <action name="hive-node">                                                                                                                     
                <hive xmlns="uri:oozie:hive-action:0.2">                                                                                              
                        <job-tracker>${jobTracker}</job-tracker>                                                                                      
                        <name-node>${nameNode}</name-node>                                                                                            
                        <job-xml>${appPath}/hive-site.xml</job-xml>                                                                                   
                        <configuration>                                                                                                               
                                <property>                                                                                                            
                                        <name>oozie.hive.defaults</name>                                                                              
                                        <value>${appPath}/hive-site.xml</value>                                                                       
                                </property>                                                                                                           
                                <property>                                                                                                            
                                        <name>hadoop.proxyuser.oozie.hosts</name>                                                                     
                                        <value>*</value>                                                                                              
                                </property>                                                                                                           
                                <property>                                                                                                            
                                        <name>hadoop.proxyuser.oozie.hosts</name>                                                                     
                                        <value>*</value>                                                                                              
                                </property>                                                                                                           
                                <property>                                                                                                            
                                        <name>hadoop.proxyuser.oozie.groups</name>                                                                    
                                        <value>*</value>                                                                                              
                                </property>                                                                                                           
                        </configuration>                                                                                                              
                        <script>create_table.hql</script>                                                                                             
                </hive>                                                                                                                               
                <ok to="end"/>                                                                                                                        
        </action>error to="fail"/>                                                                                                                    


        <kill name="fail">                                                                                                                            
                <message>hive failed, please check your process once again</message>                                                                  
        <end name="end"/>                                                                                                                             

</workflow-app>
```

### 3. job.properties

This is the file used as a configuration when firing up Oozie work task

```markup
nameNode=hdfs://sandbox-hdp.hortonworks.com:8020rties                                                                                                 

jobTracker=sandbox-hdp.hortonworks.com:8050                                                                                                           
oozie.libpath=${nameNode}/user/oozie/share/lib/hive                                                                                                   
oozie.use.system.libpath=true                                                                                                                         
appPath=${nameNode}/user/maria_dev/workflowsaria_dev/workflows
```

{% hint style="info" %}
**hostname -f** can be used to find out vm hostname. Mine is _sandbox-hdp.hortonworks.com_
{% endhint %}

### 4. hive-site.xml

This is the hive config file, which will be import to our executed folder to support for hive configuration that specified at workflow.xml

```markup
/var/lib/ambari-server/resources/stacks/HDP/2.1/services/HIVE/configuration/hive-site.xml
```

### Once the preparation is done, time to move to our execution process:

Move your files into workflows directory:

```markup
mkdir workflows
cd workflows
```

Transfer it to Hadoop file system:

```markup
hadoop fs -put workflow.xml /user/maria_dev/workflows/
hadoop fs -put create_table.hql /user/maria_dev/workflows/
hadoop fs -put /var/lib/ambari-server/resources/stacks/HDP/2.1/services/HIVE/configuration/hive-site.xml
```

Fire up Oozie:

```markup
su maria_dev
oozie job -oozie http://lcaolhost:11000/oozie -config job.properties -run
```

{% hint style="success" %}
Oozie supports UI panel.

View the result from: _**127.0.0.1:11000/oozie/**_
{% endhint %}


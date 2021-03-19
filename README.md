# Alluxio-SQL-Engines-Comparison

Step 0: Install latest Ubuntu on the working machine.

Updating: sudo apt update; sudo apt -y upgrade; sudo apt install vim

Step 1: Install Spark on Ubuntu 20.04.2.0 LTS

Before downloading and setting up Spark, we need to install necessary dependencies:

    - JDK
    - Scala
    - Git
Installing from the terminal with the command: ```sudo apt install default-jdk scala git -y.```
Verify installation with the following commands: ```java -version; javac -version; scala -version; git --version.```

Spark Installation:
Dowloading latest Spark with Hadoop 2.7: ```wget https://downloads.apache.org/spark/spark-3.1.1/spark-3.1.1-bin-hadoop2.7.tgz```
Extract the files: ```tar xvf spark-*```
Create a directory for Spark: ```sudo mv spark-3.1.1-bin-hadoop2.7 /opt/spark``` (no output after successful operation)

Configuring Spark Environment: 
Adding Spark Home Paths: ```echo "export SPARK_HOME=/opt/spark" >> ~/.profile ;echo "export PATH=$PATH:$SPARK_HOME/bin:$SPARK_HOME/sbin" >> ~/.profile ;echo "export PYSPARK_PYTHON=/usr/bin/python3" >> ~/.profile```

ALTERNATIVELY, use vim and .bashrc.

Open with: ```vim ~/.bashrc```
Insert the following: ```export SPARK_HOME=/opt/spark; export PATH=$PATH:$SPARK_HOME/bin:$SPARK_HOME/sbin```
Activate the changes: ```source ~/.bashrc```

Running Spark:
Start Master node: ```start-master.sh ```
Check local host for Spark GUI: http://127.0.0.1:8080/
Create 1 worker node: ```start-worker.sh spark://yourURL. Mine is spark://sergei-VivoBook-ASUSLaptop-X421IA-M433IA:7077 ```
In order to run Spark Shell: ```/opt/spark/bin/spark-shell```
To shut the nodes down: ```stop-master.sh``` and ```stop-worker.sh```

Setting up an hdfs database:
Getting SSH and PDHS. SSH is needed for Hadoop and PDSH for better ssh resource management.
 ```sudo apt-get install ssh
    sudo apt-get install pdsh
 ```
Download Hadoop 2.7 from the Apache website: https://hadoop.apache.org/release/2.7.0.html.
Unpack: ```tar xvf hadoop-*```
Create a directory hadoop in opt and move the unpacked archive there, same as Spark.
Edit the file etc/hadoop/hadoop-env.sh to define some parameters as follows:

  set to the root of your Java installation
  ```export JAVA_HOME=/usr/java/latest```
To find JAVA_HOME: ```dirname $(dirname $(readlink -f $(which javac)))```

do the following with the found directory:
```JAVA_HOME=your_java_path (mine was JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-amd64)
    export JAVA_HOME
```


Go to the Hadoop folder: /hadoop-2.7.0/bin and execute ```./hadoop``` The usage documentation will be shown.
Installing curl also helps: ```sudo apt install curl -y```




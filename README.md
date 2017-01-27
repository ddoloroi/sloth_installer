#Installing CDH made easy

##Pre-Req -

1.) Unzip the package slot_current.zip and it will create directory called "installer"

2.) Change directory to installer -- DO NOT rename the directory, otherwise installer will not work.

3.) Create private key file CDH.pem and paste content of your private key

4.) Change the permission of CDH.pem file to 600: chmod 600 CDH.pem

5.) Edit hdfs.group file and change/Add hostname of your EC2 instances for hadoop cluster with last entry where installer is staged

##Setup 

6.) execute run_cmd.sh to test passwordless ssh is working - example execution
```shell
[ec2-user@ip-10-1-4-91 installer]$ ./run_cmd.sh
Enter CMD to be executed on remote hosts: hostname
 -------------------------
Executing command on Host : 10.1.4.93
-------------------------
ip-10-1-4-93.us-west-2.compute.internal
[ec2-user@ip-10-1-4-91 installer]$
```

7.) execute "1_prepare_nodes" script and it will disable and reboot the nodes"
        ** during this setup, you are required to reboot the machines and script will sequentially ask do you wish to reboot

##Installer 

8.) After successful execution of step above, execute script "2_setup_database_node" - This script will download and install required packages for MySQL and Java

9.) After completing step 8, proceed with step 9, execution of script "3_setup_cm" - after script completes, cloudera manager should be installed with MySQL.

10.) Execute step 10 after step #9 - execute script "4_start_cm" and this will start "cloudera manager."

11.) Execute script "5_check_cm_rest" - This script will executes REST API to cloudera manager.

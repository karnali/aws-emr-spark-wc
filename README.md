# Amazon Elastic Map Reduce (EMR) cluster using Spark application. 
This is a simple project based on Amazon Elastic Map Reduce (EMR).  This EMR cluster counts words from an input text file located in s3 bucket using Spark application.  The output text file is saved back to s3 bucket once the job is completed.
Finally we will terminate our EMR cluster.  


#### Create a s3 bucket and uplad input text file.  
![s3-inputfile](images/s3-inputfile.png)

#### Head over to AWS console and create Amazon Elastic Map Reduce (EMR) cluster.  
* Enter cluster anme. 
* Select latest EMR release.  
* Under applications: Select Spark
* Instance Type: m4.xlarge
* Number of Instances: 3 1 master and 2 core nodes.  
* Use your ec2 key pair or create one.  
* Click on Create cluster.  
![emr-cluster](images/emr-cluster.png) 

#### Open SSH on master node.  
* Click on Security Group for Master.  
* Edit inbound rule for SSH port 22 to My IP.  
![sg-master-ssh](images/sg-master-ssh.png)

#### SSH into Master node. 
* Open terminal in your local computer. Enter yes.  
```
ssh -i "~/key_pair.pem" hadoop@ec2-34-224-93-103.compute-1.amazonaws.com
``` 
![emr-ssh](images/emr-ssh.png)


#### Our cluster is ready and accepting jobs.  
![emr-ready](images/emr-ready.png) 

#### Create word count python script and submit to Spark/EMR cluster.  
* Create word count python script (/scripts/spark-emr-wc.py) 
* Submit to Spark/EMR cluster.
* Use the tee commands to read input and write output file (spark-emr-wc-out.txt).  

```
sudo spark-submit spark-emr-wc.py | tee spark-emr-wc-out.txt
```

![spark-submit](images/spark-submit.png)


#### Copy spark-emr-wc-out.txt to our s3 buket. 
```
aws s3 cp spark-emr-wc-out.txt s3://spark-emr-wc-bucket/

``` 
![outtos3](images/outtos3.png)

#### Download and open spark-emr-wc-out.txt. Here is the content of our word count file. 
![outputfile](images/outputfile.png)


#### Finally, Terminate your EMR cluster.
![terminate](images/terminate.png)


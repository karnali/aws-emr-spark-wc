# aws-emr-spark-wc

```
ssh -i "~/key_pair.pem" hadoop@ec2-34-224-93-103.compute-1.amazonaws.com

sudo spark-submit spark-emr-wc.py | tee spark-emr-wc-out.txt

aws s3 cp spark-emr-wc-out.txt s3://spark-emr-wc-bucket/

```

![emr-cluster](images/emr-cluster.png) 
![emr-ready](images/emr-ready.png) 
![emr-ssh](images/emr-ssh.png)
![emr](images/emr.png)
![outputfile](images/outputfile.png)
![outtos3](images/outtos3.png)
![s3-inputfile](images/s3-inputfile.png)
![sg-master-ssh](images/sg-master-ssh.png)
![spark-submit](images/spark-submit.png)
![terminate](images/terminate.png)

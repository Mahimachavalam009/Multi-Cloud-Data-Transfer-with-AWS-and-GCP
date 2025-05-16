# Multi-Cloud-Data-Transfer-with-AWS-and-GCP


# outline :

![image](https://github.com/user-attachments/assets/83baa5f0-2fd9-4de2-9749-4860f9f050c9)

# What is multi-cloud?
Multi-cloud means spreading your data and services across multiple cloud providers. Companies like this because it means:

Higher reliability – If AWS has an outage, GCP can keep your apps running and have a copy of your data.

More flexibility – You can make the most of each provider's different strengths. For example, AWS is best known for their compute services, and GCP for their data/AI services.

Cost savings – Since pricing varies across cloud platforms, multi-cloud lets you optimize on costs.

# Step 1 - Store Data in an S3 Bucket
 This bucket will serve as the source for our data transfer to GCP Cloud Storage.

 Create a new S3 bucket.
 
```
Navigate to S3
First, let's find the S3 service in the AWS Management Console.
Log in to the AWS Management Console as your IAM Admin user.
In the search bar at the top of the console, type S3.
Select S3 from the search results.
```



![image](https://github.com/user-attachments/assets/6008e725-50ae-470e-ae76-b0140d35ae38)


2. Upload files to your S3 bucket.
# What kind of files can I upload?
You can upload virtually any type of file to S3, from documents and images to videos and backups. S3 is versatile and can store any data you need in the cloud!


![image](https://github.com/user-attachments/assets/9917d676-77a3-4b29-8d5e-f6b255f2f94c)


# Step 2 -  set up your Google Cloud Platform account.

# Step 3- Set Up a Storage Transfer from AWS to GCP

Turns out, there's a handy service in GCP that can help us transfer data from AWS to GCP
Create a new transfer job in GCP's Storage Transfer Service.


![image](https://github.com/user-attachments/assets/7e77eee6-5f6b-42e9-9ea4-a1eaa7f7e50d)


In the GCP console, on the left look for storage and click on storage transfer


![image](https://github.com/user-attachments/assets/8bd6c220-74e7-4c48-8782-938c51ff7132)

# Storage Transfer Service is a Google Cloud service designed for transferring data in and out of GCP Cloud Storage (which is like GCP's version of Amazon S3).
Instead of transferring directly between S3 and GCS, we need this service because cloud providers don't offer native ways to connect to their competitors.
Storage Transfer Service handles authentication between the two platforms, starts and stops the transfer, and makes sure data transfers correctly. Without it, you'd need to build your own transfer system, which would mean downloading all your data to a computer first, then uploading it again to the other cloud - slow, expensive, and prone to errors!


![image](https://github.com/user-attachments/assets/d947d83b-c8cd-451e-8e56-6dd3287b95a9)


# Step 4 - Create a custom IAM role for GCP.

Let's head to the IAM console to create our role.
Head back to the AWS Management Console
In the search bar, type IAM and select IAM.
create a role: 


![image](https://github.com/user-attachments/assets/5d06fbf6-fa18-4048-98e0-fc3220f113e9)

edit the JSON file, and replacing the subject_id wiith gcp api: 


![image](https://github.com/user-attachments/assets/4188c6af-3de6-486d-a626-3a0b3627140a)

create role: 


![image](https://github.com/user-attachments/assets/8e37cf74-a92a-49a5-98db-494d3d205fb5)

 we'll use this role's to complete the S3 source configuration in GCP.

 # Step 5 - Transfer Your Objects from S3 to GCS

 ![image](https://github.com/user-attachments/assets/dfcd8bf4-b427-459f-8027-1b313999c6ac)

copy the arn: 

![image](https://github.com/user-attachments/assets/a4f28380-57c3-4b19-9943-defe6c982d44)

paste it in the gcp: 

![image](https://github.com/user-attachments/assets/b92697c0-149c-4113-9674-d05469b439fb)


make sure the region is same as the one you had in the aws console: 

![image](https://github.com/user-attachments/assets/653bf57b-1c7b-44a6-825b-e98e4fee32b6)

now that you've create the transfer job :

![image](https://github.com/user-attachments/assets/a151da0f-8235-4402-b5fc-f1c221d9c642)

in the gcp console, hover to cloud->buckets :

![image](https://github.com/user-attachments/assets/58e79110-69f9-41d1-a02e-17e905483fd4)

# You should see the files from your S3 bucket listed in your GCP Cloud Storage bucket:

![image](https://github.com/user-attachments/assets/115cb148-1d53-47d2-aeff-98f9e19ba04f)


   

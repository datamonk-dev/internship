# Google Drive clone 

Build a google drive clone hosted on your AWS EC2 instance. This service should should allow user to 
- list all the files uploaed 
- upload a file 
- delete a file 

Requirements 
- All the uploaded file should be stored in a S3 bucket 
- The metadata corresponding to the files (e.g. file name, S3 path) should be stored in the Sqlite database. 
- The service should be hosted on the EC2 instance  and should be accessible from the public IP. 
- The application should be dockerized and be running on a container on the EC2 instance.

You should submit following artifacts in the [google form](https://forms.gle/yaQjnWWYXVX83e3p8) 
- Github repository containing the code 
- Screen recording showcasing the functionalities (CRUD operations), S3 buckets the artifacts being saved to, EC2 instance that is running the application. 



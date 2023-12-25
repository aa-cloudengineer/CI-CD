# Install Jenkins in EC2 Instance using User Data Script

Steps for installing Jenkins on an EC2 using (Ubuntu system):
   
Prerequisites:

   -  AWS Account + User Data


Steps:

    1. Login into AWS and search for EC2 in services:
    
       Click on EC2 and explore the dashboard
       
   ![searchforec2](https://github.com/aa-cloudengineer/CI-CD/assets/144057103/f1d97b4f-1e2b-47ce-9587-ac906fbe81fc)
    
    2. Launch an EC2 Instance
       For creating a new instance, click on instances and choose Launch instances from the dropdown.

   ![launchEC2](https://github.com/aa-cloudengineer/CI-CD/assets/144057103/bb1c0f95-beb5-45a5-9f11-fa7409c87a9c)

    3. Configure EC2
      Enter the name of your server like "Jenkins server" and choose Amazon Machine Image(AMI). An AMI is a template that contains a software configuration (for example, an operating system, an application server, and           applications). In my case, I am selecting Ubuntu Server 22.04.

   ![ConfigEC2](https://github.com/aa-cloudengineer/CI-CD/assets/144057103/0544a343-7c19-4528-8c74-e3205140aeeb)

    4. Create new key pair
      Choose the instance type eligible for the free tier ( t2.micro) or higher instance type based on your server requirements. Click Create new key pair.

   ![CreateNewKP](https://github.com/aa-cloudengineer/CI-CD/assets/144057103/3d14d4cb-eeee-4d2e-95a9-634e688166d8)

    The key pair will allow you to SSH into the machine you just created. Create the key pair and download it, make sure to keep it safe as you will not be able to download it again. Choose key pair type as RSA and .pem       as private key format and click Create key pair.   

   ![CreateNewKP2](https://github.com/aa-cloudengineer/CI-CD/assets/144057103/e0da789b-ddb2-4640-acf1-a455878f3b38)
    
    5. Configure network settings and Storage
       Keep VPC and Subnet defaults in the network setting. Edit the security group and allow HTTP traffic from the internet at port 8080, by default Jenkins runs on port 8080. 
       AllowSSH at port 22 from anywhere. Select the amount of storage you want for your system, 8 GB is eligible for the free tier.

   ![ConfigureNet-Storage](https://github.com/aa-cloudengineer/CI-CD/assets/144057103/72ee85ff-3398-4095-a189-0d4e647a9556)

    6. Advance details
      Expand advance details section and scroll to the end. Copy and paste the user data script to install Jenkins at the time of launch. Lastly, click Launch instance in the bottom right corner.

   ![UserData](https://github.com/aa-cloudengineer/CI-CD/assets/144057103/5e7c3b22-13d2-491a-90fe-9161ae66108b)

    Your instance is running now, In order to access Jenkins in your local click the instance id of a running instance.

   ![InstanceID](https://github.com/aa-cloudengineer/CI-CD/assets/144057103/aaf52423-7379-4ce7-ad90-bd26ddc3cd64)

    Click on your instance id and copy Public IPv4 address.
    
   ![PublicAdd](https://github.com/aa-cloudengineer/CI-CD/assets/144057103/be87afe0-5a8b-4918-b961-e4c7217dab0a)
    
    7. Access Jenkins
       Go to your browser and search with Public IPv4 address:8080.

   ![AccessJenkins6](https://github.com/aa-cloudengineer/CI-CD/assets/144057103/a0c223cb-b8a1-4db7-9967-493658a6c029)

    8. Connect to your instance
       Click the connect option in your instance menu. Go to the EC2 Instance Connect option and click connect.

   ![Conncet2Instace7](https://github.com/aa-cloudengineer/CI-CD/assets/144057103/4beeb54a-352c-44dc-97b6-94f018c1e16e)

   Copy the path from the browser and cat into the EC2 terminal as shown below. Be the root user first:

   sudo -i
   cat /var/lib/jenkins/secrets/initialAdminPassword
   Copy the password and paste it into the Jenkins console. Install suggested plugins. Set your username and password for future login.

   ![Conncet2InstaceCLI7](https://github.com/aa-cloudengineer/CI-CD/assets/144057103/a9ae0450-a9e7-4409-9cae-38c980aa4cad)
   
    9. Finally, start using the jenkins.
    
    ![Welcome2Jenkins](https://github.com/aa-cloudengineer/CI-CD/assets/144057103/c68a1802-30e3-4ea6-941d-355be1ce6b0e)

Amazon Elastic Compute Cloud(EC2) is a web service that provides secure, resizable computing capacity in the cloud. It allows users to rent virtual computers, launch as many or as few virtual servers as needed, configure security and networking, and manage storage. Amazon EC2 enables you to scale up or down to handle changes in requirements or spikes in popularity, reducing your need to forecast traffic.

User data script is the easiest and most popular way to send instructions to an instance at launch. You should allow a few minutes of extra time for the tasks to complete before you test that the user script has finished successfully.

When you launch an instance in Amazon EC2, you have the option of passing user data to the instance that can be used to perform common automated configuration tasks and even run scripts after the instance starts.

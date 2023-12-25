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

    5. Set up Argo CD:
        Install Argo CD on the Kubernetes cluster.
        Set up a Git repository for Argo CD to track the changes in the Helm charts and Kubernetes manifests.
        Create a Helm chart for the Java application that includes the Kubernetes manifests and Helm values.
        Add the Helm chart to the Git repository that Argo CD is tracking.

    6. Configure Jenkins pipeline to integrate with Argo CD:
       6.1 Add the Argo CD API token to Jenkins credentials.
       6.2 Update the Jenkins pipeline to include the Argo CD deployment stage.

    7. Run the Jenkins pipeline:
       7.1 Trigger the Jenkins pipeline to start the CI/CD process for the Java application.
       7.2 Monitor the pipeline stages and fix any issues that arise.

This end-to-end Jenkins pipeline will automate the entire CI/CD process for a Java application, from code checkout to production deployment, using popular tools like SonarQube, Argo CD, Helm, and Kubernetes.

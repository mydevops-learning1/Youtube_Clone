# Build and Deploy a Modern YouTube Clone Application in React JS with Material UI 5

# Step 1
create a web app with settings as shown below

<img width="337" alt="image" src="https://github.com/user-attachments/assets/b2619874-c80a-494a-893c-2d6ec4745564">

# Step 2
Create a pipeline with below shown jobs

<img width="818" alt="image" src="https://github.com/user-attachments/assets/f574597c-f358-42fd-975c-d8eed81931d9">

<img width="794" alt="image" src="https://github.com/user-attachments/assets/eb30596e-064e-46b6-aeaf-4a3723598a7f">


<img width="818" alt="image" src="https://github.com/user-attachments/assets/63ceab9d-4b62-4b94-b30c-96b750b74e7b">


<img width="842" alt="image" src="https://github.com/user-attachments/assets/4ed31a3d-ff58-4dab-a263-1b7849c021bc">


<img width="707" alt="image" src="https://github.com/user-attachments/assets/2f6a7310-9531-4def-8dc9-bfca41f9ee34">

Runt the pipeline and see the youtube application is deployed.


# alternatively you can use the below yaml code 



      trigger: none
      
      name: Deploy-Bicep-Code-via-Pipeline
      
      pool: Azure Pipelines
      
      jobs:
      - job: Job_1
        displayName: Build
        pool:
          vmImage: ubuntu-latest
        steps:
        - checkout: self
          clean: true
          fetchTags: false
        - task: Npm@1
          displayName: npm install
          inputs:
            verbose: false
        - task: Npm@1
          displayName: npm build
          inputs:
            command: custom
            verbose: false
            customCommand: run build
        - task: PublishBuildArtifacts@1
          displayName: 'Publish Artifact: drop'
          inputs:
            PathtoPublish: build
        - task: AzureRmWebAppDeployment@4
          displayName: 'Azure App Service Deploy: day4youtube'
          inputs:
            ConnectedServiceName: 13a58610-b8ec-45b5-82fb-3aed7e81735f
            WebAppKind: webAppLinux
            WebAppName: day4youtube
            Package: $(System.DefaultWorkingDirectory)/build
            RuntimeStack: STATICSITE|1.0




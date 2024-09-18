# GitOps project with ArgoCD AWS EKS

# What is GitOps?

Gitops it’s a DevOps practice that uses Git repositories as a single source of truth for managing both applications and infrastructure

# How it works?

You connect your git repo with gitops tool and it will constantly check your repo If you have made any changes. Ex: you changed the image in the deployment manifest, you don’t have to manually run k apply as the gitops tool will automatically detect any changes made and synchronizes your app or infrastructure to match the desired state that you have defined in your repo (gitops uses git as single source of truth)

![image](https://github.com/user-attachments/assets/a55a863b-2278-49c1-bbcc-c2b5ffa45c17)

![image](https://github.com/user-attachments/assets/909bb56a-bb59-4de1-a7cb-32998e431866)

# Advantages

With gitops you can automate the deployment and management of infrastructure reducing the need of any manual intervention and minimizing human errors.
**Version control:** with Git as a foundation in gitops you have full version control and you can easily track any changes or roll back if any issue arises
**Consistency:** when you use gitops with your different environments like staging, production and development all of them will have same config settings that you have defined in your git repositories that will avoid any configuration issues that might occur if you do it manually
**Security:** you can control access to your repos providing robust security and only allowing authorized users to make changes to your app or to your infrastructure
**Efficiency**: or faster time to deployments when using gitops, you don’t have to manually run the commands reducing the time that it takes to deploy your changes or updates

# Steps

Create an AWS EKS cluster named GitOps:

![image](https://github.com/user-attachments/assets/9da429da-754b-41d9-a6a3-f4698a637649)

We will be using this image nasi101/tetris on Docker Hub which will be in our manifest file to deploy our tetris scheme

![image](https://github.com/user-attachments/assets/ffe32dc1-f5ba-4311-8703-a74ca4ac621d)

Manifest file with deployment yml and svc yml:

![image](https://github.com/user-attachments/assets/02d6557d-ca97-405e-848b-d7299e17640c)

![image](https://github.com/user-attachments/assets/ee277876-ba12-4f22-a22b-461302a054ed)

we create a github repo like:

![image](https://github.com/user-attachments/assets/266fa776-fb3f-432f-bd09-c7432a9ff8df)

Argocd requires a server with 2cpi and 4gb of ram, get medium!

![image](https://github.com/user-attachments/assets/c3aadc50-d02f-4d06-a467-ce95cddcfc5d)

![image](https://github.com/user-attachments/assets/cbfa1b1d-8e8e-4d2e-a55e-5bfd6dc435fe)

we install ArgoCD

![image](https://github.com/user-attachments/assets/50fae98b-aef5-4770-931a-c03d83cdf63f)

![image](https://github.com/user-attachments/assets/455249f3-a764-480a-a91e-4b1977f32b5b)

and copying the url we get the ArgoCD UI:

![image](https://github.com/user-attachments/assets/720a9b7a-0078-4ba0-adb5-8e1b06592aba)

![image](https://github.com/user-attachments/assets/08133900-7c6a-42ff-b2b1-0e2277b5347b)

We connect repo using https:

![image](https://github.com/user-attachments/assets/933e886c-b5c8-4333-90df-84b375efe838)

![image](https://github.com/user-attachments/assets/fbece089-fa4e-4c84-83c3-7c8ddc205631)

![image](https://github.com/user-attachments/assets/6f88bb12-c7e8-4a60-9d24-7ff3d374efa5)

![image](https://github.com/user-attachments/assets/4ce1fd21-3f2f-41d0-bfec-a4d6844b5e6f)

![image](https://github.com/user-attachments/assets/0a0ea505-cc2e-4d40-ba3b-16c5a727b4f5)

![image](https://github.com/user-attachments/assets/85227726-1d4f-4caa-ba0f-0bca11239f34)

![image](https://github.com/user-attachments/assets/3d7aff73-6c9c-4507-ab90-9af11a26f0ce)

![image](https://github.com/user-attachments/assets/4cf9e38f-16d8-455b-819c-076e47aea586)

![image](https://github.com/user-attachments/assets/61549518-6e18-465a-abe3-3424ef947143)

![image](https://github.com/user-attachments/assets/5b5c62f1-d3de-484e-9316-05d5a37e256e)

We use load balancer as service type

![image](https://github.com/user-attachments/assets/f48b24fd-5eb7-444e-bb62-54eef2cbd893)

![image](https://github.com/user-attachments/assets/c02d6145-9968-42f1-b1e0-12094dfbd110)

Open in a new tab and we should have our Tetris application deployed in our cluster

![image](https://github.com/user-attachments/assets/3d86e364-8819-4d39-af38-4d03334f8154)

Now let’s make a change – new version. I’m going to change the deployment file in the manifest and use tetrisv2 image ![image](https://github.com/user-attachments/assets/489301c0-0772-470c-964a-d3fe46ec45f6)

![image](https://github.com/user-attachments/assets/96ea6b9a-6e95-44f7-8de6-d95d6a3209b2)

We change to version to tetrisv2 in the deployment.yml

![image](https://github.com/user-attachments/assets/9c8a517a-73b6-4ddc-b116-76b26861d39e)

![image](https://github.com/user-attachments/assets/c6f01640-de73-4756-8df9-ff0cf3f3a6b8)

![image](https://github.com/user-attachments/assets/5667bb5a-6159-4e13-9584-3ec2268ae687)

And here we have the New version!

![image](https://github.com/user-attachments/assets/7a8620d4-aa63-404d-93cd-9051cde5b061)

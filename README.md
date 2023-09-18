# Simple Notes App
This is a simple notes app built with React and Django.

## Requirements
1. Python 3.9
2. Node.js
3. React



# Project Architecture/ Overview





<img width="953" alt="overview" src="https://github.com/iamsouvik9/Notes-App-Deployment/assets/79768737/da35ad58-eb0e-4028-9193-683cf24007e9">




## 1. Create a EC2 instance on AWS. 



<img width="960" alt="1" src="https://github.com/iamsouvik9/Notes-App-Deployment/assets/79768737/5275b485-fe3d-4076-a02a-1c6825366059">




## 2. Install Docker in the EC2 instance



<img width="960" alt="2" src="https://github.com/iamsouvik9/Notes-App-Deployment/assets/79768737/533e7a85-a2f9-48b8-9543-9b885d2e899f">






## 3.Add user to the docker group so that it does not raise "permission denied error". 


<img width="960" alt="3" src="https://github.com/iamsouvik9/Notes-App-Deployment/assets/79768737/23a56498-f751-4f7f-98a9-d18b5ccb00e9">




## 4. Install Java on the EC2 instance 



<img width="960" alt="4" src="https://github.com/iamsouvik9/Notes-App-Deployment/assets/79768737/74955377-9a8b-4f8c-95cc-0fd3244b22a3">




## 5. We have to install Jenkins on the EC2 instance. So I have created a *.sh script to install Jenkins.



<img width="960" alt="5" src="https://github.com/iamsouvik9/Notes-App-Deployment/assets/79768737/9b50a650-e80b-468e-8834-8a33d28ad735">






<img width="960" alt="6" src="https://github.com/iamsouvik9/Notes-App-Deployment/assets/79768737/89579716-4dac-4f8c-bd0b-1f535978879d">




## 6. Install docker-compose 

Install docker-compose so that when we trigger the pipeline to re-deploy the application on port 8000, docker-compose will first bring the already deployed service down and after that it will re-deploy the application on the same port. So, in this way the Jenkins will never find the port 8080 busy amd the pipeline will not fail.





<img width="960" alt="8" src="https://github.com/iamsouvik9/Notes-App-Deployment/assets/79768737/f016b4fb-3703-4ba1-928e-f8d9b361cefb">




## 7. Provide the initial admin passwor dto login the Jenkins server




<img width="960" alt="7" src="https://github.com/iamsouvik9/Notes-App-Deployment/assets/79768737/9987d9c3-0855-487d-891c-06e2071f94ae">





## 8.Install the necessary plugins



<img width="960" alt="9" src="https://github.com/iamsouvik9/Notes-App-Deployment/assets/79768737/7ff97ded-5ec6-4874-a0f2-e41e1af2ac1b">



## 9. On the Jenkins dashboard go to Manage plugins --> Credentials and then create a new credential for the dockerHub login.


<img width="960" alt="10" src="https://github.com/iamsouvik9/Notes-App-Deployment/assets/79768737/7a1b4872-1ee3-4ca7-9127-333e06224df5">




## 10. Create a pipeline in Jenkins for the deployment



<img width="960" alt="18" src="https://github.com/iamsouvik9/Notes-App-Deployment/assets/79768737/67d5b783-7706-4dbe-870b-0cc7303be7d6">




## 11. Enable GitHub webhooks so that every time developoer will push in the main branch a fresh buil will be made.



<img width="960" alt="13" src="https://github.com/iamsouvik9/Notes-App-Deployment/assets/79768737/42c9035e-d0ba-40af-b94d-0e740b849976">



## 12. Go to the GitHub repo which we are using in this project and create a webhook.



<img width="960" alt="14" src="https://github.com/iamsouvik9/Notes-App-Deployment/assets/79768737/c1ef6137-ce43-4029-be31-a1bccbb59540">



## 13. Save the pipeline and click on build pipeline



<img width="960" alt="15" src="https://github.com/iamsouvik9/Notes-App-Deployment/assets/79768737/a0e7757b-cea8-4b98-9eab-0c32a0497c72">



## 14. See the Job dashboard



<img width="960" alt="17" src="https://github.com/iamsouvik9/Notes-App-Deployment/assets/79768737/5c8d28d1-9e1d-4d65-94f5-853102c4f44c">



## 15. Make sure the GitHub webhook is triggered successfullly.




<img width="960" alt="16" src="https://github.com/iamsouvik9/Notes-App-Deployment/assets/79768737/6b9fc494-4a44-48e9-99b3-e8d91dcacab4">



## 16. Access the application on the web-browser on port 8000




<img width="960" alt="11" src="https://github.com/iamsouvik9/Notes-App-Deployment/assets/79768737/4620e5e9-3606-4c54-b6d4-235632f3206c">




<img width="960" alt="12" src="https://github.com/iamsouvik9/Notes-App-Deployment/assets/79768737/07d0c0f5-7e98-4287-9b67-344de6c84333">




## Note : I received an failed Job error in the 1st build



I got an error in the 1st build and it was because I forgot to add ubuntu user to the docker group so I received this "permission denied error"
I solved it by running "sudo usermod -aG docker $USER" and then after that "newgrp docker" in the CLI





<img width="960" alt="20" src="https://github.com/iamsouvik9/Notes-App-Deployment/assets/79768737/97c614a5-33a6-4a22-aa9a-e0d43fec58e9">


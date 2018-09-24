Release Pipeline for Microservices

Abstract
Setup Steps

Get the environment from this link: https://assignworkspace.herokuapp.com/
Enter your email address and click on ‘Create Workspace’ 
You should see links similar to the ones shown below



<Prereq: Github account>

2. Open https://github.com and log into your account. Fork the below github repos to your github account

https://github.com/GHCdemo/microservices-1 
https://github.com/GHCdemo/microservices-2 
https://github.com/GHCdemo/microservices-3 

3. 
Open Jenkins:
Login with below credentials:
Username: admin 
Password: admin

Click on ‘Credentials’ on the left menu. Dummy credentials are already added for this setup. Click on ‘your-github-username…’ link
Click on update from the left side menu
Enter your github account name in the username field (It is case sensitive. So make sure you are entering as it is)
Enter your github password in the ‘Password’ field
Click on save


Go to Jenkins Home ->Manage Jenkins -> Configure System
Search for ‘Jenkins Location’ on the page or scroll down a little until you find it.
Replace localhost with the ip of the machine you got.
Click on ‘Save’ at the end of the page

4. update your github account as an organization in Jenkins.
Go to Jenkins home, click on ‘github-org’. Click on ‘Configure’ from the left menu.
Give your Github username in owner field (It is case sensitive).
Click on Save at the end of the page.

You should see the scanning log and all your repos (if any) which has Jenkinsfile in it will appear. Since you forked all 3 microservices repos, you should now see microservices-1 repo and a build should trigger automatically. 
Click on your organization name.

Explanation to the pipeline here. And about adding the same pipeline to other microservices as well. 
Homework: Optional step is to add the same pipeline to other microservices.
Your artifacts can be seen in artifactory at this location: http://<host>:8081/artifactory 


5. Go to your microservices-3 fork and create a new file called ‘Jenkinsfile’ 
Copy the contents from the below link and commit the file https://github.com/GHCdemo/Demo-WorkSheets/blob/master/Jenkinsfile-final 

Do the same thing for microservices-1 and microservices-2 repositories. 

Go back to Jenkins and on the left side of the organization, you should see ‘Scan Organization Now’ link. Click on that, and you should now see microservices-3 repo in the list.
Verify the pipeline. It should have all the stages just like microservice-1 but coming from a shared pipeline.

6. Let’s modify the shared pipeline.
Copy the below file from the link and modify your onePipeline.groovy groovy file in shared-pipeline repository.
https://github.com/GHCdemo/Demo-WorkSheets/blob/master/Jenkinsfile-add-sonar-stage 

And rerun any of your microservices builds. It should now have a new stage ‘Sonar Analysis’.

[Optional]
To automatically trigger builds for any changes to your microservices repositories, we have to generate a token in Github.com.
Enter Token description in the below link and click on ‘Generate token’ button: https://github.com/settings/tokens/new?scopes=admin:repo_hook,repo,repo:status 
Copy the token you are shown on the screen.

Open Jenkins:
Click on ‘Credentials’ on the left menu. 2 dummy credentials are already added for this setup. . Click on ‘Your github token’ from the list at the center.
Click on update from the left side menu
Paste the token in the ‘Secret’ field and click on Save

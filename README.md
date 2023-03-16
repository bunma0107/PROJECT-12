# PROJECT-12
Ansible Refactoring and Static Assignments (Imports and Roles)


Step 1 – Jenkins job enhancement

Go to your Jenkins-Ansible server and create a new directory called ansible-config-artifact – we will store there all artifacts after each build.

![image](https://user-images.githubusercontent.com/113097621/225572775-9b5baddb-ca86-49b0-ac7a-7da72b139189.png)

Change permissions to this directory, so Jenkins could save files there – 

![image](https://user-images.githubusercontent.com/113097621/225573337-55d92b03-ba45-44c6-abb6-be1ab2d07cc2.png)

Go to Jenkins web console -> Manage Jenkins -> Manage Plugins -> on Available tab search for Copy Artifact and install this plugin without restarting Jenkins

![image](https://user-images.githubusercontent.com/113097621/225574019-658b1d73-5b54-4fd6-94ae-4c5d976897dd.png)

![image](https://user-images.githubusercontent.com/113097621/225574209-81039a96-242a-4473-a2b4-7384c76ec86c.png)

Create a new Freestyle project and name it save_artifacts.

![image](https://user-images.githubusercontent.com/113097621/225575450-14876c13-c4fa-4c35-99e2-8b406ad74db5.png)

![image](https://user-images.githubusercontent.com/113097621/225575558-1beff456-5a57-4277-a686-9ccea72c7ef6.png)

The main idea of save_artifacts project is to save artifacts into /home/ubuntu/ansible-config-artifact directory. To achieve this, create a Build step and choose Copy artifacts from other project, specify ansible as a source project and /home/ubuntu/ansible-config-artifact as a target directory.

![image](https://user-images.githubusercontent.com/113097621/225579869-074accfa-3c75-4ef3-b1d3-1402d51d1bbf.png)



![image](https://user-images.githubusercontent.com/113097621/225571449-46a2ceb9-c372-43b8-912d-5c699748fc61.png)

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

![image](https://user-images.githubusercontent.com/113097621/225586996-854c4004-14da-40aa-8c83-f392b1d13b5f.png)

![image](https://user-images.githubusercontent.com/113097621/225587074-3990864c-7be4-448f-8d6e-62abce670dd7.png)

Lets Check our build
![image](https://user-images.githubusercontent.com/113097621/225608903-66b12195-1ec6-42a5-9959-5a64a2162096.png)

Refactor Ansible code by importing other playbooks into site.yml

Create a new file names site.yml Under Playbooks and Create a new folder in root of the repository and name it static-assignments. The static-assignments folder is where all other children playbooks will be stored. 

![image](https://user-images.githubusercontent.com/113097621/225613990-08a7f899-3895-4cf6-9a6e-44721b58d02f.png)

Move common.yml file into the newly created static-assignments folder.

![image](https://user-images.githubusercontent.com/113097621/225615148-ddc2ff05-dfb9-44a5-8b10-f9c0ceeec728.png)

Inside site.yml file, import common.yml playbook

![image](https://user-images.githubusercontent.com/113097621/225616634-dc764058-4a17-452e-a6a2-e0d4927701d2.png)

My Ansible folder structure should looks like this
![image](https://user-images.githubusercontent.com/113097621/225618639-5eb71a7a-29c4-464a-9358-fb72b591dc95.png)


    Run ansible-playbook command against the dev environment
Since you need to apply some tasks to your dev servers and wireshark is already installed – you can go ahead and create another playbook under static-assignments and name it common-del.yml. In this playbook, configure deletion of wireshark utility.

![image](https://user-images.githubusercontent.com/113097621/225624665-8f66febf-30f1-42c5-88f9-871f9658a406.png)

update site.yml with - import_playbook: ../static-assignments/common-del.yml instead of common.yml and run it against dev servers:

![image](https://user-images.githubusercontent.com/113097621/225626072-c1f753cc-ab61-4487-baf1-9995be25ac92.png)










push pull
![image](https://user-images.githubusercontent.com/113097621/225608063-73e67bd2-386d-4e9b-aa24-e0731fcd39fe.png)


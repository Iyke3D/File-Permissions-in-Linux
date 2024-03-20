# Use File Commands to Manage Permissions in Linux (Tools of the Trade - SQL & Linux)
<p><b>Synopsis</b></br></br>
The softcopy of this Portfolio is available in https://drive.google.com/file/d/1a7pWAx9LcPXZvO-bNQTBnut5j0yumLJV/view?usp=sharing </br>
Review the scenario below. Then, complete the step-by-step instructions.

You are a security professional at a large organization. You mainly work with their research team. Part of your job is to ensure users on this team are authorized with the appropriate permissions. This helps keep the system secure. 

Your task is to examine existing permissions on the file system. You’ll need to determine if the permissions match the authorization that should be given. If they do not match, you’ll need to modify the permissions to authorize the appropriate users and remove any unauthorized access.</br></br>
<b>Project description</b></br>
The project is about using Linux commands for Authorization. It consists of the following:
1.	Checking permissions for files in a directory
2.	Check for incorrect file permissions and change permissions as needed
3.	Remove unauthorized access to a directory
My task in the organization I work is to examine existing permissions and files in the projects folder and determine if the permission is allowed then the authorization should be given but if they do not match, then I will need to modify the permissions to authorize the appropriate users and remove any unauthorized access. This helps to keep the system secure.</br></br>

<strong>Check file and directory details</strong></br></br>
![image](https://github.com/Iyke3D/File-Permissions-in-Linux/assets/118365903/f53a3f6e-f42b-4bbe-acea-da192197a0be) </br><b>Figure 1 – Navigate to the Project Folder</b></br></br>
When I opened the terminal, I have to first navigate to the projects folder as shown in the Figure 1 as shown above. The cd command is Change Directory which helps with the navigation process. The /home/researcher2/projects means to navigate to the home, then the researcher2 sub-directory and the projects directory in that order.</br></br>
![image](https://github.com/Iyke3D/File-Permissions-in-Linux/assets/118365903/02df56f7-d48d-484b-a574-ec80397cfc09) </br><b>Figure 2 – Show Files and Directory Listing</b></br></br>
I used the <strong>ls command</strong> which is to show the file and directory listing together with the -l flag command which shows the permissions assigned to both files and directory. From Figure 2 above, there are 4 files (project_k.txt, project_m.txt, project_r.txt and project_t.txt) and 1 directory (drafts). Using the ls alone will only show these files and folders alone. However, using it with the -l command will show the access rights in the form of rwx.</br>
![image](https://github.com/Iyke3D/File-Permissions-in-Linux/assets/118365903/7edce073-7092-41c6-bc64-b5b42d775315) </br><b>Figure 3 – Show hidden File with the -a command</b></br></br>
To further see extra details of each file and folder especially the hidden folders, I used the <strong>-a flag</strong> to see if there is a hidden file or folder that has been archived in the file system. Consequently, the .project_x.txt is the only hidden file as shown in Figure 3.</br>

<strong>Describe the permissions string</strong></br></br>
![image](https://github.com/Iyke3D/File-Permissions-in-Linux/assets/118365903/7ab499af-d61e-490a-9a74-e39953242662) </br></br><b>Figure 4 – Combining both the l and the -a commands</b></br></br>
For demonstration purposes, I decided to combine both the l and the a flags with the listing to show all extra details including the hidden file and/or directory. This is written as ls  -la. The permission string rwx in Figure 4 means that the file has Read, Write and Execute commands. Read means that the file or the folder (directory) can be read or opened but cannot be edited (changing its name or editing the contents of the file. The d in drwx stands for directory which means that the object is a directory and not a file. However, those without the d string but with – symbol e.g. -rwx means that the object is a file with the Read, Write and Execute permission. The Execute permission means that the object can be executed.</br>

<strong>Change file permissions</strong></br></br>
![image](https://github.com/Iyke3D/File-Permissions-in-Linux/assets/118365903/3f69bbff-e5ff-4a2b-99a1-ed015c6b0cab) </br><b>Figure 5 – Change File Permission with the chmod command</b></br></br>
In analyzing the permissions for the file, I noticed that the project_k.txt file has the write permission assigned to the owner other (there are three types of owners which are: User, Group and others) which they should not have. I now changed it with the command chmod o-w project_k.txt. The <i><strong>chmod command is a linux command that is used to modify the permissions and access mode of files and directories</strong></i>. In changing the access rights for the file, I ensured that I wrote the o-w command must be written together without any space in between them.</br>
![image](https://github.com/Iyke3D/File-Permissions-in-Linux/assets/118365903/9c3ef7a1-bc27-4737-8b43-70cdd4c84e88) </br><b>Figure 6 – Change the File Permission of the project_m.txt File</b></br></br>
Furthermore, I also noticed that the group owners of the project_m.txt file has both Read and Write permissions. To remedy the situation, I now changed the file permission for the group owners of the project_m.txt file with the following command: <i><strong>chmod g-r, g-w project_m.txt</strong></i></br>
The g-r means to remove read permission of the group owners of the file. This is possible with the -r command. Likewise, the g-w means to remove the write permission of the group owners of the project_m.txt file. I also ensured that both command is separated with a comma.</br>

<strong>Change file permissions on a hidden file</strong></br></br>
![image](https://github.com/Iyke3D/File-Permissions-in-Linux/assets/118365903/a7249a7d-9b4c-4605-a854-8d1105c5078d) </br><b>Figure 7 – Change the File Permission for a hidden file</b></br></br>
The only hidden file in the projects directory in Figure 7 is .project_x.txt. The . notation next to the filename denotes that the file is a hidden file in Linux Operating System. The users and the group owners have Write permissions which they are not supposed to have. Likewise, I was also instructed to assign the Read permission for the group owners.  To solve the issue, I used the following command to change the access rights of the file: <i><strong>chmod u-w, g+r, g-w .project_x.txt</strong></i> </br>

<strong>Change directory permissions</strong></br></br>
![image](https://github.com/Iyke3D/File-Permissions-in-Linux/assets/118365903/5b7072f4-c244-4d7a-aae0-40ffae9607c3) </br><b>Figure 8 – Change the Directory Permission</b></br></br>
The only directory in the projects folder is the drafts directory (it is in dark blue color). I changed the directory permission of the group owners to remove the execute command for the directory using the following command: <i><strong>chmod g-x drafts</strong></i> </br>

<b>Summary</b></br>
The chmod is a required linux command to change file permissions for both files and directories on the file system. The use of <strong>hyphen (-)</strong> together with the chmod and the owner (User, Group and Other) means that you want to remove the access rights to that file or folder but with the <strong>plus (+) </strong>notation, the individual will have the permission added to them. We can use the ls command to list the files and folders that exists in a particular folder like the home directory. 
We can use the ls -la command to display the details of a file of a root folder including any hidden files and folder.  
</p>

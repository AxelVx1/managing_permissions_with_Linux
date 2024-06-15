# managing_permissions_with_Linux
Using Linux commands in Bash Shell to manage users.

# Glossary:
1. [Checking File and Directory Details](#checking_file_and_directory_details)
2. [Describing the Permission Strings](#describing_the_permission_strings)
3. [Changing File Permissions](#Changing_File_Persmissions)
4. [Changing File Permissions on Hidden Files](#changing_file_permissions_on_hidden_files)
5. [Changing Directory Permissions](#changing_directory_permissions)
6. [Summary](#summary)

# Scenario:

To enhance our system's security, the research team at my organization needs to update the file permissions for specific files and directories within the "projects" directory. Currently, the permissions do not align with the necessary authorization levels. To address this issue, I carried out the following tasks:

# Checking_File_and_Directory_Details:

![Image](https://github.com/AxelVx1/managing_permissions_with_Linux/blob/main/Linux1.png?raw=true)

To check the permissions of each file and directory in "projects" I utilize the "ls" command followed by the "-la" option. This displays a detailed list of the current directory’s contents with all permissions and any hidden files. Now, I can use this information to look at the permissions associated with each file/directory and adjust them accordingly.

# Describing_the_Permission_Strings:

The first column shown in the screenshot displays a 10-character string that represents the permissions. We can analyze this string to determine who is authorized to access the file and their specific permissions.

 - 1st character: This character is either a "d" or a hyphen (-) and indicates the file type. If it’s a "d", it’s a directory. If it’s a hyphen (-), it’s a regular file.
 - 2nd-4th characters: These characters indicate the read (r), write (w), and execute (x) permissions for the user. When one of these characters is a hyphen (-) instead, it indicates that this permission is not granted to the user.
 - 5th-7th characters: These characters indicate the read (r), write (w), and execute (x) permissions for the group. When one of these characters is a hyphen (-) instead, it indicates that this permission is not granted for the group.
 - 8th-10th characters: These characters indicate the read (r), write (w), and execute (x) permissions for other. This owner type consists of all other users on the system apart from the user and the group. When one of these characters is a hyphen (-) instead, that indicates that this permission is not granted for other.

As an example, we can take a look at the permissions for "project_r.txt", which are "-rw-rw-r--". The first character is a hyphen so we can tell this is a file and not a directory. The first three characters are "rw-", this means the user has read and write permissions and the same is true for group because its permissions are also "rw-". Finally, we see that other has only read permissions because the 8th-10th characters are "r–-". 

# Changing_File_Persmissions:

My organization determined that other should not have write access to any files. To make these changes I will have to remove their write access from "project_k.txt". The following screenshot shows my actions:

![Image](https://github.com/AxelVx1/managing_permissions_with_Linux/blob/main/Linux2.png?raw=true)

I utilized the "chmod" command to change the permissions and then checked my work using the "ls -la" from before.

# Changing_File_Persmissions_on_Hidden_Files:

The research team at my organization recently archived "project_x.txt". They decided that no one should have write access to this project, but the user and group should have read access enabled. The following screenshot shows my actions:

![Image](https://github.com/AxelVx1/managing_permissions_with_Linux/blob/main/Linux3.png?raw=true)

I can tell that ".project_x.txt" is a hidden file because it begins with a period (.). In this case, I removed write permission from user and group while enabling read permission to the group. 

# Changing_Directory_Persmissions:

Finally, my organization only wants the "researcher2" user to have access to the "drafts" directory and its contents. Meaning, no one other than "researcher2" should have execute permissions. The following screenshot shows my actions:

![Image](https://github.com/AxelVx1/managing_permissions_with_Linux/blob/main/Linux4.png?raw=true)

From the image we see that line 1 indicates the current directory (projects), and line 2 indicates the parent directory (home). Next, Line 3 displays a file titled ".project_x.txt" and Line 4 is the directory (drafts) with restricted permissions. We can see that only researcher2 has execute permissions. It was previously determined that the group had execute permissions, so I used the "chmod" command to remove them.

# Summary:

For this project I altered various permissions in the "projects" directory to match my organization’s needs. I utilized different commands such as "ls -la" to check the permissions for the directory and "chmod" to change the permissions on files and directories.

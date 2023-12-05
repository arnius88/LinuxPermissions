<h1>Using Linux to manage file permissions</h1>


<h2>Project description and scenario</h2>

The research team in my company has requested an update of the permissions to access specific files within the `projects` directory. After examination, it appears that the existing permissions do not match the authorisation that should be given. Updating these permissions will allow the research team to carry out their job and keep the system secure. 
<br/>

<h2>Project walk-through:</h2>

 <h3><p align="center">Check file and directory details: </h3>

To determine the existing permissions in the `/home/researcher2/projects` directory, the following command was used in Linux:<br />

<img width="60%" alt="image" src="https://github.com/arnius88/LinuxPermissions/assets/152484037/22e69d99-81dd-4ed5-8987-f37c9201153f">
<br/>

The standard output shows the current permissions for each file and directory in the `/home/researcher2/projects` directory:
<br/>

<img width="60%" alt="image" src="https://github.com/arnius88/LinuxPermissions/assets/152484037/7cfed10f-e453-49d3-bf45-d275345b8a13">
<br/>

In order to check the existing permissions for each file I used the `ls` command together with the `-la` option to display a detailed listing of the file contents, including hidden files. The output of my command indicates that there are eight elements within the folder: one directory named `drafts`; one hidden file named `.project_x.txt`; and five other project files. The 10-character string at the beginning of each line indicates the permissions set on each file or directory.<br />

<h3><p align="center">
Describe the permissions string: </h3>

<img width="60%" alt="image" src="https://github.com/arnius88/LinuxPermissions/assets/152484037/59bd7979-20fa-4146-bcda-a8212f383c20">
<br />

In the example above, the line describing permissions for the `project_m.txt` file begins with a 10-digits string. Each character conveys different information about the permissions.
<br />

The **first character** indicates the type of file we’re looking at:
<br />

+ `d` for directory
+ `-` for a regular file
<br />

The **second to fourth characters** indicate the type of permission for the User owner:
<br />

+	`r` for read
+	`w` for write
+	`x` for execute
+	in case of lack of permission, `-` will appear.
<br />

The **fifth to seventh characters** indicate the type of permission for the Group owner:
<br />

+	`r` for read
+	`w` for write
+	`x` for execute
+	in case of lack of permission, `-` will appear.
<br />

In the example above, we are looking at a regular file type named `project_m.txt` where the User owner has permission to both read and write the file, the Group owner has read only permission and the Other owner lacks any permission. In this case, no owner has execute permission on the file.
<br/>

<h3><p align="center">Change file permissions:</h3>

<img width="60%" alt="image" src="https://github.com/arnius88/LinuxPermissions/assets/152484037/c8194b8b-3669-45c7-a441-856fd5863f96">
<br/>

I received a request to revoke write permission for the Other owner from the file named `project_k.txt`.
<br/>

The following command allowed me to remove write permission for Other from the specified file:
<br/>

`chmod o-w project_k.txt`
<br/>

The `chmod` command allowed me to change permissions on the specified file with two arguments:
<br/>

+ the first argument after `chmod` describes how to change permissions. In this case `o-w` indicates that we want to remove (`-` sign) write permission to the Other owner;
+ The second argument is the file name that needs the permission modified.
<br/>

<h3><p align="center">Change file permissions on a hidden file:</h3>

I was able to check permissions for active and archived files by using `ls -la`. Archived files are hidden files that are recognisable by a `.` immediately in front of the file name.
<br/>

<img width="60%" alt="image" src="https://github.com/arnius88/LinuxPermissions/assets/152484037/f91813fd-9457-4efe-ab41-f8611c9212a4">
<br/>

The `.project_x.txt` file was recently archived by the research team, therefore no owner was meant to have write permissions on it. It appeared that both User and Group owners still had write permissions on the specific file.
<br/>

The following `chmod` command:
<br/>

`chmod u-w,g-w,g+r .project_x.txt`
<br/>

allowed me to revoke write permissions to both User (`u-w`) and Group (`g-w`). At the same time, I was able to add read permission to Group by adding `g+r`.
<br/>

<h3><p align="center">Change directory permissions:</h3>

Currently, both User and Group owners have execute permission enabled for the directory named `drafts`. However, the company decided that only User owner (in this case `researcher2`) should have execute permission on that specific directory.
<br/>

<img width="60%" alt="image" src="https://github.com/arnius88/LinuxPermissions/assets/152484037/a6969f15-4d8e-4ea9-9914-f08d9ff59267">
<br/>

In order to modify the permissions accordingly I used the following command on Linux:
<br/>

`chmod g-x drafts`
<br/>

In the above example, I only needed to remove execute permission from the Group owner by specifying `g-x` in the first argument of the `chmod` command, since the User owner already had full permission for the `drafts` directory.
<br/>

<h2>Project summary:</h2>

In the above example, I have shown my ability to update the existing permissions in the `projects` directory using Linux command-line in order to match the level of authorization my organization wanted. The main command that allowed me to achieve this was `chmod`.
<br/>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>

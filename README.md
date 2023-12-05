<h1>Using Linux to manage file permissions</h1>


<h2>Description and Scenario</h2>

The research team in my company has requested an update of the permissions to access specific files within the `projects` directory. After examination, it appears that the existing permissions do not match the authorisation that should be given. Updating these permissions will allow the research team to carry out their job and keep the system secure. 
<br/>

<h2>Program walk-through:</h2>

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
Describe the permissions string: <h3/>

<img width="60%" alt="image" src="https://github.com/arnius88/LinuxPermissions/assets/152484037/59bd7979-20fa-4146-bcda-a8212f383c20">

In the example above, the line describing permissions for the `project_m.txt` file begins with a 10-digits string. Each character conveys different information about the permissions.
<br />

The **first character** indicates the type of file we’re looking at:
<br />





<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>

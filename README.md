# Linux File Permissions Management

## Project Description
The research team at my organization needs to update the file permissions for certain files and directories within the `projects` directory. The permissions do not currently reflect the level of authorization that should be given. Checking and updating these permissions will help keep their system secure. 

Step 1: Make the Project Directory and Move into the Project Directory

<img src="https://i.imgur.com/pukPeuw.png" width="750">

## Checking File and Directory Details
To begin, I used the `ls` command with the `-la` option to display a detailed listing of the file contents that also returned hidden files. The output of my command indicates that there is one directory named `drafts`, one hidden file named `.project_x.txt`, and five other project files.

<img src="https://i.imgur.com/mmH5BXZ.png" width="750">

The 10-character string in the first column represents the permissions set on each file or directory. This string can be deconstructed to determine who is authorized to access the file and their specific permissions:
* **1st character**: Indicates the file type; a `d` indicates a directory, and a hyphen (`-`) indicates a regular file.
* **2nd-4th characters**: Indicate the read (`r`), write (`w`), and execute (`x`) permissions for the user.
* **5th-7th characters**: Indicate the read (`r`), write (`w`), and execute (`x`) permissions for the group.
* **8th-10th characters**: Indicate the read (`r`), write (`w`), and execute (`x`) permissions for other (all other users on the system apart from the user and the group).
* **Hyphens (`-`)**: When a hyphen appears in place of `r`, `w`, or `x`, it indicates that specific permission is not granted.

<img src="https://i.imgur.com/M1M8Tb8.png" width="750">

## Changing File Permissions
The organization determined that "other" shouldn't have write access to any of their files. 
* **Standard Files:** I determined `project_k.txt` must have the write access removed for other. I used the `chmod` command to change these permissions.

<img src="https://i.imgur.com/jzIT8O9.png" width="750">

* **Hidden Files:** The team archived `.project_x.txt` and requested that no one have write access, but the user and group should have read access. I removed write permissions from the user with `u-w`, removed write permissions from the group with `g-w`, and added read permissions to the group with `g+r`. 

<img src="https://i.imgur.com/qpg9dcE.png" width="750">

## Changing Directory Permissions
My organization only wants the `researcher2` user to have access to the `drafts` directory and its contents. This means no one other than `researcher2` should have execute permissions. I previously determined that the group had execute permissions, so I used the `chmod` command to remove them. 

<img src="https://i.imgur.com/EH9SlBq.png" width="750">

## Summary
I changed multiple permissions to match the level of authorization my organization wanted for files and directories in the `projects` directory. The first step was using `ls -la` to check the permissions for the directory, which informed my decisions in the following steps. I then used the `chmod` command multiple times to successfully change the permissions on the files and directories.

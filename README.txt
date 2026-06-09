# Linux File Permissions Management

## Project Description
[cite_start]The research team at my organization needs to update the file permissions for certain files and directories within the `projects` directory[cite: 19]. [cite_start]The permissions do not currently reflect the level of authorization that should be given[cite: 20]. [cite_start]Checking and updating these permissions will help keep their system secure[cite: 21]. 

## Checking File and Directory Details
[cite_start]To begin, I used the `ls` command with the `-la` option to display a detailed listing of the file contents that also returned hidden files[cite: 26]. [cite_start]The output of my command indicates that there is one directory named `drafts`, one hidden file named `.project_x.txt`, and five other project files[cite: 27].

[cite_start]The 10-character string in the first column represents the permissions set on each file or directory[cite: 28]. [cite_start]This string can be deconstructed to determine who is authorized to access the file and their specific permissions[cite: 30]:
* [cite_start]**1st character**: Indicates the file type; a `d` indicates a directory, and a hyphen (`-`) indicates a regular file[cite: 32, 33].
* [cite_start]**2nd-4th characters**: Indicate the read (`r`), write (`w`), and execute (`x`) permissions for the user[cite: 34].
* [cite_start]**5th-7th characters**: Indicate the read (`r`), write (`w`), and execute (`x`) permissions for the group[cite: 36].
* [cite_start]**8th-10th characters**: Indicate the read (`r`), write (`w`), and execute (`x`) permissions for other (all other users on the system apart from the user and the group)[cite: 38, 39].
* [cite_start]**Hyphens (`-`)**: When a hyphen appears in place of `r`, `w`, or `x`, it indicates that specific permission is not granted[cite: 35, 37, 40].

## Changing File Permissions
[cite_start]The organization determined that "other" shouldn't have write access to any of their files[cite: 47]. 
* [cite_start]**Standard Files:** I determined `project_k.txt` must have the write access removed for other[cite: 49]. [cite_start]I used the `chmod` command to change these permissions[cite: 52].
* [cite_start]**Hidden Files:** The team archived `.project_x.txt` and requested that no one have write access, but the user and group should have read access[cite: 57, 58]. [cite_start]I removed write permissions from the user with `u-w`, removed write permissions from the group with `g-w`, and added read permissions to the group with `g+r`[cite: 63, 64]. 

## Changing Directory Permissions
[cite_start]My organization only wants the `researcher2` user to have access to the `drafts` directory and its contents[cite: 66]. [cite_start]This means no one other than `researcher2` should have execute permissions[cite: 67]. [cite_start]I previously determined that the group had execute permissions, so I used the `chmod` command to remove them[cite: 70]. 

## Summary
[cite_start]I changed multiple permissions to match the level of authorization my organization wanted for files and directories in the `projects` directory[cite: 73]. [cite_start]The first step was using `ls -la` to check the permissions for the directory, which informed my decisions in the following steps[cite: 74, 75]. [cite_start]I then used the `chmod` command multiple times to successfully change the permissions on the files and directories[cite: 75].
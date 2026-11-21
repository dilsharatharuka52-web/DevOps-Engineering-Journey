# **Linux Administration – Complete Lesson 01**

DevOps Beginner Practice

English + Sinhala

අද ඔයා ඉගෙනගෙන තියෙන්නේ Linux Administration වල ඉතාම වැදගත් කොටසක්. මේවා DevOps Engineer කෙනෙක් විදිහට Linux servers manage කරනකොට දිනපතාම භාවිතා වෙන commands.

අපි මේ lesson එක කොටස් 9කට බෙදලා ඉගෙන ගමු.

1. `ls` – Listing files and directories
    
2. Hidden files – Hidden files බලන ආකාරය
    
3. `ls -F` – File types හඳුනාගැනීම
    
4. Sorting – Time සහ reverse order අනුව files බලන ආකාරය
    
5. `tree` – Directory structure
    
6. Linux Permissions – File permissions
    
7. `chmod` සහ `umask` – Permission management
    
8. `find` – Files search කිරීම
    
9. `cat`, `less`, `head`, `tail`, `nano` – File content management
    

සෑම කොටසකම:

- Simple English definition
    
- සිංහල පැහැදිලි කිරීම
    
- Commands
    
- Practical examples
    
- Practice questions
    

# **1. Linux** `ls` **Command**

## **1.1 What is ls?**

**Simple English:**

`ls` is a Linux command used to list files and directories.

**සිංහලෙන්:**

Linux වල දැනට තියෙන directory එකේ files සහ folders බලාගන්න `ls` command එක භාවිතා කරනවා.

Example:

```
ls
```

Output:

```
documents  downloads  projects  notes.txt
```

මෙහි පෙන්වන්නේ current directory එක ඇතුළේ තියෙන files සහ directories.

## **1.2 Understanding** `ls -l`

Command:

```
ls -l
```

`-l` කියන්නේ Long Listing Format.

මෙහිදී files පිළිබඳ වැඩි විස්තර පෙන්වනවා.

Example output:

```
-rw-rw-r-- 1 jason users 10400 Sep 27 08:52 sales.data
```

මෙහි කොටස් 7ක් තියෙනවා.

**Understanding ls -l output**

# **-rw-rw-r--**

File permissions

**1**

`1`

Hard link count

**2**

`jason`

Owner name

**3**

`users`

Group name

**4**

`10400`

File size in bytes

**5**

`Sep 27 08:52`

Last modification time

**6**

`sales.data`

File name

**වැදගත්:**

ඔයාගේ notes වල number of links කියන්නේ hard link count එක. ඒක file එකට සම්බන්ධ hard links ගණනයි. Directories වලදී subdirectories නිසාත් මේ අගය වැඩි වෙන්න පුළුවන්.

File size `10400` කියන්නේ bytes.

## **1.3 More useful ls commands**

|Command|Meaning|
|---|---|
|`ls`|List files|
|`ls -l`|Detailed listing|
|`ls -lh`|Human-readable file sizes|
|`ls -lt`|Newest modified files first|
|`ls -la`|Include hidden files|
|`ls -R`|Recursive listing|
|`ls --color`|Colorize output|

Example:

```
ls -lh
```

Instead of:

```
10400
```

ඔයාට මෙවැනි readable size එකක් පෙන්වන්න පුළුවන්:

```
11K
```

# **2. Hidden Files in Linux**

## **2.1 What are hidden files?**

**Simple English:**

Hidden files are files whose names begin with a dot (`.`).

**සිංහලෙන්:**

Linux වල file name එකේ මුලට `.` (dot) එකක් තියෙනවා නම් ඒ file එක hidden file එකක් විදිහට සලකනවා.

Examples:

```
.env
.gitignore
.bashrc
.profile
.ssh
```

මේ files සාමාන්‍ය `ls` command එකෙන් පෙන්වන්නේ නැහැ.

ඇයි hidden කරන්නේ?

- Configuration files hide කරන්න.
    
- System settings organize කරන්න.
    
- Sensitive application configuration files සාමාන්‍ය listing එකෙන් වෙන් කර තබන්න.
    

සැලකිල්ල: Hidden කිරීම security protection එකක් නෙවෙයි.

## **2.2 How to show hidden files?**

```
ls -a
```

`-a` = All files.

Example output:

```
.  ..  .env  .gitignore  notes.txt  projects
```

මෙහි:

|Symbol|Meaning|
|---|---|
|`.`|Current directory|
|`..`|Parent directory|
|`.env`|Hidden file|
|`.gitignore`|Hidden file|

## **2.3 Combine command options**

Linux වල options combine කරන්න පුළුවන්.

මේ commands තුනේ ප්‍රතිඵල සමානයි:

```
ls -l -a
ls -la
ls -al
```

**Remember:**

`ls -la` = Long listing + All files.

DevOps practical example:

```
ls -la ~/.ssh
```

SSH configuration සහ key files තියෙන directory එක පරීක්ෂා කරන්න පුළුවන්.

# **3. Listing Files by Type –** `ls -F`

## **3.1 What is ls -F?**

**Simple English:**

`ls -F` displays special symbols to identify file types.

**සිංහලෙන්:**

File එකක් directory එකක්ද, executable එකක්ද, symbolic link එකක්ද කියලා file name එක අසල special symbols පෙන්වනවා.

Command:

```
ls -F
```

Example output:

```
documents/
backup/
script.sh*
shortcut@
notes.txt
```

|Symbol|Meaning|
|---|---|
|`/`|Directory|
|`*`|Executable file|
|`@`|Symbolic link|
|No symbol|Regular file|

## **3.2 What is a symbolic link?**

**Simple English:**

A symbolic link is a shortcut that points to another file or directory.

**සිංහලෙන්:**

Symbolic link එකක් කියන්නේ වෙනත් file එකකට හෝ directory එකකට සම්බන්ධ shortcut එකක්.

Example:

```
touch original.txt
ln -s original.txt shortcut.txt
ls -l
```

Output:

```
original.txt
shortcut.txt -> original.txt
```

මෙහි `shortcut.txt` කියන්නේ `original.txt` වෙත point කරන symbolic link එකක්.

![[Pasted image 20261113163232.png]]
Symbolic links භාවිතා කරන අවස්ථා:

1. Long file paths කෙටි කරගැනීමට.
    
2. Software versions අතර shortcuts සෑදීමට.
    
3. Applications වලට අවශ්‍ය file location එකක් පහසුවෙන් ලබාදීමට.
    

Example:

```
ln -s /opt/myapp/releases/v2 /opt/myapp/current
```

මෙයින් `current` කියන link එක `v2` release එකට point කරනවා.

# **4. Listing Files by Time and Reverse Order**

මේ commands files sort කරලා පෙන්වන්න භාවිතා කරනවා.

## **4.1** `ls -t`

```
ls -t
```

**English:** List files by modification time.

**සිංහල:** අලුතින්ම modify කරපු files මුලින් පෙන්වනවා.

Example:

```
file3.txt
file2.txt
file1.txt
```

## **4.2** `ls -r`

```
ls -r
```

Reverse order එකට files පෙන්වනවා.

## **4.3** `ls -latr`

```
ls -latr
```

මේක වැදගත් command එකක්.

Breakdown:

|Option|Meaning|
|---|---|
|`-l`|Long format|
|`-a`|All files|
|`-t`|Sort by modification time|
|`-r`|Reverse order|

එකතු කළාම:

**Hidden files ඇතුළුව, detailed information සමඟ, පැරණිම modified file එක මුලින් පෙන්වනවා.**

DevOps practical use:

Server එකක මෑතකදී modify වුණු files හොයාගන්න:

```
ls -lt
```

පැරණිම modified files බලන්න:

```
ls -latr
```

## **4.4** `ls -R`

```
ls -R
```

**Recursive listing** කියන්නේ directory එක ඇතුළේ තියෙන subdirectories ද ඇතුළුව සියලුම files list කරන එකයි.

උදාහරණයක්:

```
projects:
app1  app2

projects/app1:
index.py  config.py

projects/app2:
main.py
```

# **5. The** `tree` **Command**

## **5.1 What is tree?**

**Simple English:**

The tree command displays directories and files in a tree-like structure.

**සිංහලෙන්:**

`tree` command එකෙන් files සහ directories ගසක අතු වගේ structure එකකට පෙන්වනවා.
![[Pasted image 20261113163217.png]]

Example:

```
tree
```

Output:

```
devops-lab/
├── documents/
│   ├── notes.txt
│   └── linux.txt
├── scripts/
│   └── backup.sh
└── projects/
    └── app.py
```

## **5.2 Useful tree options**

|Command|Purpose|
|---|---|
|`tree`|Show files and directories|
|`tree -d`|Directories only|
|`tree -L 2`|Limit depth to 2 levels|
|`tree -a`|Include hidden files|
|`tree -c`|Colorize output|

If `tree` is not installed:

Ubuntu/Debian:

```
sudo apt update
sudo apt install tree
```

Practice:

```
tree -d
tree -L 2
tree -a
```

# **6. Linux File Permissions**

Very important for DevOps

මේ කොටස හොඳට ඉගෙන ගන්න. Linux server security වලට මේක අත්‍යවශ්‍යයි.

## **6.1 What are file permissions?**

**Simple English:**

File permissions control who can read, write, and execute files or directories.

**සිංහලෙන්:**

Linux system එකේ file එකක් හෝ directory එකක් කවුද භාවිතා කරන්නේ, කවුද edit කරන්නේ, කවුද execute කරන්නේ කියන දේ පාලනය කරන්නේ permissions මඟින්.

## **6.2 Three permission types**

|Symbol|Name|Meaning|
|---|---|---|
|`r`|Read|කියවීමට|
|`w`|Write|ලිවීමට / වෙනස් කිරීමට|
|`x`|Execute|ක්‍රියාත්මක කිරීමට|

Example:

```
-rwxr-xr--
```

මේක කොටස් තුනකට බෙදෙනවා:

# **- rwx | r-x | r--**

**User**

`rwx`

Owner

**Group**

`r-x`

Group

**Other**

`r--`

Everyone else

## **6.3 Permission categories**

|Symbol|Name|Meaning|
|---|---|---|
|`u`|User|File owner|
|`g`|Group|File's group|
|`o`|Others|Other users|
|`a`|All|User + Group + Others|

Example:

```
chmod u+x script.sh
```

මෙයින් ownerට execute permission එක add කරනවා.

## **6.4 Important difference: File vs Directory permissions**

මෙයත් අනිවාර්යයෙන් දැනගන්න.

|Permission|File|Directory|
|---|---|---|
|`r`|Read file content|List directory contents|
|`w`|Modify file content|Create/delete/rename entries (with appropriate access)|
|`x`|Execute file|Enter/traverse directory|

උදාහරණයක්:

Directory එකකට `x` permission නැත්නම් ඒ directory එක හරහා files වෙත යන්න බැහැ.

# **7. Changing Permissions –** `chmod`

## **7.1 What is chmod?**

**Simple English:**

`chmod` means Change Mode. It changes file and directory permissions.

**සිංහලෙන්:**

File එකක හෝ directory එකක read, write, execute permissions වෙනස් කරන්න `chmod` command එක භාවිතා කරනවා.

## **7.2 Symbolic method**

Syntax:

```
chmod [who][operator][permission] filename
```

Operators:

|Operator|Meaning|
|---|---|
|`+`|Add permission|
|`-`|Remove permission|
|`=`|Set exact permission|

Examples:

**1. Add execute permission to owner**

```
chmod u+x script.sh
```

**2. Remove write permission from group**

```
chmod g-w notes.txt
```

**3. Give read permission to everyone**

```
chmod a+r notes.txt
```

**4. Set owner read/write, group read, others no access**

```
chmod u=rw,g=r,o= notes.txt
```

Check:

```
ls -l notes.txt
```

## **7.3 Numeric permission method**

මේක ඉතාම වැදගත්.

Linux numeric permissions සඳහා:

|Permission|Number|
|---|---|
|Read (`r`)|4|
|Write (`w`)|2|
|Execute (`x`)|1|
|None (`-`)|0|

ඒවා එකතු කරලා permission number එක හදාගන්නවා.

**How numeric permissions work**

# **4**

**Read**

100 in binary

# **2**

**Write**

010 in binary

# **1**

**Execute**

001 in binary

Examples:

|Combination|Calculation|Result|
|---|---|---|
|`r--`|4|4|
|`-w-`|2|2|
|`--x`|1|1|
|`rw-`|4 + 2|6|
|`r-x`|4 + 1|5|
|`-wx`|2 + 1|3|
|`rwx`|4 + 2 + 1|7|

### **Example: chmod 755**

```
chmod 755 script.sh
```

Breakdown:

|Category|Calculation|Permission|
|---|---|---|
|Owner|4+2+1 = 7|`rwx`|
|Group|4+0+1 = 5|`r-x`|
|Others|4+0+1 = 5|`r-x`|

Result:

```
-rwxr-xr-x
```

### **Common permission values**

|Number|Permission|Use|
|---|---|---|
|777|`rwxrwxrwx`|Everyone full access (usually unsafe)|
|755|`rwxr-xr-x`|Common directory/executable permissions|
|700|`rwx------`|Owner only|
|644|`rw-r--r--`|Common regular file|
|600|`rw-------`|Private file|
|640|`rw-r-----`|Owner and group read access|

## **7.4 Practical chmod lab**

Create a script:

```
cd ~/devops-lab

touch deploy.sh

echo '#!/bin/bash' > deploy.sh
echo 'echo "Deploying application"' >> deploy.sh
```

Check permission:

```
ls -l deploy.sh
```

Add execute permission:

```
chmod u+x deploy.sh
```

Execute:

```
./deploy.sh
```

Expected:

```
Deploying application
```

# **8. The** `umask` **Command**

අපි කලින් umask ගැන ඉගෙන ගත්තා. දැන් ඒක මේ lesson එකට සම්බන්ධ කරගමු.

## **8.1 What is umask?**

**Simple English:**

`umask` controls the default permissions of newly created files and directories.

**සිංහලෙන්:**

අලුතින් create කරන files සහ directories වල default permissions පාලනය කරන command එක තමයි `umask`.

## **8.2 Check current umask**

```
umask
```

ඔයාගේ කලින් terminal output එක:

```
0002
```

ඒ කියන්නේ current umask value එක 0002.

## **8.3 Default permissions**

Linux වල සාමාන්‍ය base permissions:

|Type|Base permission|
|---|---|
|Regular file|666|
|Directory|777|

ඊට umask එක apply වෙනවා.

|Umask|New file|New directory|
|---|---|---|
|000|666|777|
|002|664|775|
|022|644|755|
|027|640|750|
|077|600|700|

**Technical note:** මේවා සාමාන්‍ය permission calculation examples. Umask එක සරල decimal subtraction එකක් නොව, permission bits ඉවත් කරන mask එකක්.

## **8.4 Practical test**

```
umask 027

touch test.txt
mkdir test_folder

ls -l test.txt
ls -ld test_folder
```

Expected:

```
-rw-r-----
drwxr-x---
```

ඔයාගේ Linux security practice එකට මේක වැදගත්.

# **9. The** `find` **Command**

Important DevOps skill

## **9.1 What is find?**

**Simple English:**

The `find` command searches for files and directories in a specified location.

**සිංහලෙන්:**

Linux system එකේ අවශ්‍ය file එකක් හෝ directory එකක් නම, size, modification time වැනි දේ අනුව සොයාගන්න `find` command එක භාවිතා කරනවා.

Syntax:

```
find [path] [expression]
```

Example:

```
find .
```

`.` කියන්නේ current directory එක.

මෙයින් current directory එක සහ ඒකේ subdirectories ඇතුළේ තියෙන files සහ directories පෙන්වනවා.

## **9.2 Find by name**

```
find . -name "notes.txt"
```

`notes.txt` කියන නම තියෙන files සොයනවා.

## **9.3 Find by name ignoring case**

```
find . -iname "NOTES.TXT"
```

මෙහි `-iname` නිසා uppercase/lowercase වෙනස නොසලකා සොයනවා.

Examples:

```
notes.txt
NOTES.TXT
Notes.txt
```

මේ තුනම match වෙන්න පුළුවන්.

## **9.4 Find directories only**

```
find . -type d
```

`d` = Directory.

## **9.5 Find files only**

```
find . -type f
```

`f` = Regular file.

## **9.6 Find and display long listing**

```
find . -name "*.txt" -ls
```

මෙයින් `.txt` files සොයාගෙන ඒවායේ detailed information පෙන්වනවා.

## **9.7 Find by modification time**

```
find . -mtime -7
```

සාමාන්‍යයෙන් මෙයින් අවසන් දින 7ක පරාසයේ modify වූ files සොයාගන්න පුළුවන්.

|Option|Meaning|
|---|---|
|`-mtime 7`|7 × 24-hour periods ago, rounded into day units|
|`-mtime -7`|Less than 7 days|
|`-mtime +7`|More than 7 days|

Exact time ranges අවශ්‍ය නම් `-mmin` හෝ `-newermt` භාවිතා කළ හැකියි.

Example:

```
find . -mmin -60
```

Last 60 minutes තුළ modified වූ files සොයනවා.

## **9.8 Find by file size**

```
find . -size +10M
```

10 MB ට වඩා විශාල files සොයනවා.

Examples:

|Command|Meaning|
|---|---|
|`-size +10M`|More than 10 MB|
|`-size -1M`|Less than 1 MB|
|`-size 100k`|Around 100 KiB in find's size units|

## **9.9 Find and execute commands**

මේක advanced concept එකක්.

Syntax:

```
find . -name "*.txt" -exec ls -l {} \;
```

මේක කොටස්වලට බලමු.

|Part|Meaning|
|---|---|
|`find .`|Search current directory|
|`-name "*.txt"`|Find text files|
|`-exec`|Run a command|
|`ls -l`|Command to execute|
|`{}`|Current found item|
|`\;`|End of exec command|

Example:

```
find . -name "*.txt" -exec ls -l {} \;
```

සොයාගත් සෑම `.txt` file එකක් සඳහාම `ls -l` execute කරනවා.

**DevOps safety tip:** `-exec rm` වැනි delete commands භාවිතා කරන්න කලින් `find` එකෙන් හොයාගන්න files මොනවාද කියලා පරීක්ෂා කරන්න.

# **10. Displaying Contents of Files**

Linux වල file content බලන්න commands කිහිපයක් තියෙනවා.

## **10.1** `cat`

**English:** Displays the contents of a file.

**සිංහල:** File එකක ඇතුළේ තියෙන text එක terminal එකේ පෙන්වනවා.

```
cat notes.txt
```

Multiple files:

```
cat file1.txt file2.txt
```

Long text file එකක් නම් සියලුම content එක එකවර display වෙන නිසා කියවීමට අපහසු වෙන්න පුළුවන්.

## **10.2** `more`

```
more notes.txt
```

Page by page file content බලන්න භාවිතා කරනවා.

- Space → Next page
    
- Enter → Next line
    
- q → Quit
    

## **10.3** `less`

```
less notes.txt
```

`less` කියන්නේ large text files browse කරන්න හොඳ command එකක්.

|Key|Function|
|---|---|
|Space|Next page|
|b|Previous page|
|↑|Previous line|
|↓|Next line|
|`/word`|Search word|
|n|Next match|
|q|Quit|

**Recommendation:** Large Linux log files කියවන්න `less` හොඳයි.

## **10.4** `head`

```
head notes.txt
```

File එකේ මුල් lines 10 පෙන්වනවා.

Specify number:

```
head -n 5 notes.txt
```

මුල් lines 5 පෙන්වනවා.

## **10.5** `tail`

```
tail notes.txt
```

File එකේ අවසාන lines 10 පෙන්වනවා.

```
tail -n 5 notes.txt
```

අවසාන lines 5 පෙන්වනවා.

## **10.6** `tail -f`

Very useful in DevOps

```
tail -f application.log
```

**English:** Continuously displays new lines added to a file.

**සිංහල:** File එකකට අලුතින් data එකතු වෙනකොට ඒවා real-time terminal එකේ පෙන්වනවා.

Example:

Terminal 1:

```
touch app.log
tail -f app.log
```

Terminal 2:

```
echo "Application started" >> app.log
echo "Database connected" >> app.log
echo "Request received" >> app.log
```

දැන් Terminal 1 එකේ අලුතින් එකතු වෙන lines පෙනෙනවා.

Stop කරන්න:

```
Ctrl + C
```

DevOps engineersලා application logs, server logs, deployment logs monitor කරන්න මේ command එක නිතර භාවිතා කරනවා.

# **11. Nano Editor**

## **11.1 What is nano?**

**Simple English:**

Nano is a simple terminal-based text editor used to create and edit files.

**සිංහලෙන්:**

Linux terminal එකෙන්ම text files create කරන්න සහ edit කරන්න භාවිතා කරන පහසු text editor එකක්.

Open:

```
nano notes.txt
```

Text එක type කරන්න.

![[Pasted image 20261113163610.png]]
Useful shortcuts:

|Shortcut|Purpose|
|---|---|
|`Ctrl + O`|Save file|
|`Enter`|Confirm filename|
|`Ctrl + X`|Exit|
|`Ctrl + K`|Cut current line|
|`Ctrl + U`|Paste cut text|
|`Ctrl + W`|Search|
|`Ctrl + G`|Help|

**Practice:**

```
nano devops-notes.txt
```

මේ text එක add කරන්න:

```
Linux Administration

Linux is important for DevOps Engineers.

Today I learned:
1. ls
2. chmod
3. umask
4. find
5. cat
6. tail
7. nano

My goal is to become a DevOps Engineer.
```

Save කරලා exit වෙන්න.

# **12. Complete Practical Lab – Linux Administration**

දැන් අපි අද ඉගෙනගත්ත හැම command එකක්ම එකම practical project එකකින් practice කරමු.

Hands-on Lab

**Project: DevOps Linux File Management**

## **Step 1 – Create project structure**

```
mkdir -p ~/devops-lab/linux-practice/{documents,scripts,logs,backup}
```

Go to the project:

```
cd ~/devops-lab/linux-practice
```

Create files:

```
touch documents/notes.txt
touch documents/sales.data
touch scripts/deploy.sh
touch logs/app.log
touch .env
touch .gitignore
```

Check directory structure:

```
tree -a
```

Expected:

```
linux-practice/
├── .env
├── .gitignore
├── backup
├── documents
│   ├── notes.txt
│   └── sales.data
├── logs
│   └── app.log
└── scripts
    └── deploy.sh
```

## **Step 2 – Add long text**

```
cat > documents/notes.txt <<'EOF'
Linux Administration

Linux is an open-source operating system.

DevOps engineers use Linux to manage servers.

Important Linux commands:
1. ls
2. chmod
3. umask
4. find
5. cat
6. tail
7. nano

My goal is to become a professional DevOps Engineer.
EOF
```

## **Step 3 – Practice listing commands**

```
ls
ls -l
ls -la
ls -lh
ls -lt
ls -latr
ls -F
ls -R
tree
tree -d
```

## **Step 4 – Practice permissions**

```
chmod 755 scripts/deploy.sh

chmod 644 documents/notes.txt

chmod 600 .env

ls -l
```

## **Step 5 – Practice umask**

```
umask 027

touch test.txt

mkdir test_directory

ls -l test.txt

ls -ld test_directory
```

## **Step 6 – Practice find**

```
find . -name "*.txt"

find . -type d

find . -type f

find . -iname "*.DATA"

find . -size +1k

find . -name "*.txt" -ls
```

## **Step 7 – Practice file viewing**

```
cat documents/notes.txt

head -n 3 documents/notes.txt

tail -n 3 documents/notes.txt

less documents/notes.txt
```



-------------------------------------------------------------------------------------------------------------------------------------------------------------

## Project: Linux Access Control System with 3 Security Levels

---

## Phase 1: Environment Setup (5 minutes)

### Step 1: Update System & Install ACL Tools

bash

```bash
sudo apt update && sudo apt install -y acl
# Verify installation
which setfacl getfacl
```

### Step 2: Create Security Groups

bash

```bash
sudo groupadd devops
sudo groupadd managers  
sudo groupadd qa
# Verify
cat /etc/group | grep -E "devops|managers|qa"
```

---

## Phase 2: User Management (10 minutes)

### Step 3: Create User Accounts

**Create Manager (Nimal):**

bash

```bash
sudo useradd -m -s /bin/bash nimal
sudo passwd nimal
# Enter password twice when prompted
```

**Create QA Team Members:**

bash

```bash
sudo useradd -m -s /bin/bash qa_alice
sudo useradd -m -s /bin/bash qa_bob
sudo passwd qa_alice
sudo passwd qa_bob
```

**Add Yourself to DevOps:**

bash

```bash
sudo usermod -aG devops $USER
# Or if your username is tharuka:
sudo usermod -aG devops tharuka
```

### Step 4: Assign Users to Groups

bash

```bash
# Manager to managers group
sudo usermod -aG managers nimal

# QA team to qa group
sudo usermod -aG qa qa_alice
sudo usermod -aG qa qa_bob
```

**Verify:**

bash

```bash
groups nimal
# Output: nimal : nimal managers

groups qa_alice  
# Output: qa_alice : qa_alice qa
```

---

## Phase 3: Project Structure (5 minutes)

### Step 5: Create Secure Directory

bash

```bash
# Create project directory
sudo mkdir -p /opt/devops-project

# Set ownership: root owns, devops is group
sudo chown root:devops /opt/devops-project

# Base permissions: Owner(rwx) Group(rwx) Others(none)
sudo chmod 770 /opt/devops-project
```

### Step 6: Create Sample Files for Testing

bash

```bash
cd /opt/devops-project
sudo touch readme.txt deploy.sh config.yml
sudo chmod 644 readme.txt
sudo chmod 755 deploy.sh
echo "Project documentation" | sudo tee readme.txt
```

---

## Phase 4: ACL Implementation (Critical - 10 minutes)

### Step 7: Apply Access Control Lists

**Level 1: DevOps (Full Control - rwx)**

bash

```bash
sudo setfacl -m g:devops:rwx /opt/devops-project
```

**Level 2: Manager/Nimal (Read + Execute - r-x)**

bash

```bash
sudo setfacl -m u:nimal:rx /opt/devops-project
```

**Level 3: QA Team (Read Only - r--)**

bash

```bash
sudo setfacl -m g:qa:r /opt/devops-project
```

### Step 8: Set Default ACLs (Inheritance)

_Ensures new files/folders inherit these permissions:_

bash

```bash
sudo setfacl -d -m g:devops:rwx /opt/devops-project
sudo setfacl -d -m u:nimal:rx /opt/devops-project
sudo setfacl -d -m g:qa:r /opt/devops-project
```

### Step 9: Verify ACL Setup

bash

```bash
getfacl /opt/devops-project
```

**Expected Output:**

plain

```plain
# file: opt/devops-project
# owner: root
# group: devops
user::rwx
user:nimal:r-x
group::rwx
group:devops:rwx
group:qa:r--
mask::rwx
other::---
default:user::rwx
default:user:nimal:r-x
default:group::rwx
default:group:devops:rwx
default:group:qa:r--
default:mask::rwx
default:other::---
```

---

## Phase 5: Testing & Validation (15 minutes)

### Step 10: Test as DevOps (You)

bash

```bash
# Refresh your group membership (important!)
newgrp devops

# Test create
touch /opt/devops-project/test_devops.txt
# Should succeed

# Test read
cat /opt/devops-project/readme.txt
# Should succeed

# Test execute
/opt/devops-project/deploy.sh
# Should succeed
```

### Step 11: Test as Manager (Nimal)

bash

```bash
# Switch to nimal user
sudo -u nimal bash

# Test read (should work)
cat /opt/devops-project/readme.txt

# Test list (should work)
ls -la /opt/devops-project/

# Test write (should FAIL)
touch /opt/devops-project/nimal_test.txt
# Expected: Permission denied

# Exit back to your user
exit
```

### Step 12: Test as QA (Alice)

bash

```bash
# Switch to qa_alice
sudo -u qa_alice bash

# Test read file content (should work)
cat /opt/devops-project/readme.txt

# Test list directory (should work)
ls /opt/devops-project/

# Test write (should FAIL)
touch /opt/devops-project/qa_test.txt
# Expected: Permission denied

# Test execute (should FAIL)
/opt/devops-project/deploy.sh
# Expected: Permission denied

exit
```

---

## Phase 6: Advanced Configuration (Optional)

### Step 13: Create Subdirectories with Different Rules

bash

```bash
# Create a "secrets" folder - DevOps only, no Manager/QA
sudo mkdir /opt/devops-project/secrets
sudo setfacl -m g:devops:rwx /opt/devops-project/secrets
sudo setfacl -m u:nimal:--- /opt/devops-project/secrets  # Block manager
sudo setfacl -m g:qa:--- /opt/devops-project/secrets    # Block QA
sudo chmod 770 /opt/devops-project/secrets
```

### Step 14: Audit & Monitoring

bash

```bash
# Check who has access to what
getfacl -R /opt/devops-project/

# Check effective permissions
sudo -u nimal namei -l /opt/devops-project/readme.txt
```

---

## Quick Reference Card

|User/Group|Permissions|Commands|
|:--|:--|:--|

|   |   |   |
|---|---|---|
|**devops** (You)|rwx (7)|`sudo setfacl -m g:devops:rwx /opt/devops-project`|
|**nimal** (Manager)|r-x (5)|`sudo setfacl -m u:nimal:rx /opt/devops-project`|
|**qa** (Team)|r-- (4)|`sudo setfacl -m g:qa:r /opt/devops-project`|

---

## Troubleshooting Common Issues

**Issue 1: "Permission denied" even after adding to group**

bash

```bash
# Solution: Log out completely or use:
newgrp devops
# Or reboot
```

**Issue 2: ACL changes not applying to new files**

bash

```bash
# Re-apply default ACLs
sudo setfacl -d -m g:qa:r /opt/devops-project
```

**Issue 3: Need to remove access for someone**

bash

```bash
# Remove specific user ACL
sudo setfacl -x u:nimal /opt/devops-project

# Remove all ACLs (reset)
sudo setfacl -b /opt/devops-project
```

**Issue 4: Check effective mask**

bash

```bash
# If mask is too restrictive, fix it:
sudo setfacl -m m::rwx /opt/devops-project
```

---

## Project Complete! ✅

You now have:

- ✅ Three-tier access control (Full/Read-Execute/Read-Only)
    
- ✅ Group-based management (easy to add/remove users)
    
- ✅ ACL implementation (bypasses Linux 1-group limitation)
    
- ✅ Default inheritance (new files auto-get correct permissions)
    
- ✅ Audit trail (getfacl shows exactly who can do what)

## The Vi Editor
- vi [ file ]  Edit file
- vim [ file ] Same as vi, but more features.
- view [ file ] Starts vim in read-only mode


## Emacs editor
- This basset editor consider Nano 

## Deleting files, Copying files, Moving files, Renaming files, Compress files, Crating archives

# Remove file
    ✔ rm file                    - remove file.
    ✔ rm -r dir                  - Remove the directory and its
                                 contents recursively
     ✔ rm -f file                - Force removal and never
                                prompt for confrmation
# Copying Files
       ✔ cp source_file destination_file copy source_file to      destination_file 
       ✔cp src_file1 [src_fileN...] dest_dir copy source_files to
       destination_directory
       ✔cp -i   run in interactive mode.
       ✔ cp -r source_directory destination copy src_directory                  recursively to destination
# Moving and Renaming Files
- mv        Move or rename file and directories.
- mv        source destination
- mv   -i    source destination
# Sorting Data
sort file                  sort text in file

- -k f     sort by key. F is the field number.
- -r        sort in reverse order.
- -u       sort unique
# Creating a Collection of Files
- tar  [ - ]  c | x | t f tarfile   [ pattern ]
  Create, extract or list contents of a tar archive using pattern, if supplied.

# Compressing Files to Save Space
- gzip         compress files.
- gunzip     Uncompressed files.
- gzcat        Concatenates compressed files
- zcat           Concatenates compressed files.
# Disk Usage
- du               Estimates file usage.
- du -k           Display sizes in kilobytes.
- du -h           Display sizes in human readable format.


## Wildcards

- A character or string used for pattern matching.
- Globing expands the wildcard pattern into a list of files and /or directories.
- Wildcards can be used with most commands.
                          - ls
                          - rm
                          - cp
- * - matches zero or more characters.
                         * *.txt
                        a* *
                        a*.txt
- ? - matches exactly one character
                      ?.txt
                      a?
                      a?.txt
    ## More wildcards - Character classes
    - [] - A character class.
    - Matches any of the characters included between the brackets
      Marches exactly one character
    - [aeiou]
    - ca[nt]*
         - [ ] can
         - [ ] cat 
         - [ ] candy
         - [ ] catch
    - [! ] - Matches any of the characters NOT included between the brackets. Matches exactly one character .
          - [ ! aeiou] *
             - baseball
             - cricket
    - use tow characters separated by a hyphen to create a range in a character class.
    - [a-g]*
         - Matches all files that start with a, b, c, d, e, f , or g.
    - -[3-6]*
         - Matches all files that start with 3, 4, 5, or 6.
    - Named Character classes
            :alpha:
            :alum:
            :digit:
            :lower:
            :space:
            :upper:
    # Matching wildcard patterns
    -  \ - escape character . Use if you want to match a wildcard character.
        - Match all files that end with a question mark:
               *\?    - done ?





## input, output and Redirection


### input/output types

## I/O Name                Abbreviation    File Descriptor
- standard input                  stdin                               0
- standard output                stdout                            1 
- standard Error                   stderr                             2


# Redirection
 Redirects standard output a file.           >       
  
 Redirect standard output to a file           >>
 Appends to any existing contents.    

Redirects input from a file to a command  <

Used with redirection to signal that a file  &
descriptor is being used.                       

Combine stderr and standard output.     2 > &1

Redirect standard error to a file               2 > file

## The Null Device
        > dev/null Redirect output to nowhere
         $ ls here not-here 2 > /dev/null
         here
         $ ls here not-here > /dev/null 2 > $1
         $ 

## Comparing Files
- how to compare the contents of files

- [ ] diff    file1   file2          Compare tow files
- [ ] sdiff   file1   file2          side-by-side comparison
- [ ] vimdiff   file1    file2     Highlight   differences in vim

  # diff output
      $ diff file1 file2 
      3c3
      < this is a line in a file.
      ------
       > This is a Line in a File
       
    # sdiff output
      $ sdiff file1 file2
      line in file 2           | line in file2
                            > more in file 2
                            
                            | Differing lines
                            < Line form file 1
                            > Line form file 2

# vimdiff
ctel -w w    Go to next winow
:q                Quit (close current window)
:qa               Quit all (close both files)
:qa!             Force quit all


# Searching in Files

## The grep command
grep       Display lines matching a pattern
grep         pattern   file


## The file Command
file file)name Display the file type

$ file sales.data
sales.data: ASCII text
$ file *
bin: directory
jason.tar: POSIX tar archive

## Searching for Text in Binary Files
strings                 Display printable strings.

## Pipes
    |                      Pipe symbol
command-output            |         command - input

grep     pattern   file
cat file     |   grep   pattern


## cut Options
-d  delimiter                            Use delimiter as the field separator

-f  N                                       Display the Nth field

## Copy file over the network












       
       




       
       













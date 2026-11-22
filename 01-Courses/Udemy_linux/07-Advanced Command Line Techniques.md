
## Lesson: Customizing PS1, Aliases & Environment Variables

**Category:** Linux Fundamentals  
**Learning Path:** DevOps Engineering  
**Level:** Beginner  
**Language:** Simple English + Sinhala

---

# 1. Customizing the Prompt with PS1

## 1.1 What is PS1?

**English:**

PS1 is a special Bash environment variable that controls the appearance of the command-line prompt.

It determines what information is displayed before you type a command.

**සිංහල:**

PS1 කියන්නේ Bash වල භාවිතා කරන විශේෂ variable එකක්. Terminal එකේ command එකක් type කිරීමට පෙර පෙන්වන prompt එකේ පෙනුම වෙනස් කිරීමට මෙය භාවිතා කරයි.

### Example

Default prompt:

```
tharuka@ubuntu:~$
```

Customized prompt:

```
[tharuka@ubuntu ~] $
```

### 1.2 PS1 Special Characters

|Character|Meaning (English)|සිංහල තේරුම|
|---|---|---|
|`\d`|Current date|වර්තමාන දිනය|
|`\h`|Short hostname|කෙටි Hostname එක|
|`\H`|Full hostname|සම්පූර්ණ Hostname එක|
|`\n`|New line|අලුත් පේළිය|
|`\t`|24-hour time|පැය 24 වෙලාව|
|`\T`|12-hour time|පැය 12 වෙලාව|
|`\u`|Current username|දැනට සිටින User නම|
|`\w`|Current working directory|දැනට සිටින Folder එක|

### 1.3 Practical Examples

**Example 1: Display username**

```
PS1="[\u] $ "
```

Output:

```
[tharuka] $
```

**Example 2: Display username and hostname**

```
PS1="[\u@\h] $ "
```

Output:

```
[tharuka@ubuntu] $
```

**Example 3: Display current directory**

```
PS1="[\w] $ "
```

Output:

```
[~/Documents] $
```

**Example 4: Display current time**

```
PS1="[\t] $ "
```

Output:

```
[10:30:25] $
```

**Example 5: Combine multiple characters**

```
PS1="[\u@\h \w] $ "
```

Output:

```
[tharuka@ubuntu ~/Documents] $
```

## 1.4 Persisting PS1 Changes

**English:**

By default, a PS1 change normally affects only the current shell session. To keep the change after opening a new terminal, add it to your Bash configuration file.

**සිංහල:**

සාමාන්‍යයෙන් PS1 වෙනස් කිරීම දැනට තිබෙන Terminal session එකට පමණයි බලපාන්නේ. හැමදාම එම වෙනස පවත්වා ගැනීමට `.bashrc` file එකට එකතු කළ යුතුයි.

**Step 1: Open the configuration file**

```
nano ~/.bashrc
```

**Step 2: Add this line**

```
export PS1="[\u@\h \w] $ "
```

**Step 3: Save and exit**

- Press `CTRL + O`
    
- Press `ENTER`
    
- Press `CTRL + X`
    

**Step 4: Reload the configuration**

```
source ~/.bashrc
```

**Important terms:**

|Command / Symbol|Meaning|
|---|---|
|`~`|Home directory|
|`.bashrc`|Bash configuration file|
|`>>`|Append content to a file|
|`source`|Reload a configuration file|
|`export`|Make a variable available to child processes|

---

# 2. Linux Aliases

## 2.1 What is an Alias?

**English:**

An alias is a shortcut or alternative name for a command.

It helps us execute frequently used or long commands using shorter names.

**සිංහල:**

Alias කියන්නේ Linux command එකකට කෙටි නමක් ලබා දීමයි. නිතර භාවිතා කරන දිග commands පහසුවෙන් ක්‍රියාත්මක කිරීමට මෙය උපකාරී වේ.

### Example

Normal command:

```
clear
```

Create an alias:

```
alias cls='clear'
```

Now execute:

```
cls
```

The `cls` shortcut performs the same task as `clear`.

## 2.2 Syntax of an Alias

```
alias name='command'
```

|Part|Explanation|
|---|---|
|`alias`|Creates or displays aliases|
|`name`|Shortcut name|
|`command`|Original command|

**Remember:** Do not put spaces around the `=` sign.

Correct:

```
alias cls='clear'
```

Incorrect:

```
alias cls = 'clear'
```

## 2.3 Useful Alias Examples

**1. Clear terminal**

```
alias cls='clear'
```

**2. List files with details**

```
alias ll='ls -lah'
```

**3. Go to home directory**

```
alias home='cd ~'
```

**4. Show current directory**

```
alias cdir='pwd'
```

**5. Update package information**

```
alias update='sudo apt update'
```

## 2.4 Viewing Aliases

Display all available aliases:

```
alias
```

Display one specific alias:

```
alias cls
```

## 2.5 Removing Aliases

Remove one alias:

```
unalias cls
```

Remove all aliases:

```
unalias -a
```

**සිංහල:**

- `unalias cls` – cls කියන alias එක ඉවත් කරයි.
    
- `unalias -a` – සියලුම aliases ඉවත් කරයි.
    

## 2.6 Persisting Aliases

**English:**

Aliases created in the current shell normally disappear when the session ends. Add them to `.bashrc` to make them available in future interactive Bash sessions.

**සිංහල:**

Terminal එක වසා දැමූ විට සාමාන්‍යයෙන් තාවකාලික aliases නැති වී යයි. ඒවා නැවතත් භාවිතා කිරීමට `.bashrc` file එකට එකතු කරන්න.

**Step 1:**

```
nano ~/.bashrc
```

**Step 2: Add aliases**

```
alias cls='clear'
alias ll='ls -lah'
alias home='cd ~'
alias update='sudo apt update'
```

**Step 3: Reload**

```
source ~/.bashrc
```

Now your aliases are ready to use!

---

# 3. Environment Variables

## 3.1 What is an Environment Variable?

**English:**

An environment variable is a name-value pair used to store configuration information that applications and processes can access.

Example:

```
EDITOR="nano"
```

Here:

- Variable name = EDITOR
    
- Variable value = nano
    

**සිංහල:**

Environment Variable කියන්නේ Name එකක් සහ Value එකක් ඇති variable එකකි. Applications සහ programs වලට අවශ්‍ය configuration information ගබඩා කිරීමට මෙය භාවිතා කරයි.

Example:

```
EDITOR="nano"
```

මෙහි `EDITOR` කියන්නේ variable name එකයි. `nano` කියන්නේ එහි value එකයි.

## 3.2 Viewing Environment Variables

There are two common methods.

**Method 1: Using printenv**

```
printenv HOME
```

Example output:

```
/home/tharuka
```

**Method 2: Using echo**

```
echo $HOME
```

Example output:

```
/home/tharuka
```

To display all environment variables:

```
printenv
```

### Important: Case Sensitivity

Linux is case-sensitive.

For example:

```
echo $HOME
```

Works because the variable name is `HOME`.

But:

```
echo $home
```

Usually displays nothing because `HOME` and `home` are different names.

## 3.3 Creating Environment Variables

Syntax:

```
export VAR="value"
```

Examples:

**Example 1:**

```
export EDITOR="vi"
```

**Example 2:**

```
export TZ="US/Pacific"
```

**Example 3:**

```
export MY_NAME="Tharuka"
```

Check the variable:

```
echo $MY_NAME
```

Output:

```
Tharuka
```

**What does export do?**

English: The `export` command makes a shell variable available to child processes.

සිංහල: `export` මගින් shell variable එක child processes වලටත් ලබා ගත හැකි ලෙස සකස් කරයි.

## 3.4 Removing Environment Variables

Use the `unset` command.

Syntax:

```
unset VAR
```

Example:

```
unset TZ
```

Check:

```
echo $TZ
```

The output should be empty if the variable has been removed.

## 3.5 Persisting Environment Variables

**English:**

Variables created in the current shell are not automatically permanent. Add them to `.bashrc` to load them in future interactive Bash sessions.

**සිංහල:**

දැනට තිබෙන Terminal session එකේ හදන variables හැමදාම පවතින්නේ නැහැ. නැවත Terminal එක Open කළත් භාවිතා කිරීමට `.bashrc` file එකට එකතු කළ යුතුයි.

**Step 1:**

```
nano ~/.bashrc
```

**Step 2: Add these variables**

```
export TZ="US/Central"
export EDITOR="nano"
export MY_NAME="Tharuka"
```

**Step 3: Reload**

```
source ~/.bashrc
```

**Step 4: Verify**

```
echo $TZ
echo $EDITOR
echo $MY_NAME
```

---

# 4. Difference Between PS1, Aliases and Environment Variables

|Feature|Purpose|Example|
|---|---|---|
|PS1|Customize terminal prompt|`PS1="[\u] $ "`|
|Alias|Create command shortcuts|`alias cls='clear'`|
|Environment Variable|Store configuration information|`export EDITOR="nano"`|

**Easy way to remember:**

- PS1 = Terminal Appearance
    
- Alias = Command Shortcut
    
- Environment Variable = Application Configuration
    

සිංහලෙන්:

- PS1 = Terminal එකේ පෙනුම.
    
- Alias = Command එකකට කෙටි නමක්.
    
- Environment Variable = Programs සඳහා settings තබා ගැනීම.
    

---

# 5. Important Linux Commands – Quick Revision

|Command|Purpose|
|---|---|
|`alias`|Display or create aliases|
|`unalias`|Remove aliases|
|`export`|Export environment variables|
|`printenv`|Display environment variables|
|`echo $VAR`|Display variable value|
|`unset`|Remove variables|
|`nano ~/.bashrc`|Edit Bash configuration|
|`source ~/.bashrc`|Reload Bash configuration|
|`pwd`|Display current directory|
|`clear`|Clear terminal screen|

---

# 6. Practical Lab Exercises

Complete these exercises in your Linux terminal.

### Exercise 1: Customize PS1

Create a prompt displaying:

- Username
    
- Hostname
    
- Current directory
    

### Exercise 2: Create Aliases

Create these aliases:

```
alias cls='clear'
alias ll='ls -lah'
alias home='cd ~'
```

Test each alias.

### Exercise 3: Remove an Alias

Remove the `home` alias.

```
unalias home
```

### Exercise 4: Create Environment Variables

```
export STUDENT="Tharuka"
export COURSE="DevOps"
export EDITOR="nano"
```

### Exercise 5: Display Variables

```
echo $STUDENT
echo $COURSE
echo $EDITOR
```

### Exercise 6: Remove a Variable

```
unset COURSE
```

Verify the result.

### Exercise 7: Permanent Configuration

Save two aliases and two environment variables in `.bashrc`.

Reload and test them.

---

# 7. Interview Questions

**Q1. What is PS1?**

Answer: PS1 is a Bash variable used to customize the command-line prompt.

**Q2. What is an alias?**

Answer: An alias is a shortcut or alternative name for a Linux command.

**Q3. What is an environment variable?**

Answer: An environment variable is a name-value pair used to store configuration information for processes and applications.

**Q4. What is the purpose of the export command?**

Answer: It makes a shell variable available to child processes.

**Q5. What is the purpose of unset?**

Answer: It removes a variable from the current shell environment.

**Q6. What is the purpose of unalias?**

Answer: It removes an existing alias.

**Q7. What is .bashrc?**

Answer: It is a Bash configuration file used to configure interactive non-login Bash shells.

**Q8. What is the difference between > and >>?**

Answer:

- `>` overwrites a file.
    
- `>>` appends content to a file.
    

---

# 8. Final Summary

In this lesson, we learned three important Linux concepts.

1. **PS1:** Customize the Linux terminal prompt.
    
2. **Aliases:** Create shortcuts for frequently used commands.
    
3. **Environment Variables:** Store configuration information for applications and processes.
    

These concepts are useful for Linux administration, automation, shell scripting and DevOps engineering.

**Practice every command yourself. Understanding the command is more important than memorizing it.**

---
# Linux Study Notes: Processes, Job Control & Cron Scheduling

## 1. What is a Process?

A **process** is a program that is currently running on a computer.

Examples:

- Opening Google Chrome
    
- Running a Python program
    
- Running an Apache web server
    
- Running a Linux command
    

**Sinhala:** Process එකක් කියන්නේ computer එකේ දැනට ක්‍රියාත්මක වෙන program එකක්.

### Important Process Terms

|Term|Meaning|
|---|---|
|PID|Process ID – unique number given to a process|
|PPID|Parent Process ID – ID of the parent process|
|Process|A running program|
|Parent Process|The process that starts another process|

Example:

```
sleep 100 &
```

This starts a background process. Linux assigns it a PID.

## 2. Monitoring Processes

Linux provides several commands to check running processes.

### 2.1 `ps` Command

`ps` means **Process Status**.

It displays information about running processes.

|Command|Description|
|---|---|
|`ps`|Show processes in the current terminal|
|`ps -e`|Show all running processes|
|`ps -f`|Show full-format information|
|`ps -ef`|Show all processes with full details|
|`ps -eH`|Show processes in a hierarchy|
|`ps -e --forest`|Show processes in a tree structure|
|`ps -u username`|Show processes owned by a specific user|
|`ps -p 1500`|Show the process with PID 1500|

Example:

```
ps -ef
```

Common output columns:

|Column|Meaning|
|---|---|
|UID|User who owns the process|
|PID|Process ID|
|PPID|Parent Process ID|
|C|CPU usage information|
|STIME|Process start time|
|TTY|Terminal associated with the process|
|TIME|CPU time used|
|CMD|Command that started the process|

**Sinhala:** `ps -ef` මගින් computer එකේ ක්‍රියාත්මක වන processes සහ ඒවාට අදාළ විස්තර බලන්න පුළුවන්.

### 2.2 `pstree`

Displays processes in a tree structure.

```
pstree
```

**Sinhala:** Parent process සහ child processes ගසක ආකාරයට පෙන්වයි.

### 2.3 `top`

Displays live process information.

```
top
```

You can see:

- CPU usage
    
- Memory usage
    
- Running processes
    
- Process IDs
    

Press `q` to quit.

### 2.4 `htop`

A more user-friendly interactive process monitoring tool.

```
htop
```

If it is not installed:

```
sudo apt update
sudo apt install htop
```

**Remember:**

- `ps` = Process information snapshot
    
- `top` = Live process monitoring
    
- `htop` = Interactive process monitoring
    
- `pstree` = Process hierarchy
    

---

## 3. Job Control

Job control allows us to manage processes running in a terminal.

There are two main types of jobs.

### 3.1 Foreground Process

A foreground process runs directly in the terminal.

Example:

```
ping google.com
```

The terminal stays busy while the command runs.

To stop it, press:

```
Ctrl + C
```

**Sinhala:** Foreground process එකක් ක්‍රියාත්මක වන විට terminal එක ඒ command එකට වෙන් වෙනවා. වෙනත් command එකක් run කරන්න බැහැ.

### 3.2 Background Process

A background process runs without keeping the terminal busy.

Use `&` at the end of a command.

Example:

```
ping google.com &
```

Now you can enter other commands in the terminal.

**Sinhala:** Background process එකක් terminal එකේ පිටුපසින් ක්‍රියාත්මක වෙනවා. ඒ අතරතුර වෙනත් commands run කරන්න පුළුවන්.

### 3.3 Important Job Control Commands

|Command|Description|
|---|---|
|`command &`|Start a command in the background|
|`jobs`|Display jobs in the current shell|
|`jobs -l`|Display jobs with process IDs|
|`Ctrl + C`|Interrupt the foreground process|
|`Ctrl + Z`|Suspend the foreground process|
|`bg`|Resume a suspended job in the background|
|`fg`|Bring a job to the foreground|
|`bg %1`|Resume job number 1 in the background|
|`fg %1`|Bring job number 1 to the foreground|

### 3.4 Practical Example

**Step 1: Start a process**

```
sleep 300
```

This command waits for 300 seconds.

**Step 2: Suspend the process**

Press:

```
Ctrl + Z
```

**Step 3: Check jobs**

```
jobs
```

**Step 4: Resume in the background**

```
bg
```

**Step 5: Bring it to the foreground**

```
fg
```

**Step 6: Stop the process**

Press:

```
Ctrl + C
```

### Difference Between Ctrl+C and Ctrl+Z

|Shortcut|Action|
|---|---|
|Ctrl + C|Interrupts the foreground process|
|Ctrl + Z|Suspends the foreground process|

Remember:

- Ctrl+C = Stop the command.
    
- Ctrl+Z = Pause the command.
    

---

## 4. Killing Processes

Sometimes a process stops responding. We can terminate it using the `kill` command.

### Syntax

```
kill PID
```

Example:

```
kill 1500
```

This sends the default signal, SIGTERM (15), asking the process to terminate gracefully.

### Important Kill Commands

|Command|Meaning|
|---|---|
|`kill 1500`|Send default SIGTERM|
|`kill -15 1500`|Send SIGTERM|
|`kill -9 1500`|Forcefully terminate the process|
|`kill -STOP 1500`|Stop/suspend the process|
|`kill -CONT 1500`|Continue a stopped process|

### Important Signals

|Signal|Number|Purpose|
|---|---|---|
|SIGTERM|15|Request graceful termination|
|SIGKILL|9|Force termination|
|SIGSTOP|19 on common Linux architectures|Stop a process|
|SIGCONT|18 on common Linux architectures|Continue a stopped process|

**Important:** Use `kill -9` only when necessary. It does not give the process a chance to clean up.

**Sinhala:** `kill` command එකෙන් process එකක් terminate කරන්න පුළුවන්. `kill -9` කියන්නේ බලහත්කාරයෙන් process එක නවත්වන එක.

---

## 5. Cron Jobs

### 5.1 What is Cron?

Cron is a Linux service used to schedule tasks automatically at specific times.

Examples:

- Run a backup every day.
    
- Delete temporary files every week.
    
- Run a script every hour.
    
- Check a server regularly.
    

**Sinhala:** Cron කියන්නේ නියමිත වේලාවක හෝ දිනයක tasks ස්වයංක්‍රීයව run කරන්න භාවිතා කරන Linux scheduler එකක්.

### 5.2 What is Crontab?

Crontab is used to create and manage scheduled tasks.

Important commands:

|Command|Description|
|---|---|
|`crontab -e`|Edit scheduled tasks|
|`crontab -l`|List scheduled tasks|
|`crontab -r`|Remove all scheduled tasks for the current user|
|`crontab -u username -l`|List another user's crontab (with suitable permissions)|

**Warning:** `crontab -r` removes all cron entries for that user. Use it carefully.

### 5.3 Cron Syntax

A cron schedule contains five time fields.

```
* * * * * command
│ │ │ │ │
│ │ │ │ └── Day of week
│ │ │ └──── Month
│ │ └────── Day of month
│ └──────── Hour
└────────── Minute
```

|Field|Allowed values|
|---|---|
|Minute|0–59|
|Hour|0–23|
|Day of month|1–31|
|Month|1–12|
|Day of week|0–7 (0 and 7 mean Sunday)|

### 5.4 Cron Special Symbols

|Symbol|Meaning|Example|
|---|---|---|
|`*`|Every value|`* * * * *`|
|`,`|Multiple values|`0 8,17 * * *`|
|`-`|Range|`0 8-17 * * *`|
|`/`|Interval|`*/5 * * * *`|

### 5.5 Common Cron Examples

|Cron expression|Meaning|
|---|---|
|`* * * * *`|Every minute|
|`*/5 * * * *`|Every 5 minutes|
|`0 * * * *`|Every hour|
|`0 2 * * *`|Every day at 2:00 AM|
|`30 8 * * *`|Every day at 8:30 AM|
|`0 8 * * 0`|Every Sunday at 8:00 AM|
|`0 0 1 * *`|First day of every month at midnight|
|`0 9 * * 1-5`|Monday to Friday at 9:00 AM|

**Important correction:**

```
02 * * * *
```

This means every hour at 2 minutes past the hour.

It does NOT mean every day at 2:00 AM.

Correct expression for daily 2:00 AM:

```
0 2 * * *
```

---

## 6. Output Redirection

Output redirection allows us to save command output into files.

Linux has three standard streams:

|Stream|Number|Meaning|
|---|---|---|
|stdin|0|Standard input|
|stdout|1|Standard output|
|stderr|2|Standard error|

### 6.1 `>` Overwrite Output

```
echo "Hello Linux" > output.txt
```

Creates a file or overwrites its existing content.

### 6.2 `>>` Append Output

```
echo "New line" >> output.txt
```

Adds new content to the end of the file.

### 6.3 Redirect Error Output

```
ls /wrong-folder 2> error.log
```

Saves error messages in `error.log`.

### 6.4 Redirect Both Output and Errors

```
ls /home > output.log 2>&1
```

Meaning:

- `>` sends standard output to `output.log`.
    
- `2>&1` sends standard error to the same destination as standard output.
    

### 6.5 Practical Backup Example

```
/root/backupdb > /tmp/db.log 2>&1
```

This runs the backup script and saves both normal output and error messages in `/tmp/db.log`.

To append instead of overwrite:

```
/root/backupdb >> /tmp/db.log 2>&1
```

### Difference Between > and >>

|Operator|Action|
|---|---|
|`>`|Overwrite|
|`>>`|Append|
|`2>`|Redirect errors|
|`2>&1`|Redirect errors to the same destination as standard output|

---

## 7. Practical Lab: Create a Cron Job

Let's create a simple cron job to test whether cron works.

### Step 1: Open crontab

```
crontab -e
```

### Step 2: Add this line

```
*/5 * * * * echo "Cron is working" >> /tmp/cron-test.log 2>&1
```

This runs every 5 minutes and adds a message to the log file.

### Step 3: Check your cron jobs

```
crontab -l
```

### Step 4: Check the output

```
cat /tmp/cron-test.log
```

Wait up to five minutes for the first scheduled execution.

### Step 5: Remove the test job

Open the crontab again:

```
crontab -e
```

Delete the test line and save.

Note: Cron jobs belonging to different users are separate. For example, use `sudo crontab -e` to edit root's crontab. A script stored under `/root` normally needs to run with root permissions.

---

## 8. Quick Revision Table

|Topic|Important command|
|---|---|
|View processes|`ps -ef`|
|Live monitoring|`top`|
|Interactive monitoring|`htop`|
|Process tree|`pstree`|
|Start background job|`command &`|
|Show jobs|`jobs`|
|Suspend foreground job|`Ctrl + Z`|
|Resume in background|`bg`|
|Bring to foreground|`fg`|
|Terminate process|`kill PID`|
|Force terminate|`kill -9 PID`|
|Edit cron jobs|`crontab -e`|
|List cron jobs|`crontab -l`|
|Overwrite output|`>`|
|Append output|`>>`|
|Redirect errors|`2>`|

---

## 9. Interview Questions and Answers

**Q1. What is a process?**

A: A process is a program that is currently running.

**Q2. What is PID?**

A: PID is a unique identification number assigned to a process.

**Q3. What is the difference between foreground and background processes?**

A: A foreground process runs directly in the terminal. A background process runs without keeping the terminal busy.

**Q4. What does Ctrl+Z do?**

A: It suspends the foreground process.

**Q5. What does the** `**bg**` **command do?**

A: It resumes a suspended job in the background.

**Q6. What does the** `**fg**` **command do?**

A: It brings a background or suspended job to the foreground.

**Q7. What is the default signal used by** `**kill**`**?**

A: SIGTERM (15).

**Q8. What is Cron?**

A: Cron is a time-based job scheduler in Linux.

**Q9. What is the purpose of** `**crontab -e**`**?**

A: It allows users to edit scheduled cron jobs.

**Q10. What is the difference between** `**>**` **and** `**>>**`**?**

A: `>` overwrites a file, while `>>` appends content to a file.

---

## 10. Practice Questions

Try answering these questions without looking at the notes.

1. What is a process?
    
2. What is the difference between PID and PPID?
    
3. Which command displays all processes?
    
4. Which command displays live process information?
    
5. What is the purpose of `pstree`?
    
6. What does `&` do at the end of a command?
    
7. What is the difference between Ctrl+C and Ctrl+Z?
    
8. What is the purpose of `bg`?
    
9. What is the purpose of `fg`?
    
10. What does `kill -9 1500` do?
    
11. What is Cron?
    
12. Which command edits cron jobs?
    
13. What does `*/5 * * * *` mean?
    
14. Write a cron expression to run a script every day at 2:00 AM.
    
15. What is the difference between `>` and `>>`?
    
16. What does `2>&1` mean?
    

**Remember:** Practice these commands in Ubuntu. Linux becomes easier when you understand each command and use it yourself.
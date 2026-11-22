
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
##Pro
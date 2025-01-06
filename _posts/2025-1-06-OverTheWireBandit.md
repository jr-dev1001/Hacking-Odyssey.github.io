---
layout: post
title:  OverTheWire Bandit Walkthrough 🐈
subtitle: What is Flag?
excerpt_image: 
categories: CyberSecurity CTF
tags: [CyberSecurity]
---

## 🎉 Happy New Year (2025)! 🎉

  <p><i>May this year bring you success, joy, and countless adventures in your learning journey!</i></p>
---

<p align="center">
  <img src="https://github.com/user-attachments/assets/8a146d32-e8f6-43d1-9a8c-444be763fc7c" alt="OverTheWire">
</p>

## Introduction

Ready to dive into the OverTheWire Bandit CTF series? 🕵️‍♂️ This walkthrough is your ultimate guide, not just for solving the challenges, but for understanding the techniques and tools behind them. Whether you’re a beginner or looking to brush up your basics, the Bandit series is perfect for honing your Linux command-line skills while navigating realistic scenarios.

> **Before You Start**: Make sure to check out the [rules](https://overthewire.org/rules/) to ensure a fair and fun experience.

This guide covers:
- Detailed objectives for each level.
- Commands and step-by-step solutions.
- Explanations to help you understand the "why" behind each step.

Let’s gear up, fire up your terminal, and tackle these challenges head-on!

> note: for each level at ssh increase the count before the username `bandit0 , bandit1, bandit3, bandit4...` and so on.

---

### Level 0
- **Objective** :  Connect to the Bandit server via SSH.
- **Steps**:
  1. SSH into the server with the provided credentials.
  2. The username is `bandit0`, and the host is `bandit.labs.overthewire.org`.
  3. Use port `2220` instead of the default port `22`.
  4. password is `bandit0`
- **Command**: 
  ```bash
  ssh bandit0@bandit.labs.overthewire.org -p 2220
  ```
  and level0 -> level1 begins

  ---
  
### Level 0 -> Level 1
- **Objective**: The password for the next level is stored in a file called readme located in the home directory.
- **Command**: 
  ```bash
  ssh bandit0@bandit.labs.overthewire.org -p 2220
  ```
  1. locate the file by `find readme` or `ls` command.
  2. use `cat readme` to read the content in the file. 
- **Password**: `ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If`
- **Explanation**: SSH (Secure Shell) is a protocol to connect to remote servers securely. Here, we use the username and host details along with a non-standard port.

---

### Level 1 -> Level 2
- **Objective**: Read a file named `-` in the home directory.
- **Steps**:
  1. Use `ls` to list the files in the directory.
     ```bash
     ls
     ```
  2. Notice a file named `-`. This is tricky because `-` is often treated as an option by commands.
  3. To read the file, prefix the name with `./` to indicate it's a file.
- **Command**: 
  ```bash
  cat ./-
  ```
- **Password**: `263JGJPfgU6LtdEvgfWU1XP5yac29mFx`
- **Explanation**: The `./` tells the shell that `-` is a file in the current directory and not an option for the `cat` command.

---

### Level 2 -> Level 3
- **Objective**: Read a file with spaces in its name.
- **Steps**:
  1. Use `ls` to list the files in the directory.
     ```bash
     ls
     ```
  2. You'll see a file named `spaces in this filename`.
  3. To read it, enclose the name in quotes or escape the spaces with `\`.
- **Command**: 
  ```bash
  cat "spaces in this filename"
  ```
- **Password**: `MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx`
- **Explanation**: Quotes or escape characters allow you to handle file names with special characters or spaces.

---

### Level 3 -> Level 4
- **Objective**: Find and read a hidden file.
- **Steps**:
  1. Use `ls` to list files, but it won't show hidden ones (files starting with `.`).
  2. Use `ls -a` to include hidden files in the listing.
     ```bash
     ls -a
     ```
  3. You'll see a hidden directory named `inhere`. Navigate into it and list files again.
  4. Inside, find a hidden file named `.hidden` and read it.
- **Command**: 
  ```bash
  cat inhere/.hidden
  ```
- **Password**: `2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ`
- **Explanation**: The `-a` flag with `ls` lists all files, including hidden ones. Hidden files are often used to store sensitive data.

---

### Level 4 -> Level 5
- **Objective**: Find the password in one of multiple files.
- **Steps**:
  1. Use `ls` to see multiple files named `file01`, `file02`, etc., in the `inhere` directory.
  2. Read all the files manually or use a single command to output them together.
- **Command**: 
  ```bash
  cat inhere/file*
  ```
- **Password**: `4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw`
- **Explanation**: The `*` wildcard matches all files starting with `file`. This saves time compared to reading files one by one.

---

### Level 5 -> Level 6
- **Objective**: Search for a file of a specific size (1033 bytes).
- **Steps**:
  1. Use the `find` command to search for files meeting specific criteria.
     ```bash
     find . -type f -size 1033c
     ```
  2. `-type f` ensures you're only looking for files.
  3. `-size 1033c` looks for files exactly 1033 bytes (`c` stands for bytes).
- **Password**: `HWasnPhtq9AVKe0dmk45nxy20cvUa6EG`
- **Explanation**: The `find` command is powerful for locating files based on attributes like size, ownership, and permissions.

---

### Level 6 -> Level 7
- **Objective**: Find a file owned by a specific user and group.
- **Steps**:
  1. Use `find` with additional filters for ownership and size.
     ```bash
     find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
     ```
  2. `-user` and `-group` filter by the file's owner and group.
  3. `2>/dev/null` suppresses permission errors during the search.
- **Password**: `morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj`
- **Explanation**: Combining filters helps narrow down the results to the exact file you're looking for.

---

### Level 7 -> Level 8
- **Objective**: Search for the password beside the keyword "millionth".
- **Steps**:
  1. Use `grep` to search for the keyword directly in the file.
     ```bash
     grep millionth data.txt
     ```
  2. The password will be displayed next to the keyword.
- **Password**: `dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc`
- **Explanation**: `grep` is a tool for searching text patterns in files.

---

### Level 8 -> Level 9
- **Objective**: Find the only unique line in a file.
- **Steps**:
  1. Use `sort` to arrange lines, then `uniq -u` to filter out duplicate lines.
     ```bash
     sort data.txt | uniq -u
     ```
  2. This command outputs the line that appears only once.
- **Password**: `4CKMh1JI91bUIZZPXDqGanal4xvAg0JM`
- **Explanation**: Sorting is necessary because `uniq` only works on consecutive identical lines.

---

### Level 9 -> Level 10
- **Objective**: Extract the password from printable strings starting with `==`.
- **Steps**:
  1. Use `strings` to extract readable text from the file.
     ```bash
     strings data.txt | grep ==
     ```
  2. Filter the results using `grep`.
- **Password**: `FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey`
- **Explanation**: `strings` is handy for reading text from binary files.

---

### Level 10 -> Level 11
- **Objective**: Decode a Base64-encoded string.
- **Steps**:
  1. Use `base64` with the `-d` flag to decode the file content.
     ```bash
     base64 -d data.txt
     ```
  2. The decoded string contains the password.
- **Password**: `dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr`
- **Explanation**: Base64 encoding is often used to represent binary data in ASCII format.

---

### Level 11 -> Level 12
- **Objective**: Decrypt a ROT13-encoded file.
- **Steps**:
  1. Use the `tr` command to perform the ROT13 transformation.
     ```bash
     cat data.txt | tr 'a-zA-Z' 'n-za-mN-ZA-M'
     ```
  2. The password will be revealed after decryption.
- **Password**: `7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4`
- **Explanation**: ROT13 shifts each letter by 13 places, a simple substitution cipher.

---

## Up Next

To be cont... XD

---
layout: post
title: Linux Foundations Part 1 🐧
subtitle: Why start with Linux?
excerpt_image: 
categories: CyberSecurity
tags: [CyberSecurity]
---

## Motivation

"In real open source, you have the right to control your own destiny. - Linus Torvalds"

<div style="text-align:center;"> 
  <img src="https://tinyurl.com/4d6kbzrt" alt="Linus Torvalds">
</div>


## The Story of Unix and Linux

### Unix: The Beginning
In 1969, a team at Bell Labs wanted to make software that could work on all computers, so they created **Unix**. They made it in **C language** (instead of assembly language), which made the code **simpler, more flexible, and easy to reuse**. Because of this, Unix’s core part, the **kernel**, became the base for operating systems that could run on different computers. Plus, Unix’s **source code was open**, so others could learn from and build on it.

Back then, **Unix** was mostly used in big organizations, like government departments, universities, and big corporations with mainframes, since regular PCs didn’t exist yet.

### The Expansion of Unix
In the 1980s, companies like **IBM** and **HP** started making their own versions of Unix. But this created a mess of different Unix “dialects.” So in 1983, **Richard Stallman** started the **GNU Project** to create a free version of Unix that anyone could use. But this project didn’t gain much popularity, and other Unix-like systems also failed to catch on.

### The Birth of Linux
In 1991, **Linus Torvalds**, a student in Finland, wanted a free version of Unix for his own PC, so he started creating his own code. His project became the **Linux kernel**, built on the **MINIX** system using the **GNU C compiler** (still the main way to compile Linux code today, though other compilers exist too).

Torvalds initially called it **Freax**, but later it became **Linux**. He first released it under a personal license that limited commercial use, but in 1992, he released Linux under the **GNU General Public License (GPL)**, making it truly open and free for all.

Linux borrowed many tools from the GNU project, so both GNU and Linux played roles in the Linux we know today.

### Linux Today
Today, Linux powers everything from **supercomputers** and **smartphones** to **web servers**, **home appliances** (like washing machines and routers), and even **cars** and **refrigerators**.



## Linux Commands

There are many commands in linux we main focus upon what a linux adminstrator regularly uses. 

- ls (lists the contents of a directory or file)
- cd (Current Directory)
- whoami (username)
- hostname (hostname)
- pwd (present working directory)
- date (date of present time)
- uname -an (system info)
Importance of system architecture (software files).
- man [command] (manual of that command)
- whereis packageName (command is used to find the location of the source, binary, and manual sections of a command)
- whatis -[commad] ( displays a brief description of a command on the command line.)
____________________________________________________________________________________________________
- sudo command (running as administrator, switch user do)
    - sudo can be run as any user without opening new shell.
    - sudo only get to one standard user. By default root will be assigned to 1st user.
- su (switch user)
    - command to switch to root user (sudo su)
    - command to switch to standard user (sudo su username)
- adduser ( for adding an user in system)
  - once you switch to other user with sudo command but it doesn't contain root privilages unless you grant so to get back just enter 'exit'.
We can further more discuss about User Management and File Management in the next blogs.



## Installation process in Linux

### installation, reinstallation and removal of software using apt
  - apt install
  - apt reinstall
  - apt remove
  - apt cache search
  - apt purge
  - apt-get(uses cache) 


### Installation of deb packages.
  - sudo dpkg -i [packagename]


### Installation using shell (running scripts)
  - sh [packagename]



## Up Next

To be continued...
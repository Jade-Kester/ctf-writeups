# picoCTF – Obedient Cat (Beginner Write-up)

## Challenge Information
- **Platform:** picoCTF
- **Category:** General Skills
- **Difficulty:** Easy
- **Challenge Name:** Obedient Cat

## Description
This challenge introduces beginners to basic Linux terminal commands by requiring the user to locate and read a file containing the flag.

## Objective
Use Linux command-line tools to navigate directories and read the contents of the provided file.

## Solution Overview
After downloading the file, I used the Linux terminal to inspect it.  
The challenge focuses on familiarizing users with basic commands rather than exploitation.

Steps taken:
1. Navigated to the directory using `cd`
2. Listed files using `ls`
3. Read the file contents using `cat`

The file was a plain text file (created using the Kate text editor), and the flag was stored directly inside it.

## Command Used
```bash
cat <filename>
```
## Flag
(Flag is redacted to avoid spoilers.)
`picoCTF{redacted}`

## Lessons Learned
• Basic Linux commands are essential for CTF challenges

• Always inspect files before assuming complexity

• Beginner challenges build habits needed for advanced cybersecurity work

## Defensive Perspective
Storing sensitive information in plaintext files can lead to exposure if access controls are misconfigured. Proper permissions and secure storage practices are essential.

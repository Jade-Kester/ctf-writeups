# picoCTF – Wave a Flag (Beginner Write-up)

## Challenge Information
- **Platform:** picoCTF
- **Category:** General Skills
- **Difficulty:** Easy
- **Challenge Name:** Wave a Flag

## Description
This challenge provides an executable file and asks the user to retrieve the flag.  
It is designed to introduce beginners to interacting with executable files and understanding command-line options.

## Objective
Analyze the provided executable file and determine how to retrieve the flag from it.

## Approach & Analysis
After downloading the file, I first inspected it directly using the Linux terminal.

Even though the file was an executable (`.exe`), I used `cat` to view its contents. This revealed multiple embedded strings, including readable messages mixed with non-readable characters.

While scanning the output, I focused on meaningful text and noticed a message referencing the `-h` option. This indicated that the executable supported a help flag, suggesting it could be run with command-line arguments to change its behavior.

The `-h` option is commonly used to display help information in a **human-readable** format, which hinted at how the challenge was intended to be solved.

## Key Observation
- Executable files can still contain readable strings
- Not all useful information requires execution or exploitation
- Help flags (`-h`) often reveal intended usage or hints

## Flag
`picoCTF{redacted}`

## Lessons Learned
- Executable files may contain readable messages when inspected
- Flags and hints can be embedded alongside other data
- Paying attention to command-line hints is critical in CTF challenges
- Beginner CTFs often reward careful observation over complex techniques

## Defensive Perspective
From a defensive standpoint, embedding sensitive information or hints directly within executables can lead to information disclosure. Proper handling of debug strings and compiled output is important when distributing binaries.

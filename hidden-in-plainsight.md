# picoCTF – Hidden in Plain Sight

**Category:** Forensics  
**Difficulty:** Easy  
**Platform:** picoCTF  
**Challenge Name:** Hidden in plainsight

---

## Overview

The challenge provides a JPEG image file and hints that the flag is hidden within it. The goal is to analyze the image and extract any concealed data using forensic and steganography techniques.

---

## Analysis

Since the file was an image, I started by checking whether it contained hidden metadata or comments. JPEG files often store additional information that is not visible when viewing the image normally.  
To inspect this, I used `exiftool`.  

```bash
exiftool img.jpg
```
   
While reviewing the metadata, I found a comment that looked like an encoded string:
`c3RlZ2hpZGU6Y0VGNmVuZHZjbVE9`   
The format and character set suggested it was Base64-encoded.

---

## Decoding the Message

I decoded the string using CyberChef.

### First Base64 decode:
`c3RlZ2hpZGU6Y0VGNmVuZHZjbVE9`
→ `steghide:cEF6endvcmQ=`  
The output revealed a tool name and another encoded string.
I decoded the second part again using Base64.

### Second Base64 decode:
`cEF6endvcmQ=`
→ `pAzzword`  
This produced a passphrase.

---

## Steganography Extraction
The word *steghide* indicated that the image likely contained hidden data embedded using the Steghide tool.

I installed Steghide:
`sudo apt install steghide`  
Then extracted the hidden content from the image:  
`steghide extract -sf img.jpg`  
When prompted for the passphrase, I entered:  
`pAzzword`  
This successfully extracted a file named `flag.txt`.

---

## Flag
`cat flag.txt`  
Output:   
`picoCTF{redacted}`

---

## Defensive Perspective
From a defensive standpoint, this challenge highlights how sensitive information can be unintentionally or intentionally hidden within media files.

Key defensive considerations include:
- Inspecting uploaded or transferred media files for hidden metadata
- Using tools like `exiftool` during forensic investigations
- Recognizing that encoded strings in metadata may indicate data exfiltration or covert communication
- Understanding steganography as a method attackers may use to hide payloads, credentials, or instructions

In real-world environments, security teams should monitor file uploads, perform metadata analysis during incident response, and be aware that images can be abused as data carriers.

---

## Lessons Learned
- Image metadata can contain hidden clues
- Encoded strings often appear in multiple layers
- Base64 is commonly used to obscure instructions or passwords
- Steganography tools like Steghide are essential for forensic challenges
- Careful inspection and pattern recognition are key CTF skills
- Defensive awareness is important when handling user-submitted media

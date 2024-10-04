# Solving 'Information' from picoCTF-2021
### Challenge Information:
- Author: SUSIE
- Classification: Forensics
- Difficulty: EASY
  ### Description and Insructions:
- Files can always be changed in a secret way. Can you find the flag? [cat.jpg](https://mercury.picoctf.net/static/d1375e383810d8d957c04eef9e345732/cat.jpg)
### Hints
1. Look at the details of the file
2. Make sure to submit the flag as picoCTF{XXXXX}
# Solution
### 1.  Download the given file
  - To start, download the given file 'cat.jpg' into your working environment. I did so using the following command.
---
    wget https://mercury.picoctf.net/static/d1375e383810d8d957c04eef9e345732/cat.jpg
--- 
- Note: the `wget` command is used to download specified files into your current working directory.
### 2. Attempting to inspect the file
  - After downloading the file, the first thing I tried to do was to display the contents of the cat.jph using the following command.
---
    cat cat.jpg
---
- After running the command you are met with a screen full of characters that is unreadable as it is data that only a computer can interpret.
  ![image](https://github.com/user-attachments/assets/bb87ad1d-4a03-49fc-abe6-264b3f14888d)
### 3. How to inspect the file
- After not being able to find anything relevant using the `cat` command I did a little bit of research and came across the `exiftool` command that extracts and outputs relevant information pertaining to a specified file.
---
    exiftool cat.jpg
---
- After running the above command you should be met with an output similar to one shown below
![image](https://github.com/user-attachments/assets/377010b8-2e60-426d-aef6-b670d2b3cdd4)
### 4. Analyzing the file data
- Now that I had a little more to work with and taking a closer look at the information returned by using the `exiftool` command there were 2 rows of information that stood out to me compared to the rest
    - Current IPTC Digest
    - License
- Both lines contained an unusual string of characters and I decided to start by finding out what what the Current IPTC Digest was in relation to cat.jpg.
-  According to iMDC, "IPTC is a popular photography metadata standard. It specifies the fields, properties, and structure of metadata in order to make it easier to manage and retrieve images." https://imagemetadatachecker.com/knowledge-base/iptc-digest
    - After reading the article by iMDC I came to the conclusion that there was nothing wrong with what I was looking at and moved on to looking at the string next to Liscense.
- When I think of a liscencse for someething the first thing that comes to mind does not match the assorted character string I was looking at. Considering this is a CTF I went with the educated guess that I might be looking at some sort of encrypted string and went back to the internet to look for any common encryption standards used in CTFs like this one.
### 5. Unencrypting the string
- Of the different encryption standards I tried to use the following command is what finally revealed the flag to me
--- 
    echo cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9 | base64 -d
---
- The echo command displays any following text out onto the screen, the | or pipe sends the output from the left side of the pipe and uses it as input for the command on the right side. base64 -d decodes files into standard output.
- Running the command outputs the flag `picoCTF{the_m3tadata_1s_modified}` to the screen

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
  - To start, download the given file 'cat.jpg' into your working environment using the `wget` command.
---
    wget https://mercury.picoctf.net/static/d1375e383810d8d957c04eef9e345732/cat.jpg
--- 
- Note: the `wget` command is used to download specified files into your current working directory.
### 2. Attempting to inspect the file
  - After downloading the file, the first thing I tried to do was to display the contents of the cat.jpg using the following command.
---
    cat cat.jpg
---
- After running the command you are met with a screen full of characters that is unreadable as the `cat` command is meant to be used to display text-based files, not binary files like `.jpg`.
  ![image](https://github.com/user-attachments/assets/bb87ad1d-4a03-49fc-abe6-264b3f14888d)
### 3. How to inspect the file
- After not being able to find anything relevant using the `cat` command I did a little bit of research and came across the `exiftool` command that extracts and outputs the metadata pertaining to a specified file.
---
    exiftool cat.jpg
---
![image](https://github.com/user-attachments/assets/377010b8-2e60-426d-aef6-b670d2b3cdd4)
- Metadata in images contains a lot of information about the file, such as timestamps, camera settings, or even embedded data. CTF challenges often hide flags in this metadata, so using exiftool to inspect files for such data is a common technique.
### 4. Analyzing the metadata
- Now that I had a little more to work with and taking a closer look at the information returned by using the `exiftool` command there were 2 rows of information that stood out from the rest: **Current IPTC Digest** and **License**
- Both lines contained an unusual string of characters and I decided to start by finding out what what the Current IPTC Digest was in relation to cat.jpg.
-  According to iMDC, "IPTC is a popular photography metadata standard. It specifies the fields, properties, and structure of metadata in order to make it easier to manage and retrieve images." https://imagemetadatachecker.com/knowledge-base/iptc-digest
- After reading the article by iMDC I came to the conclusion that there was nothing wrong with what I was looking at and moved on to looking at the string next to License.
- When I think of a license for someething the first thing that comes to mind does not match the assorted character string I was looking at. Considering this is a CTF I went with an educated guess that I might be looking at some sort of encrypted string and went back to the internet to look for any common encryption standards used in CTFs like this one.
### 5. Unencrypting the string
- Of the different encryption standards I tried to use the following command is what finally revealed the flag to me
--- 
    echo cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9 | base64 -d
---
- The `echo` command displays any following text out onto the screen, the `|` or pipe takes the output from the left side of the pipe and uses it as input for the command on the right side. `base64 -d` decodes the file into standard output.
- Running the command outputs the flag `picoCTF{the_m3tadata_1s_modified}` to the screen.
## Thoughts and conclusions
- By analyzing the file's metadata and decoding a base64 string hidden within the "License" field, we successfully uncovered the flag for this challenge. This exercise highlights the importance of inspecting metadata and understanding basic encoding techniques in CTF forensics challenges. One key takeaway from this challenge is the use of the `exiftool` command as it is very powerful when it comes to inspecting the metadata of a file.
# Flag
- picoCTF{the_m3tadata_1s_modified}

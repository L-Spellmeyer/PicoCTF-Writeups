# Solving 'Obedient Cat' in picoCTF-2021
### Information:
- Author: SYREAL
- Classificatioins: General Skills
- Difficulty: EASY
### Description and Instructions
- This file has a flag in plain sight (aka "in-the-clear"). Download flag.

### Hints
1. Any hints about entering a command into the Terminal (such as the next one), will start with a '$'... everything after the dollar sign will be typed (or copy and pasted) into your Terminal
2. To get the file accessible in your shell, enter the following in the Terminal prompt: `$ wget https://mercury.picoctf.net/static/704f877da185904ec3992e7255a15c6c/flag`
3. $ man cat

# Solution
1. Download the given file
   - I started this challenge by downloading the given file `https://mercury.picoctf.net/static/704f877da185904ec3992e7255a15c6c/flag` into my working environment. To do this I used the `wget` command:
```
        wget https://mercury.picoctf.net/static/704f877da185904ec3992e7255a15c6c/flag
```
  - This command will download the contents of the given file into your current working directory
2. Display contents of the file
   -  After the file finished downloading check to make sure the file was downloaded succesfully by using the `ls` command. This command will display all the files from the current working directory. After ensuring the file was downloaded use the `cat` command followed by the file you wish to output.
```
      cat flag
```
- After running the command the flag will be revealed: picoCTF{s4n1ty_v3r1f13d_1a94e0f9}

# Thoughts and conclusions:
- This was a very simple and straightforward challenge. The key takeaways are the use of the `wget` and other basic terminal commands. Remember these commands as you will use them to inspect numerous files throughout many challenges.

  # Flag:
  - picoCTF{s4n1ty_v3r1f13d_1a94e0f9}

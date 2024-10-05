# Solving 'Verify' from picoCTF-2024
### Challenge Information:
- Author: JEFFERY JOHN
- Classification: Forensics
- Difficulty: EASY
### Description and Instructions:
- People keep trying to trick my players with imitation flags. I want to make sure they get the real thing! I'm going to provide the SHA-256 hash and a decrypt script to help you know that my flags are legitimate.
- You can download the challenge files here:
    - [challenge.zip](https://artifacts.picoctf.net/c_rhea/20/challenge.zip)
- The same files are accessible via SSH here:
    - `ssh -p 55234 ctf-player@rhea.picoctf.net`
- Using the password `f3b61b38`. Accept the fingerprint with `yes`, and `ls` once connected to begin. Remember, in a shell, passwords are hidden!
    - Checksum: fba9f49bf22aa7188a155768ab0dfdc1f9b86c47976cd0f7c9003af2e20598f7
    - To decrypt the file once you've verified the hash, run ./decrypt.sh files/<file>.
### Hints:
1. Checksums let you tell if a file is complete and from the original distributor. If the hash doesn't match, it's a different file.
2. You can create a SHA checksum of a file with `sha256sum <file>` or all files in a directory with `sha256sum <directory>/*`.
3. Remember you can pipe the output of one command to another with |. Try practicing with the 'First Grep' challenge if you're stuck!
# Solution
1.

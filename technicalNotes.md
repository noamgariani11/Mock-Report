# Data Aquisition

There were multiple technical steps in the data aquistion stage. This document outlines all of those steps.

# Images

Before touching the laptop many images were taken from different angles. Images were taken from the outside and then opened the laptop to look at the inside.

The link to the recorded images could be found [here](https://github.com/noamgariani11/Mock-Report/blob/main/images.md).

# Cracking password

Unfournately, when out Digital Forensics team received the laptop it was password protected. Although there are ways to use digital forensics tools to take out the hard drive and get the disk image that way, Sten Walker (Yone), decided to encrypt his hard drive. The only way this laptop would be useful is if we can get access laptop with his password.

Since he uses a very insecure operation system, Windows, it was possible to retreive his hash. Mimikatz software was used to retreive the password md5 hash.

Here is are the hashes of the password retreived with Mimikatz:

MD5 hash: ```025d43b1978d96e4d40d2316c90e3caa```

SHA1 hash: ```ef678205593788329ff416ce5c65fa04f33a05bd```

I then used hashcat on the MD5 hash with the password wordlist rockyou.txt.gz to get the password. This is the command:

```hashcat -a 0 -m 0 -o cracked.txt hash.txt rockyou.txt.gz```

Mode 0 is for md5, Mode 100 is for SHA1, and Mode 1400 is for SHA256. In this case "-m 0" was used to dictate that this is a md5 hash. This first part, "-a 0", specified that this is a dictionary attack. And the last part "-o" specified the output file "cracked.txt", the hash input file "hash.txt", and lastly the wordlist which in this case is "rockyou.txt.gz". Most might think that you have to use "gunzip" on rockyou.txt.gz, but hashcat can actually run it while it is in the gz format, it just takes a bit longer.

This is the password that was used: ```a1b2c3d4e5f6```

# Hashes

These are the hashes of the disk image to ensure that nothing was changed. It was orginally from the laptop itself and then check when retreived the disk image.

```certutil -hashfile C:\disk.img MD5```: 9233a28d820528f67ebf2416e0e896cb

```certutil -hashfile C:\disk.img SHA1```: eec891f16972515fe4d464ed9037eb32b6a6334f 

```certutil -hashfile C:\disk.img SHA256```: ad5133f0081f81d987ab699a45bef742582a11219e3f8da85ace13b483729c7b

Multiple copies (3) were made and they all have the same hashes as the orginal laptop disk hashes.

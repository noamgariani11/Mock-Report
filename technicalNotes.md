# Data Aquisition

There were multiple technical steps in the data aquistion stage. This document outlines all of those steps.

# Images

Before touching the laptop many images were taken from different angles. Images were taken from the outside and then opened the laptop to look at the inside.

The link to the recorded images could be found [here](https://github.com/noamgariani11/Mock-Report/blob/main/images.md).

# Cracking password

Unfortunately, when our Digital Forensics team received the laptop it was password protected. Although there are ways to use digital forensics tools to take out the hard drive and get the disk image that way, Sten Walker (Yone), decided to encrypt his hard drive. The only way this laptop would be useful is if we can get access laptop with his password.

Since he uses a very insecure operating system, Windows, it was possible to retrieve his hash. Mimikatz software was used to retrieve the password md5 hash.

Cellebrite UFED could do a similar task, but our organization doesn't have the resources to afford it.

Here are the hashes of the password retreived with Mimikatz:

MD5 hash: ```025d43b1978d96e4d40d2316c90e3caa```

SHA1 hash: ```ef678205593788329ff416ce5c65fa04f33a05bd```

I then used hashcat on the MD5 hash with the password wordlist rockyou.txt.gz to get the password. This is the command:

```hashcat -a 0 -m 0 -o cracked.txt hash.txt rockyou.txt.gz```

Mode 0 is for md5, Mode 100 is for SHA1, and Mode 1400 is for SHA256. In this case "-m 0" was used to dictate that this is an md5 hash. This first part, "-a 0", specified that this is a dictionary attack. And the last part "-o" specified the output file "cracked.txt", the hash input file "hash.txt", and lastly the wordlist which in this case is "rockyou.txt.gz". Most might think that you have to use "gunzip" on rockyou.txt.gz, but hashcat can run it while it is in the gz format, it just takes a bit longer.

This is the password that was used: ```a1b2c3d4e5f6```

# Hashes

These are the hashes of the disk image to ensure that nothing was changed. It was orginally from the laptop itself and then check when retreived the disk image.

```certutil -hashfile C:\disk.img MD5```: 9233a28d820528f67ebf2416e0e896cb

```certutil -hashfile C:\disk.img SHA1```: eec891f16972515fe4d464ed9037eb32b6a6334f 

```certutil -hashfile C:\disk.img SHA256```: ad5133f0081f81d987ab699a45bef742582a11219e3f8da85ace13b483729c7b

Multiple copies (3) were made and they all have the same hashes as the orginal laptop disk hashes.

# RAM

When looking at volatile memory like RAM our team uses a tool called Volatility. We analyzed the RAM for any clues as to what was left on this laptop. This gave us more clues as to what was happening. More specifically it showed us documents, browsing history, apps, and more that helped in the search for the disk and in gathering the evidence as a whole.

# Log Analysis

(Note: This is based on the log analysis and forensics modules of NCX. This isn't exactly what it was, but similar.)

A packet capture (pcap) was captured over the Sten Walkers (Yone) operation. This was important because it possibly contained information that could expose certian parts of what was happenening. The tool that was used to view this network traffic capture was wireshark.

The packet capture had many bit torrent files along with on packet that in plain text listed many different encryption types. Additionally later on in the pcap file it was found that in a converstion between to people the key phrase to the encryption was shown in plain text. The usual process to find this conerstation by looking at the packets, but for simplification I just ran strings on the pcap and got similar results. I then looked at the packets though to follow the process.

Once the bittorrent file was reconstructed from the pcap was recounstructed it was ready to be decrypted with one of the encryption types and the key found. I first ruled out the encryption types that didn't require a key, then I started with the least secure encryption types on the list and systematiallly attempted each one. It ended up being DES-EBC encryption and was sucessfully decrypted with the key.

The decrypted recovered file ended up being an image with malware installed inside of it. When running binwalk extract you could extract the malware. Then by getting the md5 hash or sha256 hash in the command line I was able to find in VirusTotal that the is a common type of malware used by this organization. I also looked at the exif data to see if anything about the image location or time could be found, but in this image the exif data was cleared. 

In this case it added nothing that out team didn't already know.

# Exif Data in Images

In every email that is sent to the customers there is an image sent from the system adminstrators or owner (Sten Walker) and since we have undercover people in teh system we are able to get these emails. Since we systematically analyse all the data the team always looks at the exif data with exiftools. Most of the time all of the exif data is cleared other than the time stamp. The time stamp just shows that the image was taken an hour before the email was sent. This means that they take a new image and upload it every time they send an email and that it isn't an automated email. 

It was the hope that they would slip up and the location would be in one of the images, but unfournatley there was never a slip-up and the information had to be found a different way. But this process was thoroughly documented anyways.

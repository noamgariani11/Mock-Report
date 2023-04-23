# Case 981529 Report

**Objective:** To access the password on the disk image to access the server which incriminates the suspect, Sten Walker (Yone).

**Computer Type:** Dell Inspiron 3511

**Operating System:** Windows 10

**Offense:** Online Drug Distribution

**Case Agent:** Noam Gariani

**Evidence Number:** 1

**Chain of Custody:** See attached form

**Examination Location:** Bryan

**Tools used:** Disk acquisition utility, Autopsy, openssl, hashcat, Linux Command Line, and Steganography tools

# Executive Summary

* The password for the "totallynotadrugonlinemarketplace" drug markertplace network was found in the disk image.
* Access to the whole network will be able to provide evidence for multiple arrests, but most notably providing key evidence in implicating Sten Walker (Yone) as the head of the organization.

# Items Analysed 

| Evidence Number  | Item Description                     |
| -------------    | -------------                        |
| 1                | Dell Inspiron 3511, Serial: H99WPT2  |

# Case Background

The site ```totallynotadrugonlinemarketplace.onion``` is one of the largest online druge marketplaces in the United States. It was beleived and later confirmed that Yone played a critical part in created this marketplace.

Here are some statistics that the FBI had found in connection to this drug marketplace: 

* 2901 Hospitilized Adults
* 781 Hospitilized Children
* 1398 Adults Died
* 256 Children Died

These connections were able to be made because there is a mark on the drugs that the DEA helped identify.

Yone was first identified as a possible suspect by revealing his real name in one of the email headers. This is very similar to how the FBI caught The Silk Road. This led to finding more information about him with Open Source Intelligence (OSINT) as well as a deployed FBI surveillance team.

Once the connection was made to Sten Walker (Yone) his laptop was seized. The objective then was to get the password off of the disk image to access the online drug marketplace. When the password was found in the disk image the new objective was to gather as much information on their network to provide evidence to this case.

# Data Collection

Before touching the laptop in question multiple images were taken. The images could be seen in the items attached. Additionally, a chain of custody form was used to keep track of who had the laptop and when. Our organization uses ISO/IEC 27037:2012 standard, the Daubert standard, and the NIST SP 800-86 when collecting digital artifacts to ensure the integrity of the investigation.

There weren't any time constraints in the collection of the laptop so our team was able to be thorough in the investigation and not miss anything. To preserve the integrity we collected compared the digital fingerprint of the laptop to make sure there was no modification of the laptop. The [technical notes](https://github.com/noamgariani11/Mock-Report/blob/main/technicalNotes.md) go more in-depth into this but the standards mentioned above were used in this process.

Initially, we look at the RAM since it was the most volatile, and then the disk. Our Digital Forensics team uses the same methodical approach that is documented for all of our cases as well as this one when reviewing the disk image and the drug marketplace network once the password was found.

# Significance of Findings

Once the password was found we were able to implicate these key actors:

* Sten Walker (Yone) - Head of the Organization
* Yakazo Jun - System Adminstrator
* Minh Quoc Nguyen - Cyber Offensive Operations
* Ugo Caesar Anele - System Adminstrator

Along with these key actors many smaller drug dealers on this marketplace were found and can later be prosecuted.

# Conclusion

possible impact

# Acknowledgements

I'd like to acknowledge the team that made this possible. Digital forensics is not an individual task it requires a team of dedicated people to go through many different avenues. With a diverse digital forensics team with many different people having different expertise, we were able to professionally and correctly analyze the files and connect them to the suspect.

I would also like to acknowledge all the investigative teams such as Bryan Police Department and the FBI who were the ones to get the laptop in the first place. It would not have been possible without them.

Lastly, I would like to acknowledge the lawyers working hard to get the people responsible for this.

# Expert Witness

Federal Rule 26 (Disclosure of Expert Testimony) and under Rules 702, 703, or 705 of the Federal Rules of Evidence these are the people that may be used at testimony:

* Noam Gariani
* John White

Also, due to this case being in Texas this case was prepared to withstand the Daubert test for the admissibility of expert witness testimony.

# Items Provided

* [Chain of Custody Form](https://github.com/noamgariani11/Mock-Report/blob/main/chain-of-custody.pdf)
* [Refrences](https://github.com/noamgariani11/Mock-Report/blob/main/references.md)
* [The disk image](https://artifacts.picoctf.net/c/485/disk.flag.img.gz)
* [Case Notes](https://github.com/noamgariani11/Mock-Report/blob/main/CaseNotes.md)
* [Technical Notes of Data Aquisition](https://github.com/noamgariani11/Mock-Report/blob/main/technicalNotes.md)
* [Autopsy Forensics Report](https://github.com/noamgariani11/Mock-Report/tree/main/MockReport%20HTML%20Report%2004-16-2023-11-33-24)

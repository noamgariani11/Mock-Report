# Data Aquisition

There were multiple technical steps in the data aquistion stage. This document outlines all of those steps.

# Images

Before touching the laptop many images were taken from different angles. Images were taken from the outside and then opened the laptop to look at the inside.



# Hashes

These are the hashes of the disk image to ensure that nothing was changed. It was orginally from the laptop itself and then check when retreived the disk image.

```certutil -hashfile C:\disk.img MD5```: 9233a28d820528f67ebf2416e0e896cb

```certutil -hashfile C:\disk.img SHA1```: eec891f16972515fe4d464ed9037eb32b6a6334f 

```certutil -hashfile C:\disk.img SHA256```: ad5133f0081f81d987ab699a45bef742582a11219e3f8da85ace13b483729c7b

Multiple copies (3) were made and they all have the same hashes as the orginal laptop disk hashes.

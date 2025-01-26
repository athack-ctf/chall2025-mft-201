# How to Solve the Challenge?

Here, the task is clear; we believe the secret file we looked on in `MFT 101` holds some data and needs to be recovered, but the question how we can recover it (can be deleted or not) and we do't have the disk image where the secret file was. Here we understand how NTFS works and what info MFT really hold. I recommend this video by 13cubed [here](https://www.youtube.com/watch?v=l4IphrAjzeY) 

The key element that we need to understand is the diffrence between a resident file and non-residen file:

<H2>Resident file:</H2>
  - Small file size <br>
  - Entire file data stored directly within the MFT record <br>
  - Faster access due to data being readily available in the MFT <br>
  
<h2>Non-resident file:</h2>
  - Large file size <br>
  - Data stored in separate clusters on disk <br>
  - MFT entry contains pointers to the locations of the data clusters 
  <br>
  <br>
  
**Example:** 
 - A small text file with only a few lines might be considered a resident file because its entire content could fit within the MFT record. <br>
 - A large video file would be a non-resident file as its data would occupy many clusters on the disk and only the starting location of that data would be stored within the MFT entry. 
<br>
<mark>Note:</mark>
<p>A resident file within the MFT (Master File Table) is typically considered to be a small file, usually around 700 bytes or less, where the entire file content can fit directly within the MFT record itself. <br>
Our Secret file meets all the requirements as it is 87 bytes of size only.
</p>

Now, how to recover the content of the file, always using MFTECmd tool by Eric Zimmerman, lets see more options and features of this tool: 
![image](https://github.com/user-attachments/assets/5cd3b49f-8692-4af8-8846-93491e6fe50f)

Notice `--de` option, it asks for  $MFT entry/sequence of a file to dump its details, we already have these info from our parse results from <mark>MFT 101</mark>, remember that csv file, let's check it back by opening it in Timeline Explorer:

![image](https://github.com/user-attachments/assets/08948878-610c-4d6a-a603-8a4262f4ead9)

ok, let's form the command now:
`MFTECmd.exe -f path/to/mft/file --de entry-seq` 

![image](https://github.com/user-attachments/assets/3682fa44-e580-45f7-b263-0059e3ea8a33)
![image](https://github.com/user-attachments/assets/eece95ce-ac61-4eb7-ae43-ae7f28b9b961)

It displays tons of useful info, plus th file content that we are looking for. 
<br>
Flag: ` ATHACKCTF{NTF$_M4s73r_fiL3_T4bL3!!!}`


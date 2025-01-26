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
  - MFT entry contains pointers to the locations of the data clusters <br>
<bold>Example:</bold>
 - A small text file with only a few lines might be considered a resident file because its entire content could fit within the MFT record. 
 - A large video file would be a non-resident file as its data would occupy many clusters on the disk and only the starting location of that data would be stored within the MFT entry. 

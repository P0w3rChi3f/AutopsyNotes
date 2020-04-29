# Autopsy Labs  

## Setup  

Before we begin with the videos, let's start downloading the data we'll need for the later labs.  We won't need them for a few sections, so you can start them now and let them download in the background.  

Autopsy: We focus on the Windows version of Autopsy.  You may encounter problems with the course if you use it on Linux or macOS since not all features are supported.  
64-bit [Autopsy](http://www.autopsy.com/download)  
Disk images.  Given the popularity of the free COVID-19 training, we have had trouble hosting these images with reasonable speeds.  If one of these is past its quota, try the other.  

[Mirror #1](https://drive.google.com/drive/folders/1YJ0v9izpUZUfB2U3IAQ8ke3T9dUe57Jb)  
OR  
[Mirror #2](https://drive.google.com/drive/folders/15b8_gKQmj7Nz6wo2n34CSD9LBu5TKgHX)  
OR  
[Mirror #3](https://file.ac/21euCO1oZvB7YmqqMxZysQ/)

Hashes for the files:
MD5 (device1_laptop.e01) = dc176d653c5613e305e831525e874090  
MD5 (device2_mediacard.e01) = c8343d3976eec2985e7580a2b6321591

[NIST NSRL Hash Set](https://sourceforge.net/projects/autopsy/files/NSRL/NSRL-266m-computer-Autopsy.zip/download)  
[Video Triage Module.](https://www.autopsy.com/add-on-modules/video-triage/) Fill out the form and download the ZIP file.  

---

## Lab 1  

Before we begin the lab, make sure you downloaded the images that were listed back in Section 1. If you want to confirm that you had no corruption, these are the MD5 values of the files:  

MD5 (device1_laptop.e01) = dc176d653c5613e305e831525e874090  
MD5 (device2_mediacard.e01) = c8343d3976eec2985e7580a2b6321591  

We will now begin the analysis of the hard drive that was found in the dognappers car.  At this point in the scenario, we haven’t searched the house yet and therefore will not have access to the media card device.  So, make sure you do not add that yet.  

1. Launch Autopsy

2. Choose “Create New Case”

3. Make a case with the following information:  
    - Name: case1  
    - Base Directory: c:\  (or where ever you'd like to store the case)  
    - Skip case number and examiner

4. Add device1_laptop.e01 image as data source.  
**NOTE: Do NOT add device2_mediacard.e01 yet**

5. Deselect ALL ingest modules.  
    - As a reminder, this is not what you’d typically do.  But, we are doing it this way for the course.  

6. Finish Adding Image.

7. Open the “Data Sources” part of the left-hand tree (we’ll cover this tree more in the next section).  
    - **Question:** How many volumes does the disk image have?  
        - 6
    - **Question:** What is the name of the unallocated space file in vol1?  
        - Unalloc_3_0_1045876
    - **Question:** Right click on vol7 and choose “File System Details”.  What file system is in vol7?  
        - NTFS

8. In Windows, open “C:\case1” in a file explorer and observe its contents.  
    - **Question:** What is the database called?  
        - autopsy.db  
    - **Question:** Roughly how big is the database (in megabytes)?  
    - 225 mb

---

## Lab 2  

Keep the same case open that you created in the last section.  Let’s look at the data in the tree.

1. **Question:** By extension, how many databases are there?  
    - 59  
2. **Question:** What is the size of the largest database?  
    - 5242880
3. **Question:** Are there any databases by MIME type yet?  
    - No
4. **Question:** What are the names of the files between 200MB and 1GB in size?  
    - $BadClus:$bad  
    - Winre.wim  
    - Chrome.7z

  ---

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

## Lab 3  

We are now going to begin analyzing the laptop.  We are starting off the case with some clues. Most notably, we have pictures that were sent with the ransom emails to Basis Technology

1. Keep same case open from previous lab, or reopen the case ("case1").  

2. Right click on device1_laptop.e01 image in tree and choose “Run Ingest Modules”  

3. Disable all modules except the following (we will pre-load some for the next lap):  

    - Hash Lookup
    - File Type Identification
    - Extension Mismatch Detector
    - Embedded File Extractor
    - Exif Parser
    - Email Parser
    - Correlation Engine

4. Configure the Hash Lookup module with two hash sets:

    - Import the NSRL File (NSRLComplete.txt-md5.idx) that you previously downloaded in Section 1.  

      - You may need to unzip the file you downloaded.  
      - You can use the default values (i.e. Type: Known).  

    - Create a New Hash Set:
      - Destination: Local
      - Name: Ransom Case
      - Hash Set Path: [Any folder on your computer]
      - Type: Notable  

    - Use "Add Hashes to Hash Set" button to copy and paste the following MD5 value into the "Ransom Case" hash set.  This is the hash of the ransom note.
07c94320f4e41291f855d450f68c8c5b

5. Start the Ingest Modules.

6. Observe:

    - Use Ingest Inbox as an indicator when ‘Known Bad’ hash hits are found.  

    - Use “Go To Result” to go to tree area of hash hits.  

    - View the hash hit.  

    - **Question**: Let ingest get at least 15% through the drive.  How many total hits are found under the “Hashset Hits” results after running the Hash Lookup Ingest Module? **6**  

    - **Question**: What are the filenames of the hash hits?  **RN.jpg**  **f_000239**  

    - One of the hits is in a folder named “Pictures”.  Right click on the file to “View” there.  

    - **Question**: How many total ".jpg" files are in the folder “Pictures” where the notable hash hit was found? **7**  

    - While reviewing the images in that folder, it is noticed that “IMG_20191024_155744.jpg” shows health violations by bringing the dog into a restaurant.  We want to tag this as Notable:  

      - Right click on it  

      - Select “Add File Tag” and choose “Notable Item”  

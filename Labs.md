# Autopsy Labs  

## Setup  

Before we begin with the videos, let's start downloading the data we'll need for the later labs.  We won't need them for a few sections, so you can start them now and let them download in the background.  

Autopsy: We focus on the Windows version of Autopsy.  You may encounter problems with the course if you use it on Linux or macOS since not all features are supported.  
64-bit Autopsy: http://www.autopsy.com/download  
Disk images.  Given the popularity of the free COVID-19 training, we have had trouble hosting these images with reasonable speeds.  If one of these is past its quota, try the other.  

Mirror #1  
OR  
Mirror #2  
OR  
Mirror #3

Hashes for the files:
MD5 (device1_laptop.e01) = dc176d653c5613e305e831525e874090  
MD5 (device2_mediacard.e01) = c8343d3976eec2985e7580a2b6321591

NIST NSRL Hash Set: https://sourceforge.net/projects/autopsy/files/NSRL/NSRL-266m-computer-Autopsy.zip/download
Video Triage Module: Fill out the form and download the ZIP file.  https://www.autopsy.com/add-on-modules/video-triage/  

---

## Lab 1  

Before we begin the lab, make sure you downloaded the images that were listed back in Section 1. If you want to confirm that you had no corruption, these are the MD5 values of the files:  

MD5 (device1_laptop.e01) = dc176d653c5613e305e831525e874090  
MD5 (device2_mediacard.e01) = c8343d3976eec2985e7580a2b6321591  

We will now begin the analysis of the hard drive that was found in the dognappers car.  At this point in the scenario, we haven’t searched the house yet and therefore will not have access to the media card device.  So, make sure you do not add that yet.  

- Launch Autopsy
- Choose “Create New Case”
- Make a case with the following information:  

```InfoCase  
    Name: case1
    Base Directory: c:\  (or where ever you'd like to store the case)
    Skip case number and examiner
```

- Add device1_laptop.e01 image as data source.  
** NOTE: Do NOT add device2_mediacard.e01 yet **

- Deselect ALL ingest modules.  

- As a reminder, this is not what you’d typically do.  But, we are doing it this way for the course.  

Finish Adding Image.

Open the “Data Sources” part of the left-hand tree (we’ll cover this tree more in the next section).  
Question: How many volumes does the disk image have?  
Question: What is the name of the unallocated space file in vol1?  
Question: Right click on vol7 and choose “File System Details”.  What file system is in vol7?  
In Windows, open “C:\case1” in a file explorer and observe its contents.  
Question: What is the database called?
Question: Roughly how big is the database (in megabytes)?  

---

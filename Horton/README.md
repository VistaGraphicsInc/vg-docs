Specs: Versant 180 Press  

# Network Scanning  

## User Scan Template  

This is useful for frequent users of Network Scanning. Without a specific User Scan Template, all files scanned using Network Scanning (e.g. DEFAULT template) will save in its preconfigured file destination (`SYN_NAS0` > `Admin` > `HORTON SCAN FOLDER`) at the top-level. This is manageable, until several documents are scanned here; therefore making it difficult for one to find the document they scanned, as the files are generically named. To counteract this *muddying up* of the waters, user can scan to their specifically named folder. The steps below will outline how to create specific scan destination within `HORTON SCAN FOLDER`.  

### User Scan Template Outline  

#### Create a New Directory for the User;  

1. Log into **SYN_NAS0**, navigate to `Admin/HORTON SCAN FOLDER`  
2. Create a new directory, named after the user; i.e. **Steve**  

#### Create a New Job Template;  

1. Log into the printer's (Horton) Config site (the printer's IPv4 address)  
2. SCAN > Job Templates  
   1. Fill in the Job Template name field with the user's (**Steve**)  
   2. Edit the **File Destination** to be the user's name as its final path  
3. Update the printer's Template List;  
   1. Properties > Network Scanning > General Settings  
      1. *Refresh Template List Now*  

Conduct a test scan using the template just added to Horton. Confirm the User Scan Template is saving properly by checking the directory you just created on the SYN_NAS0 server.  

***  
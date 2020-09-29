Writeup for Wolfie's Contact challenge:

Description for Wolfie's Contact:

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/Wolfie's%20Contact/Images/forensic_writeup1.JPG)

From the description we found out that there is something about contacts or friends in this challenge ..Let's download the file given in the challenge.

Using file command, I found that it is of EWF file format and then I searched the internet which can be used for this types of files which suggested a very nice Digital forensics tool called FTK_Imager from AccessData which runs only in Windows.So switched to windows and Download this tool.

Then go to File->Add Evidence Item->Image file Radio Button->Next->Browse->Select the Challenge file->Click Finish.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/Wolfie's%20Contact/Images/forensics_writeup2.JPG)

We can see a folder called Contacts in the left side Evidence tree menu

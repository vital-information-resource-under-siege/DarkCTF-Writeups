Writeup for Wolfie's Contact challenge:

Description for Wolfie's Contact:

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/Wolfie's%20Contact/Images/forensic_writeup1.JPG)

From the description we found out that there is something about contacts or friends in this challenge ..Let's download the file given in the challenge.

Using file command, I found that it is of EWF file format and then I searched the internet which can be used for this types of files which suggested a very nice Digital forensics tool called FTK_Imager from AccessData which runs only in Windows.So switched to windows and Download this tool.

Then go to File->Add Evidence Item->Image file Radio Button->Next->Browse->Select the Challenge file->Click Finish.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/Wolfie's%20Contact/Images/forensics_writeup2.JPG)

We can see a folder called Contacts in the left side Evidence tree menu .Let's select that folder and view the files in that folder.

And one file called the dealer.contact has a flag like value in between the <c:Notes> tag .It seems like it is part of a flag.

darkCTF{

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/Wolfie's%20Contact/Images/forensics_writeup3.JPG)

Let's search for more files with values in between <c:Notes> tag.

Ah well!!In the broker.contact file we got a another flag like value.

C0ntacts_

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/Wolfie's%20Contact/Images/forensics_writeup4.JPG)

Let's check more files in this folder which has <c:Notes> tag with a value in between them.

Wowiee!!Another interesting file that has a value between <c:Notes> that looks like a flag.

4re_

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/Wolfie's%20Contact/Images/forensics_writeup5.JPG)

Okkk I think it's end of the road for the challenge because a tag appears to be the having the closing braces for the flag format ..Let's try assembling it and see if any more value is missing .

1mp0rtant}

No more parts are required I was able to submit the flag.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/Wolfie's%20Contact/Images/forensics_writeup6.JPG)

The flag for the challenge is  darkCTF{C0ntacts_4re_1mp0rtant}

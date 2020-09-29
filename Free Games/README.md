Writeup for Free Games Forensics Writeup:

Description of the challenge:

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/Free%20Games/Images/free%20games.JPG)

From the description we need to search for a url based on downloads.Autopsy is a very good tool that link web downloads and also has a keyword search for making it ease.

 I am gonna use this autopsy tool in windows version.Lets open the tool.

Click on New Case

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/Free%20Games/Images/free%20games1.JPG)


Give a case name and directory in which the case files are gonna be stored  and click Next.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/Free%20Games/Images/free%20games2.JPG)

These are optional information which can u skip by not filling any fields and clicking finish.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/Free%20Games/Images/free%20games3.JPG)

As we have file that is of EWF file format select disk image or VM file and select Next.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/Free%20Games/Images/free%20games4.JPG)

Select the file in the select data source and if you want to ignore the orphan files click the check box below it .

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/Free%20Games/Images/free%20games5.JPG)

Select the modules you want to add for analying the disk image file .Most of the modules are already selected for user's comfort and click Next.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/Free%20Games/Images/free%20games6.JPG)

This image shows that file has been added successfully and also ready for doing forensics

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/Free%20Games/Images/free%20games7.JPG)

In the left side you can see different options that can used for analyzing this disk image.The Web downloads looks interesting as the description says it as a downloaded file.Let's look out there..

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/Free%20Games/Images/free%20games8.JPG)

Okk from the downloads among media files there is a zip file called PencakSilat that can be a game let's try a google search on the game.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/Free%20Games/Images/free%20games9.JPG)

Google searched confirmed that this name belongs to a game and from the above image we can see full url to the game 

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/Free%20Games/Images/free%20games10.JPG)

Okk let's enclose the url into the darkCTF{} and submit the flag ..

The flag for the challenge is darkCTF{http://aries.dccircle34.com/realitydownloadgo/c4d37739ca3dc3ed2d4852395d5ed228/784b4647446e334c58556e5473326556422e624f612e51432e4a6472/2019/07/31/PencakSilat2_1.zip}








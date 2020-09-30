Writeup for strings challenge:

Description for the strings challenge:

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/strings/Images/Screenshot_20200930_061049.jpeg)

The challenge says it's manipulation of couple of strings means the user input and and binary's own strings is manipulated to form a value ..So if we give a perfect it will work with the value in binary and form a value 

Okk let's go with the standard first three steps and find out what are the information we can able to dig up in the binary.The fist three steps are normal execution,ltrace and strings 

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/strings/Images/Screenshot_20200930_061238.jpeg)

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/strings/Images/Screenshot_20200930_061252.jpeg)

From the above image we can see that the binary is itself prompting the user to give a specific value as input and after giving the value nothing happens it does not print anything neither positive nor negative when used with ltrace we find out that a value's string length is checked multipled times and the length of that string and the user input string is both equal to 18. And strncat concates 1 byte 18 times to join the string and at the far right of the strncat we can see address which seems to be stack address chances that without displaying the flag the flag maybe formed in the stack.And from the strings there are less number of functions 
the strings command didn't help with some info this time.

Let's view this in ghidra's decompiler if complex let's proceed to gdb because we have the info about the flag being formed in the stack.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/strings/Images/Screenshot_20200930_061630.jpeg)

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/strings/Images/Screenshot_20200930_061654.jpeg)

It's bit complex so I think it's gdb to the rescue the flag and from the disas main we found that rsp is being added at the end which may place the flag above the stack pointer so let's place a breakpoint before that instruction and print stack contents in strings.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/strings/Images/Screenshot_20200930_062524.jpeg)

Wowiee that looks like flag let's enclose between the darkCTF{} as per in the description

The flag for the challenge is darkCTF{wah_howdu_found_me}


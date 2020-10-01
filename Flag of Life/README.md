Writeup for Flag of Life Misc challenge:

Description for the challenge:

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/Flag%20of%20Life/Images/Screenshot_20201001_140826.jpeg)

Frankly I was not able to get any idea from the challenge description.

They gave us a netcat link for the challenge let's connect to the challenge server and see what we can find about the challenge.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/Flag%20of%20Life/Images/Screenshot_20201001_140945.jpeg)

Okk it's just ask for our name.Let's give a name and proceed the challenge.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/Flag%20of%20Life/Images/Screenshot_20201001_141058.jpeg)

The demon guard flageon says we have to give a key with a certain shape and size.The hint is the shape of the key is square.The problem is the device needs the edge length as input to make the key.And we have only 3 tries.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/Flag%20of%20Life/Images/Screenshot_20201001_141325.jpeg)

Let's try a sample number 100 and see what is the output.The output turned out to be "The size of your key is off by 10000 sq cm." wait it just squared the number and states we are at a distance of 10000 sq cm from the input length ...If we give zero then our size of key is off by 0 sq cm which would give us the flag.So lets give 0 and take the flag home.Okk 0 given and enter key pressed ..Wait whattt "Device only takes positive integers as input" we can't give 0 .

Okk let's try the number 2^32 = 4,294,967,296 because int has 32 bits giving this value would occur a data type overflow and the where all the bits of the variable changes to 0 and a overflow bit containes 1 which would not matter.Okk lets give 4,294,967,296 as input and get our flag...It does not produce any output did the program crash ..

Oh Man i forget about the fact that our key is getting squared and squaring this huge value can cause problems sometimes and crashes the problem.The thing is we have to get the value 4,294,967,296 after the squaring ocurred means the input should be square root of 4,294,967,296.. I am bit lazy let's use a online square root calculator to get the square root.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/Flag%20of%20Life/Images/Screenshot_20201001_150521.jpeg)

The square root of 4,294,967,296 is 65536.Let's give this as input to the challenge server and get the flag.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/Flag%20of%20Life/Images/Screenshot_20201001_150915.jpeg)

Hoorah!!! Our calculations were correct by giving input as 65536 and squaring this value caused a data type overflow which zeroed out all 32 bits and outputtted the flag for the challenge..

The flag for the challenge is darkCTF{-2147483648_c0m3s_aft3r_2147483647}


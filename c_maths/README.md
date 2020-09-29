Writeup for the C_maths challenge:

The description for the c_maths challenge writeup is:
![alt text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_131000.jpeg)

Ok from the description the information we can get from the challenge is flag is dispersed into 3 parts ,wen need to know some maths and C programming to crack this challenge and the flag resides in a server.They gave a netcat link and the copy of binary to us for reverse it..

The steps I always use to analyze and reverse the binary is:-

  1.Run the binary first to get information about the data type of the input the binary accept from the user.
  
  2.Strings command to check the printable strings in the binary if it is a easy challenge you will be fortunate enough to find the flag in here.
  
  3.Ltrace the binary to find the library calls it's making to libc this is helpful when strings functions are used for processing the input or string comparing the flag with the user input and also strace can be useful sometimes which outputs the system calls done by the binary.
                             
4.Then the  most step is to view in graph mode in a nice debugger I use IDA freeware or Cutter(radare2's GUI version) and analyze the function flow of the binary and see how the input is processed and compared.

5.Then poceed to debug the binary by setting breakpoints and single stepping instructions and try to get more information of the binary most of the time many will get enough information about the binary to get the flag but if ida's graph seems to be complex then you need to put the binary file in decompiler to get more information about the binary and the debug the program. I use Ghidra's decompiler which is partially good.

6.I am sort of a old school person so I use GDB to debug the program.

7.Then it is happy reversing to get the flag.

Okk now let's proceed to get the flag:

1.As per the steps first we are gonna run the binary file.
![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_161438.jpeg)
Okk strange it does not display anything but still lets give some input and see what is the output.
![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_162003.jpeg)
2.Okk I think it's time for step 2 the use of strings command and see its output whether can we find anything useful info about the binary or even the strings.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_162503.jpeg)

Okk i just filtered out most of the useless things from the strings output from the above image there are some really juicy information we can get:-

Some of the functions present in the binary that caught my attention is strncmp so there is a string compare going on we can find the string using the ltrace command really good,srand functions means worrying signs of random values being processed in the binary,malloc means values are getting allocated in the heap,along stack we also need to watch over the heap,system functions along with some commands present in the binary cat small chunk.txt and cat big chunk.txt and also a negative statement saying nothing for u here depicting the failure because of not providing a corect input and a filename called rev2.c that maybe the name of the source code of this binary and some user defined function names func1 and func3.There also other functions called random function and func2 which is not in the filtered image of the strings output.

3.Now the ltrace command and also with positive signs of strncmp present in the strings let's search for the string that is getting compared with the user input.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_164625.jpeg)

This writeup is totally recap of how i found the flag.So I kinda recap the mistakes the think I did u can see that strlen is called on a specific string and so i gave the same string as the output but it turned out that it compared with the string p1e8s3   .So in this time i gave the input as p1e8s3 and watched the output of the program in ltrace.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_170920.jpeg)

Okk 9 times the random function executes with starting value as 100 and ending value as 10000 and prints the value and a number of power functions and finally a sqrt and a scanf that asks for user input and maybe the input is correct it may give the second part of the flag and giving a sample 12345 gives a error message that nothing for u here and program gets terminated.

4.Due to heavy amount of maths functions lets proceed to the next step open the function in IDA.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_171728.jpeg)

Hehehe the reason for showing this image was showing it had many branches and it is necessary to see a decompiled version of the binary in ghidra before proceeding to debug the binary in gdb.

5.Fortunately in ghidra there are less number of undefineds and a near perfect source code is generated by it's decompiler.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_174359.jpeg)

The output of ghidra is not full i just removed the part till the strncmp as we found what the first part of flag

Now we have two options to make 1.analyze using ghidra output and some gdb single stepping of instructions or 2.duplicating the programing that came from ghidra's decompiler but there is a chances for error when going for this option .But still went for the second option and duplicated the program from the random function till the second scanf and the changes in my program where I created a array that stores the 9 random values that came from the binary which i gave as arguements for my program.The C program that i wrote for finding the second part of my flag was 

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_175708.jpeg)

Now let's try to take the second part of the flag.

things to do first run the binary get the random values give it as arguements for the C program we built and get the second part of the flag and give to the binary.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_180216.jpeg)

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_180201.jpeg)

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_180245.jpeg)

The value we given was right meaning the program we created did its job perfectly but the second part of the flag resides on the server on a file small_chunk.txt so lets connect to the server and repeat the same process to get the flag.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_182952.jpeg)

So the second part of the flag was _just_ and then we received a number and again asks user for a input maybe for the final part of the flag.Lets analyze again in  ghidra.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_185300.jpeg)

As a undefined in main function and also a undefined in func2 is present let's go to gdb and set breakpoint after function 3 and see heap as a malloc is present in func2.Keeping the breakpoint before the function 3 has some reasons because looping is present in func2 so placing in this position would complete the number of allocations due to looping.For beginning lets see first 100 words in heap.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_191751.jpeg)

Oh man not a single chunk present let's print 200 words from the heap and see.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_191903.jpeg)

Yeah there are some chunks and these looked like linked lists and let's try to find out the series in which the values are allocated.0x69=105,0x72=114,0x7b=123,0x81=129..Lets print another 100 chunks and find bout the series..

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_193334.jpeg)

0x84=132,0x8a=138,0x8d=141,0x93=147,0x96=150 .From all these numbers the series looks like from 100 which sum of numbers are equal to 6 and multiples of 6 then when i went on to print more chunks to find the final chunk allocated to see the end of series 

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_194937.jpeg)

The last chunk allocated was 0x181e which is 6174 
!!!!!!Note these values are always random due to presence of random function in the binary  the main intention of writeup is to describe about the binary file and how i was able to crack the challenge!!!!! The value always first allocated will always be 105 but the final value will not be 6174..

The final value 6174 whose sum of numbers is  18 which is multiple of 6 and also the last multiple of 6 before 6177 the random value given by binary and now the function 3 which sums the value present in the heap when counter value and by 1 gives zero and I dont know why but the processing of linked link starts from the second value not 6174 but the value  6165.So i created a python script to compute the sum when the binary gives a value after the second part of the flag.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_201733.jpeg)

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_202007.jpeg)

Okk we got the value for the third part of the flag ..Finallly happy tears let's submit the value to the binary and it's gonna throw a error saying that no such file or firectory exists that means success after that we have to repeat the same process to the server.Lets set breakpoint where our value is comapred lets see both the value our user input and the value by the binary.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_202341.jpeg)

okk the value in the stack is 1578057 and the value in in eax register is hex lets convert into decimal.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_202327.jpeg)

Same value there is nothing stopping us to get the flag  and lets continue the execution of the binary..

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_203352.jpeg)

Whaatttt ....Noo the compare was succeeeded then why is the nothing for u here ..That was the reaction from me when this happened what really happened is we skipped the part of time function which we can see in the decompiled version in Ghidra.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_203735.jpeg)

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_203757.jpeg)

Okk the above first image is the place where first time function where it stores the number of seconds from epoch and also on the second image the same happens and when the user input is incorrect and then it compares 5 with the difference of the first and second time variable if any one of the compare is true then it outputs nothing is here.To get the flag you need to give the input and get the flag within five seconds so let's create a another python script that connects to the server and gets the flag for us.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_205553.jpeg)

The script gonna make a socket connection send the p1e8s3 to server and get the random values from the server and compute the value by using the previously created C file to compute the value to get the second part of the flag and another python script to get the third part of the flag where both the file source images  i have given above and okk let's try the script and find out that can we get the flag atleast this time.

![alt_text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_210216.jpeg)

Finally we got the flag which is darkCTF{p1e8s3_just_give_me_the_flag}







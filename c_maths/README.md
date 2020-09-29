Writeup for the C_maths challenge:

The description for the c_maths challenge writeup is:
![alt text](https://github.com/vital-information-resource-under-siege/DarkCTF-Writeups/blob/master/c_maths/images/Screenshot_20200929_131000.jpeg)

Ok from the description the information we can get from the challenge is flag is dispersed into 3 parts ,wen need to know some maths and C programming to crack this challenge and the flag resides in a server.They gave a netcat link and the copy of binary to us for reverse it..

The steps I always use to analyze and reverse the binary is:-

  1.Run the binary first to get information about the data type of the input the binary accept from the user.
  
  2.Strings command to check the printable strings in the binary if it is a easy challenge you will be fortunate enough to find the flag in here.
  
  3.Ltrace the binary to find the library calls it's making to libc this is helpful when strings functions are used for processing the input or string comparing the flag with the user input and also strace can be useful sometimes which outputs the system calls done by the binary.
                             
4.Then the  most step is to view in graph mode in a nice debugger I use IDA freeware or Cutter(radare2's GUI version) and analyze the function flow of the binary and see how the input is processed and compared.

5.Then poceed to debug the binary by setting breakpoints and single stepping intsructions and try to get more information of the binary most of the time many will get enough information about the binary to get the flag but if needed more information you need to put the binary file in decompiler to get more information about the binary . I use Ghidra's decompiler which is partially good.

6.Then it is happy reversing to get the flag.

Okk now let's proceed to get the flag:

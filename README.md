# A Java Logic Error with System Out Print, exposed with Ghidra
A demonstration, using Ghidra, that System Out Print in Java causes a logic glitch that bloats Java Bytecode. 

Ghidra Java C Bytecode Compiler Glitch 

TL; DR JAVA ASSIGNS A VARIABLE TO A PRINT STREAM OBJECT BEFORE EVERY SINGLE SYSTEM.OUT.PRINT STATEMENT, DOUBLING ALL SYSTEM.OUT.PRINT LINES IN BYTECODE. THIS CAN BE FIXED BY DECLARING A PRINTSTREAM OBJECT YOURSELF.

![alt text](https://raw.githubusercontent.com/mrvirus9898/Ghidra_Java_Glitch_SystemOutPrint/main/SystemPrint%20Demo/SystemPrint%20Picture%201.PNG)
![alt text](https://raw.githubusercontent.com/mrvirus9898/Ghidra_Java_Glitch_SystemOutPrint/main/PrintStream%20Demo/PrintStream_Demo%201.PNG)

Requirements to reproduce:
Java installed on computer
Ghidra installed on computer

Versions used for this report </br>
Java 1.8.0_321 </br>
Java SE Runtime Environment build 1.8.0_321-b07 </br>
Java HotSpot 64-Bit Server VM build 25.321-b07, mixed mode </br>
javac 17.0.2 </br>
Ghidra Version 10.1.2 Build PUBLIC

Steps to reproduce
1) Create Java file
2) Add multiple System.out.print statements to the file
3) Compile .Java file to .Class file
4) Add and Open .Class file in Ghidra
5) Analyize the .Class file with Ghidra, and select Main method.
6) You will see "pPVar1 = System_out;" before every previously written ".print" statement. 
7) Close .Class file
8) Record the file size of the .Class file
9) Remove .Class file from Ghidra, and close Ghidra
10) Return to .Java file
11) Add Import PrintStream
12) Add PrintStream terminal;
13) Set terminal to System.out
14) replace all "System.out.print" statements with "terminal.print" statements
15) Compile .Java file to .Class file
16) Add and Open .Class file in Ghidra
17) Analyize the .Class file, and select Main method.
18) You will no longer see duplicate "pPVar1 = System_out" statements.
19) Record the file size of the .Class file
20) The new file size will be less then the old file size, but the program will still run.

The "SystemPrint Demo" Folder has example code, .Java, .Class, and .C files consistent with steps 2-9 </br>
The "PrintStream Demo" Folder has example code, .Java, .Class, and .C files consistent with steps 11-17 </br>

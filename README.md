# A Java Logic Error with System Out Print, exposed with Ghidra
A demonstration, using Ghidra, that System Out Print in Java causes a logic glitch that bloats Java Bytecode. 

Ghidra Java C Bytecode Compiler Glitch 

TL; DR JAVA ASSIGNS A VARIABLE TO A PRINT STREAM OBJECT BEFORE EVERY SINGLE SYSTEM.OUT.PRINT STATEMENT, DOUBLING ALL SYSTEM.OUT.PRINT LINES IN BYTECODE.

Requirements to reproduce:
Java installed on computer
Ghidra installed on computer

Versions used for this report
Java 1.8.0_321
Java SE Runtime Environment build 1.8.0_321-b07
Java HotSpot 64-Bit Server VM build 25.321-b07, mixed mode
javac 17.0.2

Steps to reproduce

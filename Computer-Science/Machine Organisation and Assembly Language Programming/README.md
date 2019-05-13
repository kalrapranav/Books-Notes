# Machine Organisation and Assembly Language Programming

## One's Complement
Negative number is simply represented by Flipping all the bits of the positive Number
0 -> 1 || 1 -> 0    
10 = 0000 1010  **&** -10 = 1111 0101  
In this method two zeros occu as 0000 0000 -> 1111 1111 will be 0 and -0

## Two's Complement
Thsi method eliminates the problem of two zeros and also makes addition/subtraction easier and efficient
0 -> 00  
1 -> 01 **||** -1 -> FF  
2 -> 10 **||** -2 -> FE  
As, we can see that for every number less than 0 that number the positive representaion of the number is subtracted from 00. 
00 - 02 = FE || -x = FF - (x-1) 
### Convert Binary to its Two's Complement negative form
Flip all the Bits and add 1 to it  
10 = 0000 1010 **||** -10 = 1111 0101 + 1 = 1111 0110
So, 10 + (-10) = 0
0000 1010 + 1111 0110 = 0000 0000

### Range of value for diffrent datatypes

| Size            | Range of Values  | Range in Hex    |
| :------------- | :----------:     | -----------:    |
|  Byte          |  -128...127      | 80...7F          |
|  Word          | -32,768...32768  | 8000.7FFF     |
| Longword       | -2,147,483,648...2,147,483,647 | 8000 0000...7FFF FFF \|

#### Some Observations: 
* Non-negative numbers always start with 0 (binary)
* Non-negative number always start with 0..7 (hex)
* Negative number always start with 1 (binary)
* Negative number always start with 0..7 (hex)

Write about connversion later 

## First Steps in Assembly Language Programming
We will be using bsvc simulator system for running our porgrams 

Assembly langauge code is divided into four sections: 
* Comments/Documentation
* Assembler and Macro Pre-processor directives
* The Code
* Storage Allocation

All programs must begin with Comments/Documention block  
Comments in the assembler begin with \* or ;  
**Register Use** block is used to document the registers used in the program  
Setup info is used by allocate the memory area in the assembler adn also set teh address, wehere the executable instruction will be loaded into the memory. 

![1](https://user-images.githubusercontent.com/19777060/57579321-33189c00-744f-11e9-8798-1c292ef1a30f.PNG)

**#minclue** import the I/O and error handling marcos

![2](https://user-images.githubusercontent.com/19777060/57579366-ac17f380-744f-11e9-9923-2b32c61d7679.PNG)  

begins with **start:**  
**initIO** macro initializes the I/O for teh system
when the **break** instruction is encountred teh excution is halted
Machine instructions are not **not case sensetive** 

![3](https://user-images.githubusercontent.com/19777060/57579435-88a17880-7450-11e9-95f5-f9ba0fad6ee9.PNG)

In assembler the formating of code is required and consist of four columns  
**First Coloumn** is for labels or comments only
**Second Coloumn** is for Instructions 
**Third Coloumns** is fr operands  
**Fourth Colummns** is optional and is for comments   
The space btw two coloumsn must me more than a space or a tab  

![4](https://user-images.githubusercontent.com/19777060/57579442-aa026480-7450-11e9-897d-07e08f19fbc3.PNG)

### Labels 
Only the first 8 character in a label are siginificant as the assembler ignores after that  
Thus my_label1 and my_label2 would be treated as same  
You can't have duplicate labels in your code 
The value for labels are their addresses  
They should always ebnd with a colon

### Instructions 
Most instructions are size specific   

![5](https://user-images.githubusercontent.com/19777060/57579495-71af5600-7451-11e9-84bf-ba9a12d1ce3a.PNG)

For size specific instructions, if the size is ommited then usally it is a word. So, move and move.w will be same. 

![5](https://user-images.githubusercontent.com/19777060/57579509-c2bf4a00-7451-11e9-8b10-3bb41c4962b3.PNG)

### Operand 
The Operand feils must have either one or two and they should be comma sperayed without a space btw them 

**Storage Allocation** should be done after the break instruction

![1](https://user-images.githubusercontent.com/19777060/57579558-f189f000-7452-11e9-8e07-a1f03b0ac3fd.PNG)
![2](https://user-images.githubusercontent.com/19777060/57579578-3e6dc680-7453-11e9-80ad-6dda7a22366a.PNG)

---
## The Bus & Memory
All communicatiob btw the CPU and memory, as well as peripherals devices, occur though the bus. 
The bus is a collection of parallel data and signal lines that is divided into three component: 
* Address bus (24 bits)
* Data Bus 
* Control Bus   
![3](https://user-images.githubusercontent.com/19777060/57582159-1e033380-7476-11e9-934d-a93262a0ea10.PNG)

#### The Address Bus 
Physical memory in a computer system (RAM) can be though as an array of bytes starting at 0.  
For readind and writing of data we need to provide the location of the address (as idx in a array).  
The address must be placed on the address bus befire executing the operation.  
**M6800 CPU** has a 24 bit address bus -> address are limited to 24 bit value

![4](https://user-images.githubusercontent.com/19777060/57582230-06787a80-7477-11e9-8e7b-6cce9c7d1ff1.PNG)

#### RAM Quantities
The amount of the RAM that can be installed in a system depends on the size of the address bus.  
M6800 having 24bit address means it has 2^24 possible address available.  

16 \* 1MB  
![1](https://user-images.githubusercontent.com/19777060/57582295-a7ffcc00-7477-11e9-8655-ff5fa88e749b.PNG)

**Example:** The Intel pentium family of CPU's has a 32-bit address bus. What is the maximum amount of RAM that can be installed in such system?    
2<sup>32</sup> = 2^2 \* 2^30 = 4 \* 1GB = 4GB (as, 2^30 = 1GB)  \[max memory]\
![2](https://user-images.githubusercontent.com/19777060/57582384-04172000-7479-11e9-9c76-b0fd60add7cc.PNG)

#### Address Ranges  
Address are given in binary, (usally) hexadecimal but never in decimal.  
The address 0 is always the first byte in the memory.   
To find the last byte in the memory, we must take a quantity of RAM, express it in KB, MB, GB and convert it in hex and subtract 1 from it (as memory starts a 0).    

**Example:** Give the range of valid address for M6800 system configured with 16MB RAM  
16 MB = 16 * 1MB  = 16 * 2^20 = 2^4 * 2^20 = 2^24 = 16^6 = 1000000 - 1 = 00FF FFFF  (for 16^x in hex it will represented as 1 follwed by x zeros)   
![3](https://user-images.githubusercontent.com/19777060/57582471-1776bb00-747a-11e9-815e-fcaa197a718a.PNG)  

#### The Data Bus  
The data in the memory of M6800 is recived in 16-bits as it is 16bit wide.   
So, to fetch a longword it is a two step process.   

#### The Control Bus
![4](https://user-images.githubusercontent.com/19777060/57582539-c5826500-747a-11e9-8946-791b0d3fa6b0.PNG)

## Addressing Memory and Register Contents
#### Byte Order
![5](https://user-images.githubusercontent.com/19777060/57582565-1b570d00-747b-11e9-9a54-6c4fc4f3342e.PNG)

![2](https://user-images.githubusercontent.com/19777060/57582585-4e999c00-747b-11e9-9a80-44c4af805910.PNG)

#### Registers
They are the high speed memeory location in CPU adn being in CPU makes them faster to access than accessing RAM.   
M6800 has 15 general purpose registers: 8 for data **[D0-D7]** and 7 **[A0-A6]** for addresses.  
![3](https://user-images.githubusercontent.com/19777060/57582635-1cd50500-747c-11e9-9506-cc56cdfbec8c.PNG)  

Instructions only over-write the postion of the size of the register, as a byte instruction will only over-write byte size of the register and word will overwite only the word size.   
**Byte:**  0000 00XX
**Word:**  0000 XXXX  
**Long Word:**  XXXX XXXX  

alpha: dc.l $01234567  
![4](https://user-images.githubusercontent.com/19777060/57582698-b8ff0c00-747c-11e9-9b8d-ec0176cba057.PNG)
![1](https://user-images.githubusercontent.com/19777060/57582715-df24ac00-747c-11e9-94cf-290231b1317d.PNG)
![2](https://user-images.githubusercontent.com/19777060/57582723-f2d01280-747c-11e9-8ae2-2c9d2d36f862.PNG)

![3](https://user-images.githubusercontent.com/19777060/57582737-26ab3800-747d-11e9-8ec6-922c65b66992.PNG)
---

## Addressing Modes
![4](https://user-images.githubusercontent.com/19777060/57583144-6d4f6100-7482-11e9-8ea3-d66327daa609.PNG)

#### Intermediate #N
It is used to specify constants-hard coded numbers.   
The operand must me preceded y #.   
move.w  #2,D1  

#### Absolute Long <ea>  
The operand is a 32 bit number representing the address in the memory to be accessed. 
  ![5](https://user-images.githubusercontent.com/19777060/57583222-2746cd00-7483-11e9-976b-ed86b024bdd5.PNG)

![1](https://user-images.githubusercontent.com/19777060/57583234-4a717c80-7483-11e9-8459-0d1c31014930.PNG)

![2](https://user-images.githubusercontent.com/19777060/57583252-6f65ef80-7483-11e9-9ae5-e3d11e111815.PNG)  
![3](https://user-images.githubusercontent.com/19777060/57583284-dd121b80-7483-11e9-809c-69b96d917d21.PNG)

![1](https://user-images.githubusercontent.com/19777060/57583302-0cc12380-7484-11e9-9467-5e263607c70b.PNG)  
![2](https://user-images.githubusercontent.com/19777060/57583316-2b271f00-7484-11e9-9b77-b03a16e9bda6.PNG)

---
## Labels vs Variables 
There are no variables in Assembly Language as labels are storage allocated not memory locations.   
In higher level langugaes the system keeps the tracks of **tye, size, location** of the variable.  
But in Assembly Language the programmer have to keep the track of these three. 

In Assembly labels associated with each other unlike higher level language being unrealted. 
![3](https://user-images.githubusercontent.com/19777060/57583427-5eb67900-7485-11e9-9bd0-38d256a62406.PNG)  

## Bitwise & Logical Operators 
**Byte addressable computer** have memory organised in bytes , group of 8 bits making one indivdivisible unit.   
Instructions take place on one of thre support sizes: **byte, word(2 bytes), long(4 bytes)**  
In the case of TRUE=1 and FALSE=0 bits are taken as a sigle peince not a unit of 8.  

![4](https://user-images.githubusercontent.com/19777060/57584291-50b92600-748e-11e9-88ea-570ea414c4ad.PNG)

#### Shift Operators
![5](https://user-images.githubusercontent.com/19777060/57584556-bd81ef80-7491-11e9-9024-be4276c376a4.PNG)

**Example:** byte x = 3; x = x << 1; System.out.print(x); || **Output:** x = 6
![1](https://user-images.githubusercontent.com/19777060/57584611-44cf6300-7492-11e9-880d-f2b64092dda4.PNG)
![2](https://user-images.githubusercontent.com/19777060/57584613-46009000-7492-11e9-9c2c-42c7ea12ecc2.PNG)

![3](https://user-images.githubusercontent.com/19777060/57584614-4731bd00-7492-11e9-8328-8535cea7a35a.PNG)





























  

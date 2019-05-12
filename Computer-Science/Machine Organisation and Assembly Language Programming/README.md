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



















  

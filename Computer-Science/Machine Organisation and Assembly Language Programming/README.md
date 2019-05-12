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
****
















  

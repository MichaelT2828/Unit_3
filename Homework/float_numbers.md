# Why doesn't 0.1 + 0.2 = 0.3?

### Initial problem

If we enter the following code into a python terminal, somehow the result is False.

<img width="219" alt="equation" src="https://user-images.githubusercontent.com/89366878/162236540-c772bfda-befe-49d1-a5e0-537d2fb9c140.png">

### Floating point numbers and arithmetic

Floating point numbers are essentially scientific notation, representing any whole number with a decimal point (For example, 5 is an integer, while 5.1 is a floating point number). Floating point arithmetic allows for huge range, as floats can easily be represented accross large decimal differences (hence the name "floating", as the decimal can "float" to a wide range of positions)<sup>[[1]](https://www.freecodecamp.org/news/floating-point-definition/#:~:text=A%20floating%20point%20number%2C%20is,float%22%20to%20any%20position%20necessary.)</sup>. For example, take a very small number, 9.25 x 10^-53. Scientific notation allows it to be represented in very few characters, but if the number was something like ...925340934... all those other digits would be left out. However, the majority of scientific, mathematic and engineering tasks do not care much about those slight inconsistencies, as long as the position of the 9.25 in the long string of digits is correct<sup>[[2]](https://softwareengineering.stackexchange.com/questions/260566/why-are-floating-point-numbers-used-often-in-science-engineering)</sup>.

### Representation of numbers in binary format

The reason why floating point numbers are important in understanding this simple math equation is the conversion between base 10, the number system we are all familiar with, and base 2, or binary which computers use. In base 10, the number scale for digits goes like so: ... 100, 10, 1, 0, 1/10, 1/100 1/1000 ... to represent 0.1 is simple and exact. However, in base 2 0.1 is represented with recursion, an infinite sequence of 0.0001100110011... Computers use floating point numbers, which means they represent numbers in scientific notation with base 2, meaning they would represent 0.1 as this long binary string of numbers, times 2 to the power of something. The problem lies in recursion, as computers aren't human, and don't intuitively know when to round. For example, 1/3 + 1/3 + 1/3 to a human working in base 10 would be a simple equation, resulting in exactly 1. However, to a copmuter this equation can be shown as something like 0.333... + 0.333... + 0.333..., which would become 0.999..., stopping only when it runs out of digits<sup>[[3]](youtube.com/watch?v=PZRI1IfStY0)</sup>.

### 0.1 + 0.2

Similarly to the previous example, adding 0.1 and 0.2 for a computer would not be so simple, as it would take the binary string of numbers that creates 0.1 in base 10, add that to the binary string of numbers that creates 0.2, and find that it runs out of digits to solve an infinite string of digits. Therefore, the tiny difference where it cuts of at the end of its calculation between the addition of 0.1 and 0.2, and 0.3, tells the computer the two numbers aren't quite the same, and returns False<sup>[[3]](youtube.com/watch?v=PZRI1IfStY0)</sup>. To prove this, the following python code will return the addition of 0.1 and 0.2:

<img width="183" alt="addition_proof" src="https://user-images.githubusercontent.com/89366878/162236390-1fe604f9-4107-4d84-b7e6-540c27f933f3.png">

### Solution

While default floating point arithmetic will not execute the desired calculation and give the proper answer, this problem can simply be solved by rounding the answer, which would negate the issue of the long string of digits that causes the issue. The python code for this problem is as such:

<img width="291" alt="fixed_equation" src="https://user-images.githubusercontent.com/89366878/162236686-84c80eee-0aa6-4a54-861a-a96e73a3dcd0.png">

### Citations

1. freeCodeCamp.org. “Floating Point Definition.” FreeCodeCamp.org, FreeCodeCamp.org, 28 Apr. 2021, https://www.freecodecamp.org/news/floating-point-definition/#:~:text=A%20floating%20point%20number%2C%20is,float%22%20to%20any%20position%20necessary. 

2. DoubleDoubleDoubleDouble                    59311 gold badge55 silver badges1111 bronze badges, et al. “Why Are Floating Point Numbers Used Often in Science/Engineering?” Software Engineering Stack Exchange, 1 Aug. 1962, https://softwareengineering.stackexchange.com/questions/260566/why-are-floating-point-numbers-used-often-in-science-engineering. 

3. Computerphile, director. YouTube, YouTube, 22 Jan. 2014, https://www.youtube.com/watch?v=PZRI1IfStY0. Accessed 8 Apr. 2022. 

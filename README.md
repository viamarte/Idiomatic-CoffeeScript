# Idiomatic-CoffeeScript

## Purpose

Idiomatic CoffeeScript is a set of best practices in CoffeeScript programming. This project is inspired
in Idiomatic JavaScript by @rwldrn.

So this also serve as a programming style guide, which is useful for team development,
so everyone can code in the same manner.

As said on the Idiomatic JavaScript: "All code in any code-base should look like a single person typed it, no matter how many people contributed",
and that's absolutely true. So this guide purpose is to apply that concept in CoffeeScript codes.

Important: In order to make this guide simple to follow it doesn't offer options and paths as the Idiomatic JavaScript does, if you want you can
fork this guide and customize it to fit your tools and style.

## How to use

Link this document refering it as the style guide for your project, so anyone know how you code.
The styling guide should be the first thing you define in your project, after it is done everything must be based on it.

## Remember what is CoffeeScript

Always remember: CoffeeScript is just JavaScript. It is not a new language, it is just a cool tool you can use to improve readability of your code.
You should use it wisely otherwise you could end up generating terrible JS. This guide will help you get an idea of the path you need to follow to get the most out of CoffeeScript.

Reading [this article](https://github.com/raganwald/homoiconic/blob/master/2011/12/jargon.md) is strongly recommended to get an idea on what CoffeeScript is. Also, this guide assumes that you already know you to use CoffeeScript. If you are a rookie please skip to this section where there are some CoffeeScript learning resources. This clarified we can proceed with the guide.

## Style guide

### 1. Regarding line writing:
	* Use 2 spaces to indent, you can also convert tabs into 2 spaces (Sublime Text 2 and other code editors allows this);
	* The maximum line length is 72 characters;
	* Don't leave trailing spaces;
	* Use one blank line to separate functions;
  * Leave one blank line at the end of the code;
	* Don't use blank lines to separate lines within the same function.

### 2. Regarding string usage:
  * Always use double quotes in strings;
  * Break long strings, CoffeeScript supports multi-line strings;
  * Use CoffeeScript string interpolation instead of concatenation.

### 3. Regarding comments:
  * Use single line (#) comments most of the time;
  * Just use multi line comments (###) on the header which contains information about the file.

Example:
	
  ```coffeescript

  add = (num1, num2) ->
    num1 + num2

  result = add 1,2

  #Breaking line because string has more than 72 characters
  string = "We performed a sum between 1 and 2 and the result
   is #{result}"
  ```

### 4. Use CoffeeScript peculiarities on your favor
  * Make use of the implicit return syntax in your projects;
  * When you have to pass a variable number of arguments to a function, use splats;
  * Instead of executing simple functions in loops use object or array comprehensions;
  * Don't use object or array comprehensions for complex stuff, it makes it hard to read;
  * Make use of closures created with ```do``` when building your modules;
  * Don't use parenthesis in function calls unless completely necessary;
  * Use CoffeeScript boolean's flexibility to improve readability;
  * Use CoffeeScript existential operator;
  * Don't use commas when writing long literal array and object notations, instead, add line breaks at each node.


Example:

  ```coffeescript
  #Using closure, you can add parameters here as well
  do ->
    
    #Array declaration without commas
    pilots = [
      "Senna"
      "Alonso"
      "Schumacher"
      "Vettel"
      "Hamilton"
      "Barichello"
    ]

    #Sample podium function, showing how you can use splats,
    #string line breaks, string interpolation and implicit return
    podium = (fisrt, second, third, rest...) ->
      "Gold Trophy: #{first}, Silver trophy: #{silver}, Bronze trophy:
       #{bronze}. Contenders: #{rest.join ","}"
    
    #Calling a function with splats
    podium pilots...

    #A more friendly aproach to boolean values.
    #No need to use splats here, I just use to reuse the elements I
    #already had.
    didSennaWin = (first, pilots...) ->
      if first is "Senna" then yes else no
  ```

### 5. Simplify complex code with classes and modules
  * Use CoffeeScript classes when apliable
  * Classes create closures
  * Classes are inheritable
  * Classes are reusable

## Development process

### 1. Code quality
  * Always lint your CoffeeScript code, you can use CoffeeLint;
  * Do not use lint the JS generated by CoffeeScript, instead, lint your CoffeeScript as said above;

### 2. Write tests
  * You should write automated tests for your CoffeeScript app;
  * Test your CoffeeScript code directly, Mocha is a good option;
  * If you need a browser environment, use PhantomJS with Mocha.

### 3. Compile your CoffeeScript
  * Always compile your CoffeeScript to JS, never use CoffeeScript code directly. Unless your are write a CoffeeScript web transpiler or something like that;
  * You can use the CoffeeScript node module itself to compile .coffee files.

### 4. Minify your JS
  * Use Ugilify JS or YUI Compressor to do this.

### 5. Sketch a good build process
  * Use Grunt to setup your building process;
  * Do everything important in this process: lint, test, compile to JS, minify JS, etc;
  * It is strongly recommended the use of a continuous integration server, Travis CI is an excellent option if you use GitHub.

## The best learning resources

Learning more about CoffeeScript is always nice, here are listed some great resources to get started with CoffeeScript or, if you are already experienced with it you can learn some good tips and tricks you can use in your code.

### Books and other textual resources

* [CoffeeScript Cookbook](http://coffeescriptcookbook.com/)
* [Smooth CoffeeScript](http://autotelicum.github.com/Smooth-CoffeeScript/interactive/interactive-coffeescript.html)
* [CoffeeScript official website](http://coffeescript.org/)
* [Testing with CoffeeScript](https://efendibooks.com/minibooks/testing-with-coffeescript)

### Screencasts

* [Introduction to CoffeeScript](http://screencasts.org/episodes/introduction-to-coffeescript)
* [Peepcode CoffeeScript screencast](https://peepcode.com/products/coffeescript)

### Slides

* [CoffeeScript - take a sip of code](https://speakerdeck.com/tsironis/coffescript-take-a-sip-of-code)
* [CoffeeScript - Six reasons and a movie](https://speakerdeck.com/tsironis/coffescript-take-a-sip-of-code)

### Virtual courses

* [Codeschool CoffeeScrip course](http://www.codeschool.com/courses/coffeescript)
* [Tuts+ CoffeeScript course](https://tutsplus.com/course/cleaner-code-with-coffeescript/)

## Author

This guide is being written by Matheus Kautzmann and it is always changing. This repo is always open to contributors, so if you disagree of something present in this document or want to add an important thing to it feel free to make a pull request or open an issue.

## License

This project is under MIT License.

The MIT License (MIT)
Copyright (c) 2013 Matheus Kautzmann

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
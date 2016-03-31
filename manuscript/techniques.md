# Techniques


## Input/Output Analysis 

The IO Analysis will be the starting point for most of your experiments working with smaller functions.  It is intended to help you (1) break down the different steps within an algorithm (2) better reason on how to write code that transitions your data from step to step.

Most functions are sole objective is to transform data from one format into another.  And because computers are methodical, specific instruments, we should be able to see the transformation take place every step of the way.  The IO analysis is all about understanding the format that you data arrives in, or the `input`, and the format that your function is expected to return, or the `output`.   Once we understand these two boundaries, we can then begin analyzing each step that needs to take place in between, and how to transform our input accordingly.

Imagine baking a cake.  We have the ingredients, or `inputs`, the cake which is the `output`, the recipe, which is supposed to tell us how to get from ingredients to cake, and finally, we have our labor.  Our labor is going to be applied to the ingredients according to the recipe and we should arrive at a cake.  

Commonly, we understand the inputs and the outputs.  We now we needs eggs, flour and sugar, and we obviously know we want a cake, but we don't have a recipe.  Could we think about the different states that the ingredients need to pass through in order to transform them into a cake?

Assuming we know nothing about baking, we guess that the ingredients that have been listed need to be mixed together somehow.  So we identify immediately that the ingredients need to be combined into one.  And thus we can say that our cake is going to take an intermediate state, "batter."   We know that we might be wrong about this.  But trial and error are the only way to find out.  So we continue.  We now have a chain of states: ingredients --> mixture --> ? --> cake.

Next, we know we need to turn this cake batter into a cake.  Let's take another guess. We know people say "bake a cake," and we know that baking takes place with heat, so why not heat up our batter?  Sounds logical.  So we put our cake into the oven at 350°.  We check it a bunch of times.  After some time it is a cake.  Hurrah! Mission Accomplished.  


Tons of variables that we may have gotten wrong.


## Start and EndPoint Analysis

This Start/Endpoint analysis is much like the IO Analysis above, but designed to be used are larger parts of your application.  If there is functionality that touches several files, then this is the analysis that you should use.  
First, try to identify the files that mark boundaries of what you are trying to accomplish.  

If you are working within Rails, perhaps this means a particular view file that contains a form.  Next you will want to identify the endpoint boundary for what you are building or debugging.  There must be a controller file in between and perhaps there are models or other classes that are referencees in the controller file.
Try to visualize the chain of files.  

Like a train, each file can be a car.  The car performs some sort of action, and then it is coupled to the next car.  You need to ensure that both the car and the coupling are working every step of the way.  Each of these can perhaps be tested by the more precise I/O analysis.

## Start with 'puts'

`puts` and `console.log` are useful for testing your assumptions.  As you should already know, we use them to print to the log or console.  They are the most primitive method of debugging and therefore the easiest to implement.  When you are thinking about how the system works, you are changing data in one way or another at each of the steps.  The more steps between the starting point and the behavior that you are expecting, the more places for your bug to live.  
The success of each of these is an assumption until you have printed these values or return values to the console and can verify that what you think you know is in fact so.


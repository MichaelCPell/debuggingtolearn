#Case Study I: FizzBuzz

##Introduction

I will begin by applying the scientific method to a classic, simple FizzBuzz project.  We start with something like:


		Description:

		Return an array containing the numbers from 1 to N, where N is the parametered value. N will never be less than 1.

		Replace certain values however if any of the following conditions are met:

		If the value is a multiple of 3: use the value 'Fizz' instead
		If the value is a multiple of 5: use the value 'Buzz' instead
		If the value is a multiple of 3 & 5: use the value 'FizzBuzz' instead

and we have a function to the tune of 


	def fizzbuzz(input)
		#Your Code Here
	end

And finally something that looks similar to a spec:

	# if input is 10,
	output is [1,2,'Fizz',4,'Buzz','Fizz',7,8,'Fizz','Buzz'];


## State Your Goal:

My goal is to take a single integer and return an array of values according to the rules of FizzBuzz.

## Understand Current Status:

The function takes one argument, which I know to be an integer.  It does nothing else, and returns nothing.

## Form a Hypothesis:

I need to loop through all the numbers from 0 to whatever the input number is, and convert some of them according to the rules.  I expect I am going to use an `if` statement and a `loop`, though other than that I don't really know much.


## Minimum Viable Trials


### Trial 1:
Can I get it to return an array?


	def fizzbuzz(input)
		array = []
	end

returns:

`[]`

Simple enough.

### Trial 2:

Now let me see if I can return an array with the right fizzes...

*::time passes::*

Couldn't think of what to do... *Simplify*  Maybe I can return array of numbers 1 to `input`.  *::Looks up for loop on google*  I didn't find a `for loop`, but I did find a `while`.  Let's try it.


	def fizzbuzz(input)
		array = []
		num = 0
		while(num < input) do 
			num
		end
	end

But this runs forever... what am I doing wrong?  *::studies code for awhile::*  Oh, num is never increasing and therefore it just runs forever.

	def fizzbuzz(input)
		array = []
		num = 0
		while(num < input) do 
			num = num + 1
		end
	end

But I'm still getting `nil`.  *::thinks critically about the code::*  Well `array` is supposed to be changing, what if I put a `puts` in the loop to make sure that it is?
	
	def fizzbuzz(input)
		array = []
		num = 0
		while(num < input) do 
			num = num + 1
			puts array
		end
		array
	end

It looks like `array` isn't changing at all on each run of the loop.  Where is my code that does that?  Oh, it doesn't exist.  Let me add it.

	def fizzbuzz(input)
		array = []
		num = 0
		while(num < input) do 
			array << num
			num = num + 1
		end
		array
	end

*Output if input is 10:*

[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

nice!  Now this is much easier to write and describe here than the thinking that is required to make it happen. For a learner, this might take incredible amounts of critical thinking in order to get it accomplished.  That said, if we use a system and follow our rules, then we should be able to make the most of critical thinking capacity and always push our knowledge towards the answers that we are looking for.

Before we move on here, we know that we want numbers starting at 1, and going to the input number.  So let's make some adjustments:

	def fizzbuzz(input)
		array = []
		num = 1
		while(num <= input) do 
			array << num
			num = num + 1
		end
		array
	end

### Trial 3:

**Can I replace just the multiples of 3 with "Fizz"?**

This is what I set out to do earlier but realized that I had a smaller problem that I would need to solve.  I know I am going to need to find out which numbers are multiples of 3.  But I don't know how to do that yet.  So instead of finding out how to do it inside the rest of the problem, let me just try it in console.  

First I google "ruby determine multiples of number" and discover the `%` operator.  It returns the remainder of a division.  Basic math tells me that if the remainer of a division is 0, then that number is a multiple, so:

	irb> 5 % 3
	 => 2 
	irb> 6 % 3
	 => 0 

Cool, now let me try to bring that in to my code:

	def fizzbuzz(input)
		array = []
		num = 1
		while(num <= input) do 
			if(num % 3 == 0)
				array << "Fizz"
			else
				array << num
			end

			num = num + 1
		end
		array
	end

Output if input is 10:

	["Fizz", 1, 2, "Fizz", 4, 5, "Fizz", 7, 8, "Fizz"]

Looking good!  


### Trial 4:

**Can we make our final product?**

Let's do our 'Buzz' and 'FizzBuzz' rules:

	def fizzbuzz(input)
		array = []
		num = 1
		while(num <= input) do 
			if(num % 3 == 0)
				array << "Fizz"
			elsif(num % 5 == 0)
				array << "Buzz"
			elsif(num % 5 && num % 3 == 0)
				array << "FizzBuzz"
			else
				array << num
			end

			num = num + 1
		end
		array
	end


	Output if input is 10:

	[1, 2, "Fizz", 4, "Buzz", "Fizz", 7, 8, "Fizz", "Buzz"]

Great, we have done it!  These are the correct values!

Let's check our work for a greater number, 15:

	[1, 2, "Fizz", 4, "Buzz", "Fizz", 7, 8, "Fizz", "Buzz", 11, "Fizz", 13, 14 , "Fizz"]

Uh oh, 15 is wrong.  It should be "FizzBuzz" but we are getting "Fizz".  *::We look at it for awhile::*, but we can't figure out why it is happening. 

### Trial 5:

Let's try using `puts` to find out what's going on.

	def fizzbuzz(input)
		array = []
		num = 1
		while(num <= input) do 
			puts "num: #{num}"
			if(num % 3 == 0)
				puts 1
				array << "Fizz"
			elsif(num % 5 == 0)
				puts 2
				array << "Buzz"
			elsif(num % 5 && num % 3 == 0)
				puts 3
				array << "FizzBuzz"
			else
				array << num
			end

			num = num + 1
			puts "-------"
		end
		array
	end

So, we should see 3 for 15, but instead we see 1.  Why would the first `if` condition be firing when the third one is *more* true?  *::We learn that to an `if`, true is true and therefore it stops functioning on the first `if`::*  

Okay, got it, now how do I make sure that the conditions occur in the right order?  I'll try trading their places;


	def fizzbuzz(input)
		array = []
		num = 1
		while(num <= input) do 
			if(num % 5 && num % 3 == 0)
				array << "FizzBuzz"
			elsif(num % 5 == 0)
				array << "Buzz"
			elsif(num % 3 == 0)
				array << "Fizz"
			else
				array << num
			end

			num = num + 1
		end
		array
	end

Success

#  Debug to Learn: The Method

## Begin with the End in Mind

You may know this concept as a user story or the "code that you wish you had."  It means that we need to be clear about what it is that we are trying to accomplish.  Once we are clear about where we are going, we have a much clearer path on how to get there.  

**Length:** 1-2 Sentences

## Understand your current starting point.

Whenever we are about to learn something new, we need a control in order to test our experiments.  We should never let our application get to the point that it is broken and we don't know what we did to break it or how to fix it.  That means that you can use git commits or other methods of saving to ensure that you always have a clean slate to start from.  

Imagine you have a stack of firewood and a fire.  You know some of the firewood is going to burn and you also know that some will not.  If your fire is burning, you can then test parts of each log in order to determine whether or not that log will burn.  However, if your fire is dead you have no way of determining which logs are good and which are bad.  You can then try to rebuild your fire, but you have to get lucky with the wood that you try to use.  Therefore we are much better off if the fire itself can test the wood that we are going to ask it to burn.  The same is true with the application.  We cannot test if a change to our code improves or breaks our application if the application starts out at a broken state.

**Length:** 1-4 Sentences

## Form a Hypothesis

Forming a hypothesis allows you to crystalize what you already know (or think you know) and provides the embarkation point for whatever you are about to know.  This is the point where you read the documentation for whatever plugin or function that you are about to use.  You can make a brief note about how you expect it to work.  This is one of the most important steps, because it is going to frame all of our Minimum Viable Trials.


**Length:** 1-4 Sentences

## Minimum Viable Trials(MVT)

We live in the age where wisdom teaches us "do as little as you believe is possible and then seek feedback."  While at this point "Minimum Viable Whatever" might be a cliché, we will use it once again here as our primary unit of work.  The MVT is the least possible code you can write or incorporate in order to learn just a little bit more about the system or code that we are trying to understand.  


The goal of an MVT is to **shrink your problem until you naturally understand what to do next**, or you feel confident that you have some kind of idea as to what you can do next.  Once this is the case, go conduct the trial and keep a record of it.  If you succeed great.  If you don't, figure out what you learned from the failure and then use that new knowledge to make your next trial more accurate.

The MVT should:

  *  as small as possible
  *  Test something that you do not already know.
  *	 be clearly testable

The MVT Checklist:

* State what you are going to try to do and why.
* Write a conclusion.  Describe what happened when you tried this approach.
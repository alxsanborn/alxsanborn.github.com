---
layout: post
title: "Understanding Ruby Self for Beginners"
date: 2016-10-16 19:58:34 -0400
comments: true
categories: Ruby, Self, Object-Oriented Programming
---

Self is one concept I struggled with while learning Ruby class methods. I wasn't sure what self referred to. I began to realize that my understanding of self depended on understanding the contexts and purposes of self.

One thing to fundamentally understand about self: self will always call on the instance of the class.

Each time you create a new object using the class (object_1 = Class.new), (object_2 = Class.new), etc. object_1 and object_2 are instances of the class.
When each of these instances (object_1, object_2, etc.) are created, Ruby will "attach" a code/number, along with the returns of any methods in the class. (example: <Class:0x007f8de283bd88 @method_1: nil>.
Why is it useful to have the instance identifier numbers?  If you create an instance of a class that (for whatever reason) contains the exact same information for each field (ex. two instances of @first_name = "Bob" and @dinner = "lasagna"), this is a useful way for you and the computer to distinguish these separate instances. After, it is possible for two different people, both with the first name of "Bob" to eat lasagna for dinner, correct?
Uses of self:

Anytime we might want to store instances of the class. One way you might do that is in the initialize method. For example: Screen Shot 2016-08-02 at 10.10.51 PM
As you can see, in line 16, when we call the method .view_all_dogs, we return all of the instances of the class Dog created thus far (fido [line 14] & misty [line 15]). Line 6 in the initialize method is where the instance is actually stored. Line 10 provides us with a way to call this method on the class.

2. Similarly, if we need to return just the instance of the particular class, we can do the following:

Screen Shot 2016-08-02 at 10.37.31 PM

Line 19 calls the view_dog method on the instance of fido and returns it. This is denoted in line 13.

3. Whenever we need to convert an instance method into a class method. Again, referencing the first screenshot example of code:Screen Shot 2016-08-02 at 10.10.51 PM

Looking at line 9, we can see that self was added to the method. This is how we transform an instance method to a class method. It is necessary to do this because we are describing information about the entire class (the class instances of each dog).

If we try to return all instances of Dog using an instance method, we get the following error message: Screen Shot 2016-08-02 at 11.06.50 PM

"fido", as an instance of of the Dog class can call on an instance method (as in example 2 of self above), but Dog, as a class, must be paired with a class method (self.method_name). When we want to ask the class for comprehensive information about it, we must call on it as a class, rather than as an instance.

---
layout: post
title: "Python Workshop at Nairobi Innovation Week 2018"
date: 2018-03-09
categories: python
---

On the 5th and 6th of March 2018, I participated in the Python workshop organized by BotLab at the Nairobi Innovation Week 2018.
The workshop aimed at teaching the Python programming language and using it to implement a basic artificial neural network called a perceptron.
Our educator at the workshop was Kevin Nderitu, a passionate software developer.

On the first day we were introduced to the Python programming language.
The following concepts were introduced:
1. Variables.
2. Conditional statements and loops.
3. Functions.
4. Strings.
5. Lists and list comprehensions.
6. Dictionaries.
7. Tuples.
8. Object oriented programming, inheritance and polymorphism.

During the session, we were given a task to write a python program that counts the number of spaces in a sentence. This was successfully achieved.
 
On the second day, we proceeded to learn about advanced concepts in python such as abstraction, encapsulation, exception catching and multi-threading. Then after we headed for the fun and interesting part of the workshop: implementation of the perceptron.

A perceptron models a single artificial neuron. It consists of a set of inputs, each having a corresponding random weight, a bias, and an activation function that generates the output. For our case, we created a perceptron to determine whether a point (x, y) on the cartesian plane is above or below a given line. This is an example of a classification problem.

The steps for coding the perceptron is described as follows:
1. Each input (x and y) is multipied with its corresponding weight. The result is called the weighted input. The weights are randomly generated for each input. Also a bias of value 1 is added to the set of inputs to ensure that the sum of the weighted inputs is always non-zero. 
2. The sum of all the weighted inputs is determined.
3. This sum is passed as a parameter to an activation function which generates the output.
4. The activation function produces the output based on the following criteria: if sum is greater than zero, it returns 1, else it returns -1.

The above steps are defined in the feedForward method of the Perceptron class, which takes the set of inputs to the perceptron as its arguement.

The perceptron needs to be trained in order to produce the correct ouput. The definition of the training function is described as follows:
1. A guess of the output is determined using randomly chosen inputs.
2. The error is evaluated, that is, the difference between the desired output (correct answer) and the guessed output.
3. Each weight is modified based on the magitude of the error. The expression for updating the weight is as follows:
New weight = old weight + (c * error * input), where c is the learning rate.

Lastly, a helper class called Generator was created to generate the training data of size n, which consisted of randomly selected values of x and y (the inputs) together with the correct answer (whether the point (x, y) is above or below the line).

The working code for the perceptron is given below:
<script src="https://gist.github.com/huzeifa/d55e7fb91c50e9184060eb4ac8b34676.js"></script>

Attending the workshop was of great benefit to me as it gave me a jump start to learn more about artificial intelligence and also it helped me to strengthen my understanding of the advance concepts of the Python programming language. 

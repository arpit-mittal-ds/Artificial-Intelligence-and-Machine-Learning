https://ocw.mit.edu/courses/find-by-topic/#cat=engineering&subcat=computerscience&spec=artificialintelligence


[MACHINE LEARNING](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-036-introduction-to-machine-learning-fall-2020/)

[DEEP LEARNING](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-s191-introduction-to-deep-learning-january-iap-2020/)

[ARTIFICIAL INTELLIGENCE](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-034-artificial-intelligence-fall-2010/)

[FinTech: Shaping the Financial World](https://ocw.mit.edu/courses/sloan-school-of-management/15-s08-fintech-shaping-the-financial-world-spring-2020/)


# MACHINE LEARNING

The way I think about machine learning is that fundamentally, it's about getting data in some form and aggregating it in a way that lets us make some kind of predictions.

So it might be that we would like to predict what's going to happen to the stock market or to the weather, or a robot might need to predict what would happen if it turns left.

Some kinds of predictions can also be actions. So it might also be that you're going to make predictions about what would be a good action to take.

So there's all different kinds of things you could predict, but fundamentally, for us, it's about taking data and not so much just analyzing it and getting insight from it. But taking data and using that data to actually kind of do some job. And so the question is well, you have to describe what the job is that you want to do and how to measure whether you're doing a good job of it.

## Example - Given a photo find the faces in the photo, if any faces exist.

**Pre-ML Approach** - Write program to process the image and find whether it contains a face ....  "Oh, well, maybe we should look for eyes and a nose and understand how they should be related."
Results were not that great...

**Post ML Approach** - ... And then people turned their attention to the problem of instead of trying for the humans to write the program to do the job (identify face), the humans started writing the program that we're taking data, this is an image of a face, this is an image of a not face. Here's another face, here's another not face and pour that
into some program which the humans still have to write and then out from that would come something that could tell a face from a not face.

So we're still writing programs. And the human and the engineering input is very important, but it's sort of **now happening at one level of abstraction up.** 

**Instead of trying to write the program to recognize the face, we try to write the program that can analyze the data to decide how to recognize the face.**

So it's been enormously successful

One crucial aspect of machine learning approaches to solving problems is that human engineering plays an important role. A human still has to frame the problem: acquire and organize data, design a space of possible solutions, select a learning algorithm and its parameters, apply the algorithm to the data, validate the resulting solution to decide whether it's good enough to use, etc. These steps are of great importance.

In general, we need to solve these two problems:

**estimation:** When we have data that are noisy reflections of some underlying quantity of interest, we have to aggregate the data and make estimates or predictions about the quantity. How do we deal with the fact that, for example, the same treatment may end up with different results on different trials? How can we predict how well an estimate may compare to future results?

**generalization:** How can we predict results of a situation or experiment that we have never encountered before in our data set?

We can describe problems and their solutions using **six characteristics**, three of which characterize the problem and three of which characterize the solution:

**Problem class:** What is the nature of the training data and what kinds of queries will be made at testing time?

**Assumptions:** What do we know about the source of the data or the form of the solution?

**Evaluation criteria:** What is the goal of the prediction or estimation system? How will the answers to individual queries be evaluated? How will the overall performance of the system be measured?

**Model type:**** Will an intermediate model be made? What aspects of the data will be modeled? How will the model be used to make predictions?

**Model class:****** What particular parametric class of models will be used? What criterion will we use to pick a particular model from the model class?

**Algorithm:** What computational process will be used to fit the model to the data and/or to make predictions?

Without making some assumptions about the nature of the process generating the data, we cannot perform generalization. In the following sections, we elaborate on these ideas.

https://user-images.githubusercontent.com/68102477/125219024-701a9a80-e307-11eb-9a5e-bff28cc1a535.mp4

There's this a kind of romantic idea about machine learning, which is that it's this magic box, and you pour data in one end and out comes super awesome programs to do things.
And it's not so easy, right?

And so-- and the human has a big role to play in setting up a machine learning program or a machine learning solution to a problem.

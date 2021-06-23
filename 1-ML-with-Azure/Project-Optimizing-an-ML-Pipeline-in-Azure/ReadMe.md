# Project: Creating and Optimizing an ML Pipeline in Microsoft Azure

I had the opportunity to create and optimize an ML pipeline. I did this using both HyperDrive and Automated ML, so that I could compare the results of the two methods.

I was provided a custom-coded model— A standard Scikit-learn Logistic Regression — the hyperparameters of which I would optimize using HyperDrive. 

I then used AutoML to build and optimize a model on the same dataset, so that I could compare the results of the two methods.

### Main steps taken:

![image](https://user-images.githubusercontent.com/68102477/122883929-fc791380-d380-11eb-87b2-1dcb4680ccaa.png)


## Getting the Starter Code

You can find all of the starter code for this project at this [Github repo.](https://github.com/udacity/nd00333_AZMLND_Optimizing_a_Pipeline_in_Azure-Starter_Files)

## Setting up the Training Script

As part of our pipeline, we'll need a training script. For this part of the project, we've provided starter code which is marked with # TODO sections where you'll need to add your code. This script will be used in the next part of the project.

## HyperDrive Pipeline

In this step, we'll build our training pipeline. You'll see ### YOUR CODE HERE ### prompts where you should add your code. Note that some of the cells have pre-filled code that you should not modify,

You'll start by getting the workspace and experiment objects running. Then, you'll build your pipeline—from creating a compute cluster, to HyperDrive, to running the train.py script containing the custom-coded Logistic Regression with a HyperDrive run.

## AutoML Run

Once you've completed your HyperDrive run (or while it is running!), you can set up your AutoMLConfig in the same Notebook. In this section, you'll import your data from the specified URL again, clean the data, and pass the cleaned data to an AutoMLConfig that you create.

## Modifying the README
Now it is time to report on your results (from both of your experiments) in the form of a README.

This README should consist of a summary of your problem statement, your architectures, how the problem was solved, and the changes you would make. The repo you cloned has a starter README with more detailed prompts on what information you need to include in order for your project to meet specifications.

Optionally, you do not need to complete the README in your Azure workspace and can modify it locally on your own machine or in GitHub itself after your code has been uploaded.


---
title: 'Important habits for Data Scientists. Part II. Technical'
date: 2023-01-31 00:00:00
featured_image: '/images/demo/demo-square.jpg'
excerpt: This post will cover most important habits for a succesful data scientist 
toc: true
---


[Part I](/blog/important-nontech-habits-for-data-scientists)

* TOC
{:toc}



Now, when we are done with non-technical piece it is time to cover the ones which many consider as more important. I would disagree and for me soft skills and habits are equally important with the hard ones. Also I've figured that they become even more important when you aim for more managerial positions. With that sa



### Non-Technical habits

##### 1. Create new environment for each new project
I know this, don't worry. This is a one-time quick project, I'll look at the data, build some visuals using some library with 13 stars on Github, that require to downgrade `pandas` but tomorrow I'll change everything back. Have been there, have done just that. Most of the times having several  projects in the same environment doesn't do any bad, sometimes this creates minor inconveniences. But from times to times  this turns into a complete disaster, like your inability to run the code you wrote 6 months ago when you desparately needed it.

There is one way out of this - create environment for each small project and then if you are done after 1 day - archive the folder. Despite how tempting it may seem to just quickly install some libraries and run couple of notebooks - just don't, you'll thank me later. 

Now, personally I am useng venv, it is very simple
```bash
python3 -m venv envname
source envname/bin/activate
pip3 install exotic-library
pip3 install jupyterlab
```
If you are a conda fan, I suggest using miniconda which is more lightweight , otherwise you'll be running out of space fairly quickly as conda installs a lot of libraries you don't need. 

---

**How it helped me?**
* I have less dependecies conflicts 
* I can quickly port my environment with requirements.txt file on another machine

---

**External links:**
[https://blog.inedo.com/python-environment-management-best-practices](https://blog.inedo.com/python-environment-management-best-practices)
[https://realpython.com/python-virtual-environments-a-primer/](https://realpython.com/python-virtual-environments-a-primer/)
[https://docs.conda.io/en/latest/miniconda.html](https://docs.conda.io/en/latest/miniconda.html)



##### 2. Writing tests together with the code
Back when I was an actuary, there was a practice of  doublechecking, that was not a conventional practice. When your boss comes in and says that this report needs to be *doublchecked*, it means that two people should be doing same task (looking at report or reproducing it) with the aim to arrive at the same results or conclusion. You won't believe me how many really stupid mistakes  we were able to catch this way before the final numbers have reached our C-level folks. 

Now I understand this is a luxurious practice with six-figures-making data scientists, but these guys are still prone to some bad errors. For some reason asking data scientists to write at least some unit tests for the edge cases rubs them the wrong way but still I believe the bare minimum in that regard should be a must have habit. 

Writing a good code is hard, and personally if I am experimenting only - I don't write tests. When you are participating in a hackathon or kaggle, you probably don't need it either. But when you are writing a code that needs to work flawlessly in production, then it is very important to ensure that when it is failing it is failing controllably. 

My aim is to make sure that the code minimally deviates from expected behavior. That is why there are two types of tests I write:

1. Tests that ensure that code fails in some specific examples (no target column, or it is of incorrect type )
2. Tests that ensure that the code works for some edge cases (dataset has no rows, or only 1 row etc)
3. Tests that ensure that input is a correct one (like if dataframe shape is something specific, or number of columns is what expected)

---

**How it helped me?**
* Saved me so much time in situations where the code runs and model trains but the underlying data is wrong
* Debug is a lot easier

---

**External links:**
https://dssg.github.io/hitchhikers-guide/curriculum/programming_best_practices/test-test-test/ds_testing/
https://www.youtube.com/watch?v=09etytJHHeY&ab_channel=DataScienceDojo
https://towardsdatascience.com/unit-testing-for-data-science-with-python-16dfdcfe3232



##### 3. Tedious Experiment Tracking
There are two types of data scientists - the ones who track their experiments learning it the hard way and the ones who haven't suffered horrible consequences of not doing so JUST YET.  For some reason it is hard to cultivate this habit without being burned omitting it. What were the hyperparameters that gave me the best model? What data I used or features generated? Did I make some change sto the code so now I cannot reproduce my results and I have to present them to the whole company in 30 minutes? Have been there, have done that myself. 


Your final goal here is reproducability of your best results. There is only one way achieving that - so track'em like your salary depends on it. Most popular is Excel spreadsheet or Google sheets. This is mostly because it doesn't require anything from you other than just jog down your experiments. But also they allow you 
1. Visualise the results with ease. This will be crucial when you have several of those and you need to see how your metric changed with respect of some parameters
2. It allows easier to set up the experiment structure. Especially when you are new. Right after first couple of experiments you will see what is best set up for you - what to test, how to write back the results, etc. 
I would advise start here, and there is an article with an example [here](https://wandb.ai/amanarora/melanoma/reports/How-to-track-all-your-experiments-using-Microsoft-Excel---VmlldzoxNTY3MjQ2) . With that said, don't overthink, if you are not doing deep learning, this may be enough. If you are DL practitioner, I'll doubt you survive without this habit at all, so you'll learn more fancy tools soon enough. 

---

**How it helped me?** 
* Was able to reproduce results of the project I did long time ago 
* Saved a ton of nerves


---
**External links:**

https://neptune.ai/blog/ml-experiment-tracking - mostly promotes Neptune.ai plaform but still good
https://dagshub.com/blog/how-to-compare-ml-experiment-tracking-tools-to-fit-your-data-science-workflow/ - a bit outdated but was good at the time




##### 4. Work on personal project for a couple of hours per week

Your work will turn into a routine sooner or later. If it haven't already, I am sure it will. Maybe you are lucky enough and your manager or a company will be very interested in your personal development (which is rare) but it only means the "routinisation" is just going to be slower. Now if you start feeling like doing less and less of new things at work, it could be worthwhile to start a pet project. Or more than one. 

As usual in cases like that - just starting means you are half way through the completion. And you can start in many different places where your hobby lies. You are interested in sports - tons of sport data is available for grab and NFL for example is regularly doing Kaggle competitions. If you are interested in writing - start a technical (or not so technical) blog. If you are interested in computer games - you can do some Reinforcement Learning project to teach an agent to play a game. Now, at this point you should know what works best for you - short projects or really long and ambitious one. Personally, I prefer short ones, because how my mind works - in a month I could easily loose interest to some particular topic and want to try another. As I've mentioned in Part I - it is not a bad thing, it is just how people are wired. However I completely understand that doing long term project may be more beneficial as it can showcase more of your ability and you can achieve better results. 

Also another suggestion - if possible, find a teammate. Working in a team is another valuable skill and learning how to coordinate a team will serve you good in your career. If the project is succesful, you will strengthen your relationship with people you were working with, and maybe will build a fundament for future collaborations.  


With habits consistency is a key. You'll hear this form every corner and every blogpost or video about productivity. Now 


---

**How it helped me?** 
* Was able to reproduce results of the project I did long time ago 
* Saved a ton of nerves


---
**External links:**

No external links, just follow your hobby. 


So that is all. Hope this helps on your way to become a better person and a proffessional

Go back to [Part I](/blog/important-nontech-habits-for-data-scientists)
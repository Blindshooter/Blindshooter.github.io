---
title: 'Important habits for Data Scientists. Part II. Technical'
date: 2023-02-26 00:00:00
featured_image: '/images/tech_intro.png'
excerpt: This post will cover most important habits for a succesful data scientist 
toc: true
---


[Part I](/blog/important-nontech-habits-for-data-scientists)

* TOC
{:toc}



Now, when we are done with the non-technical piece, it is time to cover the ones many consider more important. I would disagree, and for me, soft skills and habits are equally important as hard ones. Also, I've figured that they become even more important when you aim for more managerial positions. But if you want to grow as an individual contributor, I've found that these habits I listed are of the utmost importance. 



### Technical habits

##### 1. Create new environment for each new project
I know this, don't worry. This is a one-time quick project, I'll look at the data and build some visuals using some library with 13 stars on Github that require downgrade `pandas`, but tomorrow I'll change everything back. Have been there and have done just that. Most of the time, having several projects in the same environment doesn't do any worse. Sometimes this creates minor inconveniences. But from time to time, this turns into a complete disaster, like your inability to run the code you wrote six months ago when you desperately needed it.

There is one way out of this - create an environment for each small project and then, if you are done after one day - archive the folder. Despite how tempting it may seem to just quickly install some libraries and run a couple of notebooks - just don't, you'll thank me later. 

Now, personally I am useng venv, it is very simple
```bash
python3 -m venv envname
source envname/bin/activate
pip3 install exotic-library
pip3 install jupyterlab
```
`venv` is my go-to in most situations, and if I feel this is probably only some quick and dirty test, I can archive the whole project folder and leave it to rest. I can always come back to it if needed in the future.

Conda is another excellent way to manage environments. Conda also has the added advantage of being able to install some non-pip packages through`conda-forge`. If you are a conda fan, I suggest using miniconda, which is more lightweight. Otherwise, you'll run out of space fairly quickly because conda installs many libraries you don't need. 

And the last one I do not use but hear hardcore ML engineers use a lot - is Docker. Docker is a platform that allows you to create, deploy, and run applications in containers. Containers are lightweight, portable, and self-contained environments that can run on any machine that has Docker installed. Data scientists can utilize Docker to create a standardized environment for their projects, which can be easily shared with others. Docker containers can also be used to simplify the deployment of machine learning models. To create a Docker container, you need to write a Dockerfile that specifies the environment and dependencies required for the project. Once the Dockerfile is written, you can build the container using `docker build`, and then run it using `docker run`

You may find a lot of resources about this on the internet and why Docker is great, but there is a lot to comprehend and learn for practical usage of the tool, and personally, the additional layer of complexity seems unnecessary if you want to run just a couple of experiments


---

**How it helped me?**
* I have less dependecies conflicts 
* I can quickly port my environment with requirements.txt file on another machine

---

**External links:**
[https://blog.inedo.com/python-environment-management-best-practices](https://blog.inedo.com/python-environment-management-best-practices)
[https://realpython.com/python-virtual-environments-a-primer/](https://realpython.com/python-virtual-environments-a-primer/)
[https://docs.conda.io/en/latest/miniconda.html](https://docs.conda.io/en/latest/miniconda.html)
[https://medium.com/analytics-vidhya/docker-for-data-science-442299c5203c](https://medium.com/analytics-vidhya/docker-for-data-science-442299c5203c)



##### 2. Writing tests together with the code
Back when I was an actuary, there was a "doublechecking" practice that was not conventional. When your boss comes in and says that this report needs to be *doublechecked*, it means that two people should be doing the same task (looking at the report or reproducing it) intending to arrive at the same results or conclusion. You won't believe how many foolish mistakes we were able to catch this way before the final numbers reached our C-level folks. 

Now, I understand this is a luxurious practice with six figures-making data scientists, but these guys are still prone to some nasty errors. For some reason asking data scientists to write at least some unit tests for the edge cases rubs them the wrong way, but still, I believe the bare minimum in that regard should be a must-have habit. 

Writing good code is hard, and personally, if I am experimenting only - I don't write tests. When you are participating in a hackathon or Kaggle, you probably don't need it either. But when you are writing code that needs to work flawlessly in production, then it is vital to ensure that when it is failing, it is failing controllably. 

I aim to ensure that the code minimally deviates from expected behavior. That is why there are two types of tests I write:

1. Tests that ensure that code fails in some specific examples (no target column, or it is of incorrect type )
2. Tests that ensure that the code works for some edge cases (dataset has no rows, or only 1 row, etc.)
3. Tests that ensure that input is correct (like if the dataframe shape is something specific or the number of columns is what is expected)

---

**How it helped me?**
* Saved me so much time in situations where the code runs and model trains but the underlying data is wrong
* Debug is a lot easier. In some cases you will know right away where the trouble is and it helps you navigate the code so much easier. 

---

**External links:**
[https://dssg.github.io/hitchhikers-guide/curriculum/programming_best_practices/test-test-test/ds_testing/](https://dssg.github.io/hitchhikers-guide/curriculum/programming_best_practices/test-test-test/ds_testing/)
[https://www.youtube.com/watch?v=09etytJHHeY&ab_channel=DataScienceDojo](https://www.youtube.com/watch?v=09etytJHHeY&ab_channel=DataScienceDojo)
[https://towardsdatascience.com/unit-testing-for-data-science-with-python-16dfdcfe3232](https://towardsdatascience.com/unit-testing-for-data-science-with-python-16dfdcfe3232)



##### 3. Tedious Experiment Tracking
There are two types of data scientists - the ones who track their experiments, learning it the hard way, and those who haven't suffered horrible consequences of not doing so JUST YET. For some reason, it is hard to cultivate this habit without being burned or omitting it. What were the hyperparameters that gave me the best model? What data I used or features generated? Did I make some changes to the code, so now I cannot reproduce my results, and I have to present them to the whole company in 30 minutes? Have been there and have done that myself. 


Your final goal here is the reproducibility of your best results. There is only one way to achieve that - so track'em as your salary depends on it. The most popular is Excel spreadsheet or Google sheets. This is mainly because it requires nothing from you other than just jogging down your experiments. But also they allow you to: 
1. Visualise the results with ease. This will be crucial when you have several of those, and you need to see how your metric changed with respect to some parameters
2. Easier to set up the experiment structure. Especially when you are new, right after the first couple of experiments, you will see what is best set up for you - what to test, how to write back the results, etc. 
I would advise starting here, and there is an article with an example [here](https://wandb.ai/amanarora/melanoma/reports/How-to-track-all-your-experiments-using-Microsoft-Excel---VmlldzoxNTY3MjQ2). With that said, don't overthink, if you are not doing deep learning, this may be enough. If you are a DL practitioner, I doubt you will survive without this habit at all, so you'll learn more fancy tools soon enough.

---

**How it helped me?** 
* Was able to reproduce results of the project I did long time ago 
* Saved a ton of nerves


---
**External links:**

[https://neptune.ai/blog/ml-experiment-tracking](https://neptune.ai/blog/ml-experiment-tracking) - mostly promotes Neptune.ai plaform but still good
[https://dagshub.com/blog/how-to-compare-ml-experiment-tracking-tools-to-fit-your-data-science-workflow/](https://dagshub.com/blog/how-to-compare-ml-experiment-tracking-tools-to-fit-your-data-science-workflow/) - a bit outdated but was good at the time



##### 4. Work on personal project for a couple of hours per week

Your work will turn into a routine sooner or later. If it hasn't already, I am sure it will. Maybe you are lucky enough, and your manager or a company will be very interested in your personal development (which is rare), but it only means the "routinization" will be slower. Now if you start feeling like doing fewer and less of new things at work, it could be worthwhile to start a pet project. Or more than one. 

As usual in cases like that - just starting means you are halfway through the completion. And you can start in many different places where your hobby lies. You are interested in sports - tons of sports data is available for grabs, and NFL, for example, is regularly doing Kaggle competitions. If you want to write, start a technical (or not-so-technical) blog. If you are interested in computer games - you can do some Reinforcement Learning projects to teach an agent to play a game. Now, you should know what works best for you - short projects or really long and ambitious ones. I prefer short ones because of how my mind works - in a month, I could quickly lose interest in some particular topic and want to try another. As I've mentioned in Part I - it is not a bad thing, it is just how people are wired. However, doing long-term projects may be more beneficial as it can showcase more of your ability, and you can achieve better results. 

Also, another suggestion - if possible, find a teammate. Working in a team is another valuable skill; learning how to coordinate a team will serve you well in your career. If the project is successful, you will strengthen your relationship with the people you were working with, and you may build a fundament for future collaborations.  


With habits, consistency is key. You'll hear this from every corner and every blog post or video about productivity. With this one, consistency is of paramount importance. I have a pet project that I try and occasionally do. But because it is technically heavy, I often spend several hours understanding what I did and why. By the time I'm comfortable continuing,  I am already tired. So better way is to make sprints with specific objectives that can be easily picked up sometime after the sprint is finished. 


---

**How it helped me?** 
* Was able to reproduce results of the project I did long time ago 
* Saved a ton of nerves


---
**External links:**

[https://artgor.medium.com/data-science-pet-projects-faq-2bf63f7f4fc9](https://artgor.medium.com/data-science-pet-projects-faq-2bf63f7f4fc9)


So that is all. Hope this helps on your way to become a better person and a proffessional

Go back to [Part I](/blog/important-nontech-habits-for-data-scientists)
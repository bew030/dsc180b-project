
# Navigating the Repository 
There are a lot of folders within the repository. If you're interested in seeing our project overview document, it can be found in the references folder or can be found [here](https://github.com/bew030/domain_project_template/blob/main/references/SIMULATING%20AIRBORNE%20TRANSMISSION%20OF%20SARS-CoV-2%20AMONGST%20BUS%20RIDERS%20-%20checkpoint%201.pdf). A list of our references along with the paper we're replicating can also be found in the references folder or can be found [here](https://github.com/bew030/domain_project_template/blob/main/references/references.md). 

# Overview 
_Created by Bernard Wong and Ziqian Cui_

COVID-19 has drastically changed the way we live our lives. As of October 2020, there have been 45.5 million cases in the world and around 1.19 million deaths, making it one of the worst epidemics in history. There have been large efforts made in order to slow the spread of the disease and a lot of research is being done to find a vaccine. However, until a vaccine is created, it’s important to understand how the virus works and how it spreads in order to prevent future epidemics from happening. One of the largest industries affected by COVID-19 has been the transportation industry; as mandated quarantines were set around the world and more and more people became fearful of infection, the airline industry has lost nearly 314 billion USD. New research supports airborne transmission being one of the largest factors of the spread of the disease, and with public transports generally being small areas with recirculating air, it’s important to understand how the virus is spread and how air conditions can affect it. In doing so we can set effective guidelines that enable air to be cleaner and prevent the spread of these respiratory droplets, thus minimizing the transmission of COVID-19. 

# The Data 
The research paper we’re replicating is an observational study that studies a worship event and the bus travel that followed shortly after. The event had initially started off with 300 individuals with only one having COVID-191. After the event, 128 of the 300 individuals travelled by bus, with 60 participants going in bus one and 68 going in bus two. Both busses had relatively similar conditions: the air conditioning system was on a heating and recirculating mode, weather conditions were the same, and passengers remained seated during the whole duration on both busses. 
After the initial participant began to experience symptoms and received the diagnosis of COVID-19, the rest of the participants began to get tested. It was found that none of the individuals in bus one were infected but 24 individuals in bus two were infected (leading to a 35.3% infection rate). Surprisingly, of the 172 individuals who did not travel by bus after the event, only 7 were infected (leading to a 4% infection rate). Even more surprising was that the 24 individuals that were infected on bus two were scattered amongst the bus, rather than grouped closely together. A visual representation of these results can be seen below in Figure 1. 
As mentioned within the research paper, the much larger infection rate within the bus along with the lack of a significantly increased risk depending on seat location suggests that the airborne spread of the virus most likely plays a significant role in the transmission of the disease. This data is extremely helpful in our investigation and will help us better simulate the airborne transmission of the disease within a small location. By simulating the transmission of COVID-19 within the air based on these findings, we can hopefully develop an accurate simulation that can then later be applied to larger areas. 

<p align="center">
	<img src="https://github.com/bew030/domain_project_template/blob/main/images_for_readme/images/results.png" />
</p>

# Setting Up the Environment
There's a variety of packages that you need to import. A dockerfile has been included in the repository which includes all the necessary set up that you need. There are a few steps for using the repository if you're a UCSD user that has access to DSMLP servers. 

1. SSH into DSMLP Servers using <user>@dsmlp-login.ucsd.edu which can be done with the command 
	
	```shell
	ssh <user>@dsmlp-login.ucsd.edu
	```

2. Clone the Github repository with 
	```shell
	git clone <repository-id> 
	```
	where repository-id is replaced with https://github.com/bew030/domain_project_template.git
	
3. Launch a container with
	```shell
	launch.sh -i <dockerhub-repo>
	```
	where dockerhub-repo is replaced with bew030/dsc180a_docker
	
4. Change into the repository with the command 
	```shell
	cd domain_project_template
	```
	
5. Enter in the command 
	```shell
	export PYTHONNOUSERSITE=NONE
	```

6. Run python code as normal based on the next section, __Using the Code__

You can use python run.py to run the file based off of the default configurations in the config file. If you'd just like to see what the code and methods looks like, you can also look at our notebook [here](https://github.com/bew030/domain_project_template/blob/main/notebooks/Example%20Notebook.ipynb).

# Using the Code 

run the following code in your Terminal: 

```python 
python run.py abm model visualize
```

Everything is based off of the [configurations](https://github.com/bew030/domain_project_template/tree/main/config) which can be modified to the user's liking.

- abm will create an agent based model based off of the parameters in [abm_params.json](https://github.com/bew030/domain_project_template/blob/main/config/abm_params.json). 

- model will create a folder of images which represent the simulation of the model based off of the parameters in [model_params.json](https://github.com/bew030/domain_project_template/blob/main/config/model_params.json). 

- visualize will create a .gif of images which best represent the simulation of the model and is based off of the parameters in [visualization_params.json](https://github.com/bew030/domain_project_template/blob/main/config/visualization_params.json).

you may also run 
```python 
python run.py test
```
to run abm, model, and visualize. 

The code is divided into three groups, [passengerBusABM](https://github.com/bew030/domain_project_template/blob/main/src/passengerBusABM.py) which contains the class that creates the agents and the environments, [visualization](https://github.com/bew030/domain_project_template/blob/main/src/visualization.py) which contains methods that create step by step images simulating the agent based model, and [timelapse](https://github.com/bew030/domain_project_template/blob/main/src/timelapse.py) which creates the final timelapse GIF visualization of the agent based model.

The final visualizations are located in a folder called 'data'. Within the folder you should find two folders; 'raw' which should include the jpg images of all the steps in the simulation, and 'timelapse' which is the final visualization product (which is a GIF of the model over time). 

# Visualizations 
An example of a timelapse of the steps can be seen here. 2 people are initially infected and has a 50% chance of breathing, 30% chance of coughing, and 20% chance of sneezing. If they breath, people 1 foot away have a 5% chance of being infected. If they cough, people 2 feet away have a 5% chance of being infected. If they sneeze, people 6 feet away have a 5% chance of being infected. Each step is a 'breath' action. 

<p align="center">
	<img src="https://github.com/bew030/busABM/blob/master/images_for_readme/images/gif_of_model.gif" />
</p>

# Badges 
[![GitHub issues](https://img.shields.io/github/issues/bew030/domain_project_template?color=purple)](https://github.com/bew030/domain_project_template/issues)
[![GitHub forks](https://img.shields.io/github/forks/bew030/domain_project_template?color=orange)](https://github.com/bew030/domain_project_template/network)
[![GitHub stars](https://img.shields.io/github/stars/bew030/domain_project_template)](https://github.com/bew030/domain_project_template/stargazers)
[![HitCount](http://hits.dwyl.io/bew030/bew030/domain_project_template.svg)](http://hits.dwyl.io/bew030/domain_project_template)

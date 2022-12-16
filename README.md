# mgt-530-sustainable-logistics
EPFL - Digitalization &amp; sustainable logistics

### Authors: Mathieu Bélanger, Yanis Cuche, Louis Delessert, Mia Frey, Sybille Roemer, Nicolas Wille

Insert here table of contents

## Introduction


## Description of the problem

The aim of this project is to show a concrete application of the vehicle routing problem (VRP). 

The company is based in Vevey and has N employees who travel by car every day. For practical reasons (available parking spaces), socio-economic reasons (gas prices, road infrastructure, traffic jams, accidents), and ecological reasons (carbon emissions and nitrogen oxides from the road sector), we would like to set up a shuttle system. This system would consist in sending a certain number of shuttles, which drive an optimized route to pick up the employees at the beginning of the day, and then bring them back again at the end of the day. 

The first step consists of getting the data. To start, one should generate randomly the location of some employees around a given company. Two steps are required here: First, the location density of people living around this company needs to be gathered. Then, using this density, it is possible to generate employees around the company in a random manner. 

Once the random locations of the employees are determined, the next step consists of estimating the cost matrix of going from the location of one employee to another (including location 0 of the company). Here, there are two different costs that can be computed: The first is the simplest one, consisting of the euclidian distance between two locations. The second is more complex but also more accurate. It consists of using the Google Maps API to enter two locations, and get the distance or time of going from one location to the other (i) by car, (ii) using public transportation, and (iii) by bike or foot. 

Once the cost matrices are generated, the second step is to apply the Vehicle Routing Problem. The challenge is to schedule each shuttle’s route while limiting overall costs. The problem aims to minimise the total costs and then the CO2 emissions. At the end, each employee must be assigned a shuttle (as presented in the Figure below).


## General VRP Mathematical Formulation


## Methodology


## Results & Analysis


## Conclusion


## Extensions


## Sources


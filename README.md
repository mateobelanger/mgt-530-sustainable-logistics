# mgt-530-sustainable-logistics
EPFL - Digitalization &amp; sustainable logistics

### Authors: Mathieu Bélanger, Yanis Cuche, Louis Delessert, Mia Frey, Sybille Roemer, Nicolas Wille

Insert here table of contents

## Introduction

All types of transportation account for one-fifth of global CO2 emissions. Of these, 45% come from passenger road transport, which includes commuters [1]. A breakdown of the CO2 emissions from transport can be found in the graphic below [1].

Include here figure 1 about global emissions

It should be noted that the efficiency of cars is increasing year after year. A car today emits on average 120gCO2 per kilometre driven compared to 170gCO2/km in 2001. In Switzerland it is 135gCO2/km, thus it is one of the highest in the world (cf. Figure below) [2]. Although the reduction is ecologically beneficial, the average car occupancy rate in Switzerland is 1.6 persons per car in general but 1.1 for commuters [3]. The latter figure shows the individualism of today's society despite the high density of public transportation in Switzerland. The share of public transportation in Switzerland has been a bit over 20% since 2006 but has just dropped to 15.6% by 2020 due to Covid-19 [4].

Include here figure 2 about carbon intensity of passengers

In 2020, 8 out of 10 people were considered commuters in Switzerland. 71% of these individuals worked outside their home municipality, 12% more than in 1990. Moreover, 52% of these people used their car for their daily commute and 27% used public transportation (15% - train, 12% - other road transport) [5].

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


## References


[1]      ‘Cars, planes, trains: where do CO2 emissions from transport come from?’, *Our World in Data*. https://ourworldindata.org/co2-emissions-from-transport (accessed Nov. 27, 2022).

[2]      H. Ritchie, M. Roser, and P. Rosado, ‘Energy’, *Our World Data*, Oct. 2022, Accessed: Nov. 27, 2022. [Online]. Available: https://ourworldindata.org/transport

[3]      ‘Utilisation de la voiture comme mode de transport individuel: captivité modale, dépendance et alternatives.’ https://litra.ch/fr/news/utilisation-de-la-voiture-comme-mode-de-transport-individuel-captivite-modale-dependance-et-alternatives/ (accessed Nov. 28, 2022).

[4]      O. fédéral de la statistique, ‘Transports publics’. https://www.bfs.admin.ch/bfs/fr/home/statistiken/mobilitaet-verkehr/querschnittsthemen/oeffentlicher-verkehr.html (accessed Nov. 28, 2022).

[5]      O. fédéral de la statistique, ‘Pendularité’. https://www.bfs.admin.ch/bfs/fr/home/statistiken/mobilitaet-verkehr/personenverkehr/pendlermobilitaet.html (accessed Nov. 28, 2022).

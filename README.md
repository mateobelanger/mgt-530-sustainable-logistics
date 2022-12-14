# mgt-530-sustainable-logistics
EPFL - Digitalization &amp; sustainable logistics

### Authors: Mathieu Bélanger, Yanis Cuche, Louis Delessert, Mia Frey, Sybille Roemer, Nicolas Wille

# Report

## Mobility in Switzerland

*Expliquer la situation en Suisse, les problèmes liés (pollution, congestion, accidents), la tendance des employés à aller en voiture au travail, …*

This report describes a shuttle solution that a company could set up to pick up and bring back employees to their homes in order to reduce emissions from commuters. But first, here is a description of Switzerland's transport and commuting situation.

All types of transportation account for one-fifth of global CO2 emissions. Of these, 45% come from passenger road transport, which includes commuters [1]. A breakdown of the CO2 emissions from transport can be found in the graphic below [1].

![Transport-CO2-emissions-by-mode-bar-chart.png](Report%200bf68eeaf4c240009154e7ba15c123f6/Transport-CO2-emissions-by-mode-bar-chart.png)

It should be noted that the efficiency of cars is increasing year after year. A car today emits on average 120gCO2 per kilometre driven compared to 170gCO2/km in 2001. In Switzerland it is 135gCO2/km, thus it is one of the highest in the world (cf. Figure) [2]. Although the reduction is ecologically beneficial, the average car occupancy rate in Switzerland is 1.6 persons per car in general but 1.1 for commuters [3]. The latter figure shows the individualism of today's society despite the high density of public transportation in Switzerland. The share of public transportation in Switzerland has been a bit over 20% since 2006 but has just dropped to 15.6% by 2020 due to Covid-19 [4].

![carbon-new-passenger-vehicles.png](Report%200bf68eeaf4c240009154e7ba15c123f6/carbon-new-passenger-vehicles.png)

In 2020, 8 out of 10 people were considered commuters in Switzerland. 71% of these individuals worked outside their home municipality, 12% more than in 1990. Moreover, 52% of these people used their car for their daily commute and 27% used public transportation (15% - train, 12% - other road transport) [5].

- References
    
    [1]      ‘Cars, planes, trains: where do CO2 emissions from transport come from?’, *Our World in Data*. https://ourworldindata.org/co2-emissions-from-transport (accessed Nov. 27, 2022).
    
    [2]      H. Ritchie, M. Roser, and P. Rosado, ‘Energy’, *Our World Data*, Oct. 2022, Accessed: Nov. 27, 2022. [Online]. Available: https://ourworldindata.org/transport
    
    [3]      ‘Utilisation de la voiture comme mode de transport individuel: captivité modale, dépendance et alternatives.’ https://litra.ch/fr/news/utilisation-de-la-voiture-comme-mode-de-transport-individuel-captivite-modale-dependance-et-alternatives/ (accessed Nov. 28, 2022).
    
    [4]      O. fédéral de la statistique, ‘Transports publics’. https://www.bfs.admin.ch/bfs/fr/home/statistiken/mobilitaet-verkehr/querschnittsthemen/oeffentlicher-verkehr.html (accessed Nov. 28, 2022).
    
    [5]      O. fédéral de la statistique, ‘Pendularité’. https://www.bfs.admin.ch/bfs/fr/home/statistiken/mobilitaet-verkehr/personenverkehr/pendlermobilitaet.html (accessed Nov. 28, 2022).
    

### Existing software for route optimization:

- [https://www.motiontools.com/last-mile-delivery-stack?utm_feeditemid=&utm_device=c&utm_term=optimo route&utm_source=google&utm_medium=ppc&utm_campaign=&hsa_cam=18822924127&hsa_grp=141602889245&hsa_mt=b&hsa_src=g&hsa_ad=633048540873&hsa_acc={536-108-5031}&hsa_net=adwords&hsa_kw=optimo route&hsa_tgt=kwd-807794010618&hsa_ver=3&gclid=EAIaIQobChMI3qHF6PXT-wIV2PZRCh1HygAcEAAYASAAEgL5i_D_BwE](https://www.motiontools.com/last-mile-delivery-stack?utm_feeditemid=&utm_device=c&utm_term=optimo%20route&utm_source=google&utm_medium=ppc&utm_campaign=&hsa_cam=18822924127&hsa_grp=141602889245&hsa_mt=b&hsa_src=g&hsa_ad=633048540873&hsa_acc=%7B536-108-5031%7D&hsa_net=adwords&hsa_kw=optimo%20route&hsa_tgt=kwd-807794010618&hsa_ver=3&gclid=EAIaIQobChMI3qHF6PXT-wIV2PZRCh1HygAcEAAYASAAEgL5i_D_BwE) (for shuttles)
- [https://optimoroute.com/what-is-route-optimization/](https://optimoroute.com/what-is-route-optimization/) (for last mile delivery → More about bikes)
- [https://www.routexl.com/](https://www.routexl.com/) (what we do, free of use)
- [https://planner.myrouteonline.com/route-planner/](https://planner.myrouteonline.com/route-planner/) (what we do, free of use, and neat)
- [https://www.verizonconnect.com/ca/solutions/route-planning-software/](https://www.verizonconnect.com/ca/solutions/route-planning-software/) (Payant mais fait pas Verizon 👀

**→ On pourrait développer le notre et le comparer aux existants !**

## Description of the problem

The aim of this project is to show a concrete application of the vehicle routing problem (VRP). 

The company is based in Vevey and has N employees who travel by car every day. For practical reasons (available parking spaces), socio-economic reasons (gas prices, road infrastructure, traffic jams, accidents), and ecological reasons (carbon emissions and nitrogen oxides from the road sector), we would like to set up a shuttle system. This system would consist in sending a certain number of shuttles, which drive an optimized route to pick up the employees at the beginning of the day, and then bring them back again at the end of the day. 

The first step consists of getting the data. To start, one should generate randomly the location of some employees around a given company. Two steps are required here: First, the location density of people living around this company needs to be gathered. Then, using this density, it is possible to generate employees around the company in a random manner. 

Once the random locations of the employees are determined, the next step consists of estimating the cost matrix of going from the location of one employee to another (including location 0 of the company). Here, there are two different costs that can be computed: The first is the simplest one, consisting of the euclidian distance between two locations. The second is more complex but also more accurate. It consists of using the Google Maps API to enter two locations, and get the distance or time of going from one location to the other (i) by car, (ii) using public transportation, and (iii) by bike or foot. 

Once the cost matrices are generated, the second step is to apply the Vehicle Routing Problem. The challenge is to schedule each shuttle’s route while limiting overall costs. The problem aims to minimizing the total costs and then the CO2 emissions. At the end, each employee must be assigned a shuttle (as presented in the Figure below).

![Figure 1: Illustration of the vehicle routing problem (Source: Google OR-tools)](Report%200bf68eeaf4c240009154e7ba15c123f6/Untitled.png)

Figure 1: Illustration of the vehicle routing problem (Source: Google OR-tools)

The next section explains the mathematical formulation of the Vehicle Routing Problem.

## **Formulation**

$V:$  The set composed of the N locations to visit (exit and arrival point denoted 0)

$A  (c_{ij}, (i,j) \in V \times V):$  Matrix of the costs associated with each path between i to j

$P  (p_{ij}, (i,j) \in V \times V) :$  Matrix of CO2 emissions associated with each path between i to j

$T  (t_{ij}, (i,j) \in V \times V) :$  Matrix of travel times associated with each path between i and j

$K:$ Set of identical shuttles

$Q  :$ Common capacity of the shuttles

**Decision variables:** 

$x_{ijk} \in (0,1), (i,j,k) \in V \times V \times K(x_{ijk} = 1$ if the shuttle k goes from i to j)

$y_{ik} \in (0,1), (i,k) \in V \times K (y_{ik} = 1$ if the shuttle k visits j)

**4 different objectives to be minimized:**

1. Costs
    
    $z_1 = \sum_{(i,j,k) \in V \times V \times K}c_{ij}x_{ijk}$
    
2. CO2 emissions
    
    $z_2 = \sum_{(i,j,k) \in V \times V \times K}p_{ij}x_{ijk}$
    
3. Travel time
    
    $z_3 = \sum_{(i,j,k) \in V \times V \times K}t_{ij}x_{ijk}$
    
4. Number of shuttles
    
    $z_4 = X$
    

Try to analyze different scenarios with different numbers of vehicles. Try to minimize the time and then look at the other objectives. 

**Constraints:**

- Each location is visited by exactly one shuttle.
    
    $\sum_{k \in K}y_{ik} = 1$
    
- Path-flow: A shuttle has to leave a node after a visit (all nodes but the firm). All shuttles that have left the firm must come back to it.
    
    $\sum_{j \in V\setminus \{i\}}x_{ijk} - \sum_{j \in V\setminus \{i\}}x_{jik} = 0, \ i \in V\setminus\{0\}, k\in K$
    
    $\sum_{j \in V\setminus \{0\}}x_{0jk} - \sum_{j \in V\setminus \{0\}}x_{j0k} = 0,\ k\in K$
    
- Coupling between the node visits of the shuttles and their routes.
    
    $y_{ik} = \sum_{j \in V\setminus \{i\}}x_{ijk}, \ i \in V\setminus\{0\}, k\in K$
    
    $y_{0k} = \sum_{i \in V\setminus \{0\}}x_{i0k}, \ k\in K$
    
- Avoid sub-tours by ensuring only one circuit for each shuttle.
    
    $u_{ik} + q_{j} \leqslant u_(jk) + Q(1-x_{ijk}), \ (i,j) \in V \times V, k \in K$
    
- Enforce the shuttle’s capacity.
    
    $q_{i} \leqslant u_{ik} \leqslant Q, \ i \in V, \ k\in K$
    

**Nuance:**

- Not all employees start and finish work at the same time.
- If the employees live less than 2 km from the company, they come by soft transportation (foot, bike, etc.) and are not considered for the model.

## Extensions

The Vehicle Routing Problem can have many different extensions. 

**1) Objective function** 

First, the model can minimizing CO2 emissions in the objective function:

$$
Z (emissions)= min\sum_{(i,j,k) \in V \times V \times K}p_{ij}x_{ijk}
$$

Once the optimal solution is found, the impact on distance, travelling time, and costs can be assessed.

Then, the objective function can be changed to one that minimizes the costs:

$$
Z (costs) = min\sum_{(i,j,k) \in V \times V \times K}c_{ij}x_{ijk}
$$

Once again it is assessed how the different factors (emissions, distance, time) vary in comparison to the first objective function.

**2) Number of vehicles** 

The model starts with the condition that there is only 1 shuttle (K = 1), which has to get all the employees, and the above functions are minimized. Then, the condition is set to K = 2, 3, and so forth up to K = 10. Each time the objective functions are minimized. Finally, one can analyze the optimal number of shuttles.

**3) Nearby employees commute with soft transportation (foot, bike, scooter, skateboard, roller, etc.)**

If an employee lives close to the office, they will not be considered for the model. The initial condition is that only people living more than 2 km far away from the office are considered for the model.

$$
if \ d_{i0} > 2 :  append\ i \ to \ V
$$

**4) People close to a train station take the train**

If an employee lives close to a train station, they will take the train to Vevey, and thus will not be considered for the model. Another initial condition is set that only considers people living more than 500 meters away from a train station.

$$
if \ d_{it} > 0,5 :  append\ i \ to \ V, \ t \in (Lausanne, Montreux, Cully, ...)
$$

**5) Employees start/finish work at different times**

Three different employee classes are considered with the help of a distribution:

1. Starting at 7h and finishing at 16h (20%)
2. Starting at 8h and finishing at 17h (60%)
3. Starting at 9h and finishing at 18h (20%)

Accordingly, there will not only be one set of employees (V), but three different ones (V1, V2, and V3).

**6) Carsharing**

Instead of shuttles, some employees could take their own car and pick up their colleagues in the morning, and drop them off in the evening. Then, the center point 0 is no longer the company, but the points are the locations of the n people sharing their cars.

# 🍫 Nestlé’s Vehicle Routing Problem
EPFL - Digitalization &amp; Sustainable Logistics

### Authors: Mathieu Bélanger, Yanis Cuche, Louis Delessert, Mia Frey, Sybille Roemer, Nicolas Wille

This project provides a concrete application for the Vehicle Routing Problem (VRP). It proposes a shuttle system to pick up employees at their homes and bring them to the company location and the other way around in the evening. To generate accurate data about the location of employees, the population density of the Swiss Confederation was used. With the help of Google Maps API, the exact travel times and distances between employees (considering the traffic) are extracted. The objective function is to minimize the total travel time. The analysis looks at the different numbers of shuttles and the maximal time of travel for every shuttle. 

The results show that there is no single best scenario that can satisfy all the criteria. However, one scenario stands out from the others, which is the **n°5**. This scenario avoids the most CO2 emissions (**1556 kg**). There are **6 shuttles**, and the average commuting time for the employees is **36 minutes** more than commuting by private cars (34 minutes being the best time, in scenario 7). The resulting daily cost for the company is **500 CHF** (438 CHF being the lowest, in scenario 3). In consequence, the 5th scenario appears to be the most relevant one to go with! Finally, different extensions to this problem are presented, which could be interesting in developing this project further.

Link to the report: https://snapdragon-leotard-088.notion.site/Report-0bf68eeaf4c240009154e7ba15c123f6 

---

title: "Weekend trip to Paris optimized with Google OR
"
permalink: /games_weekendtrips/
toc: false
classes: wide

---

I love travelling to new cities and places. There is always so many new places to explore. With larger cities, the list of places usually gets very long. Too long to plan the trip efficiently myself. And finding an optimal way to visit as many places as possible is an almost impossible task.

When planning my trips by hand, I usually start by collecting all the places I want to visit. For a trip to Paris, this list is quite extensive and will have well beyond 20 locations. 

Common route planning tools usually limit the number of places to 10. That is not enough to plan the optimal route for all places at once. Usually, it ends with me dropping many places I would have liked to visit, because I do not have the time to plan everything.

With all our technology at hand, wouldn't it be nice, if a machine could solve this problem? So that we can spend more time travelling and less time planning?


## Operations Research

The field of operations research is the science of making optimal decisions. Typical applications are the optimization of resource allocations, scheduling of project tasks and logistics.

Organizing a weekend trip to Paris fits well into this field. On a weekend, we have resource constraints (2 days in Paris), we need to schedule our appointments (consider opening hours of museums) and we need manage the logistics of our own body (moving from place A to B).

In general, this an optimization problem, where we need to formulate our objective and constraints. It is usually formulated in a way, where a solution is found by finding the minimum value of an objective function subject to constraints and penalties.


## Places to visit

A city like Paris has numerous places worth visiting. For the purpose of this analysis, I selected the following few sights. Where 'Duration' is the amount of time I would like to spend at each site.

|    | Name                     | Address                                                     |   Duration (in sec) |
|---:|:-------------------------|:------------------------------------------------------------|-----------:|
|  0 | Tour Eiffel              | Champ de Mars, 5 Av. Anatole France, 75007 Paris, France    |        900 |
|  1 | Arc de Triomphe          | Pl. Charles de Gaulle, 75008 Paris, France                  |        900 |
|  2 | Sacre Coeur              | 35 Rue du Chevalier de la Barre, 75018 Paris, France        |        900 |
|  3 | Notre Dame               | 6 Parvis Notre-Dame - Pl. Jean-Paul II, 75004 Paris, France |        900 |
|  4 | Pantheon                 | Pl. du Panthéon, 75005 Paris, France                        |       1800 |
|  5 | Tour Montparnasse        | 33 Av. du Maine, 75015 Paris, France                        |       1800 |
|  6 | Louvre                   | Rue de Rivoli, 75001 Paris, France                          |       3600 |
|  7 | Orsay                    | 1 Rue de la Légion d'Honneur, 75007 Paris, France           |       2700 |
|  8 | Rodin                    | 77 Rue de Varenne, 75007 Paris, France                      |       2700 |
|  9 | Invalides                | 129 Rue de Grenelle, 75007 Paris, France                    |       1800 |
| 10 | Jardin de Luxembourg     | 75006 Paris, France                                         |       1800 |
| 11 | Musee de Picasso         | 5 Rue de Thorigny, 75003 Paris, France                      |       1800 |
| 12 | Parc monceau             | 35 Bd de Courcelles, 75008 Paris, France                    |       1800 |
| 13 | Shakespeare  and company | 37 Rue de la Bûcherie, 75005 Paris, France                  |       1800 |
| 14 | Place vendome            | Pl. Vendôme, 75001 Paris, France                            |        900 |
| 15 | Les halles               | 1 Rue Pierre Lescot, 75001 Paris, France                    |       1800 |
| 16 | Place de vosges          | Pl. des Vosges, 75004 Paris, France                         |        900 |
| 17 | Place de la Bastille     | Pl. de la Bastille, 75004 Paris, France                     |        900 |
| 18 | Les catacombes           | 1 Av. du Colonel Henri Rol-Tanguy, 75014 Paris, France      |       3600 |
| 19 | Père Lachaise Cemetery   | 16 Rue du Repos, 75020 Paris, France                        |       1800 |

For the hotel, I selected the "Best Western Premier Faubourg 88" located at "88 Rue du Faubourg Poissonnière, 75010 Paris, France", where I had a very pleasant stay. 


## Problem Definition with Google OR-Tools

A typical use case for Google OR is to find optimal routes for package deliveries (Vehicle Routing). Given resource and time constraints, the algorithm can find optimal solutions for a set of delivery trucks.

The optimization problem for a weekend trip to Paris can formulated as follows:

Objective:
* Minimize the amount of time walking and visiting places

Inequality Constraints:
* Limit the time spent walking and visiting places to 8 hours a day.
* Limit the distance walked to 15km a day

Penalties:
* Apply a penalty for dropping places

*(For details, have a look at the documentation: https://developers.google.com/optimization/)*

## Solution

The optimal solution allows the visit of almost all places. Assuming a departure at 8:00am every day, a scheduled plan for weekend in Paris could look like this.
* Duration: Time in seconds spent at each site
* Transit: Time in seconds it takes to walk to the current place
* Time of Arrival: The arrival time
* Time of Departure: The time you should leave to be at the next place on time

Skipped places: Les catacombes and Père Lachaise Cemetery.

**Day 1**

|    |   Day | Name                             |   Duration |   Transit | Time of Arrival   | Time of Departure   |
|---:|------:|:---------------------------------|-----------:|----------:|:-----------------:|:-------------------:|
|  0 |     1 | Best Western Premier Faubourg 88 |          0 |         0 | 08:00             | 08:00               |
|  1 |     1 | Arc de Triomphe                  |        900 |      3214 | 08:53             | 09:08               |
|  2 |     1 | Tour Eiffel                      |        900 |      1759 | 09:37             | 09:52               |
|  3 |     1 | Invalides                        |       1800 |      1213 | 10:13             | 10:43               |
|  4 |     1 | Rodin                            |       2700 |       337 | 10:48             | 11:33               |
|  5 |     1 | Tour Montparnasse                |       1800 |      1408 | 11:57             | 12:27               |
|  6 |     1 | Jardin de Luxembourg             |       1800 |      1150 | 12:46             | 13:16               |
|  7 |     1 | Pantheon                         |       1800 |       693 | 13:27             | 13:57               |
|  8 |     1 | Shakespeare  and company         |       1800 |       688 | 14:09             | 14:39               |
|  9 |     1 | Les halles                       |       1800 |       897 | 14:54             | 15:24               |
| 10 |     1 | Best Western Premier Faubourg 88 |          0 |      1469 | 15:48             | 15:48               |

**Day 2**

|    |   Day | Name                             |   Duration |   Transit | Time of Arrival   | Time of Departure   |
|---:|------:|:---------------------------------|-----------:|----------:|:-----------------:|:-------------------:|
| 11 |     2 | Best Western Premier Faubourg 88 |          0 |         0 | 08:00             | 08:00               |
| 12 |     2 | Sacre Coeur                      |        900 |      1259 | 08:20             | 08:35               |
| 13 |     2 | Parc monceau                     |       1800 |      2166 | 09:12             | 09:42               |
| 14 |     2 | Place vendome                    |        900 |      1890 | 10:13             | 10:28               |
| 15 |     2 | Orsay                            |       2700 |       767 | 10:41             | 11:26               |
| 16 |     2 | Louvre                           |       3600 |       881 | 11:41             | 12:41               |
| 17 |     2 | Notre Dame                       |        900 |      1324 | 13:03             | 13:18               |
| 18 |     2 | Place de la Bastille             |        900 |      1464 | 13:42             | 13:57               |
| 19 |     2 | Place de vosges                  |        900 |       461 | 14:05             | 14:20               |
| 20 |     2 | Musee de Picasso                 |       1800 |       528 | 14:29             | 14:59               |
| 21 |     2 | Best Western Premier Faubourg 88 |          0 |      2104 | 15:34             | 15:34               |

And for a visual presentation of the optimized weekend trip with day 1 in orange and day 2 in blue.

![Map of optimal solution](/assets/images/Paris_small.png)


## Outlook

Now, these first results are already quite nice. But there is a lot of room for extensions:
* There are many more than just 20 places to visit in Paris
* The choice of the Accomodation will change the whole plan
* Introduction of penalties for each place: "I can miss the Place Vendome, but NOT the Arc the Triomphe"
* Include lunch, coffee and dinner places
* Consider opening hours of places. While you can look at the Tour Eiffel 24/7, the Louvre is open only during specific hours.


Also, expect more cities to be analyzed!


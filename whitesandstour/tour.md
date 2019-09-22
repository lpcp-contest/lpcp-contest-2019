# Organizing a visit to White Sands

(Use this FileName pattern for submissions: __tour__) 

Mary wants to organize a visit to White Sands for attendees of a
conference.  There are various activities (the set __A__ of all
possible activities) for this visit and tour operators may offer a
group of activities as a package for some price: an operator __T__
offers __O__ packing some units of various activities __(a,u)__
![](https://latex.codecogs.com/svg.latex?$a&space;\in&space;A$),
![](https://latex.codecogs.com/svg.latex?u&space;\in&space;U) for a
price __P__ (a positive integer) where __U__ represents positive
integers as numbers of units of activities.  For example, an operator
may offer 1 unit of activity full moon hike tour and 2 units of Lake
Lucero tour as a package for $200.

Mary contacts tour operators and collect their offers.  Considering
the number of the attendees, she wants to book specific number of
units of various activities; for example 3 units of White Sands
monument tour, 1 unit of full moon hike and 2 units of Lake Lucero
tour.  An offer of a tour operator can be accepted __only as a
whole__.  Considering all the accepted offers, if there are more units
of an activity than needed, the __surplus can be freely disposed__.
Mary also wants to __minimize__ the cost of the visit.  Additionally,
she accepts at most __K__ offers from one tour operator to reduce the
chance of eventual problems with an operator.

You can help Mary to find the minimum total cost of the visit.

## Input format:

An input file for LP systems contains the following facts:

- A relation of `offer(T,O,A,U)` facts indicating that tour operator
  __T__ offers a package __O__ that includes __U__ units of activity
  __A__.  For example, if we have only two facts `offer(1,1,1,2)` and
  `offer(1,1,2,3)` related to the tour operator 1 and their package 1,
  that package is composed of 2 units of activity 1 and 3 units of
  activity 2.

- A relation of `price(T,O,P)` facts indicating that tour operator
  __T__ offers a package __O__ for price __P__.

- A relation of `need(A,U)` facts indicating that Mary needs to book
  __U__ units of activity __A__.

- A fact `maxacceptedoffer(K)` specifying __K__ as the maximum number
  of offers that can be booked from each tour operator.

Assume that all instances satisfiable.

## Output format:

The output should contain exactly one fact of the form `totalcost(C)`,
where C is the minimum total cost of the visit satisfying the
requirements.

## Example:

### Instance 1

LP input (instance1.pl):

```
% 1. offer of operator 1
offer(1,1,1,1).         
offer(1,1,2,2).         
price(1,1,8).           
                        
% 1. offer of operator 2
offer(2,1,2,1).         
offer(2,1,3,1).         
price(2,1,9).           
                        
% 2. offer of operator 2
offer(2,2,3,2).         
offer(2,2,4,1).         
price(2,2,10).          
                        
% 1. offer of operator 3
offer(3,1,3,1).         
offer(3,1,4,1).         
price(3,1,6).           
                        
need(2,1). need(3,3). need(4,1).
                              
maxacceptedoffer(1).          
```

Output:

```
totalcost(24).
```
                   
Accepted offers: 

offer 1 of tour operator 1,
offer 2 of tour operator 2,
offer 1 of tour operator 3.


### Instance 2

LP input (instance3.pl):

```
offer(1,1,1,1).     offer(2,1,3,2).     offer(3,1,1,3).
offer(1,1,3,1).     price(2,1,3).       offer(3,1,2,1).
offer(1,1,4,1).                         offer(3,1,3,2).
price(1,1,7).       offer(2,2,1,2).     price(3,1,5).
                    offer(2,2,2,1).     
offer(1,2,2,2).     offer(2,2,3,2).     offer(3,2,2,2).
offer(1,2,5,1).     offer(2,2,5,2).     offer(3,2,4,2).
price(1,2,7).       price(2,2,9).       price(3,2,5).
                    
                    offer(2,3,4,2).
                    price(2,3,4).

maxacceptedoffer(2).

need(1,3). need(2,2). need(3,4). need(4,1). need(5,3).
```

Output:

```
totalcost(25)
```

Accepted offers: 

offer 2 of tour operator 1,
offer 2 of tour operator 2,
offer 3 of tour operator 2,
offer 1 of tour operator 3.


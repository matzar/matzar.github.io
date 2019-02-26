---
layout: post
title:  "darts simulator"
image: ''
date:   2015-12-12 00:00:00
tags:
- C++
description: ''
categories:
- individual projects
---

{% highlight javascript %}

Language: C++
Platform: Windows
Workload: 150 hours
Module: Programming in C++
Year/Semester: 1st/1st
​​This was my submission project for C++ module. 
At the time I had been learning programming for 7 months and this was my first, big project.

{% endhighlight %}

<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/8uQ6leX4g8c" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

## Description

I have used OOD, inheritance and polymorphism. The program starts asking you how many players you want to have, how to name them and have many games you want to simulate. Every simulation starts with “nearest the bull” game, to see who throws first. The winner is picked and the simulation continues in the established order, e.g.: if you have four players and ‘Player3’ won “nearest the bull” game he will start first and then accordingly ‘Player4’ (the program will loop the player’s vector to the beginning), ‘Player1’ and ‘Player2’. The simulation is based on the ‘Nine Darts Finish’ strategy. The players aim for the T20 to score the highest possible score which is 180. They keep aiming triple as long as it will leave them with the lowest and still possible to win score.  If it’s possible to win by aiming for the bull or the double (in this order) they will do it. Otherwise, they will keep aiming for the highest possible score. If the score is odd and it’s impossible to win by aiming for the double or the bull they will aim for the single to make it even but it will never be smaller than 2. In other words, if they keep missing, they will be left with the lowest winning score which is 2.  And if they bust the score will go back to the one they had before the turn started. The idea for the checkout was to that recreate a three 167s (T20-T19-Bull) which is considered a pure or perfect nine dart finish by some players and a 141 checkout (T20-T19-D12). It is possible to get a very similar effect in my program.

### Here’s sample output of a checkout on the bull:

{% highlight javascript %}

// Player's name and score
Player2 Turn. Score: 120

// Player's aim
Aim Triple 20

// What player hit(how many points) Score: current score = previous score - hit score
Scored Triple 20(60) Score: 60 = 120 - 60

// Player's aim
Aim Bull

// What player hit(how many points) Score: current score = previous score - hit score
Scored Bull 50 Score: 0 = 50 - 50           

{% endhighlight %}

### Sample output of a checkout on the double (close to 141 checkout):

{% highlight javascript %}

Player1 Turn. Score: 132
Aim Triple 20
Scored Triple 20(60) Score: 72 = 132 - 60
Aim Triple 20
Scored Triple 20(60) Score: 12 = 72 - 60
Aim Double 6
Scored Double 6(12) Score: 0 = 12 - 12

{% endhighlight %}

​The whole game is handled by the ‘Game’ class. The function member ‘Play’ calls ‘NineDartFinish’ function which receives vector of pointers to ‘GenericPlayer’, that points to the ‘Player’ object, which are created on the heap. It is possible because ‘Player’ class inherits from ‘GenericPlayer’ class so ‘Player’ object is also a member of ‘GenericPlayer’ class. It allows me to have functions that accept a pointer to ‘GenericPlayer’ and can work with either ‘Player’ or ‘GenericPlayer’ object. This approach allows me to easily add different types of players and also having the user to play with the computer would take a lot of less changes in the program.
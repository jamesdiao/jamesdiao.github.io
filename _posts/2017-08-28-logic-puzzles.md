---
layout: post
title: "Logic Puzzles"
date: 2017-08-28
author: James Diao
location: New Haven, CT
---

I really enjoy logic puzzles, and I thought I'd compile a list of my favorites before I forget them all. Solutions range from recursion to binary encoding; none requires math. When you're ready, click on the title for an answer and explanation. (If you liked these, check out <a href="/archives/2017/08/28/probability-problems">my probability problems</a>!)

### Contents

### [Easy](#easy)
  1. [Amoeba Jar](#AmoebaJar)
  2. [Cake Cutting](#CakeCutting)
  3. [Predicting Coin Flips](#PredictingCoinFlips)
  4. [Missing Square](#MissingSquare)
  5. [Coins in a Line](#CoinsInLine)
  
### [Medium](#medium)
  1. [King and Poison](#KingAndPoison)
  2. [100 Airplane Seats](#100AirplaneSeats)
  3. [Prisoners and Lightbulb](#PrisonersAndLightbulb)
  4. [Ranking Racehorses](#Racehorses)
  5. [The Fox and the Duck](#FoxDuck)
    
### [Hard](#hard)
  1. [100 Pirates](#100Pirates)
  2. [201 Islanders](#201Islanders)

### [Very Hard](#veryhard)
  1. [Nim](#Nim)
  2. [Coins on a Chessboard](#CoinsAndChessboard)

<br>

### Easy

1. [Amoeba Jar](/html/amoeba-solution.html)<a name="AmoebaJar"></a>  
> You've successfully engineered a new species of amoeba with a very impressive doubling time of 3 minutes (i.e., every 3 minutes, each amoeba will split into 2 new amoeba). You put a single amoeba in a jar, and it takes exactly one hour to fill the jar. You put two amoeba in a second jar. How long does it take to fill the second jar?  
*Note: I first heard this problem in an interview and it's been super interesting to see how people approach it. So far, around one-third (12/36) of my friends have answered this correctly on their first try. When given multiple tries, half (18/36) eventually figure it out.*

2. [Cake Cutting](https://mathematicslounge.wordpress.com/2014/09/06/splitting-a-cake-with-a-missing-piece/)<a name="CakeCutting"></a>  
> Jeremy and Jane would like to split a cake, but their friend Bob has already cut out a piece for himself. Bob’s slice is a rectangle of arbitrary size and rotation. How can Jeremy and Jane divide the remaining cake into two equal portions using a single cut from their knife?  
![Cake Question Img](/img/cake-question.png)

3. [Predicting Coin Flips](https://www.futilitycloset.com/2015/10/01/cruel-and-unusual-3/)<a name="PredictingCoinFlips"></a>  
> Two mathematicians have been arrested and will soon both be imprisoned in separate towers. Each morning, a guard at each tower will flip a coin and show the result to his prisoner. Each prisoner must then guess the result of the coin flip at the other tower. If at least one guess is correct, both prisoners are spared. But if both guesses are incorrect, both prisoners will be executed. The mathematicians are allowed to briefly confer before being locked up. What strategy can spare them indefinitely?  
![Prisoner Coin Img](/img/prisoner-coin.jpg)

4. [Missing Square](https://en.wikipedia.org/wiki/Missing_square_puzzle)<a name="MissingSquare"></a>  
> Both A and B are constructed from the same shapes, but B is magically missing a square. Where did it go?  
![Missing Square](/img/missing-square.png)

5. [Coins in a Line](https://articles.leetcode.com/coins-in-line/)<a name="CoinsInLine"></a>
> There are an even number of coins in a line, and each coin has a positive integer value. The total amount of money on the table is odd. We play a game: I take a coin from either end of the line, and then you take a coin from either end of the remaining line, and we continue taking turns until all the coins are gone. Whomever has more money at the end wins. What strategy can guarantee that the first player will always win? Is this strategy optimal (e.g., does it always maximize your earnings)?

<br>

### Medium

1. [King and Poison](https://medium.com/i-math/a-king-1000-bottles-of-wine-10-prisoners-and-a-drop-of-poison-2dd1959a8dd2)<a name="KingAndPoison"></a>  
> The King invites 1000 senators to his party, and each senator brings a bottle of wine. Soon after, the King discovers that one was poisoned. However, the King has 10 prisoners whom he decides can help him determine which bottle contains the poison. The poison has no effect on the prisoner until exactly 24 hours later, when the infected prisoner suddenly dies. The King needs to determine which bottle of wine is poisoned by tomorrow, and hence only has time for one round of testing. How can the King administer the wine to the prisoners to ensure that 24 hours from now, he is guaranteed to have found the poisoned wine bottle?

2. [100 Airplane Seats](https://medium.com/i-math/solving-an-advanced-probability-problem-with-virtually-no-math-5750707885f1)<a name="100AirplaneSeats"></a>  
> 100 passengers board an airplane with exactly 100 seats. Everyone has a ticket with an assigned seat number. However, the first passenger has lost their ticket and takes a random seat. Every subsequent passenger attempts to choose their own seat, but takes a random seat if their’s is taken. Suppose you are the very last passenger to board the plane. What is the probability that you will get your assigned seat?

3. [Prisoners and Lightbulb](https://sites.math.washington.edu/~morrow/336_11/papers/yisong.pdf)<a name="PrisonersAndLightbulb"></a>
> Starting tomorrow, 100 prisoners will be isolated and unable to communicate. Each day, the warden will choose one of the prisoners uniformly at random and place him in a room with a lightbulb and switch. The prisoner can observe the current state of the bulb (on or off) and chooses whether to toggle the lightbulb. The prisoner may also choose to announce whether (s)he believes all prisoners have visited the room at least once. If this announcement is true, all prisoners are set free; if not, all prisoners are executed. The prisoners are allowed to count how many days have elapsed. The prisoners may discuss with each other before the game begins the next day. What is the prisoners' best strategy to guarantee success and minimize their expected time of release?  
*Hard Addendum: how about if the prisoners cannot count the elapsed days?*  
*How about if every single prisoner needs to declare and be certain?*  
![Prisoners Lightbulb Img](/img/prisoners-lightbulb.png)

4. [Ranking Racehorses](https://mindyourdecisions.com/blog/2017/05/11/can-you-solve-the-25-horses-puzzle-google-interview-question/)<a name="Racehorses"></a>
> You need to identify the fastest 3 horses out of 25. You can race up to 5 at a time to find out their relative speeds. You do not have a watch, and cannot learn any of their absolute speeds. What is the minimum number of races you need to conduct? 

5. [The Fox and the Duck](http://www.mytechinterviews.com/the-fox-and-the-duck)<a name="FoxDuck"></a>
> A duck is in the center of a circular lake. A fox, which runs four times faster than the duck can swim, runs along the circumference of the lake. The duck wants to make it to the shore and fly to safety. How can it do this, regardless of how the fox runs?

### Hard

1. [100 Pirates](https://en.wikipedia.org/wiki/Pirate_game)<a name="100Pirates"></a>   
> 100 pirates discover a chest containing 100 gold coins, and need to divvy it up. The pirates are ranked based on seniority (Pirate 1 to Pirate n, where Pirate n is the most senior). The most senior pirate gets to propose a plan and then all the pirates vote on it. If at least half agree on the plan, the proposal passes. Otherwise, he is thrown off the ship and the next most senior pirate makes a proposal. The first priority of the pirates is to stay alive and the second is to maximize their take. The pirates are all rational, greedy, and perfect logicians. What plan can pirate n devise to win maximize his gold while winning enough votes? 

2. [201 Islanders](https://xkcd.com/solution.html)<a name="201Islanders"></a>
> There are 201 people on an island. 100 of them have blue eyes, 100 have brown eyes, and 1 has green eyes (the Guru). No one knows the color of their own eyes. Every night, a ferry stops at the island. Any islanders who have figured out the color of their own eyes will leave the island, and the rest stay. Everyone can see everyone else at all times and keeps a count of the number of people they see with each eye color (excluding themselves), but they cannot otherwise communicate. Once per day, the Guru tells them whether she sees at least one person with blue eyes. All islanders are perfect logicians. Everyone on the island knows all the rules in this paragraph. Who leaves the island, and on what night? 

### Very Hard

1. [Nim](https://en.wikipedia.org/wiki/Nim)<a name="Nim"></a>
> In the game of Nim, two players take turns removing objects from distinct heaps (in the below illustration, matches from distinct rows). On each turn, a player must choose a heap and take a non-zero number from that heap. The goal of the game is to avoid taking the last object. How can the first player win from any initial game state? 
![Sample Nim Setup](/img/nim-matches.png)

2. [Coins on a Chessboard](http://datagenetics.com/blog/december12014/index.html)<a name="CoinsAndChessboard"></a>
> The jailer will take you into a private cell. In the cell will be a chessboard. The jailer will take 64 coins and place them, one-by-one, on each square on the board. He will place the coins on the board in any way he wants (in a pattern, at random, etc.). Once all the coins have been placed, the jailer will point to one of the squares on the board and say: "This square is the magic square." You must then choose exactly one coin to turn over--heads to tails, or tails to heads. You cannot opt out of this choice. You will then be led out of the room, and your friend will be led in. Your friend will look at the board of coins and guess the magic square. If he guesses correctly, you are both pardoned. If he guesses incorrectly, you are both executed. The jailer explains these rules to you and your friend and then gives you time to confer. What is the strategy that maximizes your chance of escape?  
<br>
![Coins Chess](/img/chess-coins.png)


### Unsorted
1. [Prisoners and Hats](https://en.wikipedia.org/wiki/Hat_puzzle#Prisoners_and_hats_puzzle)
2. [DataGenetics Blog](http://datagenetics.com/blog.html)
3. [Quora](https://www.quora.com/What-are-the-best-brain-teasers?page_size=10#!n=72)
4. [Balance Puzzles](https://en.wikipedia.org/wiki/Balance_puzzle)
5. [Notakto](https://en.wikipedia.org/wiki/Notakto)
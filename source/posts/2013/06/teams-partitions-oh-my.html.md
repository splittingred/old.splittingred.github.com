---
title: Teams, Partitions, Oh My!
date: 2013-06-20 11:15 CDT
tags: kag, algorithms, ruby
teaser: Team balancing is actually trickier than it sounds.
---

One of my off-work hobbies is [working on a matchmaking system](/portfolio/kag-gather) called "KAG Gather" for the indie
game [King Arthur's Gold](http://kag2d.com/), where the system sets up "matches" of 5v5 games for people who are
awaiting a game in the IRC lobby. The system is fairly feature-complete, having detailed stats and achievements, a
ranking algorithm, and quite a bit of other neat stuff inside.

However, I've run into some challenges with the team balancing. Getting even teams automagically, it seems, is a lot
trickier than you'd think.

### NP-what?

In the world of computer science, there are certain problems ("problems" there is defined academically, meaning
something you have to solve) that simply do not have fast solutions, or at least none we've been able to discover. These
problems - called [NP-complete](https://en.wikipedia.org/wiki/NP-complete) - can be solved, but as the complexity of
them grow, the time to solve them exponentially grows.

An example of an NP-complete problem is the ["Traveling Salesman"](https://en.wikipedia.org/wiki/Travelling_salesman_problem)
problem, where given cities and distances between each city, find the shortest possible route that goes to each city
only once and then returns to the starting city. While this can be solved (as Google has proven), the time it takes to
do so grows with the number of cities involved.

### Partitioning (Without Hard Drives)

My specific NP-complete problem for my team balancing situation is the [Partition Problem](https://en.wikipedia.org/wiki/Partition_problem),
in which you are given a list of random numbers, and you need to put them into groups such that each group has a (mostly)
equal sum. So, say I have the following numbers:

    [1,2,4,4,2,3]

And I want to split them into two groups with roughly equal sums. I need my program to do it so this is the solution:

    [4,3,1] [4,2,2]

Which gives one group a sum of 8, and the other 8 as well. (There are other solutions, but we'll pick this one.)

### Back to Teams, Please

So, how is this relevant to what I was doing? Well, it was very relevant. Each player in Gather has a "score" (and rank)
based on quite a few factors: K/D ratio, games played, win/loss ratio, classes picked, etc. This score determines their
overall rank in the Gather system, and allows me to do team balancing. Prior to this solution, to do balancing, I was
just sorting the players in the upcoming match by their score, and then looping through them, alternating which team
they went to. So, rank #1 to red, #2 to blue, #3 red, and so on.

The problem was that this didn't really give even matches; the first team always had #1 and #3, and therefore always had
the upper hand. So I adjusted it to do #1 red, #2/3 blue, #4/5 red, #6/7 blue, etc. This worked slightly better, but
still had a sum difference that sometimes crept over 10% of the total (read: could be better).

So I went to digging. And that's when I found the partition problem was the answer.

### Getting Greedy

One of the proposed solutions to the partition problem is the "greedy approximation" algorithm, is where you iterate
through the array, and assign the current item to whichever subset has the smaller sum.

For an example, let's go back to our numbers list. After sorting, you'd get this:

    [4,4,3,2,2,1]

Then you'd do the iteration, and after your first two steps, you'd have:

    [4] [4]   (4 sum in each)

Then the next would go:

    [4,3] [4]   (7 in first, 4 in second)

And so on:

    [4,3] [4,2]       (7/6)
    [4,3] [4,2,2]     (7/8)
    [4,3,1] [4,2,2]   (8/8)

Boom! We've now got even sums!

### Edge Cases

So, this works great for my team balancing - I can just sort the current queue of players by score, then do the
algorithm to split them into separate teams. However, there was a flaw: this algorithm doesn't separate the two teams
necessarily into equal sized groups; it just tries to get them as close as possible. So, in some cases, like below,
you'd end up with one team having 6 or 7 people, and the other 3:

    The set of:
    [8,4,3,2,1,1]

    Ends up as:
    [8,1] [4,3,2,1]  (9/10)

This, obviously, is a problem, since the point of the balancing system was to get close teams in score, for sure, but
definitely *not* uneven teams! So, I introduced a slight tweak to the algorithm: once one team had the maximum number
of players (which was the total # of players divided by two), then just stick all the remaining players that haven't
been placed into the other team.

On first thought, you'd think that would unbalance the teams; however, it's not really the case. Think of it this way:
The remaining people that get dumped into the smaller-sized team usually have lower scores, so they won't add much to the
sum of the smaller-sized team. However, the smaller-sized team has higher-scoring individuals in it - which is why it
is smaller! So it all evens out in the end.

In fact, it really does. Differences in scores between the teams now average at about 3% of the total score of the team,
which is *far* better than before!

Not to mention, we got to do some cool science while we were at it. Even teams, rejoice!
---
title:  "Part 1 -- Introduction"
date:   2016-05-01 00:00:00 +0000
excerpt: "Solving Connect Four: history, references and tutorial goals."
---

This tutorial explains, step-by-step, how to build the Artificial Intelligence behind this [Connect Four perfect solver](http://connect4.gamesolver.org/)

# Connect Four game and rules
Connect Four (or Four-in-a-line) is a two-player strategy game played on a 7-column by 6-row board. Each player has a color and drops succesively a disc of his color in one column, the disc falls down to the lowest empty cell of the column. The first player to make an alignment of four discs of his color wins, if the board is filled without alignment it's a draw game. More details on the game [here](https://en.wikipedia.org/wiki/Connect_Four).

![Connect Four example. Author: Silver Spoon. License: CC BY-SA 3.0 (http://creativecommons.org/licenses/by-sa/3.0)](/data/connect4.gif){: .align-center}

# Solving Connect Four, an history.
Connect Four is a strongly solved perfect information strategy game: first player has a winning strategy whatever his opponent plays. Initially, the game was first solved by [James D. Allen](http://fabpedigree.com/james/index.htm) (October 1, 1988), and independently by [Victor Allis](https://en.wikipedia.org/wiki/Victor_Allis) two weeks later (October 16, 1988). At this time, it was not yet feasible to brute force completely the game. Both solutions are based on rule based approaches in combination with knowledge database. James D. Allen's strategy[^1] was later published in a more complete book[^2], while Victor Allis' solution was published in his thesis[^3].

[^1]: James D. Allen, [Expert Play in Connect-Four](/data/expert_play_in_connect_4.html)
[^2]: James D. Allen, [The Complete Book of Connect 4](http://james.fabpedigree.com/connect4.htm): History, Strategy, Puzzles. Sterling Publishing Company (2010). ISBN 1402756216.
[^3]: Victor Allis, [A Knowledge-based Approach of Connect-Four](http://www.informatik.uni-trier.de/~fernau/DSL0607/Masterthesis-Viergewinnt.pdf), Vrije Universiteit, October 1988

Later, with more computational power, the game was strongly solved using brute force resolution. [John Tromp](https://tromp.github.io/) extensively solved the game and published in 1995 an opening database providing the outcome (win, loss, draw) of any 8-ply position. John Tromp's solver[^4] recently solved the 8x8 board in 2015.

[^4]: John Tromp, [John's Connect Four Playground](https://tromp.github.io/c4/c4.html)

The final step in solving Connect Four is to compute the best number of plies before the end of the game in addition to outcome (win, loss, draw). [GameCrafters](https://www.ocf.berkeley.edu/~gamers/) from Berkely university provided a first online solver[^5] computing the number of remaining moves to perform the perfect strategy. As well as Christian Kollmann's solver build as student project in Graz University of Technology[^6]. Mine[^7], is the acheivement of a nostagic project: my first big computer program was a Connect Four (non perfect) AI, coded long time ago when I was 16 years old.

[^5]: (defunct) GameCrafters, Berkeley University, [Connect Four solver](http://nyc.cs.berkeley.edu:8090/gcweb/ui/game.jsp?game=connect4) 
[^6]: Christian Kollmann, Graz University of Technology, [Connect Four solver](http://connect4.ist.tugraz.at:8080/)
[^7]: Pascal Pons, gamesolver.org, 2015, [Connect Four solver](http://connect4.gamesolver.org/)

# Purpose of this tutorial
This tutorial is itended to be a pedagogic step-by-step guide explaining the differents algorithms, tricks and optimization requiered to build a very fast Connect Four solver able to solve any valid position in a few milliseconds. We start with a very basic and inefficient solver that will be improved little by little.

I hope this tutorial will be a comprhensive and useful resource for intermediate or advanced algorithm and computer science trainings. C++ source code is provided under the [GNU affero GLP licence](http://www.gnu.org/licenses/agpl-3.0.en.html).

# Tutorial plan
  {% include nav_list nav="side" %}

# References

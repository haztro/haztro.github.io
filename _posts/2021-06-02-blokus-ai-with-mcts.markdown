---
layout: post
title:  "Blokus AI"
---

I've been playing [Blokus](https://en.wikipedia.org/wiki/Blokus) (super fun board game) a bit and thought it'd be interesting to try and make an AI for it. I wanted to learn more about Monte Carlo Tree Search so I thought I have a go at implementing my own in Python. There are plenty of [resources](https://en.wikipedia.org/wiki/Monte_Carlo_tree_search) describing how MCTS works so I won't go into that here. The code for my implementation is available [here](https://github.com/haztro/blokus-ai).

Once I was confident I had something that worked I first tested it using Tic Tac Toe since it's obvious in Tic Tac Toe when an agent is performing well/poorly. Pitting two MCTS agents against one another resulted in a (roughly) 50/50 win/loss rate (the player to move first won slightly more often). 

Next, I moved on to writing the game logic for Blokus. A piece is represented by a sequence of moves that traverse the grid. For example the 1x2 pieces is represented as [[[1, 0]], [[0, -1]]]. There are two entries here because there's two possible orientations for the 1x2 piece. It's then trivial to rotate these entries by 90 degree increments. Once I was satisfied with the game logic I wrote a little GUI in pygame and started simulating some games. 


![image tooltip here](/assets/blokus-ai/duo.gif)

This is the result of two MCTS agents (iteration=10000) vsing eachother. A common strategy in Blokus is to use all the biggest pieces points (as this earns you the most points) and this is exactly what happens in this simulation so it's neat to see this emerge. At some point I'd like to improve this by getting an AlphaZero agent to play Blokus.

The code for this project is available on [Github](https://github.com/haztro/blokus-ai)

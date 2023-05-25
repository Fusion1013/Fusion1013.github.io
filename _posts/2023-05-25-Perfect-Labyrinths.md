---
layout: post
title: Generating Perfect Labyrinths
---

Many games use randomly generated labyrinths to automatically create challenges for players. An important aspect when procedurally generated labyrinths are used in games is that they must have a solution, the player can not be presented by an impossible task. This post will present three different methods for generating labyrinths with these properties, known as Perfect Labyrinths.

![_config.yml]({{ site.baseurl }}/images/DepthFirstSearchMaze.png)

## Method
A few of the methods described below make use of two graphs. One of the graphs is a Planar Graph, which represents all possible walls in the labyrinth. We call it 'G'. The other graph is the Dual to 'G', we call it 'G*'. The algorithms work by moving along 'G*' and removing edges in 'G' when these are crossed. The algorithm terminates once all nodes in G* have been visited at least once. Because the algorithms move from node to node along the edges of G*, the labyrinth generated must be perfect once the algorithm terminate, which means all nodes can be reached from any arbitrarily chosen starting node.

To create the entrance and exit of the maze we can simply remove two randomly chosen edges from the outer cycle of the graph. This method works since we have a perfect labyrinth. To ensure that the maze is not trivial to solve, a minimum distance between these edges can be introduced to prevent them from appearing next to each other.

## Aldous-Broder's Algorithm
Let us begin by taking a look at one of the simplest algorithms for creating a perfect labyrinth.
---
title: "Strategic Movements in Infinite Grids: An Analysis of the Cop and Robber Game"
author: "Ryan Donghan Kwon"
date: 2022-05-17
---

# Strategic Movements in Infinite Grids: An Analysis of the Cop and Robber Game

**Ryan Donghan Kwon, *IEEE Student Member* \<ryankwon@ieee.org\>**

## 1. Introduction

The game of cops and robbers, played on graph structures, is a classic topic in the field of combinatorial game theory[^gardner1976mathematical]. In recent years, this topic has garnered significant attention due to its implications in various fields including network security, autonomous navigation, and distributed systems[^quilliot1983jeux][^bonato2011game]. Despite the considerable body of research in this area, the problem becomes notably complex when considered on an infinite grid, especially in the context of the cop's and robber's intelligent and strategic movements[^clarke1980cops].

### 1.1 Problem description

In the context of this paper, the problem is defined on an infinite square grid, where the cop and the robber can move to any directly connected grid cell in a turn. The cop and the robber are considered intelligent and move strategically, where the robber aims to evade capture and the cop aims to capture the robber as quickly as possible. The game is played with the robber moving first, followed by the cop. The initial condition is such that the Taxi Geometry distance between the robber and the cop is an even number.

### 1.2 Literature review

Several strategies and results have been proposed for the game of cops and robbers on graphs[^clarke1980cops][^quilliot1983jeux]. However, most of these results do not apply directly to the infinite grid scenario due to its unbounded nature[^bonato2006cops]. There exist some studies that focus on the infinite grid or similar structures[^bonato2011game], but the problem remains non-trivial due to the unrestricted movements of the cop and the robber.

### 1.3 Objective and scope of the paper

The objective of this paper is to analyze the problem of the game of cops and robbers on an infinite grid, considering the optimal strategies for the cop and the robber. The paper aims to provide a generalized solution for the game given the initial conditions, particularly when the Taxi Geometry distance between the cop and the robber is an even number. The findings of this paper can potentially contribute to the existing body of research in combinatorial game theory and provide novel insights into strategic decision-making in infinite, grid-based environments.

## 2. Theoretical Background

### 2.1 Game Theory and its Relevance to the Problem

Game theory, a significant branch of mathematics, involves the study of mathematical models of strategic interaction among rational decision-makers[^osborne2004introduction]. It has wide applications in various fields such as economics, computer science, and political science. In the context of our problem, cops and robbers game, the players' strategic interactions are critical, and an understanding of game theory provides a solid foundation for analyzing these interactions.

### 2.2 Graph Theory and its Application in Grid-based Problems

Graph theory is a fundamental tool used to mathematically represent problems in fields like computer science, operations research, and logistics[^diestel2017graph]. In the game of cops and robbers, the infinite grid can be represented as an infinite graph where each cell corresponds to a vertex and the connections between cells correspond to edges. This graph representation of the problem allows us to leverage the vast body of knowledge and techniques from graph theory to analyze and solve the problem.

### 2.3 The Concept of Distance in Taxi Geometry and its Significance

Taxi Geometry, also known as Manhattan distance, is a metric defined as the sum of the absolute differences of their coordinates[^rosenfeld1969distance]. In an infinite grid, the taxi distance between two cells is the minimum number of moves a player must make to get from one cell to the other. The concept of Taxi Geometry plays a crucial role in determining the strategies of the cop and the robber as they try to minimize and maximize this distance, respectively.

## 3. Problem Analysis

In this section, we dive deeper into the problem at hand, examining the unique constraints and potential strategies each player may employ.

### 3.1 Problem Constraints

The game is conducted on an infinite grid with the following rules:

1. Both players can only move horizontally or vertically by one grid cell per turn.
2. The robber moves first, followed by the cop.
3. Both players are assumed to be rational and always strive to optimize their strategy.

The objective for the cop is to occupy the same cell as the robber, while the robber aims to evade the cop indefinitely.

### 3.2 Robber's Optimal Strategy

Given that the robber moves first, an optimal strategy would involve moving in a way that maximizes the minimum distance from the cop at any given point in time. The robber could achieve this by moving towards grid cells that are as far as possible from the cop and avoiding corners or edges that limit potential escape routes.

### 3.3 Cop's Optimal Strategy

The cop aims to minimize the distance to the robber. An effective strategy might involve predicting the robber's next move based on his previous actions and choosing a path that potentially cuts off the robber's escape routes. It's important to note that since the grid is infinite, the cop cannot merely corner the robber; the cop must also strategically limit the robber's options to evade.

### 3.4 The Role of Parity in the Game

The initial condition of the problem states that the Taxi Geometry distance between the cop and the robber is an even number. This condition plays a significant role in the game because it preserves the parity of the distance between the players throughout the game. The implications of this condition on the players' strategies and the game outcome will be discussed further in the next section.

## 4. Solution Framework

In this section, we propose a general framework for solving the problem. This framework incorporates the theoretical background discussed earlier and applies it to devise strategies for the cop and the robber.

### 4.1 Distance-based Strategy

Given that both the cop and the robber aim to minimize and maximize the Taxi Geometry distance between them, respectively, an effective strategy for both players would involve making moves based on the current distance between them. We propose a distance-based strategy, where each player's move is determined based on the current state of the grid and the position of the other player.

### 4.2 Parity-based Strategy

As noted in the problem analysis section, the parity of the Taxi Geometry distance between the cop and the robber plays a significant role in determining the outcome of the game. With the initial condition that this distance is even, the robber can always ensure to maintain an even distance from the cop by moving in a certain way. Similarly, the cop can strive to reduce this distance while maintaining its evenness.

### 4.3 Robber's Strategy

The robber's strategy involves maximizing the minimum distance from the cop at any point. With the help of the parity-based strategy, the robber can ensure an even distance from the cop, reducing the cop's chances of capturing him. Further, by strategically choosing the direction of movement based on the cop's position and the current state of the grid, the robber can successfully evade the cop.

### 4.4 Cop's Strategy

The cop's strategy, on the other hand, involves minimizing the distance to the robber while preserving the evenness of this distance. This can be achieved by predicting the robber's moves and choosing a path that not only reduces the current distance but also potentially cuts off the robber's escape routes.

The next section will detail the implementation of these strategies and discuss their effectiveness.

## 5. Case Studies

### 5.1 Simulation of various initial settings and strategies
### 5.2 Analysis and discussion of results

## 6. Generalized Solution

### 6.1 Proposal of a general solution for given initial distances
### 6.2 Proof of the solution's effectiveness and limitations
### 6.3 Discussion on the adaptability of the solution

## 7. Conclusion and Future Work

### 7.1 Recap of findings and their implications
### 7.2 Suggestions for future research directions in this field

## References

[^gardner1976mathematical]: Gardner, M. (1970). "Mathematical Games: The fantastic combinations of John Conway's new solitaire game 'life'." *Scientific American*, 223(4), 120-123.

[^quilliot1983jeux]: Quilliot, A. (1983). "Jeux et pointes fixes sur les graphes." Thèse de 3e cycle, Université de Paris VI.

[^bonato2011game]: Bonato, A., & Nowakowski, R. J. (2011). *The Game of Cops and Robbers on Graphs.* American Mathematical Society.

[^clarke1980cops]: Clarke, E. (1980). "The Cops and Robber Game." *American Mathematical Monthly*, 87(5), 347-356.

[^bonato2006cops]: Bonato, A., Gordinowicz, P., Prałat, P. A., & Nowakowski, R. J. (2006). "Cop-win graphs and game chromatic number." *Congressus Numerantium*, 180, 211-221.

[^osborne2004introduction]: Osborne, M. J. (2004). *An Introduction to Game Theory.* Oxford University Press, USA.

[^diestel2017graph]: Diestel, R. (2017). *Graph Theory.* (5th Edition). Springer.

[^rosenfeld1969distance]: Rosenfeld, A., & Pfaltz, J. (1968). "Distance functions on digital pictures." *Pattern Recognition*, 1(1), 33-61.

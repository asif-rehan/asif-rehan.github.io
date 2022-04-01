---
id: 558
title: 'Game Theory Concepts for Reinforcement Learning'
date: '2020-12-07T03:38:25+00:00'
author: 'Asif Rehan'
excerpt: 'There are many flavors of games in Game Theory which are interesting from Machine Learning perspectives, especially from multi-agent Reinforcement Learning applications. Here is the summary of multiple game types are if MinMax algorithm works and what type of strategy one needs to employ.'
layout: revision
guid: 'https://asifrehan.com/538-revision-v1/'
permalink: /538-revision-v1/
---

There are many flavors of games in Game Theory which are interesting from Machine Learning perspectives, especially from multi-agent Reinforcement Learning applications. Here is the summary of multiple game types are if MinMax algorithm works and what type of strategy one needs to employ.

<figure class="wp-block-table is-style-stripes">| **Game ID** | **\#Players** | **Outcome** | **Deterministic**? | **Information** | **\#Round** | **Strategy** |
|---|---|---|---|---|---|---|
| 1 | 2 | Zero-sum | Deterministic | Perfect Information | Single | MinMax works, Pure strategy |
| 2 | 2 | Zero-sum | **Stochastic** | Perfect | Single | MinMax works, Pure strategy |
| 3 | 2 | Zero-sum | Stochastic | **Hidden** | Single | **MinMax does NOT work**, **Mixed Strategy** |
| 4 | 2 | **Non-zero sum** | Stochastic | Hidden | outcome is same for every round | Solve for Nash Equilibrium, Pure or mixed |
| 5 | 2 | **zero-sum** | Stochastic | Hidden | defined by gamma | With finite states, it is a [Markov Decision Process.](https://asifrehan.com/wp-admin/post.php?post=254&action=edit) Solve [Minimax-Q algorithm](http://people.virginia.edu/~sdp5f/CSRG/publications/793_fall04/Seminar06RL.pdf) |
| 6 | 2 or more | Non-zero sum | Stochastic | Not-hidden | Defined by gamma | Active Research! |

</figure>## Comments on Strategy

**Game ID#4:** If strongly dominant strategy is present, then pure strategy might work or else might need a mixed strategy

**Game ID#5:**  For small number of rounds (gamma~=0), betrayal might provide more reward, but for infinite number of rounds (gamm~=1), cooperation yields more reward

## **Interesting Facts from the Theory** 

1. Tit-for-Tat is not [subgame perfect](https://en.wikipedia.org/wiki/Subgame_perfect_equilibrium) when considering a longer future time horizon! It means it can give itself more rewards overall if it does not choose to retribute against the other player! So forgiveness is a better virtue! This forgiving strategy is called Pavlov state machine!
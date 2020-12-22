# Reinforcement Learning

Python notebook: https://github.com/daviskregers/data-science-recap/blob/main/22-reinforcement-learning.ipynb

- You have some sort of agent that explores some space
- As it goes, it learns the value of different state changes in different conditions
- Those values inform subsequent behaviour of the agent
- Examples: Pac-Man, Cat & mouse game
- Yields fast on-line performance once the space has been expored

## Q-learning

- A specific implementation of reinforcement learning
- You have:
    - A set of enviromental variables `s`
    - A set of possible actions in those states `a`
    - A value of each state/action `Q`
- Start off with Q values of 0
- Explore the space
- As bad things happen after a given state/action, reduce it's `Q`
- As rewards happen after a given state/action - increase it's `Q`

- What are some state/actions here?
    - Pac-man has a wall to the west
    - Pac-man dies if he moves one step south
    - Pac-man just continues to live if going north or east
- You can "look ahead" more than one step by using a discount factor when computing Q (here s is previous state, s' is current state.
- $Q(s,a) += discount * (reward(s,a) + max(Q(s')) - Q(s,a))$

## The exploration problem

- How do we efficiently explore all of the possible states?
    - Simple approach: always choose the action for a given state with the highest Q. If there's a tie, choose at random.
        - But that's really inefficient, and you might miss a lot of paths that way.
    - Better way:
        - If a random number is less than epsilon, don't follow the highest Q, but choose at random
        - That way, exploration never totally stops
        - Choosing epsilon can be tricky.

## Recap

- You can make an intellingeng pac-man in a few steps:
    - Have it semi-randomly explore different choices of movement (actions) given different conditions (states)
    - Keep track of the reward or penalty associated with each choice for a given state/action (Q)
    - Use those stored Q values to inform it's future choices

## Implementing Reinforcement Learning

- Python Markov Decision Process toolbox:
    - https://pymdptoolbox.readthedocs.io/en/latest/
- Cat&mouse example:
    - https://github.com/studywolf/blog/tree/master/RL/Cat%20vs%20Mouse%20exploration

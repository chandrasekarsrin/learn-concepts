# Design patterns

- bit more conceptual.
- helps software developers to solve commonly occuring problems like experts do.
- already proven by experts.
- helps to create design vocabulary.

## Gang of Four : Design Patterns: Elements of Reusable Object oriented software.
- Contains number of patterns and solutions.
- There are 23 problems and solutions in this book.
- Categories of problems:
    - creational ( how objects are created)
    - structural patterns ( how objects are connected and they are interacting)
        - decomposition and generalization
        - association, composition, inhertience, aggregation and interface relationships.
        - analogy: food with ingredients pairings.
        - various suitable relationships between objects
    - Bheavioural pattern (how objects distribute work)
        - how independent objects works towards a single goal.
        - analogy: game plan in a race track. 

## Creational Patterns
### SingletonPatterns
- having only one object for a class.
- only single object should be created for a class.
    - example: user preferences in a game. 
1. make the constructor private.
1. declare a class variable and make it private.

### Facade pattern:
- does not add more functionality
- act as a point of entry to your subsystem.
- wrapper class that ecnapsulates client subsystem by hiding the complexity.


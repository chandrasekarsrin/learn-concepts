# Object Oriented Analysis and Design
- Why we need OOAD or infact design ?
    - reuse
    - easy maintenabiity
    - extensablity without ripple effects

# Software Design vs Architecture
- Design: outlining a software solution to a specific problem. by designing the details of indvidual components and responsibilities. low level design
- Architecture: system design. higher level aspects of a system.

## Keep it simple:
- probably good chance of getting it right.
- its easy to explain to someone.

## Object oriented modelling
- practice of representing key concepts as objects in your software.
- way of keeping your code organized and flexible.
- think everything in your system as objects.

For example, if you emagine a Seminar room here are the objects that you can think of:
- room
- chair
- table
- projector
- white board

- all the living and non living things are represented as objects.
- each objects knows about its details.
- think objects.

## Conceptual and Technical design
- spend time on requirement analysis and design. they are critical.

- Eliciting requirements
    - asking more questions to clarify it enough.
- Outlining design
    - Conceptual Mockups (helps to clarify requirements)  (object oriented analysis)
        - identify major compoents and differ technical details.
        - define components responsibility and associated(colloborators) responsiblity.
    - Technical Diagrams   ( helps to communicate the design during implementation.)  (object oriented design)
        - technical details for each components.
        - refine conceptual mockups during the design. because now you have better context on what works and what not.

User story is one powerful technique to represent requiremnts. 
Example:
Imagine that you introduce the user story technique to your customer, and they give you the following sentence:

As an online shopper, I want to add an item to my shopping cart, so that I can purchase it.

Usually, the nouns correspond to objects in your software. So in this example, you have identified three objects: first, the user role is associated with an object in the software (the online shopper). An item could be any product at the store, while a shopping cart is an object for tracking items for purchase.

Let's have another look at the sentence:

As an online shopper, I want to add an item to my shopping cart, so that I can purchase it.

Verbs can help you identify the requirements that your objects might have. In this example, add and purchase might be responsibilities of the shopping cart. Verbs may also help you identify connections between objects.

The last point is a bit more subtle: a user story can also help you discover connections between objects. In this example, it is probably fairly obvious. One online shopper is typically associated with one shopping cart. The shopping cart should be capable of holding multiple items.

As a OCI cloud customer i want to create build stage so that i can setup continuous integration.

Customer
Build stage
   build source
   
## Categories of  Objects:
- entity objects
    - corespond to real world entity in problem space
- boundary objects
    - objects that deals with another software system.
    - the other system could be user, internet, another software system etc..
- control objects
    - responsible for coordination between objects
    - Example: mediator object simply coordinates between different objects so that they are loosely coupled.

- organizing your software into these categories of objects gives better reusablity, maintainability and flexibility.
- when you start desigining your software first you will identify entity objects later when it gets big other objects might be required to make it more flexible.

## Competing qualities and tradeoffs
- balancing between convinience, performance and security.
- Context is very important to decide on such tradeoffs.
- design review can help unintended consequences.
- competing qualities should be balanced.

## Record, organize and refine components (conceptual design)
- Identify 
    - components
    - responsibilities
    - connections
- interatively improve the design by identifying complex components and breaking it down.

CRC cards: 
- Class Responsibility Collaborator cards.
- techinique to do conceptual design

## Object modelling representation:
- goals of the software design is to identify models of all the objects
- models are represented in UML diagram

## Language
Imperative pradigm: (fortan and cobol) : 1960s
- global data and
- break larger programs into smaller subroutines directly accessing glboal variables.
- computing was costly so above helps to optimize it.
- somtimes global data will not be there as expected by subroutines.

Algo68 & Pascal
- local variables was introduced.
- Abstract data types was introduced. it helps to group related data together and define a type.
- it helps to organize data in a meaningful way.

mid 1970s, computing is less expensive and humans more expensive:
- one file per program becomes a problem now days.
- C and modular 2 came with way to organize program into seperate files.
- developer can declare abstract data type but there he cannot extend existing types(for example inheritence, polymorphism etc..).

1980s object oriented design:
- make Abstract data type easier to write.
- structure a system around ADT called classes.
- extend ADT with concept called inheritance.
- now we can build software with real world objects.
- Java, C++, C# was created using object oriented design.

## Principles of Object oriented Design
### Abstraction
- only expose essential details.
- should define abstract data type, its attributes, behaviours.
- abstractions are formed with the context
- they are not fixed , evolve it over time.

### Encapsulation
- binding data and functions together.
- attributes and methods.
- methods access attributes.
- helps with data integrity.

### Decomposition
- break the whole system into small parts and identify relationships
- fixed or dynamic, sharing, lifetime of the object.
    - association  (very loose)
        - some relationship
        - their relationship will only exist for sometime.
        - example: a relationship between person and airline.
        - straight line with cardinality
        - one exist without existence of the other.
        - ```dotnetcli
        public class Food {
            public void pair(Wine wine) {
            }
        }
        ```
    - aggregation 
        - 'has a' relationship
        - weak relationship.
        - they can both exist without other.
        - a empty daimond will show which one is a whole.
        - ```dotnetcli
        public class PetStore{
              private List<Pet> pets;
  
              public Employee(){
                    this.pets = new ArrayList<>();;
              }
              public void addPet(Pet pet) {
                    this.pets.add(pet);
            }
        }
    - composition
        - strong 'has a' relationship.
        - whole cannot exist without its parts
        - filled daimond will show which one is whole.
        - ```dotnetcli
        public class Employee{
              private Salary salary;
  
              public Employee(Salary employeeSalary){
                    this.salary = employeeSalary;
              }
        }
        ```

### Generaisation
- helps to reuse
- can be achieved through
    - inheritence
    - methods
- dont repeat yourself 
- Generalizatoin using inheritance
    - solid line arrow. super class are always at the top. array will be on the super class side.
- Generalization using interface
    - dotted line arrow.

## Technical design
- UML diagrams (class diagram) much closer to implementation.
    - attributes with + public
    - attributes with - private
    - attributes with # protected
- class diagram and its relationships.
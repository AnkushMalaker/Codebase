# Inheritance

Represents an "IS-A" relationship, or a parent child relationship.

## Syntax for intheritance

`class Subclass-name extends Superclass-name{//methods}`

## Types

1. Single B -> A
2. Multilevel C -> B -> A
3. Hierarchial (C, B) -> A
4. Multiple (not supported in Java through class) C -> (A,B)
5. Hybrid D -> (B,C) -> A

# Aggregation

Represents a "HAS-A" relationship.  
For example, Employee HAS-A address, where address is a different class with its own attributes.  
In above example, we'd have to say `Address empAddress;` in the Employee definition to use the address class.

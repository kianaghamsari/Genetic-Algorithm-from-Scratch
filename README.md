# Genetic Algorithm from Scratch — Expression Solver

A genetic algorithm (GA) implemented from scratch in Python to construct a mathematical
expression that evaluates as close as possible to a given target value.

> This project was originally developed as part of a university assignment and later published for reference.

---

## Problem Description (with Example)

The goal is to automatically generate a mathematical expression using:
- a fixed list of **numbers**
- a fixed list of **operators**
- a fixed number of **expression slots**

such that the final expression evaluates to a **target value**.

### Example Input
```

Numbers:    [1, 2, 3, 4, 5, 6, 7, 8]
Operators:  [+ , - , *]
Slots:      21
Target:     18019

```

Each candidate solution (chromosome) represents a valid expression like:
```

6 * 7 * 6 * 6 * 6 * 2 - 8 * 2 * 7 - 7 - 6

```

Which evaluates to:
```

18019

```

The genetic algorithm evolves such expressions over generations to minimize:
```

fitness = | target − evaluated_expression |

```

---

## Approach

- **Chromosome Representation**  
  Alternating sequence of numbers and operators:
```

[number, operator, number, operator, ..., number]

````

- **Fitness Function**  
Absolute difference between the evaluated expression and the target value.

- **Selection**  
Elitism strategy: top-performing chromosomes are preserved each generation.

- **Crossover**  
Two-point crossover between parent chromosomes.

- **Mutation**  
Random gene replacement:
- numbers mutate to numbers
- operators mutate to operators

- **Stopping Conditions**
- Exact solution found (fitness = 0)
- Maximum number of generations reached
- No improvement for several generations

---

## How to Run

You will be prompted to enter:

* number of slots
* allowed numbers
* allowed operators
* target value

---

## Example Output

During execution, the algorithm prints the best expression per generation:

```
Generation 28:
Best Expression: 6*7*6*6*6*2-8*2*7-7-6
Fitness: 0
```

The program stops once an exact match is found.

---

## Notes

* This implementation uses Python `eval()` for simplicity.
* For production-grade usage, a safe expression parser should be used instead.

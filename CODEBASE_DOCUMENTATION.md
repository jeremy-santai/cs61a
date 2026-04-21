# CS 61A Codebase Documentation

## Overview

This repository contains solution implementations for CS 61A: Structure and Interpretation of Computer Programs at UC Berkeley. The codebase includes four major projects that progressively teach fundamental computer science concepts: recursion, object-oriented programming, data structures, and interpreters.

## Table of Contents

1. [Project Structure](#project-structure)
2. [Projects](#projects)
3. [Core Concepts](#core-concepts)
4. [File Organization](#file-organization)
5. [Usage Guide](#usage-guide)

---

## Project Structure

The repository is organized as follows:

```
cs61a/
├── codebases/           # Main project implementations
│   ├── hog.py          # Hog dice game project
│   ├── ants.py         # Ants vs SomeBees tower defense game
│   ├── cats.py         # Typing test implementation
│   ├── scheme_*.py     # Scheme interpreter implementation
│   └── ...
├── resources/          # Project summaries and course materials
│   └── projects/       # High-level project documentation
├── notes/              # Study notes and exam preparation
├── history/            # Historical references and course materials
└── README.md           # Repository overview
```

---

## Projects

### 1. **The Game of Hog** (`hog.py`)

**Purpose:** Teach recursion, control flow, and strategy development through a dice game simulation.

**Key Components:**

#### Core Functions
- **`roll_dice(num_rolls, dice=six_sided)`**
  - Simulates rolling dice `num_rolls` times
  - Returns the sum of all outcomes
  - **Special Rule:** If any roll is 1, return 1 (Pig Out rule)
  - Used for basic game mechanics

- **`boar_brawl(player_score, opponent_score)`**
  - Calculates bonus points when rolling 0 dice
  - Formula: `3 × |last_digit(player_score) - last_digit(opponent_score)|`
  - Returns minimum of 1 point
  - Encourages risky play decisions

- **`take_turn(num_rolls, player_score, opponent_score, dice=six_sided)`**
  - Main turn-taking function that coordinates game rules
  - If `num_rolls == 0`, calls `boar_brawl()`
  - Otherwise, calls `roll_dice()`
  - Respects game constraints (0-10 dice per turn)

#### Advanced Rules
- **`sus_points(score)` and `sus_update()`**
  - Sus Fuss rule: Special scoring for certain prime number configurations
  - Adds strategic depth to score management

#### Strategy Functions
- **`always_roll(n)`**
  - Returns a strategy function that always rolls `n` dice
  - Example: `strategy = always_roll(3)` creates a player who always rolls 3 dice

- **`catch_up(score, opponent_score)`**
  - Rolls 5 dice if ahead, 6 dice if behind
  - Simple competitive strategy

- **`is_always_roll(strategy, goal=GOAL)`**
  - Determines if a strategy always chooses the same number of dice
  - Tests strategy consistency across all possible game states

#### Game Execution
- **`play(strategy0, strategy1, update, score0=0, score1=0, dice=six_sided, goal=GOAL)`**
  - Simulates a complete game between two strategies
  - Returns final scores as `(score0, score1)`
  - Manages turn alternation and goal checking

#### Analysis Functions
- **`make_averaged(original_function, samples_count=1000)`**
  - Higher-order function that returns averaged version of any function
  - Samples `original_function` `samples_count` times with given arguments
  - Used for statistical analysis of strategy performance

- **`max_scoring_num_rolls(dice=six_sided, samples_count=1000)`**
  - Determines optimal number of dice (1-10) to maximize average score
  - Balances risk (rolling 1s) vs. reward (higher rolls)

**Key Concepts Taught:**
- Conditional logic (if/else, while loops)
- Function composition
- Higher-order functions
- Statistical reasoning
- Game theory basics

---

### 2. **Ants vs. SomeBees** (`ants.py`)

**Purpose:** Teach object-oriented programming through a tower defense game.

**Core Class Hierarchy:**

#### Base Classes

- **`Place`**
  - Represents a location on the game board
  - Attributes: `name`, `exit` (next place), `entrance` (previous place), `ant`, `bees`
  - Methods: `add_insect()`, `remove_insect()`
  - Special attribute: `is_hive` (True only for the hive)

- **`Insect`** (Abstract base class)
  - Base for all insects (ants and bees)
  - Attributes: `health`, `place`, `damage`, `is_waterproof`, `doubled`
  - Key Methods:
    - `reduce_health(amount)`: Damages insect and removes if health ≤ 0
    - `action(gamestate)`: Defines insect behavior each turn
    - `add_to(place)`: Places insect in a location
    - `remove_from(place)`: Removes insect from location
    - `double()`: Doubles damage if not already doubled

#### Ant Classes (Protected Colony)

- **`Ant`** (Base ant class)
  - Attributes: `food_cost` (resources required), `is_container` (can hold other ants), `implemented` (ready to use)
  - Methods: `construct()` (factory method), `can_contain()`, `store_ant()`, `remove_ant()`
  - Abstract implementation system prevents unimplemented ants from being used

- **`HarvesterAnt`**
  - **Action:** Produces 1 additional food per turn
  - **Cost:** 2 food
  - **Purpose:** Resource generation
  - **Code:** Simply increments `gamestate.food` by 1

- **`ThrowerAnt`** (Ranged attacker)
  - **Attributes:**
    - `damage`: 1 point per throw
    - `food_cost`: 3 food
    - `upper_bound`, `lower_bound`: Range limits (can be overridden)
  - **Key Methods:**
    - `nearest_bee()`: Scans places backward toward hive to find nearest bee in range
    - `throw_at(target)`: Reduces target bee's health by damage
  - **Action:** Throws at nearest bee in range

- **`ShortThrower`** (Close-range variant)
  - **Extends:** `ThrowerAnt`
  - **Range:** 0-3 places
  - **Cost:** 2 food (cheaper than standard ThrowerAnt)

- **`LongThrower`** (Long-range variant)
  - **Extends:** `ThrowerAnt`
  - **Range:** 5+ places
  - **Cost:** 2 food

- **`FireAnt`** (Area damage)
  - **Damage:** 3 points
  - **Cost:** 5 food
  - **Action:** Damages all bees in its place when it dies
  - **Special Behavior:** `reduce_health()` override to apply AoE damage to all bees in location

- **`WallAnt`** (Tank/Blocker)
  - **Health:** 4 (double normal ant)
  - **Cost:** 4 food
  - **Purpose:** Strategic placement to block bee advancement

- **`HungryAnt`** (High-burst damage)
  - **Cost:** 4 food
  - **Action:** Instantly kills a bee but needs 3 turns to digest
  - **Attributes:** `chewing_turns` (cooldown period), `turns_to_chew` (current cooldown)
  - **Limitation:** Can't attack while digesting

- **`ContainerAnt`** (Composite pattern)
  - **Attribute:** `is_container = True`
  - **Method:** `can_contain(other)`: Returns True if can hold another ant
    - Cannot contain other container ants
    - Can only hold one ant
  - **Methods:** `store_ant()`, `remove_ant()`
  - **Purpose:** Allows multiple ants per location for advanced strategies

**Bee Mechanics:**
- Bees attack from the hive, moving through Places toward the exit
- Each bee has health and damages ants they encounter
- Multiple bees can occupy the same place
- Bees are removed when health reaches 0

**Game State:**
- `gamestate.food`: Available food for buying ants
- Turn-based system: All ants act, then all bees act
- Victory condition: Eliminate all incoming bees
- Defeat condition: Bee reaches exit

**Key Concepts Taught:**
- Object-oriented design patterns
- Inheritance and method overriding
- Polymorphism
- Game state management
- Resource management (food economy)

---

### 3. **Typing Test** (`cats.py`)

**Purpose:** Teach functional programming and string manipulation through typing statistics.

**Core Functions:**

#### Phase 1: Basic Statistics

- **`pick(paragraphs, select, k)`**
  - Selects the k-th paragraph that satisfies `select` predicate
  - **Recursive Implementation:** Tests each paragraph recursively
  - Returns empty string if fewer than k matching paragraphs
  - **Usage:** `pick(texts, lambda p: len(p) < 50, 2)` gets 3rd short paragraph

- **`about(subject)`**
  - **Returns:** A predicate function that checks if paragraph contains subject words
  - **Inner Function:** `contain(paragraph)` → searches for any subject word
  - **Case-Insensitive:** Converts all text to lowercase
  - **Punctuation-Agnostic:** Removes punctuation before analysis
  - **Usage:** `about_dogs = about(['dog', 'pup']); about_dogs('I have a dog!')`

- **`accuracy(typed, source)`**
  - Calculates typing accuracy as percentage of words typed correctly
  - **Formula:** `(correct_words / total_typed_words) × 100`
  - **Edge Cases:**
    - Empty typed string: 0% unless source is also empty (100%)
    - Extra words typed: Counted as wrong, lowers accuracy
    - Missing words: Not counted in denominator
  - **Example:** Typing "Cute Dog!" vs "Cute Dog." = 50% (2/4 words match)

- **`wpm(typed, elapsed)`**
  - Calculates Words Per Minute
  - **Formula:** `(num_characters / 5) / (elapsed_seconds / 60)`
  - Standard: 5 characters = 1 word
  - **Validation:** `elapsed > 0` required

#### Phase 2A: Autocorrection with Diff Functions

- **`autocorrect(typed_word, word_list, diff_function, limit)`**
  - Suggests closest word from dictionary based on diff function
  - Returns `typed_word` if difference exceeds `limit`
  - **Tie-breaking:** First matching word in dictionary wins
  - **Algorithm:** Iterates through word_list, finds minimum difference
  - **Uses:** Custom diff functions to quantify "closeness" between words

- **`feline_fixes(typed, source, limit)`**
  - **Diff Function:** Counts substitutions needed + length difference
  - **Substitution Rule:** Match characters at same positions
  - **Length Difference:** Added to total diff if words are different lengths
  - **Example:** 
    - "nice" → "rice" = 1 (one substitution)
    - "rose" → "hello" = 5 (4 substitutions + 1 length difference)
  - **Optimization:** Uses early termination when limit exceeded

#### Phase 2B: Edit Distance (Levenshtein)

- **`minimum_mewtations(typed, source, limit)`**
  - Calculates **Edit Distance** (Levenshtein distance)
  - Allows three operations:
    1. **Addition:** Insert character from source
    2. **Removal:** Delete character from typed
    3. **Substitution:** Replace character
  - **Dynamic Logic:** Returns minimum cost among three operations
  - **Pruning:** Stops if operations would exceed limit
  - **Example:** "cats" → "scat" = 2 (add 's', remove 's')
  - **Base Cases:**
    - Empty typed or source: Return length difference
    - Operations exceeded: Return 1 if strings differ

#### Phase 3: Multiplayer Progress Tracking

- **`report_progress(typed, source, user_id, upload)`**
  - Tracks typing test progress
  - **Progress Metric:** `correct_words / total_source_words`
  - **Upload Function:** Called with dict containing `id` and `progress`
  - **Returns:** Final progress as float (0.0 to 1.0)
  - **Example:** Typed 3/5 words correctly = 0.6 progress

- **`time_per_word(times, words)`**
  - Calculates time elapsed per word typed
  - **Input:** List of timestamps and list of words
  - **Output:** List of times for each word (time[i+1] - time[i])

**Utility Functions:**
- Uses from `utils` module:
  - `lines_from_file(filename)`: Read text from file
  - `lower(string)`: Convert to lowercase
  - `remove_punctuation(string)`: Strip punctuation
  - `split(string)`: Split into words

**Key Concepts Taught:**
- Functional programming (higher-order functions, recursion)
- String processing and parsing
- Algorithm design (edit distance, dynamic programming)
- Performance metrics
- Data structures for caching (memoization patterns)

---

### 4. **Scheme Interpreter** (`scheme_*.py`)

**Purpose:** Teach interpreter design, functional programming, and language implementation.

**Files:**
- `scheme_classes.py`: Object representations for Scheme values
- `scheme_forms.py`: Special form implementations (if, define, lambda, etc.)
- `scheme_eval_apply.py`: Core evaluation and application logic

**Key Components:**

#### Evaluation Model

- **`eval(expr, env)`**
  - Evaluates Scheme expressions in given environment
  - Handles:
    - **Literals:** Numbers, strings, booleans
    - **Variables:** Symbol lookup in environment
    - **Function Calls:** Evaluate and apply
    - **Special Forms:** if, define, lambda, quote, etc.

- **`apply(func, args, env)`**
  - Applies evaluated function to evaluated arguments
  - Handles:
    - **Built-in Functions:** Mathematical operations, list operations
    - **User-Defined Functions:** Lambda expressions and defined procedures
    - **Argument Binding:** Creates new environment for function

#### Special Forms

Special forms are evaluated differently (not all arguments evaluated immediately):

- **`if`**: Conditional evaluation
  - `(if condition consequent alternative)`
  - Only evaluates branch taken

- **`define`**: Variable and function definition
  - `(define x 5)` creates variable
  - `(define (square x) (* x x))` creates function

- **`lambda`**: Anonymous function creation
  - `(lambda (x) (* x x))` creates square function
  - Returns procedure object

- **`quote`**: Prevents evaluation
  - `(quote (1 2 3))` returns list, not evaluated
  - `'(1 2 3)` shorthand notation

- **`begin`**: Sequence evaluation
  - Evaluates multiple expressions in order
  - Returns last value

- **`let`**: Local variable binding
  - `(let ((x 5) (y 10)) (+ x y))`
  - Creates local scope

#### Built-in Procedures

- **Arithmetic:** `+`, `-`, `*`, `/`, `%`, `**`
- **Comparison:** `<`, `>`, `=`, `<=`, `>=`
- **List Operations:** `cons`, `car`, `cdr`, `list`, `append`, `length`
- **Type Checking:** `number?`, `symbol?`, `list?`, `pair?`
- **Logic:** `and`, `or`, `not`

#### Environment Model

- **`Environment`**: Maps symbols to values
- **Frames:** Stack of environments for scoping
- **Lookup:** Searches from current frame up through parent frames
- **Set:** Updates variable in environment where it was defined

**Key Concepts Taught:**
- Interpreter design
- Parsing and evaluation
- Environment and scoping
- Functional programming principles
- Meta-programming (writing programs that process programs)

---

## Core Concepts

### Concepts by Project

| Concept | Hog | Ants | Cats | Scheme |
|---------|-----|------|------|--------|
| Recursion | ✓ | - | ✓ | ✓ |
| OOP/Classes | - | ✓ | - | - |
| Higher-Order Functions | ✓ | - | ✓ | ✓ |
| String Manipulation | - | - | ✓ | ✓ |
| Functional Programming | ✓ | - | ✓ | ✓ |
| Game Simulation | ✓ | ✓ | - | - |
| Data Structures | ✓ | ✓ | ✓ | ✓ |
| Interpreter Design | - | - | - | ✓ |

### Programming Patterns

1. **Higher-Order Functions**
   - Functions that take/return functions
   - Used in: `make_averaged()`, `about()`, `always_roll()`

2. **Strategy Pattern**
   - Different behaviors for same interface
   - Used in: Hog strategies, different ant types

3. **Factory Pattern**
   - Creating objects through factory methods
   - Used in: `Ant.construct()`

4. **Container Pattern**
   - Objects holding other objects
   - Used in: `ContainerAnt`, place holding ants/bees

5. **Recursion**
   - Functions calling themselves
   - Used in: Most algorithms throughout codebase

---

## File Organization

### By Type

**Game Projects:**
- `hog.py` - Dice game strategy
- `ants.py` - Tower defense game

**Language Projects:**
- `cats.py` - Text analysis and correction
- `scheme_*.py` - Language interpreter

**Study Materials:**
- `notes/` - Exam prep and key takeaways
- `resources/` - Lesson notes and project summaries
- `history/` - Past exam questions

### By Functionality

**Core Logic:**
- Game rules and mechanics
- Class definitions and inheritance
- Algorithm implementations

**Strategy/AI:**
- Player strategies (Hog)
- Ant placement algorithms (Ants)

**Utilities:**
- Helper functions for testing
- Input/output handling
- Data processing

---

## Usage Guide

### Running Individual Projects

#### Hog Game
```python
# Run with default strategies
from codebases.hog import play, always_roll_5, sus_update, six_sided

# Simulate a game
scores = play(always_roll_5, always_roll_5, sus_update)
print(f"Final scores: {scores}")

# Test strategy analysis
from codebases.hog import max_scoring_num_rolls
optimal_rolls = max_scoring_num_rolls()
print(f"Optimal dice to roll: {optimal_rolls}")
```

#### Ants vs SomeBees
```python
from codebases.ants import HarvesterAnt, ThrowerAnt, FireAnt, Place

# Create game board
exit = Place("Exit")
board = Place("Place_0", exit)
hive = Place("Hive")
hive.is_hive = True

# Place ants
harvester = HarvesterAnt()
board.add_insect(harvester)
```

#### Typing Test
```python
from codebases.cats import accuracy, wpm

# Test accuracy
acc = accuracy("Cute Dog!", "Cute Dog.")
print(f"Accuracy: {acc}%")

# Calculate WPM
speed = wpm("hello friend hello buddy hello", 15)
print(f"WPM: {speed}")
```

#### Scheme Interpreter
```python
from codebases.scheme_eval_apply import eval

# Evaluate expressions
result = eval(parse("(+ 2 3)"), global_env)
print(result)  # 5
```

### Testing

Each project includes problem-specific test cases:

```python
# Docstring tests
python3 -m doctest codebases/hog.py

# Specific function test
python3 -m doctest codebases/hog.py -v
```

---

## Key Takeaways

### Programming Fundamentals
1. **Control Flow:** if/else, loops, recursion
2. **Data Types:** Primitives, sequences, objects
3. **Functions:** Definition, application, higher-order functions
4. **Scope:** Local vs global, closures, environments

### Software Design
1. **Abstraction:** Hide complexity behind simple interfaces
2. **Composition:** Combine simple components into complex systems
3. **Inheritance:** Reuse code through class hierarchies
4. **Separation of Concerns:** Each component has single responsibility

### Algorithm Design
1. **Correctness:** Implement precise specifications
2. **Efficiency:** Consider time and space complexity
3. **Trade-offs:** Balance different design goals
4. **Testing:** Verify behavior with diverse test cases

---

## Additional Resources

- **Lecture Notes:** See `resources/lessons/` for chapter notes
- **Exam Practice:** See `notes/practice-final.md` and `history/` for past exams
- **Project Details:** See `resources/projects/` for project-specific summaries
- **Key Concepts:** See `notes/cs61a-key-takeaways.md` for concept review

---

## Contributing

When modifying code:
1. Maintain existing docstring format
2. Keep functions focused and single-purpose
3. Add comments for non-obvious logic
4. Update relevant test cases
5. Test your changes thoroughly

---

**Last Updated:** 2024
**Course:** CS 61A - Structure and Interpretation of Computer Programs
**Institution:** UC Berkeley

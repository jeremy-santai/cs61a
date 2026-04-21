# CS 61A Architecture & Design Guide

## System Architecture Overview

```
┌─────────────────────────────────────────────────────────────┐
│                     CS 61A Codebase                         │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ┌──────────────┐  ┌────────────────┐  ┌──────────────┐   │
│  │   Hog Game   │  │ Ants vs Bees   │  │ Typing Test  │   │
│  │    (Hog)     │  │   (Ants)       │  │   (Cats)     │   │
│  └──────────────┘  └────────────────┘  └──────────────┘   │
│                                                             │
│  ┌─────────────────────────────────────────────────────┐   │
│  │        Scheme Interpreter (Scheme)                 │   │
│  │  ┌──────────────────────────────────────────────┐  │   │
│  │  │  Parsing → Evaluation → Application         │  │   │
│  │  │  ┌────────┐  ┌──────────┐  ┌────────────┐  │  │   │
│  │  │  │ Lexer  │→ │ Parser   │→ │ Evaluator  │→ App  │  │
│  │  │  └────────┘  └──────────┘  └────────────┘  │  │   │
│  │  └──────────────────────────────────────────────┘  │   │
│  └─────────────────────────────────────────────────────┘   │
│                                                             │
│  Supporting Systems:                                       │
│  • Game simulation engines                                 │
│  • String processing & analysis                           │
│  • Environment/scope management                           │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## Project Design Patterns

### 1. Hog Game Architecture

```
Game Simulation Layer
├── Core Game Logic
│   ├── roll_dice()          [Probability]
│   ├── take_turn()          [Game Rules]
│   ├── boar_brawl()         [Bonus Rules]
│   └── sus_points()         [Special Rules]
│
├── Game Loop
│   └── play()               [Orchestration]
│
├── Strategy Layer
│   ├── always_roll()        [Simple Strategy]
│   ├── catch_up()           [Complex Strategy]
│   ├── is_always_roll()     [Strategy Analysis]
│   └── winner()             [Strategy Comparison]
│
└── Analysis Layer
    ├── make_averaged()      [Statistical Analysis]
    ├── max_scoring_num_rolls() [Optimization]
    └── average_win_rate()   [Performance Metrics]
```

**Design Principles:**
- **Separation of Concerns:** Logic, strategy, and analysis are separate
- **Composability:** Strategies combine with game logic
- **Testability:** Each function has clear input/output
- **Extensibility:** New strategies can be added without modifying core

**Data Flow:**
```
Strategy (scores) 
    ↓
    → decide rolls
    ↓
take_turn() 
    ↓
    → calculate points
    ↓
play() 
    ↓
    → update scores & check win condition
```

### 2. Ants vs Bees Architecture

```
Object Model
├── Spatial Model
│   └── Place Network
│       ├── name: str
│       ├── exit: Place
│       └── entrance: Place
│
├── Entity Hierarchy
│   ├── Insect (Abstract Base)
│   │   ├── health: int
│   │   ├── place: Place
│   │   ├── action(gamestate)
│   │   └── reduce_health(amount)
│   │
│   ├── Ant (Extends Insect)
│   │   ├── food_cost: int
│   │   ├── implemented: bool
│   │   ├── is_container: bool
│   │   └── construct(gamestate)
│   │   │
│   │   ├── HarvesterAnt        [Resource Generation]
│   │   ├── ThrowerAnt          [Ranged Attacker]
│   │   │   ├── ShortThrower    [Close Range]
│   │   │   └── LongThrower     [Long Range]
│   │   ├── FireAnt             [Area Damage]
│   │   ├── WallAnt             [Tank]
│   │   ├── HungryAnt           [One-shot Killer]
│   │   └── ContainerAnt        [Composite Container]
│   │
│   └── Bee (Not implemented, for reference)
│       └── advance()
│
└── Game State
    ├── food: int               [Resource pool]
    ├── time: int               [Turn counter]
    └── places: List[Place]     [Board state]
```

**Design Principles:**
- **Inheritance Hierarchy:** Common behavior in base classes
- **Polymorphism:** Different ants behave differently via method overriding
- **Encapsulation:** Place manages ants and bees
- **Factory Pattern:** `construct()` creates ants with validation
- **Container Pattern:** ContainerAnt demonstrates composition

**Turn Sequence:**
```
Each Turn:
1. Ants Act
   - All ants call action(gamestate)
   - Ants interact with environment
   
2. Bees Act
   - All bees move/attack
   - Bees reduce ant health
   
3. Cleanup
   - Remove dead insects
   - Update game state
   
4. Check End Condition
   - Victory: All bees dead
   - Defeat: Bee reaches exit
```

### 3. Typing Test Architecture

```
Text Processing Pipeline
├── Data Input Layer
│   ├── lines_from_file()    [I/O]
│   └── split()              [Tokenization]
│
├── Text Normalization Layer
│   ├── lower()              [Case Normalization]
│   └── remove_punctuation() [Symbol Removal]
│
├── Analysis Layer
│   ├── Filtering
│   │   ├── pick()           [Select paragraphs]
│   │   └── about()          [Predicate creation]
│   │
│   ├── Metrics
│   │   ├── accuracy()       [Word match %]
│   │   └── wpm()            [Speed metric]
│   │
│   └── Comparison
│       ├── feline_fixes()   [Substitution diff]
│       └── minimum_mewtations() [Edit distance]
│
├── Correction Layer
│   ├── autocorrect()        [Spell checker]
│   └── diff_function        [Distance metric]
│
└── Tracking Layer
    └── report_progress()    [User progress]
```

**Design Principles:**
- **Pipeline Architecture:** Data flows through transformation stages
- **Higher-Order Functions:** Predicates customize filtering
- **Functional Composition:** Combine simpler functions
- **Metrics-Driven:** Statistics guide corrections

**Algorithm Layers:**

```
Simple Diff (feline_fixes)
├── Compare characters at same positions
├── Count substitutions needed
└── Add length difference

Complex Diff (minimum_mewtations)
├── Consider insertions (add character)
├── Consider deletions (remove character)
├── Consider substitutions (replace character)
└── Return minimum-cost operation
```

### 4. Scheme Interpreter Architecture

```
Interpreter Pipeline
│
├─ 1. LEXING (Text → Tokens)
│   ├── Tokenize input
│   ├── Skip whitespace/comments
│   └── Output: Token stream
│
├─ 2. PARSING (Tokens → AST)
│   ├── Read expressions
│   ├── Handle lists, atoms, symbols
│   └── Output: S-Expression tree
│
├─ 3. EVALUATION (AST + Environment → Value)
│   ├── eval(expr, env)
│   │   ├── Literals → return value
│   │   ├── Symbols → lookup in environment
│   │   ├── Special Forms → handle specially
│   │   │   ├── if: evaluate condition first
│   │   │   ├── define: register in environment
│   │   │   ├── lambda: create procedure
│   │   │   └── quote: return unevaluated
│   │   └── Function Call → evaluate & apply
│   │
│   └── Environment Stack
│       ├── Global Frame
│       ├── Function Frame 1 (bindings)
│       ├── Function Frame 2 (bindings)
│       └── ... (local scopes)
│
└─ 4. APPLICATION (Function + Arguments → Result)
    ├── apply(func, args, env)
    │   ├── Built-in: Direct operation
    │   ├── User-defined: Create frame + evaluate body
    │   └── Return: Result value
    │
    └── Output: Final value

Example Evaluation:
    (define (square x) (* x x))
    (square 5)
    
    Parse:  (square 5)
    Eval:   Look up square → get (lambda (x) (* x x))
    Apply:  Create {x: 5}, eval (* x x) → 25
```

**Environment Model:**

```
Global Environment
├── x: 10
├── square: λ(x) → (* x x)
└── ...

When calling (square 5):
    ┌─────────────────┐
    │ {x: 5}          │ ← Function frame
    │ parent: Global  │
    └─────────────────┘
           ↓
    Evaluates (* x x) with x=5 → 25
```

---

## Data Flow Diagrams

### Hog Data Flow

```
┌──────────────────┐
│ Starting Scores  │
│ (0, 0)           │
└────────┬─────────┘
         │
         ├─→ Strategy0 Decides Rolls
         │        │
         │        └─→ take_turn()
         │             ├─→ roll_dice() or boar_brawl()
         │             └─→ sus_points() [if enabled]
         │                  │
         ├─→ Update Score0  │
         │        │         │
         ├─→ Check Win?     │
         │        │         │
         ├─→ Switch Players │
         │        │         │
         └─→ Strategy1 Decides Rolls
                  │
                  └─→ [Repeat...]

Final: (Score0, Score1) when either ≥ GOAL
```

### Ants Data Flow

```
┌─────────────────┐
│ Game State      │
│ • food: 30      │
│ • places: [..] │
│ • time: 0       │
└────────┬────────┘
         │
         ├─→ Player Action
         │   ├─→ Select Ant Type
         │   ├─→ Check Cost
         │   └─→ Place at Location
         │        │
         ├─→ Game Tick
         │   ├─→ Ants Act
         │   │   ├─→ HarvesterAnt: food += 1
         │   │   ├─→ ThrowerAnt: throw at nearest_bee()
         │   │   └─→ [other actions]
         │   │
         │   ├─→ Bees Act
         │   │   ├─→ Move/Attack
         │   │   └─→ Reduce ant health
         │   │
         │   ├─→ Cleanup
         │   │   └─→ Remove dead insects
         │   │
         │   └─→ Check End Condition
         │        ├─→ Victory: No bees remain
         │        └─→ Defeat: Bee reached exit
         │
         └─→ [Repeat if game continues]
```

### Cats Data Flow

```
Input: typed="Cute Dog!"
       source="Cute Dog."

    ├─→ Tokenize & Normalize
    │   └─→ ["cute", "dog"] (lowercase, split)
    │
    ├─→ Compare with Source
    │   └─→ ["cute", "dog"] (source tokens)
    │
    ├─→ Calculate Accuracy
    │   ├─→ correct: 1 ("cute" matches, "dog" doesn't)
    │   ├─→ total: 2
    │   └─→ accuracy: 1/2 × 100 = 50%
    │
    └─→ Output: 50.0
```

---

## Module Dependency Graph

```
hog.py
├── Depends on: dice module (six_sided)
├── Depends on: ucb module (main decorator)
└── Self-contained otherwise

ants.py
├── Depends on: random (shuffle)
├── Depends on: collections.OrderedDict
├── Depends on: ucb module (interact)
└── Object model is self-contained

cats.py
├── Depends on: datetime
├── Depends on: ucb module (main decorator)
├── Depends on: utils module
│   ├── lines_from_file()
│   ├── lower()
│   ├── remove_punctuation()
│   └── split()
└── Core algorithms are self-contained

scheme_*.py (Interpreter)
├── scheme_eval_apply.py (core engine)
│   └── Uses: scheme_forms.py & scheme_classes.py
├── scheme_forms.py (special forms)
│   └── Uses: scheme_classes.py
└── scheme_classes.py (data structures)
    └── Self-contained
```

---

## Class Hierarchy Diagram

### Insect Class Hierarchy

```
                        Insect
                    (abstract base)
                        │
           ┌────────────┴────────────┐
           │                         │
          Ant                       Bee
           │              (represented in game)
           │
    ┌──────┼──────┬────────┬────────┬────────────┐
    │      │      │        │        │            │
Harvester Thrower Fire    Wall    Hungry    ContainerAnt
Ant       Ant     Ant     Ant     Ant
    │
    ├──────┬──────┐
    │      │      │
Short   Long  (base)
Thrower Thrower
```

**Inheritance Relationships:**

```
Ant
├── food_cost, implemented, is_container (class attrs)
├── __init__, construct, can_contain (methods)
└── Specialized subclasses override:
    ├── action() [unique behavior]
    ├── food_cost [resource cost]
    ├── implemented [enable in game]
    └── Special attributes as needed
```

---

## State Management

### Hog State

```
Immutable Approach:
- Scores: (int, int) - treated as immutable
- Strategy state: Functions have no internal state
- Side effects: Dice rolling produces random values
- Update mechanism: Return new scores, don't modify

# This is good:
new_score = old_score + take_turn(num_rolls, old_score, opp_score)

# Avoid:
score_holder.add_to_score(take_turn(...))  # If possible
```

### Ants State

```
Mutable Approach:
- Place network: Objects with mutable references
- Insect placement: Objects moved between places
- Health values: Updated in-place
- Food pool: Mutable integer

# State update cycle:
place.ant = new_ant           # Ant placed
ant.health -= damage          # Damage applied
place.remove_insect(ant)      # If dead

# Environment accessed via:
gamestate.food               # Resource pool
gamestate.time               # Turn counter
```

### Cats State

```
Functional Approach:
- Input strings: Immutable
- Processing: Pure functions return new strings/values
- State tracking: Environment manages progress

# Process:
original_text = "The quick fox"
lowered_text = lower(original_text)  # New string
cleaned_text = remove_punctuation(lowered_text)  # New string
words = split(cleaned_text)  # New list

# No modification of original
```

---

## Testing Architecture

### Test Strategy by Project

**Hog Testing:**
- **Unit Tests:** Individual functions (roll_dice, take_turn)
- **Integration Tests:** Full game (play() function)
- **Strategy Tests:** Analyze strategy behavior
- **Statistical Tests:** Verify probabilities over many samples

**Ants Testing:**
- **Unit Tests:** Individual ant types and actions
- **Integration Tests:** Game board interactions
- **Regression Tests:** Board state after actions
- **Gameplay Tests:** Full game scenarios

**Cats Testing:**
- **Unit Tests:** Individual functions (accuracy, wpm)
- **Comparison Tests:** Diff functions with known data
- **Integration Tests:** Full typing test flow
- **Edge Cases:** Empty strings, special characters

**Scheme Testing:**
- **Parsing Tests:** Correctly parse expressions
- **Evaluation Tests:** Evaluate to correct values
- **Environment Tests:** Scope and binding
- **Special Forms Tests:** Control flow behavior

---

## Performance Characteristics

### Time Complexity Analysis

| Operation | Complexity | Notes |
|-----------|-----------|-------|
| `roll_dice(n)` | O(n) | Rolls n times |
| `take_turn()` | O(n) | Calls roll_dice or boar_brawl |
| `play()` | O(g × n) | g=turns to goal, n=roll_dice complexity |
| `nearest_bee()` | O(d) | d=distance to hive |
| `accuracy()` | O(n) | n=number of words |
| `feline_fixes()` | O(n×m) | n,m=string lengths |
| `minimum_mewtations()` | O(n×m) | n,m=string lengths |
| Scheme eval | O(n) | n=expression size |

### Space Complexity Analysis

| Operation | Complexity | Notes |
|-----------|-----------|-------|
| `make_averaged()` | O(1) | Constant per sample |
| Ants board | O(p + a + b) | p=places, a=ants, b=bees |
| Scheme environment | O(v) | v=variables in scope |
| Edit distance | O(n×m) | Can be memoized/optimized |

---

## Extensibility Points

### Where to Add Features

**Hog Extensions:**
```python
# New game rules: Modify sus_points() logic
# New strategies: Implement function returning 0-10
# Custom dice: Pass alternative dice function

def six_sided_weighted():
    """Return weighted dice (more 6s)"""
    return random.choices([1,2,3,4,5,6], weights=[1,1,1,1,1,3])[0]

play(my_strategy, opp_strategy, sus_update, dice=six_sided_weighted)
```

**Ants Extensions:**
```python
# New ant types: Subclass Ant and implement action()
class SniperAnt(ThrowerAnt):
    name = "Sniper"
    food_cost = 6
    damage = 2
    implemented = True
    upper_bound = float("inf")  # Infinite range
    
    def action(self, gamestate):
        # Find strongest bee instead of nearest
        pass

# New effects: Override reduce_health() in Insect subclass
```

**Cats Extensions:**
```python
# Custom diff functions: Return integer difference
def phonetic_diff(typed, source, limit):
    """Diff based on pronunciation similarity"""
    # Compare phonetic sounds instead of letters
    pass

autocorrect(typed_word, word_list, phonetic_diff, 5)
```

**Scheme Extensions:**
```python
# New special forms: Add case in eval()
if is_special_form(expr, 'my-form'):
    # Handle my-form specially
    pass

# New built-ins: Add to global environment
global_env.update({'my-function': my_python_function})
```

---

## Best Practices

### Code Organization

1. **Logical Grouping:** Related functions together
2. **Clear Naming:** Function names describe behavior
3. **Docstrings:** Explain purpose, arguments, return value
4. **Type Hints:** (When available) Clarify expected types
5. **Constants:** Named constants for magic numbers

### Error Handling

1. **Assertions:** Check preconditions in functions
2. **Type Checking:** Verify input types
3. **Boundary Testing:** Handle edge cases
4. **Error Messages:** Clear, actionable error text

### Maintainability

1. **DRY (Don't Repeat Yourself):** Extract common patterns
2. **Single Responsibility:** One function = one purpose
3. **Composition:** Build complex behavior from simple parts
4. **Documentation:** Update when code changes
5. **Testing:** Test all public functions

---

**Last Updated:** 2024
**For:** CS 61A - Structure and Interpretation of Computer Programs

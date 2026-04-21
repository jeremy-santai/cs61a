# CS 61A Implementation Guide

## Getting Started

### Prerequisites

- Python 3.6+
- Basic understanding of recursion and OOP
- Familiarity with command line

### Running Code

```bash
# Run entire file (auto-executes main)
python3 codebases/hog.py

# Run specific tests
python3 -m doctest codebases/hog.py

# Debug specific function
python3 -c "from codebases.hog import roll_dice; print(roll_dice(3))"

# Interactive REPL
python3
>>> from codebases.hog import *
>>> play(always_roll(5), always_roll(6), sus_update)
```

---

## Detailed Implementation Walkthrough

### Hog Implementation

#### Phase 1: Dice Rolling

**Understand First:**
- Roll_dice simulates actual dice
- If any roll is 1, immediately return 1
- Otherwise sum all rolls

**Implementation Steps:**

```python
def roll_dice(num_rolls, dice=six_sided):
    """Simulate rolling NUM_ROLLS dice"""
    assert type(num_rolls) == int, "num_rolls must be an integer."
    assert num_rolls > 0, "Must roll at least once."
    
    # Start with 0 sum
    total = 0
    
    # Roll each die
    for _ in range(num_rolls):
        roll_result = dice()  # Get one die result
        
        # If we rolled a 1, return immediately
        if roll_result == 1:
            # BUT: still need to roll remaining dice (for side effects)
            # Roll remaining times to consume RNG sequence
            for _ in range(num_rolls - 1):
                dice()  # Call but don't use result
            return 1
        
        # Add to running total
        total += roll_result
    
    return total
```

**Key Points:**
- Must call `dice()` exactly `num_rolls` times (RNG consistency)
- Return 1 immediately if any roll is 1
- Sum all rolls otherwise

#### Phase 2: Boar Brawl Bonus

**Understand First:**
- When rolling 0 dice, get bonus points
- Bonus = 3 × difference of last digits
- Minimum bonus is 1

**Implementation:**

```python
def boar_brawl(player_score, opponent_score):
    """Return bonus points for rolling 0 dice"""
    # Get last digit of each score
    p_digit = player_score % 10
    o_digit = opponent_score % 10
    
    # Calculate difference
    diff = abs(p_digit - o_digit)
    
    # Apply formula: 3 × diff, minimum 1
    bonus = 3 * diff
    
    return max(1, bonus)  # At least 1
```

**Edge Cases to Test:**
```python
boar_brawl(48, 45)  # |8-5| = 3, so 3×3 = 9
boar_brawl(10, 15)  # |0-5| = 5, so 3×5 = 15
boar_brawl(10, 10)  # |0-0| = 0, so max(1, 0) = 1
```

#### Phase 3: Take Turn

**Understand First:**
- Coordinates between rolling and boar brawl
- If rolling 0 dice, use boar brawl
- Otherwise, roll dice

**Implementation:**

```python
def take_turn(num_rolls, player_score, opponent_score, dice=six_sided):
    """Return points scored this turn"""
    assert type(num_rolls) == int, "num_rolls must be an integer."
    assert num_rolls >= 0, "Cannot roll negative dice."
    assert num_rolls <= 10, "Cannot roll more than 10 dice."
    
    if num_rolls == 0:
        # Use Boar Brawl rule
        return boar_brawl(player_score, opponent_score)
    else:
        # Roll the dice
        return roll_dice(num_rolls, dice)
```

#### Phase 4: Sus Fuss Rule

**Understand First:**
- Special rule for prime-related scoring
- If score has 3 or 4 factors, find next prime
- Apply to total score (not just turn points)

**Implementation:**

```python
def is_prime(n):
    """Check if n is prime"""
    if n < 2:
        return False
    if n == 2:
        return True
    if n % 2 == 0:
        return False
    
    for divisor in range(3, int(n**0.5) + 1, 2):
        if n % divisor == 0:
            return False
    return True

def num_factors(n):
    """Count factors of n"""
    count = 0
    for i in range(1, n + 1):
        if n % i == 0:
            count += 1
    return count

def sus_points(score):
    """Apply Sus Fuss rule to score"""
    factor_count = num_factors(score)
    
    # If 3 or 4 factors, find next prime
    if factor_count == 3 or factor_count == 4:
        while not is_prime(score):
            score += 1
    
    return score

def sus_update(num_rolls, player_score, opponent_score, dice=six_sided):
    """Update score including Sus Fuss rule"""
    # Calculate points earned this turn
    turn_points = take_turn(num_rolls, player_score, opponent_score, dice)
    
    # Add to current score
    new_score = player_score + turn_points
    
    # Apply Sus Fuss rule
    final_score = sus_points(new_score)
    
    return final_score
```

#### Phase 5: Game Loop

**Understand First:**
- Players alternate turns
- Use strategy functions to decide rolls
- Use update function to apply game rules
- Stop when someone reaches goal

**Implementation:**

```python
def play(strategy0, strategy1, update, score0=0, score1=0, dice=six_sided, goal=GOAL):
    """Simulate a complete game"""
    
    while score0 < goal and score1 < goal:
        # Player 0's turn
        rolls = strategy0(score0, score1)  # Ask strategy how many to roll
        score0 = update(rolls, score0, score1, dice)  # Apply rules
        
        # Player 1's turn
        rolls = strategy1(score1, score0)  # Note: reversed scores for opponent perspective
        score1 = update(rolls, score1, score0, dice)  # Apply rules
    
    return (score0, score1)
```

#### Phase 6: Strategy Analysis

**Higher-Order Functions:**

```python
def always_roll(n):
    """Return a strategy that always rolls n dice"""
    def strategy(score, opponent_score):
        return n
    return strategy

# Usage:
my_strategy = always_roll(5)
print(my_strategy(50, 45))  # Always returns 5

def catch_up(score, opponent_score):
    """Roll 5 if ahead, 6 if behind"""
    if score < opponent_score:
        return 6  # Try to catch up
    else:
        return 5  # Play it safe
```

**Statistical Analysis:**

```python
def make_averaged(original_function, samples_count=1000):
    """Return averaged version of a function"""
    def averaged_func(*args):
        total = 0
        for _ in range(samples_count):
            total += original_function(*args)
        return total / samples_count
    return averaged_func

# Usage:
average_roll = make_averaged(roll_dice, 100)
print(average_roll(3))  # Average of rolling 3 dice 100 times

def max_scoring_num_rolls(dice=six_sided, samples_count=1000):
    """Find optimal number of dice (1-10) to maximize score"""
    average_roller = make_averaged(roll_dice, samples_count)
    
    best_rolls = 1
    best_score = 0
    
    for num_rolls in range(1, 11):
        avg_score = average_roller(num_rolls, dice)
        if avg_score > best_score:
            best_score = avg_score
            best_rolls = num_rolls
    
    return best_rolls
```

---

### Ants Implementation

#### Core Class Structure

**Place Class:**

```python
class Place:
    """Represents a location on the board"""
    
    def __init__(self, name, exit=None):
        self.name = name
        self.exit = exit      # Next place (toward exit)
        self.bees = []        # List of bees here
        self.ant = None       # Single ant (or container)
        self.entrance = None  # Previous place
        
        # Link bidirectionally
        if exit is not None:
            exit.entrance = self
    
    def add_insect(self, insect):
        """Add an insect to this place"""
        insect.add_to(self)
    
    def remove_insect(self, insect):
        """Remove an insect from this place"""
        insect.remove_from(self)
```

**Insect Base Class:**

```python
class Insect:
    """Base class for all insects"""
    
    damage = 0
    is_waterproof = False
    doubled = False
    
    def __init__(self, health, place=None):
        self.health = health
        self.place = place
    
    def reduce_health(self, amount):
        """Damage the insect"""
        self.health -= amount
        
        # Remove if dead
        if self.health <= 0:
            self.death_callback()
            self.place.remove_insect(self)
    
    def action(self, gamestate):
        """Do action each turn (override in subclasses)"""
        pass
    
    def add_to(self, place):
        """Add self to place"""
        self.place = place
    
    def remove_from(self, place):
        """Remove self from place"""
        self.place = None
```

#### Ant Implementations

**HarvesterAnt (Simple):**

```python
class HarvesterAnt(Ant):
    name = "Harvester"
    implemented = True
    food_cost = 2
    
    def action(self, gamestate):
        """Produce food each turn"""
        gamestate.food += 1
```

**ThrowerAnt (Requires Logic):**

```python
class ThrowerAnt(Ant):
    name = "Thrower"
    implemented = True
    damage = 1
    food_cost = 3
    upper_bound = float("inf")
    lower_bound = float("-inf")
    
    def nearest_bee(self):
        """Find nearest bee in range"""
        place = self.place
        distance = 0
        
        # Walk backward through places toward hive
        while not place.is_hive:
            # Check if bee here and in range
            if place.bees:  # If bees in this place
                in_range = self.lower_bound <= distance <= self.upper_bound
                if in_range:
                    return random.choice(place.bees)
            
            # Move to next place backward
            place = place.entrance
            distance += 1
        
        return None  # No bee found
    
    def throw_at(self, target):
        """Throw at target if exists"""
        if target is not None:
            target.reduce_health(self.damage)
    
    def action(self, gamestate):
        """Throw at nearest bee"""
        self.throw_at(self.nearest_bee())
```

**Range Variants:**

```python
class ShortThrower(ThrowerAnt):
    name = "Short"
    food_cost = 2
    implemented = True
    upper_bound = 3  # Can't throw more than 3 away

class LongThrower(ThrowerAnt):
    name = "Long"
    food_cost = 2
    implemented = True
    lower_bound = 5  # Can only throw 5+ away
```

**Special Abilities:**

```python
class FireAnt(Ant):
    name = "Fire"
    damage = 3
    food_cost = 5
    implemented = True
    
    def reduce_health(self, amount):
        """When fire ant dies, burn bees in place"""
        # Make copy of bee list (will be modified)
        bees_to_burn = list(self.place.bees)
        
        # Call parent reduce_health (handles death)
        super().reduce_health(amount)
        
        # If we died, burn all bees
        if self.health <= 0:
            for bee in bees_to_burn:
                bee.reduce_health(amount + self.damage)
```

**Container Pattern:**

```python
class ContainerAnt(Ant):
    is_container = True
    
    def __init__(self, *args, **kwargs):
        super().__init__(*args, **kwargs)
        self.ant_contained = None
    
    def can_contain(self, other):
        """Check if can hold another ant"""
        # Can't contain other containers or if already holding
        return not other.is_container and self.ant_contained is None
    
    def store_ant(self, ant):
        """Store ant inside"""
        self.ant_contained = ant
    
    def remove_ant(self, ant):
        """Remove stored ant"""
        if self.ant_contained is ant:
            self.ant_contained = None
```

---

### Cats Implementation

#### Phase 1: Text Selection

**Pick Function:**

```python
def pick(paragraphs, select, k):
    """Select kth paragraph matching predicate"""
    
    # Base case: exhausted paragraphs
    if k >= len(paragraphs):
        return ""
    
    # If this paragraph matches, use it
    if select(paragraphs[k]):
        return paragraphs[k]
    
    # Otherwise, try next
    return pick(paragraphs, select, k + 1)
```

**About Function:**

```python
def about(subject):
    """Return function that checks if paragraph contains subject words"""
    
    def contains_subject_word(paragraph):
        # Normalize: lowercase, remove punctuation, split into words
        words = split(lower(remove_punctuation(paragraph)))
        
        # Check if any subject word appears
        for subj_word in subject:
            if subj_word in words:
                return True
        return False
    
    return contains_subject_word

# Usage:
about_dogs = about(['dog', 'pup'])
about_dogs("I have a dog")  # Returns True
about_dogs("I have a cat")  # Returns False
```

#### Phase 2: Metrics

**Accuracy:**

```python
def accuracy(typed, source):
    """Percentage of words typed correctly"""
    
    typed_words = split(typed)
    source_words = split(source)
    
    # Edge case: both empty
    if len(typed_words) == 0 and len(source_words) == 0:
        return 100.0
    
    # Edge case: typed nothing
    if len(typed_words) == 0:
        return 0.0
    
    # Count correct words
    correct = 0
    for i in range(min(len(typed_words), len(source_words))):
        if typed_words[i] == source_words[i]:
            correct += 1
    
    # Calculate percentage
    return (correct / len(typed_words)) * 100
```

**Words Per Minute:**

```python
def wpm(typed, elapsed):
    """Calculate typing speed in words per minute"""
    
    # Standard: 5 characters = 1 word
    words_typed = len(typed) / 5
    
    # Convert seconds to minutes
    minutes_elapsed = elapsed / 60
    
    # WPM = words / minutes
    return words_typed / minutes_elapsed
```

#### Phase 3: Spell Correction

**Simple Diff (Substitutions):**

```python
def feline_fixes(typed, source, limit):
    """Count substitutions needed + length difference"""
    
    # Base case: empty strings
    if typed == "" or source == "":
        return max(len(typed), len(source))
    
    # If no operations left
    if limit == 0:
        return 0 if typed == source else 1
    
    # Characters match: no operation needed
    if typed[0] == source[0]:
        return feline_fixes(typed[1:], source[1:], limit)
    
    # Characters don't match: must substitute
    return 1 + feline_fixes(typed[1:], source[1:], limit - 1)
```

**Complex Diff (Edit Distance):**

```python
def minimum_mewtations(typed, source, limit):
    """Calculate edit distance (min operations to transform typed → source)"""
    
    # Base case: empty strings
    if typed == "" or source == "":
        return max(len(typed), len(source))
    
    # No operations left
    if limit == 0:
        return 0 if typed == source else 1
    
    # Characters match: continue
    if typed[0] == source[0]:
        return minimum_mewtations(typed[1:], source[1:], limit)
    
    # Must do one of three operations:
    
    # 1. Add: insert character from source
    add_cost = 1 + minimum_mewtations(typed, source[1:], limit - 1)
    
    # 2. Remove: delete character from typed
    remove_cost = 1 + minimum_mewtations(typed[1:], source, limit - 1)
    
    # 3. Substitute: replace character
    substitute_cost = 1 + minimum_mewtations(typed[1:], source[1:], limit - 1)
    
    # Return minimum
    return min(add_cost, remove_cost, substitute_cost)
```

**Autocorrect:**

```python
def autocorrect(typed_word, word_list, diff_function, limit):
    """Find best correction from word_list"""
    
    # If word is already in list, return it
    if typed_word in word_list:
        return typed_word
    
    # Find word with smallest difference
    best_word = typed_word
    best_diff = limit + 1  # Start above limit
    
    for word in word_list:
        diff = diff_function(typed_word, word, limit)
        
        # Better match found
        if diff < best_diff:
            best_diff = diff
            best_word = word
    
    # Only return suggestion if within limit
    if best_diff <= limit:
        return best_word
    else:
        return typed_word
```

---

## Common Debugging Techniques

### Print Debugging

```python
# Add strategic prints
def take_turn(num_rolls, player_score, opponent_score, dice=six_sided):
    print(f"DEBUG: num_rolls={num_rolls}, player={player_score}, opp={opponent_score}")
    
    if num_rolls == 0:
        result = boar_brawl(player_score, opponent_score)
        print(f"DEBUG: boar_brawl returned {result}")
        return result
    else:
        result = roll_dice(num_rolls, dice)
        print(f"DEBUG: roll_dice returned {result}")
        return result
```

### Assertion Debugging

```python
def my_function(x):
    # Check precondition
    assert x > 0, f"x must be positive, got {x}"
    assert isinstance(x, int), f"x must be int, got {type(x)}"
    
    # ... implementation
```

### Doctest Usage

```python
# In function docstring:
def square(x):
    """
    Return x squared.
    
    >>> square(5)
    25
    >>> square(-3)
    9
    """
    return x * x

# Run: python3 -m doctest -v my_module.py
```

### Tracing Recursion

```python
def my_recursive_function(n):
    # Base case
    if n <= 1:
        print(f"BASE CASE: n={n}")
        return 1
    
    # Recursive case
    print(f"ENTER: n={n}")
    result = n * my_recursive_function(n - 1)
    print(f"EXIT: n={n}, result={result}")
    return result

# Output shows execution order:
# ENTER: n=3
# ENTER: n=2
# ENTER: n=1
# BASE CASE: n=1
# EXIT: n=2, result=2
# EXIT: n=3, result=6
```

---

## Testing Checklist

Before submitting, test:

- [ ] All doctest examples pass
- [ ] Edge cases handled (empty, single element, max values)
- [ ] Type checking works (wrong type inputs rejected)
- [ ] Assertion messages are clear
- [ ] Recursive functions have proper base cases
- [ ] No infinite loops
- [ ] Performance is acceptable for test inputs
- [ ] Code follows style conventions
- [ ] All functions documented with docstrings

---

## Performance Optimization Tips

### Hog

```python
# ✗ Inefficient: Extra dice rolls
def roll_dice(n):
    for i in range(n):
        result = dice()
        if result == 1:
            return 1  # WRONG: other rolls not called

# ✓ Efficient: All rolls called, early return
def roll_dice(n):
    total = 0
    for i in range(n):
        result = dice()
        if result == 1:
            # Still call remaining dice
            for j in range(i + 1, n):
                dice()
            return 1
        total += result
    return total
```

### Cats

```python
# ✗ Inefficient: Recomputes lower() multiple times
def accuracy(typed, source):
    for word in typed_words:
        if word.lower() == source.lower():  # Called many times

# ✓ Efficient: Normalize once
def accuracy(typed, source):
    typed_words = [w.lower() for w in split(typed)]
    source_words = [w.lower() for w in split(source)]
    # Then compare
```

### Ants

```python
# ✗ Inefficient: Checks all bees repeatedly
def nearest_bee(self):
    for distance in range(100):
        for place in board:
            for bee in place.bees:  # O(n²) or worse

# ✓ Efficient: Walk the chain once
def nearest_bee(self):
    place = self.place
    distance = 0
    while not place.is_hive:
        if place.bees:
            if self.lower_bound <= distance <= self.upper_bound:
                return place.bees[0]
        place = place.entrance
        distance += 1
```

---

**Last Updated:** 2024
**For:** CS 61A - Structure and Interpretation of Computer Programs

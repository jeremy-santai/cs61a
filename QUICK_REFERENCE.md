# CS 61A Quick Reference Guide

## Function Quick Lookup

### Hog.py Functions

| Function | Purpose | Key Args | Returns |
|----------|---------|----------|---------|
| `roll_dice(num_rolls, dice)` | Simulate dice rolls | num_rolls, dice | sum or 1 |
| `boar_brawl(p_score, o_score)` | Get bonus points for 0 rolls | scores | 3×\|digit_diff\| |
| `take_turn(num_rolls, ...)` | Single turn logic | num_rolls, scores | points |
| `sus_update(num_rolls, ...)` | Turn with Sus Fuss rule | num_rolls, scores | new_score |
| `always_roll(n)` | Strategy: always roll n | n | strategy function |
| `catch_up(score, o_score)` | Strategy: catch up logic | scores | 5 or 6 |
| `is_always_roll(strategy)` | Check if strategy is constant | strategy | bool |
| `make_averaged(func, samples)` | Average function output | func, samples | averaged function |
| `max_scoring_num_rolls(dice)` | Find optimal rolls (1-10) | dice | int (1-10) |
| `play(s0, s1, update)` | Full game simulation | strategies, update | (score0, score1) |

### Ants.py Classes

| Class | Purpose | Key Attributes | Key Methods |
|-------|---------|-----------------|------------|
| `Place` | Board location | name, exit, entrance, ant, bees | add_insect, remove_insect |
| `Insect` | Base insect | health, place, damage | reduce_health, action |
| `Ant` | Base ant | food_cost, implemented | construct, can_contain |
| `HarvesterAnt` | Food generator | food_cost=2 | action → +1 food |
| `ThrowerAnt` | Ranged attacker | damage=1, food_cost=3 | nearest_bee, throw_at |
| `ShortThrower` | Close range | range 0-3, cost=2 | (inherits) |
| `LongThrower` | Long range | range 5+, cost=2 | (inherits) |
| `FireAnt` | Area damage | damage=3, cost=5 | reduce_health (AoE) |
| `WallAnt` | Tank ant | health=4, cost=4 | (basic) |
| `HungryAnt` | One-shot kill | cost=4, cooldown=3 | action (with chewing) |
| `ContainerAnt` | Composite pattern | is_container=True | can_contain, store_ant |

### Cats.py Functions

| Function | Purpose | Key Args | Returns |
|----------|---------|----------|---------|
| `pick(paragraphs, select, k)` | Select kth matching paragraph | list, predicate, int | string |
| `about(subject)` | Create word-search predicate | subject words | predicate function |
| `accuracy(typed, source)` | % words correct | strings | float (0-100) |
| `wpm(typed, elapsed)` | Words per minute | string, seconds | float |
| `autocorrect(word, list, diff, limit)` | Spell correction | word, list, function, int | corrected word |
| `feline_fixes(typed, source, limit)` | Substitution diff | strings, int | int (diff) |
| `minimum_mewtations(typed, source, limit)` | Edit distance | strings, int | int (distance) |
| `report_progress(typed, source, uid, upload)` | Track progress | lists, id, callback | float (0-1) |

---

## Common Patterns

### Creating a Custom Hog Strategy

```python
def my_strategy(score, opponent_score):
    """Return number of dice to roll (0-10)"""
    if opponent_score - score > 20:
        return 10  # Risky when behind
    elif score > 80:
        return 1   # Conservative when ahead
    else:
        return 6   # Default

# Test it
from hog import play, sus_update
result = play(my_strategy, always_roll(5), sus_update)
```

### Creating a New Ant Type

```python
class MyAnt(Ant):
    name = "MyAnt"
    food_cost = 3
    implemented = True
    
    def action(self, gamestate):
        """Called once per turn"""
        # Your ant's behavior here
        pass
```

### Calculating String Difference

```python
# Substitution-based difference (feline_fixes)
def my_diff(typed, source, limit):
    # Count how many characters differ
    diff = 0
    for i in range(min(len(typed), len(source))):
        if typed[i] != source[i]:
            diff += 1
    diff += abs(len(typed) - len(source))
    return diff

# Use with autocorrect
correction = autocorrect("speling", word_list, my_diff, 2)
```

---

## Game Rules Reference

### Hog Scoring

| Event | Points |
|-------|--------|
| Roll dice | Sum of rolls |
| Roll a 1 (Pig Out) | 1 point only |
| Roll 0 dice (Boar Brawl) | 3 × \|last_digit(my_score) - last_digit(opp_score)\| (min 1) |

### Ants vs Bees

| Phase | Action |
|-------|--------|
| Ant Action | All ants perform their action |
| Bee Action | All bees move toward exit |
| Removal | Dead insects removed |
| Check Win | Did bees reach exit? |

### Ant Costs (Food)

- HarvesterAnt: 2
- ShortThrower: 2
- LongThrower: 2
- ThrowerAnt: 3
- WallAnt: 4
- HungryAnt: 4
- FireAnt: 5

---

## Debugging Tips

### Hog Issues

**Problem: Function returns wrong values**
```python
# Debug with print statements
def take_turn(num_rolls, player_score, opponent_score, dice=six_sided):
    print(f"num_rolls={num_rolls}, player={player_score}, opp={opponent_score}")
    # ...implementation
```

**Problem: Strategy not working**
```python
# Trace strategy decisions
strategy = my_strategy
print(f"Rolls: {strategy(50, 45)}")  # What does it return?
print(f"Rolls: {strategy(80, 40)}")  # Test edge cases
```

### Ants Issues

**Problem: Ant not appearing**
- Check `implemented = True`
- Check `food_cost` doesn't exceed available food
- Verify `add_to()` is called correctly

**Problem: Bees not dying**
- Verify `damage` > 0
- Check `reduce_health()` is called
- Ensure bee is in correct place

### Cats Issues

**Problem: Accuracy always wrong**
```python
# Debug word comparison
typed_words = split(typed)
source_words = split(source)
print(f"Typed: {typed_words}")
print(f"Source: {source_words}")
```

**Problem: Autocorrect returning wrong word**
- Check diff_function returns valid numbers
- Verify limit is reasonable
- Test tie-breaking with duplicate words

---

## Performance Tips

### Hog Optimization

1. **Averaging:** Use `make_averaged()` for reliable statistics
2. **Strategy Testing:** `is_always_roll()` quickly tests for constant strategies
3. **Sampling:** Use 1000 samples for good balance of speed/accuracy

### Ants Optimization

1. **Bee Lookup:** `nearest_bee()` scans backward efficiently
2. **Container Ants:** Check `is_container` before operations
3. **Health Tracking:** Remove dead insects immediately

### Cats Optimization

1. **Caching:** Edit distance can be memoized for repeated comparisons
2. **Early Stopping:** Feline fixes stops if difference exceeds limit
3. **Preprocessing:** Remove punctuation once, not repeatedly

---

## Test Case Templates

### Hog Testing

```python
# Test a simple turn
from hog import take_turn, six_sided

# No rolls (Boar Brawl)
assert take_turn(0, 48, 45, six_sided) == 9  # 3 * |8-5|

# With rolls
assert take_turn(1, 0, 0, lambda: 5) == 5

# Pig Out
assert take_turn(2, 0, 0, lambda: 1) == 1
```

### Ants Testing

```python
# Create game state
from ants import Place, HarvesterAnt

exit_place = Place("Exit")
place1 = Place("Place_1", exit_place)

# Place ant
ant = HarvesterAnt()
place1.add_insect(ant)
assert place1.ant is ant
```

### Cats Testing

```python
# Test accuracy
assert accuracy("Cute Dog!", "Cute Dog.") == 50.0
assert accuracy("", "") == 100.0
assert accuracy("a", "") == 0.0

# Test WPM
assert wpm("hello friend hello buddy hello", 15) == 24.0
```

---

## Environment Variables & Constants

### Hog
- `GOAL = 100` - Points needed to win
- `six_sided` - Standard die function (1-6)

### Ants
- No critical constants (configurable per game)

### Cats
- `FINAL_DIFF_LIMIT = 6` - Default distance limit

---

## Error Messages & Solutions

| Error | Cause | Solution |
|-------|-------|----------|
| `AssertionError: num_rolls must be an integer` | Wrong type passed | Convert to int or check input |
| `IndexError` in autocorrect | Empty word list | Check list isn't empty |
| `RecursionError` | Infinite recursion | Check base case in recursion |
| `NameError: undefined variable` | Typo in variable | Check spelling and scope |
| `AttributeError: 'NoneType'` | Accessed None object | Add None check before access |

---

## Quick Reference: Key Algorithm Complexities

| Operation | Time | Space | Example |
|-----------|------|-------|---------|
| roll_dice | O(n) | O(1) | n = num_rolls |
| nearest_bee | O(m) | O(1) | m = distance to hive |
| pick (recursive) | O(n) | O(n) | n = paragraphs |
| accuracy | O(n) | O(n) | n = words |
| edit_distance | O(n×m) | O(n×m) | n,m = string lengths |

---

## Study Tips

1. **Understand the Rules:** Before coding, ensure you understand game/algorithm rules
2. **Write Test Cases First:** Define expected behavior before implementation
3. **Use Docstrings:** Read docstrings to understand function contracts
4. **Trace Execution:** Hand-trace code with examples to verify logic
5. **Build Incrementally:** Implement one function at a time, test often
6. **Refactor:** Clean up working code to improve readability
7. **Analyze Complexity:** Think about runtime and space requirements

---

**Last Updated:** 2024
**For:** CS 61A - Structure and Interpretation of Computer Programs

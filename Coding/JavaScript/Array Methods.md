1. `myArr.some(predicate)` returns true *iff  predicate returns true at least once*
2. `myArr.every(predicate)` returns false *iff predicate returns false at least once*
3. Negate some to mimic `none` which does not exist in JS. `!myArr.some(predicate)`
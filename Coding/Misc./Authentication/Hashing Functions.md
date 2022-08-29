- Never store passwords *as is*. Instead, run passwords through a hashing function and store the result.

# Characteristics of a Hash Function
1. *One way function* that is infeasible to invert. i.e. If we get out hands on the hashed result of a password, it would be impossible to reverse engineer the password back.
2. Small change in input yields large change in output.
3. *Deterministic* - same input yields same output.
4. *Extremely unlikely* for two different inputs to yield the same output.
5. Password hash functions are *deliberately show*.

## What is a Password Salt?
- A salt is a *random value* added to a password before we hash it.
- We generate a *random* salt each time before we hash a password.
- The reason is that a lot of people use the *same common passwords* for a lot of sites. If you just hash the passwords we get a lot of repeated hashes which makes them easier to guess.

	
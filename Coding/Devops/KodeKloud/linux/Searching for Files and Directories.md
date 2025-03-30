## locate

- `locate city.txt`
- `sudo updatedb` to update the db to include recent directories/files.

## find

```bash
# find directory/file with the exact name city under /home/user1
find /home/user1 -name city

# find specifically files
find /home/user1 -type f -name city

# find specifically directories
find /home/user1 -type d -name city

# Partial match (case-insensitive)
find /home/user1 -iname '*city*'  
```

## searching within files

### grep

```bash
# partial match b
grep second sample.txt

# case insensitive
grep -i second sample.txt

# searches recursively within a directory
grep -r second /home/user1

# only matches whole word, e.g. does not match example
grep -w exam examples.txt
```
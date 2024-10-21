- key-value store
- best used as a secondary db, e.g. caching
- basically a huge JS object
- do not store stuff you can't afford to lose

## setup
- `docker run -dit --rm --name=my-redis -p 6379:6379 redis:6.0.8`
- `docker exec -it my-redis redis-cli`

## naming convention
To avoid key collisions, one can name keys in the form `user:achang:city`

## commands
- `INCR <key>`
- `DECR <key>`
- `INCRBY <key> 10`
- `DECRBY <key> 10`
- `MSET score1: 10, score2:20`, `MGET score1, score2`
- `EXISTS <key>` returns 1 if key exist, 0 if not
- `DEL <key>`
- `SET <key> <value> XX` set iff key exists
- `SET <key> <value> NX` set iff key does not exist
- `SET fitness:total:btholt 750kj EX 3600` key self deletes in 3600s
- `TYPE <key>` 

## types
so far we have only dealt with strings. Use the following commands to deal with other data types

### list
- `RPUSH notifications:achang "feed the dog" "take out trash"`
- `LRANGE notifications:achang 0 -1` get back the whole list
- `RPOP notifications:achang` remove from right

### hash
- `HMSET btholt:profile title "Principal Program Manager" name "Brian Holt"`
- `HGET btholt:profile title` returns the title
- `HGETALL btholt:profile` return every key value pair

### set
- `SADD colors red blue yellow green black pink brown`
- `SMEMBERS colors` returns the set
- `SISMEMBER colors green` 1 if green is part of colors, 0 otherwise
- 
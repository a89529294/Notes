- `brew install redis`
- `brew services start redis`
- `redis-cli ping` verify its running
- basic usage
```
redis-cli           # Start Redis command line interface
> SET foo bar       # Set a key
> GET foo           # Get a key
> KEYS *            # List all keys
> FLUSHALL          # Clear all data
> exit              # Quit
```
- `brew services stop redis`
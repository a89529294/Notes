*Throttle* fires througout, *debounce* fires at the end.

Lets say we have a limiting rate of `1000ms`. A user is scrolling around for 5 seconds. Assuming scroll events fire every 1ms. A *debounced* function fill only fire at `6000ms`, `1000ms` after the last event. A *throttled* function will fire at `1000ms`,`2000ms`, `3000ms`, `4000ms`, `5000ms`. 
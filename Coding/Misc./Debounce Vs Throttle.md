*Throttle* fires throughout, *debounce* fires at the end.

Lets say we have a limiting rate of `1000ms`. A user is scrolling around for 5 seconds. Assuming scroll events fire every 1ms. A *debounced* function will only fire at `6000ms`, `1000ms` after the last event. A *throttled* function will fire at `1000ms`,`2000ms`, `3000ms`, `4000ms`, `5000ms`. 

- In a **debounce** function, the timer is reset every time the function is invoked. This means the function execution is postponed until after the delay period has passed without any further invocations. This is useful when you want to ensure the function is executed after a certain period of quiet, such as waiting for the user to stop typing in a search box.
    
- In a **throttle** function, once the function is invoked, further invocations will be ignored during the delay period. After the delay period, the function can be invoked again. This is useful when you want to ensure the function is not executed more frequently than a certain rate, such as handling scroll or resize events.
    

So yes, the difference lies in whether or not the timer is reset on subsequent invocations within the delay period. Good observation! 😊
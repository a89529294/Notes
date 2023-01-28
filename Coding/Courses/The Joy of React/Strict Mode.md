Every render *runs twice*, not just mount.
Note that it does so *without* actually unmounting then remounting. It simply runs the function twice *synchronously*. 
If you have a `useEffect` with a cleanup function on first render it will run the effect. On the second render it will run the cleanup then the effect.
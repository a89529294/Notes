- `lsof -i:port_number` find all pids on port_number
- `kill -9 $(lsof -t -i:port_number)` kill all processes on port_number
- `kill -9 pid` kill process identified by pid
- 


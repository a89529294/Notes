- It serves as both a `type` and a `value`
```ts
enum ContractStatus {
	Permanent,
	Temp,
	Apprentice
}
const employeeStatus: ContractStatus = ContractStatus.Temp
console.log(employeeStatus) // 1
console.log(ContractStatus[employeeStatus]) # 'Temp'
```
- Note the two way reference between `1` and `'Temp'` only exists if the values are numbers.
- `ContractStatus.Temp` is of type `ContractStatus`. 
- `ContractStatus` will be converted into a JS object.
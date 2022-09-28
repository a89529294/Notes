Assuming we want to use the *pipeline* operator in our NextJs app.

1. `npm i -D @babel/plugin-proposal-pipeline-operator @babel/core`
2. create a `.babelrc` file and put in the following
```rc
{
"presets": ["next/babel"],
"plugins": [
["@babel/plugin-proposal-pipeline-operator", { "proposal": "fsharp" }]
]
}
```

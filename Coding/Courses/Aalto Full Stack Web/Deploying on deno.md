1. `cd path-to-project`
2. `deployctl deploy --entrypoint=app-run.js`
3. wait for token and project name to be auto generated
4. If you want to update the project re run `deployctl deploy --prod` in the project folder. Without `--prod` you will just deploy to a preview environment.
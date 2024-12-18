Run `pm2 start npm -- run start` or `pm2 start "npm run start"
- `npm`: Indicates that PM2 should run an npm script.
- `-- run start`: Runs the `start` script defined in your `package.json`. 
	Then run `pm2 save` and `pm2 startup`.
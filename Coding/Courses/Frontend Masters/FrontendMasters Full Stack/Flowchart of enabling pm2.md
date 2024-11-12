1. `cd ~`
2. `npm i -g pm2`, possibly need to run `pnpm setup` first.
3. `pm2 start app.js --watch`
4. `pm2 save` then `pm2 startup` setup auto restart, remember to follow the instruction.

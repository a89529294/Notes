```js
const express = require('express');
const cors = require('cors');
const app = express();

// Determine the allowed origin based on the environment
const allowedOrigin = process.env.NODE_ENV === 'development'
  ? 'http://localhost:5173'  // Development frontend URL
  : 'https://your-frontend-domain.com'; // Production frontend URL

// CORS settings
const corsOptions = {
  origin: allowedOrigin,
  methods: ['GET', 'POST', 'PUT', 'DELETE'],
  allowedHeaders: ['Content-Type', 'Authorization'],
  credentials: true, // Allow cookies
  preflightContinue: false,
  optionsSuccessStatus: 200, // For legacy browsers
};

app.use(cors(corsOptions));

// Cookie settings middleware
const isDev = process.env.NODE_ENV === 'development';
app.use((req, res, next) => {
  const cookieOptions = isDev
    ? { httpOnly: true, secure: false, sameSite: 'Lax' }
    : { httpOnly: true, secure: true, sameSite: 'None' };

  res.cookie('yourCookieName', 'cookieValue', cookieOptions);
  next();
});

// Preflight request handler
app.options('*', cors(corsOptions));

// Your routes here...

app.listen(3000, () => console.log('Server running on port 3000'));
```

to run this either in `prod` or `env` mode, 
`NODE_ENV=development node app.js`
`NODE_ENV=production node app.js`

## safari notes
1. uncheck settings->privacy->prevent cross site tracking, if safari is blocking cookies during developement.
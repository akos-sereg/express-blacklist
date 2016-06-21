# express-blacklist

NodeJS Express middleware that rejects incoming traffic from a pre-defined source (blacklist file)<br/>

# Usage

```
$ npm install express-blacklist
```

Setting up your express server with express-blacklist support
```javascript
var blacklist   = require('express-blacklist');

app.use(blacklist.blockRequests('blacklist.txt'));
```


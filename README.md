# express-blacklist

NodeJS Express middleware that rejects incoming traffic from a pre-defined source (blacklist file)<br/>

# Usage

```
$ npm install express-blacklist
```

Setting up your express server with express-blacklist support
```javascript
var blacklist = require('express-blacklist');

app.use(blacklist.blockRequests('blacklist.txt'));
```

# Integrate express-blacklist with [express-defend](https://github.com/akos-sereg/express-defend)

You might want to do this if you want to detect and reject malicious traffic on your site, when an attacker tries to find XSS or Path traversal security issues on your site.

```javascript
var expressDefend = require('express-defend');
var blacklist = require('express-blacklist');

app.use(blacklist.blockRequests('blacklist.txt'));
app.use(expressDefend.protect({ 
    maxAttempts: 5, 
    dropSuspiciousRequest: true, 
    logFile: 'suspicious.log', 
    onMaxAttemptsReached: function(ipAddress, url){
        blacklist.addAddress(ipAddress);
    } 
}));
```

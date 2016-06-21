var blacklist   = require('./express-blacklist');
var defend = require('express-defend');

app.use(blacklist.blockRequests('blacklist.txt'));
app.use(defend.protect({ 
    maxAttempts: 5, 
    dropSuspiciousRequest: true, 
    logFile: 'suspicious.log', 
    onMaxAttemptsReached: function(ipAddress){
        blacklist.addAddress(ipAddress);
    } 
}));
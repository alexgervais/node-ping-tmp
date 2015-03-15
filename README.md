# node-ping

A simple wrapper for performing system ICMP ping in node.js

## Installation

```
npm install alexgervais/node-ping
```

## Support

Supported platforms are `linux` and `darwin` (Mac OSX)

## Options

```node
var options = {
    numeric: true, // Numeric output only. Default is true.
    timeout: 1,    // Timeout, in seconds. Default is 1.
    replies: 1,    // Number of pings to perform. Default is 1.
    extra: []     // Any other options to be passed as-is to the system process. These can be platform-dependant.
}
```

## Usage

### error-first callback pattern

```node
var ping = require('ping');
var options = {};

var hosts = ['192.168.1.1', 'google.com', 'yahoo.com'];
hosts.forEach(function (host) {
    ping.icmp.probe(host, options, function (err, data) {
        var msg = data.alive ? 'host ' + data.host + ' is alive' : 'host ' + data.host + ' is dead';
        console.log(msg);
    });
});
```

### Q promise

```node
hosts.forEach(function (host) {
    ping.icmp.probe(host, options)
    .then(function (res) {
        console.log(res);
    });
});
```

## License

MIT

## Credits

Forked from Daniel Zelisko http://github.com/danielzzz/node-ping

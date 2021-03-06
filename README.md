# Description

Find free port synchronously, useful when you need to get the port directly without callback.

Like config [webpack-dev-server](https://github.com/webpack/webpack-dev-server) with port automatically.

```javascript
module.exports = {
    ...
    output: '...',
    devServer: {
        ...
        port: "a free port"
    }
};
```

# Installation
```
npm install find-port-free-sync --save-dev
```

# Options

## start
`type: number | default: 1`

Start of range to find, should be greater than 0

## end
`type: number | default: 65534`

End of range to find, should be less than 65535

## num
`type: number | default: 1`

Number of ports to find, relates to the return value
- When `num === 1`, return a free random `port` if found, `null` if not
- When `num > 1`, return an array of free `[port]` orderly if found, empty array `[]` if not

## ip
`type: string | default: 0.0.0.0|127.0.0.1`

It will scan local adress by default, specify an ip here

## port
`type: number | default: null`

If port is defined, it will return whether the port is free around `start` `end` `ip` option


## Examples
Find a free port for local address
```javascript
let findFreePort = require('find-port-free-sync');

let port = findFreePort();
```
Find 10 free ports between 10000 and 30000 for 192.168.1.1
```javascript
let findFreePort = require('find-port-free-sync');

let port = findFreePort({
    start: 10000,
    end: 30000,
    num: 10,
    ip: '192.168.1.1'
});
```
Check if a port is free
```javascript
let findFreePort = require('find-port-free-sync');

let portIsOk = findFreePort({
    port: 12345
});
```

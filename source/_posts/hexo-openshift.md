---
title: Connect hexo and Openshift
tags:
 - hexo
 - openshift
Categories:
comments: true
date: 2016-06-08

---
Connect hexo and openshift

It isn't very hard. You just start application with node, then `npm install hexo-cli` and `hexo start` but on hexo start Hard time begins. You can't just run your server. There are problems with ip and port address. I found two commands which u have to join to your `../node_modules/hexo-server/index.js` file so it should looks like:

``` javascript
'use strict';
var PORT = process.env.OPENSHIFT_NODEJS_PORT || 8080;
var IPADDRESS = process.env.OPENSHIFT_NODEJS_IP || '127.0.0.1';
var assign = require('object-assign');

hexo.config.server = assign({
  port: PORT,
  log: false,
  ip: IPADDRESS,
  compress: false,
  header: true
}, hexo.config.server);

hexo.extend.console.register('server', 'Start the server.', {
  desc: 'Start the server and watch for file changes.',
  
...
```
  It is first step, then you have to turn of your running node server. Just kill this process.
  I did it:
``` bash
$ ps aux 
```
Find pid of your node server and then:
``` bash
$ pkill <PID>
```
And run server
``` bash
$ hexo server
```
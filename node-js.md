---
title: How to node.js
kind: article
keywords: nodejs, node, js, javascript, howto
created_at: 2015-aug-12 09:58:00
is_draft: true
---

# node.js

`#!/usr/local/bin/node`

## Process

`process.argv // array, also contains the invoking app/script name`

```js
process.env[(process.platform == 'win32') ? 'USERPROFILE' : 'HOME']
```

`process.platform // string, current running platform, e.g. 'darwin'`

## Callbacks

```js
var fs = require('fs');
var myNumber = undefined;

function addOne(callback) {
	fs.readFile('number.txt', function(err, fileContents) {
		myNumber = parseInt(fileContents);
		myNumber++;
		callback();
	});
}

function logMyNumber() {
	console.log(myNumber);
}

addOne(logMyNumber);
```

## Modules

Group functionality into modules.

```js
// themodule.js, exports a single function
module.exports = function(blah, callback) {
	// do some blah
	if (err) // if an error occurs, early out
		return callback(err);

	callback(null, someResult);
};


// test.js
var themodule = require('./themodule'); // .js not needed

themodule('blah!', function(err, result) {
	/* ... */
});
```

## File System

```js
var fs = require('fs');

Synchronous filesystem method names end with 'Sync'.

var myBuffer = fs.readFileSync('path/to/file.txt').toString();
```

### Paths

```js
var path = require('path');

console.log(path.extname('somefile.txt')); // '.txt'
```

### Inter Process Communication

```js
var ipc = require('ipc');

// send event
ipc.send('some-event');

// handle event
ipc.on('some-event', function() {
	// blah
});
```

## Useful NPM modules

Q - promises-based async programming
node-drawille - drawing in terminal with unicode braille characters

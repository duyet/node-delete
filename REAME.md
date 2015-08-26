# node-delete

Delete files, folders in Nodejs using globs.

It also protects you against deleting the current working directory and above.


## Install

```sh
$ npm install --save node-delete
```

## Usage

```js
var del = require('node-delete');

del(['tmp/*.js', '!tmp/duyetdev.js'], function (err, paths) {
	console.log('Deleted files/folders:\n', paths.join('\n'));
});
```


## Beware

The glob pattern `**` matches all children and *the parent*.

So this won't work:

```js
del.sync(['public/assets/**', '!public/assets/goat.png']);
```

You have to explicitly ignore the parent directories too:

```js
del.sync(['public/assets/**', '!public/assets', '!public/assets/goat.png']);
```

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

del(['tmp/*.js', '!tmp/d.js'], function (err, paths) {
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


## API

### del(patterns, [options], callback)
### del.sync(patterns, [options])

The async method gets an array of deleted paths as the second argument in the callback, while the sync method returns the array.

#### options

Type: `object`

See the node-glob [options](https://github.com/isaacs/node-glob#options).

#### options.force

Type: `boolean`  
Default: `false`

Allow deleting the current working directory and files/folders outside it.

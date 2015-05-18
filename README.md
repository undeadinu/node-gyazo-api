Gyazo-API
=========
[Gyazo API](https://gyazo.com/api/docs) wrapper for Node.js

- https://github.com/shokai/node-gyazo-api
- https://www.npmjs.org/package/gyazo-api

[![Build Status](https://travis-ci.org/shokai/node-gyazo-api.svg?branch=master)](https://travis-ci.org/shokai/node-gyazo-api)


Usage
-----

Register new application and get [ACCESS TOKEN](https://gyazo.com/oauth/applications), then

### upload("filepath") or upload("stream")

```javascript
var Gyazo  = require('gyazo-api');
var client = new Gyazo('ACCESS_TOKEN');

client.upload('/path/to/file.jpg')
.then(function(res){
  console.log(res.data.image_id);
  console.log(res.data.permalink_url);
})
.catch(function(err){
  console.error(err);
});
```

### list

```javascript
client.list({page: 1, per_page: 50})
.then(function(res){
  console.log(res.data[0]);
  console.log(res.response.headers['x-current-page']); // => 1
  console.log(res.response.headers['x-per-page']);     // => 50
})
.catch(function(err){
  console.error(err);
});
```

### delete

```javascript
client.delete(image_id)
.then(function(res){
  console.log(res.data.image_id);
});
```


Test
----

setup

    % npm install
    % export GYAZO_TOKEN=a1b2cdef3456   ## set your API Token

run test

    % npm test

or

    % grunt


Contributing
------------
1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

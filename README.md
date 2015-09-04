# simpledi-async

## API

### `di.get(name)`

#### Example:

```javascript
var myConfig = di.get('myConfig');
```

### `di.get(name, callback)`

#### Example:

```javascript
di.get('myConfigFromCdn', function(error, config) {
  // do something with config
});
```

### `di.register(name, function)`

#### Example:

```javascript

// Example: sync
di.register('myConfig', function() {
  return {
    config: true
  }
});

// Example: async
di.register('myConfig', function(done) {
  xhr('http//config.js', done)
});
```

### `di.register(name, function, dependencies)`

#### Example:

```javascript

// Example: sync
di.register('myConfig', function(otherConfig) {
  return {
    otherConfig: otherConfig
    config: true
  }
}, ['otherConfig']);

// Example: async
di.register('myConfig', function(cdnUrl, done) {
  xhr(cdnUrl + '/config.js', done)
}, ['cdnUrl']);
```

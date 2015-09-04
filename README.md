# simpledi-async

## API

### `di.get(name)`

Synchronously resolves dependencies.

**Warning:** There can't be any async dependencies in the chain. If an async dependency is detected it will throw an error.

#### Example:

```javascript
var myConfig = di.get('myConfig');
```

### `di.get(name, callback)`

Asynchronously resolves dependencies.

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

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
### `di.registerAsync(name, function)`

#### Example:

```javascript

// Example: sync
di.register('myConfig', function() {
  return {
    config: true
  }
});

// Example: async
di.registerAsync('myConfig', function(done) {
  xhr('http//config.js', done)
});
```

### `di.register(name, dependencies, function)`
### `di.registerAsync(name, dependencies, function)`

#### Example:

```javascript

// Example: sync
di.register('myConfig', ['otherConfig'], function(otherConfig) {
  return {
    otherConfig: otherConfig
    config: true
  }
});

// Example: async
di.registerAsync('myConfig', ['cdnUrl'], function(cdnUrl, done) {
  xhr(cdnUrl + '/config.js', done)
});
```

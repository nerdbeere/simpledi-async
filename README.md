# simpledi-async

## API

### `di.get(name)`

#### Example:

```javascript
var myConfig = di.get('myConfig');
```

### `di.get(name, callback)`

```javascript
di.get('myConfigFromCdn', function(error, config) {
  // do something with config
});
```

### `di.register(name, function)`

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

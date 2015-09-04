# simpledi-async

## API

### `di.get(name)`;

#### Example:

```javascript
var myConfig = di.get('myConfig');
```

### `di.get(name, callback)`;

```javascript
di.get('myConfig', function(error, config) {
  // do something with config
});
```

### `di.register(name, function)`;

### `di.register(name, function, dependencies)`;

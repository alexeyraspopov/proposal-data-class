# Immutable Data Class for ECMAScript

Inspired by [Kotlin/Scala Data Classes](https://kotlinlang.org/docs/reference/data-classes.html).

See approximate implementation [here](https://github.com/alexeyraspopov/dataclass).

Example with class fields:

```javascript
data class User {
  name = 'Anonymous';
  age = 0;
}

const user = new User({ age: 23 });
// > User { name: 'Anonymous', age: 23 }

const updated = user.copy({ name: 'Liza' });
// > User { name: 'Liza', age: 23 }

const isEqual = user.equals(updated);
// false
```

Example with flowtype notation:

```javascript
data class User {
  name: string = 'Anonymous';
  age: number = 0;
}
```

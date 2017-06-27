# Immutable Data Class for ECMAScript

Inspired by [Kotlin/Scala Data Classes](https://kotlinlang.org/docs/reference/data-classes.html), [Ember Model](https://guides.emberjs.com/v2.13.0/models/defining-models/), [Backbone Model](http://backbonejs.org/#Model).

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

_Desugars into:_

```javascript
class User {
  constructor({ name = 'Anonymous', age = 0 }) {
    Object.defineProperties(this, {
      name: {
        configurable: false,
        enumerable: true,
        writable: false,
        value: name,
      },
      age: {
        configurable: false,
        enumerable: true,
        writable: false,
        value: age,
      }
    });
  }

  copy({ name, age }) {
    return new User({ name, age });
  }

  equals(user) {
    return (
      user !== null &&
      user !== undefined &&
      this.constructor === user.constructor &&
      this.name === user.name &&
      this.age === user.age
    );
  }
}
```


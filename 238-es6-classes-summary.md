# JavaScript Class Concepts Recap

## ✅ 1. What Is Method Chaining?

Chaining means calling multiple methods on the same object in a single line.

```js
acc1.deposit(300).withdraw(100).requestLoan(5000);
```

To make chaining work, each method must return `this` (the object):

```js
deposit(val) {
  this.#movements.push(val);
  return this;
}
```

---

## ✅ 2. Public Field vs Constructor Property

```js
class Student {
  university = 'University of Lisbon'; // public field
  constructor(name) {
    this.name = name; // constructor property
  }
}
```

| Type             | Defined In          | Belongs To    |
| ---------------- | ------------------- | ------------- |
| Public field     | Outside constructor | Each instance |
| Constructor prop | Inside constructor  | Each instance |

---

## ✅ 3. `#` Before a Property (Private Fields)

```js
class Student {
  #course;
  constructor(course) {
    this.#course = course;
  }
}
```

- `#course` is **private**: only accessible inside the class.

---

## ✅ 4. `super()` in Child Class

```js
class Student extends Person {
  constructor(name, birthYear, course) {
    super(name, birthYear); // Call parent constructor
    this.course = course;
  }
}
```

- You must call `super()` **before** using `this`.

---

## ✅ 5. Instance Property

An **instance property** is a variable that belongs to each object.

```js
class Person {
  constructor(name) {
    this.name = name; // instance property
  }
}
```

Each object has its own copy.

---

## ✅ 6. Getter and Setter

```js
class Student {
  set testScore(score) {
    this._testScore = score <= 20 ? score : 0;
  }

  get testScore() {
    return this._testScore;
  }
}
```

- Setter: `student.testScore = 18`
- Getter: `console.log(student.testScore)`
- Uses `_testScore` to avoid conflict with method name.

---

## ✅ 7. Static Method and Property

```js
class Student {
  static numSubjects = 10;

  static printCurriculum() {
    console.log(`There are ${this.numSubjects} subjects`);
  }
}

Student.printCurriculum(); // ✅
```

- `static` makes it belong to the class, not the object.
- Accessed like `Student.numSubjects`.

---

## ✅ 8. Classes Are Just Syntactic Sugar

```js
class Person {
  constructor(name) {
    this.name = name;
  }
}

// Same as:

function Person(name) {
  this.name = name;
}
```

JavaScript classes are just a cleaner way to write constructor functions.

---

## ✅ 9. Classes Are Not Hoisted

```js
const p = new Person(); // ❌ Error

class Person {
  constructor(name) {
    this.name = name;
  }
}
```

- You must define the class **before** using it.

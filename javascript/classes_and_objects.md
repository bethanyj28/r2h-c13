# Classes and Objects

## Object
An object is a data structure that contains a set of _keys_ and _values_. Keys can be any string or number, values can be anything (including functions or other objects).
 
### Examples
```js
const user = {
  username: "coolcat",
  email: "person@gmail.com",
  accountCreated: "2007-03-04",
  isProUser: true,
  stars: 20,
}
 
console.log(user.username) // logs "coolcat"
```
 
```js
const adoptableDog = {
  name: "Cheddar",
  age: 2,
  breed: "American Pit Bull",
  shelter: "Humane Society of Charlotte",
  bestFriend: {
    name: "Nutmeg",
    age: 4,
    breed: "Labrador",
  },
}

console.log(adoptableDog.bestFriend) // logs {name: "Nutmeg", age: 4, breed: "Labrador"}
```

You can even use constructors for objects:
```js
function Square(length) {
  this.width = length
  this.height = length
  this.area = this.width * this.height
  this.willItFit = function(size){
   return size < this.area
  }
}

const reallyCoolSquare = new Square(42)
console.log(reallyCoolSquare.width) // logs "42"
console.log(reallyCoolSquare.area) // logs "1764" (which is 42 * 42)
console.log(reallyCoolSquare.willItFit(20)) // logs "true"
console.log(reallyCoolSquare.willItFit(2000)) // logs "false"
```

## Classes
Classes are similar to objects in that they create a data structure with _keys_ and _values_. They are a bit nicer to look at for more advanced usecases.

// TODO: add more

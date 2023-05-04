# Loops

## `for` loop

### Examples
Prints out numbers to 100:
```js
for (let i = 0; i <= 100; i++) {
  console.log(i)
}
```
Prints out all items in an array:
```js
letters = ['a', 'b', 'c']
for (let i = 0; i < letters.length; i++) {
  console.log(letters[i])
}
```
What would happen if we switch `i < letters.length` to `i <= letters.length`?

### When to use a `for` loop
`for` loops are the most general loop and can be used any time you need a loop. If no other loop fits your use case - use this one

### Structure of a `for` loop
```
for (initialization; condition; afterthought) {
  // loop code
}
```
`initialization` is _initializing_ the counting variable (in the above examples, this is `i`).

`condition` is what tells the loop to stop looping. This value must evaluate to true or false. 

`afterthought` is an action to occur _each time_ the loop executes. 

Using the following loop as an example, let's walk through this:
```js
for (let i = 2; i <= 4; i += 2) {
  console.log(i)
```
- `initialization` is `let i = 2`
- `condition` is `i <= 4`
- `afterthought` is `i += 2 ` (which adds 2 to `i`)

1. The `initialization` runs, setting a variable `i` equal to 2.
2. The `condition` is evaluated - is `2 <= 4`? This evaluates to true, so we execute the loop code.
3. 2 is logged to the console.
4. The `afterthought` is run: 2 is added to `i` (which is currently 2), making `i` equal to 4.
5. The `condition` is evaluated - is `4 <= 4`? This evaluates to true, so we execute the loop code.
6. 4 is logged to the console.
7. The `afterthought` is run: 2 is added to `i` (which is currently 4), making `i` equal to 6.
8. The `condition` is evaluated - is `6 <= 4`? This evaluates to false, so we break out of the loop.

## `while` loop

### Examples
I'm thinking of a number:
```js
secretNumber = 4
guessedNumber = false
while (!guessedNumber) { // while we haven't guessed the number
  guess = Math.floor(Math.random() * 11) + 1 // generates a random number from 1 to 10
  
  console.log(`Is ${guess} your number?`)
  
  if guess == secretNumber {
    guessedNumber = true
  }
}
```

### When to use a `while` loop
A `while` loop is essentially a `for` loop without the `initialization` and `afterthought`. These are nice when you need to loop until a `condition` is met but doesn't necessarily need to iterate in numerical order - or iterate at all.

## `do...while` loop

### Examples
A progress bar that adds between 1 and 10 each loop
```js
let progress = 0
do {
  progress += (Math.floor(Math.random() * 11) + 1) // add a random number between 1 and 10 to progress
  if progress > 100 { // in case progress is over 100
    progress = 100
  }
  console.log(`Progress: ${progress}`)
} while (progress < 100)
```

### When to use a `do...while` loop
A `do...while` loop is exactly the same as a `while` loop except the code in the `do` section will always execute at least once even if the `condition` is not true, where the `while` loop will not execute at all unless the `condition` is true.

## `for...in` loop

### Examples
```js
const car = {
  make: "Toyota",
  model: "Rav4",
  year: 2006,
}

for (const attribute in car) {
  console.log(`${attribute} is ${car[attribute]}`)
}
```
This would log:
```
make is Toyota
model is Rav4
year is 2006
```

```js
const letters = ['a', 'b', 'c']
for (const letter in letters) {
  console.log(letter)
}
```
This would log:
```
0
1
2
```

### When to use the `for...in` loop
When you need to iterate through property fields, which can be helpful for iterating through object properties as seen in the example above.

## `for...of` loop

### Examples
```js
const car = {
  make: "Toyota",
  model: "Rav4",
  year: 2006,
}

for (const attribute of car) {
  console.log(attribute)
}
```
This would log:
```
Toyota
Rav4
2006
```

```js
const letters = ['a', 'b', 'c']
for (const letter of letters) {
  console.log(letter)
}
```
This would log:
```
a
b
c
```

### When to use the `for...of` loop
When you need to iterate through property values, which is especially helpful when working with arrays.

# Practice problems

1. Write out everything the following loop will print. Bonus: what will it print if we change `break` to be `continue`?
   ```javascript
    for(let i = 5; i > 0; i--) {
      if (i % 3 == 0) {
        console.log("Red light")
        break
      }
      console.log("Green light")
    }
   ```
2. How many times will these loops print "Party Time 💃🕺" if `time = 7`? How about if `time = 11`?
   ```javascript
    while(time < 11){
      console.log("Party Time 💃🕺")
      time++
    }
   ```
   
   ```javascript
    do {
      console.log("Party Time 💃🕺")
      time++
    } while (time < 11)
    ```
3. You are given the following code. Write the function `printIt` which will print every number in the matrix (2D array).
   
   _Warning: this is a tricky one!_
   ```javascript
    let matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
    printIt(matrix)
   ```
4. Given an array of numbers and a target number, write a function that will return the two numbers that add up to the target number. You can assume that one and only one pair will add up to to the number.
   
   _Warning: this is another tricky one!_
   ```
   Example input: [2, 15, 4, 22], 6
   Example output: [2, 4]
   ```
   ```javascript
   function twoSum(arr, target) {
      // fill in the code here!
   }
   ```

Answers are [here](https://github.com/bethanyj28/r2h-resources/blob/main/loops/answers.md)!

# Resources

[Codecademy](https://www.codecademy.com/learn/introduction-to-javascript/modules/learn-javascript-loops)

[Mozilla Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Loops_and_iteration)

# Answers

<details>
  <summary> Write out everything the following loop will print.</summary>
  
  ## With `break`
  1. Green light
  2. Green light
  3. Red light
  
  ## With `continue`
  1. Green light
  2. Green light
  3. Red light
  4. Green light
  5. Green light
  
</details>

<details>
  <summary> How many times will these loops print "Party Time 💃🕺" if time = 7? How about if time = 11?</summary>
  
  ## time = 7
  Both loops will print "Party Time 💃🕺" four times.
  
  ## time = 11
  The while loop will not print anything but the do while loop will print "Party Time 💃🕺" once.
  
</details>

<details>
  <summary> You are given the following code. Write the function printIt which will print every number in the matrix (2D array).</summary>
  
  ```javascript
  function printIt(matrix) {
    for (let i = 0; i < matrix.length; i++) {
      for (let j = 0; j < matrix[i].length; j++) {
        console.log(matrix[i][j])
      }
    }
  }
  ```

</details>

<details>
  <summary> Given an array of numbers and a target number, write a function that will return the two numbers that add up to the target number. You can assume that one and only one pair will add up to to the number.</summary>
  
  ```javascript
  function twoSum(arr, target) {
    for (let i = 0; i < arr.length; i++) {
      for (let j = i+1; j < arr.length; j++) {
        if (arr[i] + arr[j] == target) {
          return [arr[i], arr[j]]
        }
      }                                
    }
  }
  ```

</details>

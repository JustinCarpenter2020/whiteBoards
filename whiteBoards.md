# White Board Wednesday
Welcome to CodeWorks's Whiteboard Wednesday Guide, the document is divided into easy(weeks 2-3), 
medium(weeks 4-6), hard (weeks 7-9), and very hard (week 10-13). The questions will elevate in difficulty and you may see many Solutions for them. To help with this process the most common Solution will be provided as well as a notes section for other possible Solutions or approaches.  

<br> 


<h2 align="center">
Easy Problems
</h2>
<br>  

### Add it up:
Given an array of numbers return the sum of all of those numbers
>EXAMPLE INPUT: [1,4,5,10] <o>// outputs: 20</o>  

<details>
<summary>Solution</summary>  

```js
function addNumbers(arr) {
  let sum = 0
  for (let i = 0; i < arr.length; i++) {
    sum += arr[i]
  }
  return sum
}
```
</details>

#### Notes:

```

```

<br>  

___

<br>

### Reverse A String:  
Given a string return that string reversed
>EXAMPLE INPUT: "String" <o>// outputs: "gnirtS"</o>  

<details>
<summary>Solution</summary>

```js
function reverseString(str) {
  let strReverse = str.split('').reverse().join('')
  return console.log("Reverse String 1:", strReverse)
}
```

```js
 function reverseString(str) {
  let strReverse = ''
  for (let i = str.length - 1; i >= 0; i--) {
    let char = str[i]
    strReverse += char
  }
  return console.log("ReverseString 2: ", strReverse)
}
```
</details>

#### Notes:

```

```

<br>

___

<br>



### Iteration madness: 
given and array of 3 numbers add them together until you reach 100 or greater, return how many full iterations of the array it took to reach 100
>EXAMPLE INPUT: [10,15,25] <o>// outputs: 2</o>  

### Solution:
<details>
<summary>Solution</summary>

```js
function iterations(arr) {
  let sum = 0
  let loops = 0
  for (let i = 0; sum <= 100; i++) {
    if (i == arr.length) {
      i = 0
      loops++
    }
    sum += arr[i]
  }
   return loops
}

```
</details>

#### Notes:

```

```

<br>

___

<br>

### Triangle fitness: 
Create a function that takes the dimensions of two triangles (as arrays) and checks if the first triangle fits into the second one.
>EXAMPLE INPUT: [1, 1, 1], [2, 2, 2] <o>// outputs: true</o>  
>EXAMPLE INPUT: [1, 2, 3], [1, 2, 2] <o>// outputs: false</o>  
>EXAMPLE INPUT: [1, 2, 3], [1, 1, 1] <o>// outputs: false</o>  



### Solution:

<details>
<summary>Solution</summary>

```js
function triangle(arr1, arr2){
  for(i=0; i< arr1.length; i++){
    if(arr1[i] > arr2[i]){
      return false
    }

  }
  return true
}

```
</details>

#### Notes:

```

```

<br>

___

<br>

<br>



<h2 align="center">
Medium Problems
</h2>
<br>


### Is Spy: 
 Given a name, determine if that name contains the word spy (in any order) and return the appropriate bool
>EXAMPLE INPUT: "Kipriyanov Stepanovich" <o>// outputs: true</o>  

<details>
<summary>Solution</summary>

```js
function isSpyEasy(str) {
  let person = str.toLowerCase()
  let s = false
  let p = false
  let y = false
  for (let i = 0; i < person.length; i++) {
    let char = person[i]
    if (char == "s") {
      s = true
    } else if (char == "p") {
      p = true
    } else if (char == 'y') {
      y = true
    }
  }
    return  s && p && y
}

```

```js
function isSpy(str) {

    let person = str.toLowerCase()
    let s = person.includes('s')
    let p = person.includes('p')
    let y = person.includes('y')
  return s && p && y
}
```
</details>

#### Notes:

```

```

<br>

___

<br>

### Jeep Climber: 
given a string of r's (rocks) and the size of a Jeep (the jeep strings length) determine if the Jeep can climb the rocks
>EXAMPLE INPUT: "___r_rrr__rrr___rr__", "gJEEPg" <o>// true, the rocks are small enough for the jeep to cross</o>  
>EXAMPLE INPUT: "___r_rrr__rrrrrrrrr___rr__", "gJEEPg" <o>// false, the rock is too wide for the Jeep to climb</o>  


<details>
<summary>Solution</summary>

```js
function jeepClimber(str, car){
  let rock = 0
  let jeep = car.length
  for( let i = 0; i < str.length; i++){
    if( str[i] == 'r'){
      rock++
      if (rock > jeep){
        return false
      }
    } else {rock = 0}
  }
  return true
}

```
</details>

#### Notes:

```

```

<br>

___

<br>

### It's High Nooooon: 
Given two strings both representing cowboys, return which cowboy shot first. This is represented by the "B". Cowboy 1 will ALWAYS be string1 and cowboy 2 will ALWAYS be string 2.
>EXAMPLE INPUT: ".........Bang..", ".......Bang" <o>// outputs: "cowboy 2 shot first"</o>  


<details>
<summary>Solution</summary>

```js
function noonDraw(str1, str2) {
  for (let i = 0; i < str1.length; i++) {
    if (str1[i] != str2[i]) {
      if (str1[i] == 'B') {
        return console.log("Bang Result ", "cowboy 1 shot first")
      }
      return console.log("Bang Result ", "cowboy 2 shot first")

    }
  }
  return console.log("Bang Result ", "both cowboys shot at the same time, they both dead")
}

```
</details>

#### Notes:

```

```

<br>

___

<br>




<h2 align="center">
Hard Problems
</h2>

### BattleShip: 
given an array of arrays representing letters and numbers for battleship return where the boat has been hit, you'll know what letter based on the array the 1 is contained in. The number will be based on the position of the 1.
>EXAMPLE INPUT: [[0,0,0,0],[0,0,0,0],[0,0,1,0],[0,0,0,0]] <o>// outputs: C-3</o>  

<details>
<summary>Solution</summary>

```js
function radarScanChar(arr) {
  let chars = ["A", "B", "C", "D"]
  for (let r = 0; r < arr.length; r++) {
    let row = arr[r]
    let char = chars[r]
    for (let c = 0; c < row.length; c++) {
      let col = row[c]
      if (col == 1) {
        return console.log(char, "-", c + 1)
      }
    }
  }
  return "No damage sustained, systems online"
}

```
</details>

#### Notes:

```

```

<br>

___

<br>


### Find the Median: 
Given two sorted arrays arr1 and arr2, return the median of the two sorted arrays combined.
>EXAMPLE INPUT: [1,3], [2] <o>// outputs: 2</o>  
>EXAMPLE INPUT: [1,3], [2,4] <o>// outputs: 2.5</o>  


<details>
<summary>Solution</summary>

```js
function median(arr1, arr2){
  let newArr = [...arr1, ...arr2]
  newArr.sort()
  if(newArr.length % 2 == 1){
   return newArr[Math.floor(newArr.length/2)]
  } else {
    let newNum = (newArr[newArr.length/2 - 1] + newArr[newArr.length/2]) / 2
    return newNum
  }

}

```

</details>

#### Notes:

```
Formula to find median (with even array length) = middle numbers added together and divided by two
ex: (2 + 3)/2
```

<br>

___

<br>



<!-- <h2 align="center">
Very Hard Problems
</h2> -->







<style>
y{
  color: #FDFD96;
}

b{
  color: #A7C7E7;
}
o{
  opacity: .5;
}
</style>

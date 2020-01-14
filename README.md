# Workshop: Building a Coolculator 🔢

Collaborators: [HFSMITH] & [meganfx]

Make sure you’re working in pairs - on a single laptop. You’ll be **pair programming**. Remember, in pair programming, there are two roles - **driver** and **navigator**.

Start by forking this repo...

![fork button](https://readme-pics.s3.amazonaws.com/fork_button.jpg)

Forking creates a copy of this repo in your own GitHub account. Add your partner as a collaborator by going to 'Settings' > 'Collaborators & teams' and entering their GitHub username in the 'Collaborators' box. That means you'll both have access to the repo.

Next, clone down the repo onto the laptop you're working on, change into the directory and run

```shell
npm install
```

This will install the required dependancies, including [Mocha](https://mochajs.org/) and [Chai](https://www.chaijs.com).

To check everything is working, run the tests with

```shell
npm test
```

You should see something like this:

![Test Ouptut](http://c.danny.is/178dbbaf264f/npmtest.png)

---

For each of the **bold** questions below...

<h3 align="center">
  🗣 Discuss &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  👩‍💻 Change &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  👀 Observe &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  🔄 Repeat
</h3>

Once you understand what's going on, **ANSWER THE QUESTION IN THIS README FILE** and make the required changes to the code.

ℹ️ Make sure you commit regularly!

---

## Part 1: Testing `Array`

Look in [`array.test.js`](test/array.test.js). This contains some tests for JavaScript's built-in Array methods.

**What do the existing tests actually test (explain in english)?**
In the code, it adds 5 to the end of the array. The first array tests, compares the ideal list with the 5 on the end, with the list where the code adds 5 to the end - checking if they are the same.
Second array tests if after a new item is added to the array [1], the length of the array should increase from 4 to 5.

**Add a test for the `pop()` method.**
``` javascript
    describe('#pop()', function() {
      it('should remove the last item from the list', function() {
        var array = [1, 2, 3, 4]
        array.pop()
        expect(array).to.deep.equal([1, 2, 3])
      })

      it('should alter the length properly', function() {
        var array = [1, 2,3,4]
        array.pop()
        expect(array.length).to.equal(3)
      })
    })
```

> 💡 **REMINDER**: Do you need to commit your answers to the questions above?

## Part 2: The Coolculator

Until now, we've been testing JavaScript's in-built functionality, which is kinda pointless - the folks who wrote JavaScript probably already have tests for this stuff. Let's take a look at our own project: the **Coolculator**. This is a class that has a bunch of methods for doing calculator-like stuff.

Read The coolculator class and tests.

**What methods does the Cooclulator currently implement?**
add function for 2 numbers

**Describe how the existing test works**
The test uses the add function to calculate the result of the numbers 2 & 3. Mathematically, we know that 2+3 = 5, so we compare the result of the function to reality of the result being 5.

**Change a value in the `add()` test so it fails.**
```javascript
it('should add', function() {
    result = mm.add(2, 3)
    expect(result).to.equal(6)
  })
```

which results in

```shell
  Array
    #push()
      ✓ should add an item to the array
      ✓ should alter the length properly
    #pop()
      ✓ should remove the last item from the list
      ✓ should alter the length properly

  Coolculator
    1) should add


  4 passing (6ms)
  1 failing

  1) Coolculator
       should add:

      AssertionError: expected 5 to equal 6
      + expected - actual

      -5
      +6
      
      at Context.<anonymous> (test/coolculator.test.js:11:23)
      at processImmediate (internal/timers.js:445:21)



npm ERR! Test failed.  See above for more details.
```

**Changethe implementation of `add()` so it always returns `1000`.**
In the add function, I have changed the 'return a+b' to 'return 1000'
```javascript
class Coolculator {
  add(a, b) {
    return 1000
  }
}
```

Now let's do some TDD! Uncomment the `multiply()` test.

**What do you expect to happen when you run your tests?**
Its going to fail, as we have not created a multiply() method within the coolculator class.

**What actually happened when you ran your tests?**
it failed.

**Add a method to the Coolculator so the test passes green**
To this class, we have added the multiply method() that will allow for the calculation to occur.
```javascript
multiply(a,b){
    return a*b;
  }
```
This passess the tests in the shell.
```shell
> ada-coolculator@1.0.0 test /Users/harryfitzgeraldsmith/di-workshop-07-tdd-intro
> mocha



  Array
    #push()
      ✓ should add an item to the array
      ✓ should alter the length properly
    #pop()
      ✓ should remove the last item from the list
      ✓ should alter the length properly

  Coolculator
    ✓ should add
    ✓ should multiply


  6 passing (5ms)

UK-C02ZT1WELVDL:di-workshop-07-tdd-intro harryfitzgeraldsmith$ 
```

**Uncomment the `subtract()` test and write some code to make it green**
Created the subtract function
```javascript
  subtract(a,b){
    return (a-b);
  }
```
Which results in
```shell
> ada-coolculator@1.0.0 test /Users/harryfitzgeraldsmith/di-workshop-07-tdd-intro
> mocha



  Array
    #push()
      ✓ should add an item to the array
      ✓ should alter the length properly
    #pop()
      ✓ should remove the last item from the list
      ✓ should alter the length properly

  Coolculator
    ✓ should add
    ✓ should multiply
    ✓ should subtract


  7 passing (6ms)
```

## Part 3: Extending the Coolculator

Add some more methods to the Coolculator class using the Red/Green/Refactor process. Be sure to write your tests first. Here are some things you could add to your calculator:

| **Function**  |                                                                                                                                                               |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| divide        | Takes two numbers and divides the first by the second                                                                                                         |
| highest       | Takes two integers and returns the highest one                                                                                                                |
| lowest        | Takes two integers and returns the lowest one                                                                                                                 |
| double        | Takes a number and doubles it                                                                                                                                 |
| square        | Takes one number and squares it                                                                                                                               |
| raise         | Takes two numbers and raises the first one to the power of the second                                                                                         |
| isNegative    | Takes a number and returns `true` if it's negative and `false` if it's positive                                                                               |
| isPositive    | Takes a number and returns `true` if it's positive and `false` if it's negative                                                                               |
| isCool        | Takes a number and returns true if the number is cool (ie. starts and ends with the same digit). Should return a boolean                                      |
| sum           | Takes an array of numbers and adds them all                                                                                                                   |
| multiplyArray | Takes an array of numbers and multiplies them all                                                                                                             |
| mean          | Takes an array of numbers and returns the mean (average)                                                                                                      |
| factorial     | Takes a single number and calculates its factorial (this is kinda hard)                                                                                       |
| random        | Takes an integer and returns a random integer between 0 and it. How might we test this? (This requires some _thinking!_, and we'll never have a perfect test) |

```javascript
class Coolculator {
  add(a, b) {
    return (a+b);
  }
  multiply(a,b){
    return (a*b);
  }
  subtract(a,b){
    return (a-b);
  }
  divide(a,b){
    return(a/b)
  }
  highest(a,b){
    return a>b?a:b
  }
  lowest(a,b){
    return b>a?a:b
  }
  double(a){
    return a*2
  }
  square(a){
    return a**2
  }
  raise(a,b){
    return a**b
  }
  isNegative(a){
    return 0>a?true:false
  }
  isPositive(a){
    return a>0? true:false
  }
  isCool(a){
    num =toString(a);
    len = length(num) - 1;
    return num[0] == num[len]?true:false
  }
  sumof(a1){
    return a1.reduce(function(a,b){
      return (a+b)
    }, 0)
  }
  multipleArray(a1){
    return a1.reduce(function(a,b){
      return(a*b)
    }, 0)
  }
  mean(a1){
    return a1.reduce(function(a,b){
      return (a+b)
    }, 0)/a1.length
  }
  factorial(a){
    multiple = 1
    for (i=a; i>0;i--){
      multiple= multiple*a
    }
    return multiple;
  }
  random(a){
    return Math.floor(Math.random() * a);
  }
}

module.exports = Coolculator
```

## Part 4 (extension): More Array Tests

⚠️ _Don't attempt this unless you've finished all your other work_

Add some more tests for JavaScript's built-in array methods:

- `indexOf()`
- `join()`
- `shift()`
- `unshift()`
- Any others you can think of!

## Part 5 (super-extension)

⚠️ _Don't attempt this unless you've finished all your other work_

Use TDD to adapt your add method so it takes an **arbitrary number** of integers as arguments, and adds them all together, eg:

```js
add(1, 2) //=> 3
add(1, 2, 7, 10) //=> 20
add(5) //=> 5
```

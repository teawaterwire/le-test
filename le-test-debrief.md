*In bold are the fundamental JavaScript concepts that this test is trying to cover.*

## Keep calm and smash it :)

0.
```javascript
var a = ['So happy to do this test', []];
console.log(a.join('!'));
```

`'So happy to do this test!'`

The idea of this first question was to **put the candidate at ease**. I thought that everybody would know how `join` worked and could infer the obvious result quite easily.
Actually, I found out that this was stressing candidates out. Some didn't know `join` and/or couldn't figure out what to do with the empty Array. But I kept it as a way to see how people go about making assumptions.

*Inside story*: I put `null` instead of `[]` at the beginning. This would give the same result but it was surprising because according to the documentation `join` "joins the string conversions of all array elements into one string". And since `String(null)` gives `'null'` this should have been `So happy to do this testnull`. I had to look at the actual `join`'s spec, and see that `undefined` and `null` are explicitely converted to empty strings. I amended Mozilla's website while I was at it :D

Btw, I chose `[]` because it's kind of "funny" that String conversion of an Array is the result of calling `join` on it!


1.
```javascript
var a = [1, 3, 6, 42];
var result = a.map(function(n) {
  return n + 1;
})
.filter(function(n) {
  return (n % 2 === 0);
})
.reduce(function(acc, n) {
  return acc * n;
}, 2);

console.log(result);
```
* `[6]`
* `16` <-
* `10`
* `null`

Who doesn't love those **higher-order functions** à la FP?! The hope here was to assess whether the candidates did love them too!

The `reduce` bit remained the main source of mistakes. And I found also weirdly difficult to explain `reduce` to someone who didn't know it beforehand.

Here's the funnel of success:
90% went past `map`,
70% past `filter` and
50% past `reduce`

2.
```javascript
var friends = ['bim', 'bam', 'boom'];
var hey = function(a) {
  return function(b) {
    console.log(a + b);
  };
};
friends.forEach(hey('Hi '));
```

`'Hi bim'`
`'Hi bam'`
`'Hi boom'`

This was maybe the easiest question of the test. Almost every candidate knew how **closures** work. Some were a bit confused by the `forEach` and wrote down an Array instead of a series of `console.log`, but globally nobody had real trouble with this one.

3.
```javascript
var o = {a: 1, b: [1, 2]};

(function(o) {
  var c = o.a;
  var d = o.b;
  c = 4;
  d.shift();
})(o);

console.log(o);
```

* `{a: 4, b: [1, 2]}`
* `{a: 1, b: [1, 2]}`
* `{a: 1, b: [1]}`
* `{a: 1, b: [2]}` <-
* `{a: 4, b: [2]}`
* `{a: 4, b: [1]}`

Hey Dawg, have you heard of **object mutation**?!
The key here is to understand that `d` is a reference to the array. Hence `shift` is going to mutate this array.

Some people were confused by the IFFE and/or didn't know `shift`'s behaviour.

4.
*[help]* `Function.bind` syntax: `fun.bind(thisArg[, arg1[, arg2[, ...]]])`
```javascript
var log = function(a, b) {
  console.log(this.c, a, b);
};
var myObject = {
  c: 'tic',
};
var myConsoleLog = log.bind(myObject, 'tac');

myConsoleLog('toc');
```
* `tic tac toc` <-
* `tic toc tac`
* `toc tac tic`
* `toc tic tac`
* `tac tic toc`
* `tac toc tic`

Nothing special here if you've used/seen `bind` before. Only 50% of the candidates could do this one.
It's interesting to note that most of the candidates didn't see the [Help] bit.

Writing React components we've come to use this **binding mechanism** a lot, this question is definitely not here to trick candidates with some hidden Javascript feature.

5.
*[Help]* `Function.apply` syntax: `fun.apply(thisArg, [argsArray])`
```javascript
var yourArray = [[2], [[['deep']]], {ok: 0}, 'end'];
var goDeep = function(a) {
 return Array.prototype.concat.apply([], a);
};
console.log(goDeep(goDeep(goDeep(yourArray))));
```

`[2, 'deep', {ok: 0}, 'end'}`

Maybe the hardest one. Only a couple could find the correct answer.

You have to know how this **applying mechanism** works, and what concat behavior is (and how it deals with objects).

6.
> Write a snippet of code using at least one of the following es6 features:
Object destructuring, arrow functions, let, template strings

`let {doge} = dogs;`

Back one year ago, **ES6** was still fairly "new". On average people had heard about `let` and arrow functions but didn't really know what was destructuring and template literals.
Generators seemed also something that people were incredibly excited about without knowing what they really were...!

7.
> Write a function `getMax` that returns the max element of an array of positive integers such as:
```javascript
getMax([1, 4, 3, 2]); // returns `4`
```

`const getMax = a => Math.max.apply(null, a);`

You'll agree that this one is dead simple. I didn't really expect the one-liner using `Math.max` but at least a **working implementation of this algorithm**.

It made me sad when people used `for` loop when they could have gone with `forEach` or `reduce` :D

The people who couldn't do it were the ones trying to over complicate the problem. Like by trying to sort the array first.

8.
> Write the `sum` function using recursion such as:
```javascript
sum(0); // returns 0
sum(1); // returns 1 (= 1 + 0)
sum(2); // returns 3 (= 2 + 1)
```

`const sum = (a, b = 0) => a ? sum(a-1, b+a) : b;`

The idea behind this one is to check if the candidate has already heard about **recursion**.

I wasn't expecting this tail-recursive one-liner, but again just a working implementation. Only 50% passed this question.

9.
```javascript
var out = 1;

var doMoreStuff = function() {
  if (!out) {
    var out = 2;
  }
  console.log(out);
};

doMoreStuff();
```

`2`

The key concept here is **hoisting**. Only 30% of candidates would know about it.

![potato](http://cdn.meme.am/instances/500x/61730954.jpg)

The key idea here is that:
> A **potato** is just a fucking potato.

*For the records, about 40 candidates took this test and only one was able to get every questions right. That adds up to 2.5% (given that they were all pre-screened).*

## Keep calm and smash it :)

0.
```javascript
var a = ['So happy to do this test', []];
console.log(a.join('!'));
```

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
* `16`
* `10`
* `null`

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
* `{a: 1, b: [2]}`
* `{a: 4, b: [2]}`
* `{a: 4, b: [1]}`

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
* `tic tac toc`
* `tic toc tac`
* `toc tac tic`
* `toc tic tac`
* `tac tic toc`
* `tac toc tic`

5.
*[Help]* `Function.apply` syntax: `fun.apply(thisArg, [argsArray])`
```javascript
var yourArray = [[2], [[['deep']]], {ok: 0}, 'end'];
var goDeep = function(a) {
 return Array.prototype.concat.apply([], a);
};
console.log(goDeep(goDeep(goDeep(yourArray))));
```

6.
> Write a snippet of code using at least one of the following es6 features:
Object destructuring, arrow functions, let, template strings

7.
> Write a function `getMax` that returns the max element of an array of positive integers such as:
```javascript
getMax([1, 4, 3, 2]); // returns `4`
```

8.
> Write the `sum` function using recursion such as:
```javascript
sum(0); // returns 0
sum(1); // returns 1 (= 1 + 0)
sum(2); // returns 3 (= 2 + 1)
```

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

![potato](http://cdn.meme.am/instances/500x/61730954.jpg)

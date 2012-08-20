### Intro

"All of us, whether experts or newcomers. Well-meaning idiots, perhaps, but idiots.
We all write bugs, all the time. That is the normal state of software.
There is no abstraction so perfect that a human won’t fuck it up at the first opportunity.
But we can try to be better, simpler, to make it easier for our future idiotic selves to figure
out what we were thinking in our cleverly idiotic brains, and chop the problems into smaller 
pieces so that our future selves can have some clues to find the maddeningly idiotic bugs we
stuffed in there."    

-- [Isaac Z. Schlueter](http://blog.izs.me/), author of [npm](http://npmjs.org/)

### Tabs vs Spaces

This is not religious problem! There is 4 space indentation. Use Spaces *not Tabs*
The reason for this is that, there still is not a standard for the placement of tabstops.
The use of spaces can produce a larger filesize, but is not significant over local networkis,
and the difference is eliminated by minification.

### Semicolons 

Semicolons are useless in JavaScript. All arguments that there are needed are pointless.

*they* say that semicolons will save your live.

``` javascript
return 
    ( 1 + 2 )
// => null

// Adding semicolon after ( 1 + 2 ) will not save you from the null

```

But this is wrong by design and semicolons will not help you.

More about this topic:
* [An Open Letter to JavaScript Leaders Regarding Semicolons](http://blog.izs.me/post/2353458699/an-open-letter-to-javascript-leaders-regarding)
* [Semicolons, Objectively](http://dailyjs.com/2012/01/19/semicolons/)

But to be like any other library or javascript code. We put semicolons. 

*** Don't forget to use them or JSHint will spank you. ***

### Editors

You can use any editor. However, having support for JS Syntax Highlighting and 
JSLint / JSHint, may save your more than once. 

### Line lenght

Limit your lines to 80 characters. I'm pretty sure that the most monitor will suport and 120 
characters or more. It's good to use the additional space to split your screen. You have editor that 
supports that, right ? ( If don't have Vim is pretty good at that :) )

### Quotes

Use single quotes, unless there is JSON.

``` javascript
// Good
var foo = 'bar';

// Bad
var foo = "bar";
```

Faster execution time and HTML uses double quotes.

### Braces

Opening braces go on the same line as the statement.

Also use *one* space before and after the statement.

``` javascript
// Good 
if (something) {
    // code...
}

// Bad
if (something) 
{
    // code...
}

// Bad
if (something){
    // code...
}
```

### Use strict

Strict Mode is a new feature in ECMAScript 5 that allows you to place a program, or a function, 
in a "strict" operating context. This strict context prevents certain actions from being taken and 
throws more exceptions (generally providing the user with more information and a tapered-down 
coding experience).

``` javascript
var imStrict = function (){
  "use strict";
  // code...
}
```

No new syntax is introduced in order to enable strict mode. This is huge. This means that you can
turn strict mode on in your scripts - today - and it'll have, at worst, no side effect in old browsers.

More on the topic:
* [Browser test for Strict Mode Support](http://java-script.limewebs.com/strictMode/test_hosted.html)  
* [JavaScript Strict Mode](http://javascriptweblog.wordpress.com/2011/05/03/javascript-strict-mode/)  
* [It's time to start using JavaScript Strict mode](http://www.nczonline.net/blog/2012/03/13/its-time-to-start-using-javascript-strict-mode/)  
* [JavaScript: Use strict](http://bdryanovski.github.com/blog/2011/11/20/javascript-use-strict/)  
* [MSDN - Strict mode](http://msdn.microsoft.com/en-us/library/br230269.aspx)  
* [Mozilla - Strict mode](https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Functions_and_function_scope/Strict_mode?redirectlocale=en-US&redirectslug=JavaScript%2FStrict_mode)  

### Void, Variable, Classes, Consts, Objects, Function declarations

Use `void 0` instead of `undefined`, becouse `undefined` could have been redefined ( Who will do that? ).

Avoid `global` vars where you can. If you use them, specify it explicity.

``` javascript
window.globalVar = 'something';
```

Declare one variable per `var` statement, it makes it easier to re-order the lines and comment.

``` javascript
// Good
var words   = [ 'foo', 'bar'];
var numbers = [ 30, 42 ];
var object  = {};

// Bad
var words = [ 'foo', 'bar' ], numbers = [ 30, 42 ], object = {};
```

Variable must be lower camel case capitalization.

``` javascript
// Good
var lowerCamelCase = 'something';

// Bad
var lower_cammel_case = 'something';
var lower_Camel_Case  = 'something';
var lower_CamelCase   = 'something';
var Lower_Camel_case  = 'something';

// etc ..

```

String variables some times contain long text use `\` or `+` to split the line no more than 80 characterrs per line.

``` javascript
// Good

var longString = 'Lorem ipsum dolor sit amet, consectetuer adipiscing elit, sed diam nonummy nibh euismod tincidunt \
ut laoreet dolore magna aliquam erat volutpat. Ut wisi enim ad minim veniam, quis nostrud exerci tation ullamcorper \
velit esse molestie consequat, vel illum dolore eu feugiat nulla facilisis at vero';

var longString = 'Lorem ipsum dolor sit amet, consectetuer adipiscing elit, sed diam nonummy nibh euismod tincidunt ' +
'ut laoreet dolore magna aliquam erat volutpat. Ut wisi enim ad minim veniam, quis nostrud exerci tation ullamcorper ' +
'velit esse molestie consequat, vel illum dolore eu feugiat nulla facilisis at vero';

// Bad 

var longString = 'Lorem ipsum dolor sit amet, consectetuer adipiscing elit, sed diam nonummy nibh euismod tincidunt ';
longString += 'ut laoreet dolore magna aliquam erat volutpat. Ut wisi enim ad minim veniam, quis nostrud exerci tation ullamcorper ';
longString += 'velit esse molestie consequat, vel illum dolore eu feugiat nulla facilisis at vero';
```

Boolean variables and functions should always be either `true` or `false`. Don't set it to `0`
unless it's supposed to be a number.

``` javascript
// Good
var active   = true;
var inactive = false;

// Bad
var active   = 1;
var inactive = 0;
```

When something is intentionally missing or removed, set it to `null`.

Class names (if they be called this way) should be capitalized using upper camel case.

``` javascript
// Good
var UserModel = function() {
    // code
}

// Bad
function User_Model() {
    // code
}
```

Don't set things to `undefined`. Reserve that value to mean "not yet set to anything."

Constants should be declared as regular variables or static class properties, using all uppercase
latters.

`const` is nice and it's supported by V8 ( Google Chrome ) and Node.js but that's all.

``` javascript
// Good
var LEVEL = 10;

// Bad
const LEVEL = 10;
var level   = 10;
```

Objects use traling commas and put short declarations on single line.

``` javascript
// Good
var object = {
    'my method': function() { /* code */ }
    ,nice: 'a'
};

// Bad
var object = { 'my method': function() { /* code */ }, nice: 'a' };

var object = { 'my method': function() { /* code */ },
               nice: 'a'
            };
// and more ...
```

Functions length, keep them short. A good function fits on a slide that the people in the last row
of a big room can comfortably read. So don't count on them having perfect vision and limit yourself.

Don't use function statements. Instead, create anonumous functions and assing them to var.

``` javascript
// Good
var displayModal = function (name, text) {
    // code...
};

// Bad
function displayModal ( name, text ) {
    // code ...
};
```

Use `self` to push current context to the closures.

```
var a = {
    b: function() {
        var self = this;
        $('selector').click(function(event) {
            self.c()
        });
    }   
};
```

Event callback should name event data variable as `event`, not `e` or anyother form.

``` javascript 
$('selector').click(function(event) { 
    console.log('clicked');
});
```

### Comma first
If there is a list of things separated by commas, and it wraps across multiple lines, put the
comma at the start of the next line, directly below the token that starts the list. Put the final 
token in the list on a line by itself. For example:

``` javascript
var magicWords = [ "abracadabra"
                 , "gesundheit"
                 , "ventrilo"
                 ]
  , spells = { 
      "fireball" : function () { setOnFire() }
    , "water" : function () { putOut() }
    }
  , a = 1
  , b = "abc"
  , etc
  , somethingElse

```
Why this is good [link](https://gist.github.com/357981)


### Short Object and Array use
Use `{}` instead of `new Object()` and `[]` instead of `new Array()`

Arrays - when the member names would be sequential integers and objects - when 
the member names are arbitary strings or names.

### Eval

Forget about it. 

*NOTE:* If you use `eval` you will die in a horrible pain. Zombie monkeys will eat your eyes.


### Operators and Conditions

Use the triple equality operator as it will work just as expected.
If your code don't work as expected. It's not the operator that will stop you, but the logic and
the date types.

``` javascript
// Good
var a = 0;
if ( a === '' ) {
    console.log('aloha')
}

// Bad
var a = 0;
if ( a == '' ) {
    console.log('olalal')
}
```

Any non-trivial conditaion should be assigned to descriptive variable:

``` javascript
// Good
var canAct = ( user.isAdmin() || user.isMaster() );

if (canAct) {
    console.log('Act a fool');
}

// Bad
if ( user.isAdmin() || user.isMaster() ) {
    console.log('Act a fool');
}
```

`for` loop could be boosted 2x faster in some browsers. If you cache the length of the object/array

``` javascript
for (var i = 0, length = myArray.length; i < length; i++)
{
    myFunction(myArray[i]);
}
```

If a block needs to wrap to the next line, use a curly brace. Don't use it if it doesn't.

``` javascript
// Good
if (foo) bar()

while (foo) {
  bar()
}

// Bad
if (foo) { bar() }

while (foo)
  bar()
```

### Extending Prototypes

Don't extend the prototypes of any objects, espacially native ones. 

Case close.

### Return statements

First, every function must return something. So put return statement on the last line of your function.
The return value expression must start on the same line as the `return` keyword in order
to avoid stuped response.
To avoid deep nesting of if-statements, always return a functions value as early as possible.

### Named closures

It's good to name your closers. After your code fails (and it will fail) in the callback stack you 
will see your function.

``` javascript
// Good
objectOrSomething.on('end', function onDisconnect() {
    console.log('User Disconnected');
});
```

But don't nest this closers, else your code will become a mess.

``` javascript
// Good
setTimeout(function() {
    user.connected( someCoolFunction );
}, 1000);

var someCoolFunction = function () { 
    console.log('Connected');
}

// Bad
setTimeout(function() {
    user.connected(function() {
        console.log('Connected');
    });
}, 1000);
```

### Getters and Setters

Setters caouse more problems than solve. Getters are not bad, and are more free of side effects.

### Whitespace
* Each ; (semicolon) in the control part of a `for` statement should be followed with a space.
* After `if`, `for`, `while` and any other operation there must be a space.
* Whitespace should follow every , (comma).

### Code validation.

Use [JSHint](http://www.jshint.com/) to validate your code insted ot [JSLint](http://www.jslint.com/).
All real code editor will support it. But if any chance that your editor miss that feature. Now is the time 
to start thinking about new editor.

### Documentation and comments

Documentation section is not ready.

Motivation talk about why we need documentation. [A documentation talk](http://zachholman.com/talk/a-documentation-talk)

Comments must start with `//` and there must be *one* space after `//`. Also comments must not be more than 80 character limit
per line. Comment are sentence. All rules that apply to a english sentence apply also to code comments. Remember that
someone will read it and will know the difference betwin `can` and `can't`.

``` javascript
// Good

// This is the comment of the code that I'm working on.

// Bad

//this is the comment of the code that im working on
```


Single line comments

``` javascript
// Good

// This a comment for the function
var awesome = function() {
    // code ...
}

// Give the dog a name
var dog = 'Rorger';


// Bad

var awesome = function() { // This a comment for the function
    // code ...
}

var awesome = function() {
    // This a comment for the function
    // code ...
}

var dog = 'Roger'; // Give the dog a name

var dog = 'Roger';
// Give the dog a name
```

Multiline comments

``` javascript
// Good

/**
 * Function: subtract()
 */

var subtract = function(a, b) {
    // code...
}

// Bad

/* Function: subtract() */

var subtract = function(a,b) {
    // code...
}
```

It's nice to leave some tags into the comments.

Rules to create and to be valid tag.
* Must be short no more than 80/180 characters (1 line max 2 lines).  
* There must be a space after `//`.  
* Every tag must start with `@`.  
* After the tag body there must be `:`. Example: `// @body: text`

Here are some tags that you could use for leaving messages for your feature self.
``` javascript
// Good

// @todo: By milk and take the trash.

// Bad

// ToDo: By milk and take the strash.
//Todo By milk and take the trash.
//!todo by milk and take the trash.
```


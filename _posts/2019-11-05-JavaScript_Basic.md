---
layout: post
title:  JavaScript_Basic
date:   2019-11-05
excerpt: "About JavaScript Basic Syntax"
tag:
- Java Script
comments: true
---
# JavaScript

	•	This page is my note about javascript.
	•	It will be difficult to read.
	•	Comment : //

Caution : Ungly English


<hr>


## Data Type

	•	JavaScript doesn't have data type.
	•	So, non-type language like php.

We can check use function typeof <br>
`typeof 5`


### Number


operator is same to the other lnguage. <br>
There are some function to calculate easily.

	•	Math.pow(3,2);       // 9,   3^2
	•	Math.round(10.6);    // 11,  rounding off
	•	Math.ceil(10.2);      : 11,  rounding up
	•	Math.floor(10.6);    : 10,  rounding down
	•	Math.sqrt(9);          : 3,   root
	•	Math.random();      : random number between 0 - 1.0

### String

String is in double quote or single quote. <br>
And It can be merged by operator +

Funtion

	•	String.length : length of string

### Variable

JavaScript's declaring variable is var.

Like this. <br>
`var a = 5;` <br>
`var s = "string";`

### Boolean

	•	true
	•	false

It is usually used 1 is true and 0 is false.

### Null

	•	null
	•	undefined


<hr>


## Operator

### Logical operator

Logical operator is smiliar to the other language.

	•	(a == b) : equal, if a = b outwardly (like (1 == '1')), it returns true.
	•	(a === b) : perpect equal, if type and value are same perpectly, It returns ture.
	•	(a != b) : not, if a and b are different, It returns true.
	•	(a !== b) : not equal, same to eqaul
	•	inequality : <, >, <=, >=
	•	(a && b) : and
	•	(a || b) : or
	•	(!a) : not

It is better to use 3 equal for purpose that checking equal.

There are many alternative false

	•	undefined
	•	0
	•	undefined variable
	•	null
	•	NaN : 0 divided error


<hr>


## Basic Syntax

### Conditional

{% highlight javascript %}
if(true){
    alert(1);
} else {
    alert(2);
}
{% endhighlight %}

It is not different to other language.

### Repetition : while

{% highlight javascript %}
while (conditional){
    repetition code
}
{% endhighlight %}

### Repetition : For

{% highlight javascript %}
for(var i = 0; i < 10; i++){
    document.write('coding everybody'+i+'<br />');
}
{% endhighlight %}

Structure of For <br>
for(Initialize variable; conditional; repeat something){ <br>
repetition code <br>
} <br>

### Control of Repetition

	•	break : Escape repetition immediately
    •	continue : doens't execute repeat code after continue and move back
    •	where starting point that begins repetition code again with next
    •	repetition code and conditional.

{% highlight javascript %}
for(var i = 0; i < 10; i++){
    if (i === 5) {
        continue
    }
    document.write(i);
}
{% endhighlight %}

This code doesn't write 5, because of continue.

### Declare function

{% highlight javascript %}
function functionName( arg ){
   Code
   return value;
}
{% endhighlight %}

It is simple way to declare function.

{% highlight javascript %}
var numbering = function (){
    i = 0;
    while(i < 10){
        document.write(i);
        i += 1;
    }   
}
numbering();
{% endhighlight %}

It is the other way to declare function. <br>
function can be defined by variable. 

### Array

defining array and function about array.

{% highlight javascript %}
var arr = ['val1', 'val2', 'val3'];
arr.length; // length of array.
arr.push(newval); // add value.
arr.concat(newval, newval2); // add multiple value.
arr.unshift(newval); // add value first index.
arr.splice(add index, # of removing, add value); //
arr.shift(); // eliminate first value.
arr.pop(); // eliminate last value.
arr.sort(); // sorting.
arr.reverse(); // sorting by reverse order.
{% endhighlight %}

`if li = ['a', 'b', 'c', 'd', 'e']; li.unshift('z');` then, <br>
`['z', 'a', 'b', 'c', 'd', 'e']` <br>
`if li = ['a', 'b', 'c', 'd', 'e']; li.splice(2, 1, 'B');` then, <br>
`return ['c'] that index 2. and add 'B' in index 2.`

### Associate Array

{% highlight javascript %}
var character = {'Seol': 228, 'Artyrie': 220, 'Bella': 209};
character["Seol"] // => 228
character.Seol // => 228

for (key in character) {
    document.write("key : " + key); // show key like a Seol.
}
{% endhighlight %}

It is like a hash in java.

### Function in Object

{% highlight javascript %}
var character = {
    'list': {'Seol': 228, 'Artyrie': 220, 'Bella': 209},
    'show' : function () {
        for(var name in this.list) {
            document.write(name+" : "+this.list[name]+"<br />");
        }
    }
};
{% endhighlight %}

'list' is key, {'Seol': 228, 'Artyrie': 220, 'Bella': 209} is value. <br>
key can have object and also function. <br>
if you want to get value that 'Seol' has, call like this. <br>
`character['list']['Seol'];`

function 'show' can be called by this way.
{% highlight javascript %}
character['show']();
character.show();
{% endhighlight %}


<hr>


## Advanced Javascript

### Module

	•	Module is made to recycle code and maintain easily.
	•	Pure JavaScript doens't have Module.

These are hello.js and index.html

{% highlight javascript %}
function hello(){
    return 'Hello world';
}
{% endhighlight %}
{% highlight HTML %}
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8"/>
    <script src="hello.js"></script>
</head>
<body>
    <script>
        alert(hello());
    </script>
</body>
</html>
{% endhighlight %}

This is modulization.

### Library

Library is similar to Module. <br>
Library is collection of well arranged code like jQuery <br>

How to use Library?

{% highlight HTML %}
<!DOCTYPE html>
<html>
<head>
    <script src="https://code.jquery.com/jquery-1.11.0.min.js"></script>
</head>
<body>
    <ul id="list">
        <li>empty</li>
        <li>empty</li>
        <li>empty</li>
        <li>empty</li>
    </ul>
    <input id="execute_btn" type="button" value="execute" />
    <script type="text/javascript">
     $('#execute_btn').click(function(){
        $('#list li').text('coding everybody');
     })
    </script>
</body>
</html>
{% endhighlight %}

This is same to next code.

{% highlight HTML %}
<!DOCTYPE html>
<html>
<body>
    <ul id="list">
        <li>empty</li>
        <li>empty</li>
        <li>empty</li>
        <li>empty</li>
    </ul>
    <input id="execute_btn" type="button" value="execute" />
    <script type="text/javascript">
    function addEvent(target, eventType,eventHandler, useCapture) {
        if (target.addEventListener) { // W3C DOM
            target.addEventListener(eventType,eventHandler,useCapture?useCapture:false);
        } else if (target.attachEvent) {  // IE DOM
            var r = target.attachEvent("on"+eventType, eventHandler);
        }
    }
    function clickHandler(event) {
        var nav = document.getElementById('list');
        for(var i = 0; i < nav.childNodes.length; i++) {
            var child = nav.childNodes[i];
            if(child.nodeType==3)
                continue;
            child.innerText = 'Coding everybody';
        }
    }
    addEvent(document.getElementById('execute_btn'), 'click', clickHandler);
    </script>
</body>
</html>
{% endhighlight %}

### API

Application Programming Interface (API) <br>
It controls environment where program works <br>
and that provided by envrionment. <br>
It is expressed by function, input, output and data type of software <br> component(function, method, operation, ect)

It is different to User Interface. (UI)
<br><br>
These are API document for JavaScript

<a href="http://www.ecma-international.org/publications/standards/Ecma-262.htm">ECMAScript</a><br>
<a href="https://opentutorials.org/course/50">생활코딩</a><br>
<a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference">JavaScript Reference (MDN)</a><br>
<a href="https://docs.microsoft.com/ko-kr/previous-versions/visualstudio/visual-studio-2010/z688wt03(v=vs.100)?redirectedfrom=MSDN">JScript Reference (MSDN)</a><br>
<br><br>
These are API document by host type that JavaScript works.

<a href="https://developer.mozilla.org/en-US/docs/Web/API">Web browser API</a><br>
<a href="https://nodejs.org/api/">nodejs API</a>

### Generics

<a href="https://regexper.com/">See regex structure on picture</a><br>
<a href="https://regexr.com/">See Regex what text matches</a>

Literal <br>
`var pattern = /a/`<br>
<br>
Object generator <br>
`var pattern = new RegExp('a');`<br>

{% highlight javascript %}
var pattern = new RegExp('a');
console.log(pattern.exec('abcdef')); // return array that RegExp ["a"]
cnosole.log(pattern.test('bcdefg')); // return boolean value false
// this is string method for generics
console.log('abcdef'.match(pattern)); // ["a"]
console.log('abcdef'.replace(pattern, 'A'));  // Abcdef
{% endhighlight %}

Gernerics has some options.

	•	/a/ : normal
	•	/a/i : doesn't distinguish capital letter.
	•	/a/g : return all of result.

See selab lecture note.

{% highlight javascript %}
var og = /a/g;
console.log("abcdea".match(og)); // ["a", "a"]
{% endhighlight %}

{% highlight javascript %}
var pattern = /(\w+)\s(\w+)/;
var str = "coding everybody";
var result = str.replace(pattern, "$2, $1");
// $2 : in pattern, 2nd group. -> after '\s' : (\w+)
// $ can be possible to recycle matching in pattern like a variable.
console.log(result); // everybody, coding
{% endhighlight %}

{% highlight javascript %}
var urlPattern = /\b(?:https?):\/\/[a-z0-9-+&@#\/%?=~_|!:,.;]*/gim;
var content = '생활코딩 : http://opentutorials.org/course/1 입니다.;
var result = content.replace(urlPattern, function(url){
    // when you find urlPattern, call 2nd parameter function in replace. 
    // where is url from? when urlPattern is matched, transfer to function
    // that is 1st parameter url.
    return '<a href="'+url+'">'+url+'</a>';
});
console.log(result); // 생활코딩 : <a href="http://opentutorials.org/course/1">http://opentutorials.org/course/1</a> 입니다.
{% endhighlight %}


<hr>


## Web Page

### document

	•	document.write('String'); : Write String on web page.
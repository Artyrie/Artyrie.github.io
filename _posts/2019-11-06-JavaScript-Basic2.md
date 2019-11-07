---
layout: post
title:  "JavaScript Basic2"
date:   2019-11-06
excerpt: "Just about JavaScript Practice"
tag:
- Java Script
comments: true
---

# JavaScript

	•	This page is my note about javascript.
	•	It will be difficult to read.
	•	Comment : //

Caution : Ungly English <br>
Sample code is almost reffered in <a href="https://opentutorials.org/course/743">생활코딩</a> 

## important concept of programming

	•	Class : design to make object.
	•	Object : making target in software world.
	•	Instance : maked detail substance in software world by design.


<hr>


# JavaScript as functional Language

## Scope

{% highlight javascript %}
var gscope = 'global variable';
function fscope(){
    lscope ='local';
}
{% endhighlight %}

{% highlight javascript %}
function main(){ 
    for(var i=0; i<5; i++){ 
        var temp = i; 
    }
console.log(temp); 
} 
main();
{% endhighlight %}

Scope is different to the other language. <br>
JS's local variable in function is usable until function ends. <br>
So, console.log(temp) works well. <br>

{% highlight javascript %}
var i = 5;
function a(){
    var i = 10;
    b();
}
function b(){
    document.write(i);
}
a();
{% endhighlight %}

This result is 5.  <br>
function scope is only in function. <br>
you must test this point. <br>
variable priority is local variable.<br>
refer this <a href="https://yuddomack.tistory.com/entry/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EB%B3%80%EC%88%98%EC%99%80-%EC%8A%A4%EC%BD%94%ED%94%84%EC%9C%A0%ED%9A%A8%EB%B2%94%EC%9C%84">lecture blog</a>

{% highlight javascript %}
MYAPP = {}
MYAPP.calculator = {
    'left' : null,
    'right' : null
}
MYAPP.coordinate = {
    'left' : null,
    'right' : null
}
 
MYAPP.calculator.left = 10;
MYAPP.calculator.right = 20;
function sum(){
    return MYAPP.calculator.left + MYAPP.calculator.right;
}
document.write(sum());
{% endhighlight %}

If you have to use global variable, <br>
you can make object for controlling the variables that you may make global. <br>
Even you don't want to use global variable, <br>

{% highlight javascript %}
(function(){
    var MYAPP = {}
    MYAPP.calculator = {
        'left' : null,
        'right' : null
    }
    MYAPP.coordinate = {
        'left' : null,
        'right' : null
    }
    MYAPP.calculator.left = 10;
    MYAPP.calculator.right = 20;
    function sum(){
        return MYAPP.calculator.left + MYAPP.calculator.right;
    }
    document.write(sum());
}())
{% endhighlight %}

you can modulize your code using unnamed function. <br>
This is formal way for modulization.


## Property of function

{% highlight javascript %}
function cal(func, num){
    return func(num)
}
function increase(num){
    return num+1
}
function decrease(num){
    return num-1
}
alert(cal(increase, 1));
alert(cal(decrease, 1));
{% endhighlight %}

Actually function is object. <br>
So, function can be value and pass as value. <br>
It is also used as return value or array of value.

{% highlight javascript %}
function sortNumber(a,b){
    return b-a;
}
var numbers = [20, 10, 9,8,7,6,5,4,3,2,1];
alert(numbers.sort(sortNumber)); // array, [20,10,9,8,7,6,5,4,3,2,1]
{% endhighlight %}

if variable is placed where front of '.', It is object. <br>
numbers.sort(); <- numbers is array object. <br>
array object has sort method. <br>

	•	 Function is partition of code what has independent function
	•	 Method is some function which is included in class / structure / ect.

{% highlight javascript %}
var numbers = [20, 10, 9,8,7,6,5,4,3,2,1];
numbers.sort()
// [1, 10, 2, 20, 3, 4, 5, 6, 7, 8, 9] sorted as string;
{% endhighlight %}

Syntax of array is array.sort(sortfunc:optional) <br>
Basically, It sorts by string (alphabet). <br>
Number was made as string, so 10 is front of 20. <br>
So, use sortfunc to decide priority of sorting.

{% highlight javascript %}
var numbers = [20, 10, 9,8,7,6,5,4,3,2,1];
var sortfunc = function(a, b) {
	console.log(a,b);
	return a-b; // return b-a <- reverse sort
}
numbers.sort(sortfunc);
{% endhighlight %}

## Using call back sample

{% highlight javascript %}
{"title":"JavaScript","author":"egoing"}
{% endhighlight %}

{% highlight html %}
<!DOCTYPE html>
<html>
<head>
<script src="//code.jquery.com/jquery-1.11.0.min.js"></script>
</head>
<body>
<script type="text/javascript">
    $.get('./datasource.json.js', function(result){
        console.log(result);
    }, 'json');
</script>
</body>
</html>
{% endhighlight %}

this code from <a href="https://opentutorials.org/course/743/6508">생활코딩</a><br>

## Inner function

{% highlight javascript %}
function outter(){
    var title = 'coding everybody';  
    function inner(){        
        alert(title);
    }
    inner();
}
outter();
{% endhighlight %}

Inner function that is in function can use local variable <br>
in outter function. <br>

## Closure

{% highlight javascript %}
function outter(){
    var title = 'coding everybody';  
    return function(){        
        alert(title);
    }
}
inner = outter();
inner();
{% endhighlight %}

`inner = outter();` ends, local variable in function outter <br>
disappears because of `outter();` is end. <br>
but as a result of `inner();`, alert 'coding everybody'. <br>
Why? local variable didn't disappear. <br>
outter function doens't disappear until inner function ends

{% highlight javascript %}
function factory_movie(title){
    return {
        get_title : function (){
            return title;
        },
        set_title : function(_title){
            title = _title
        }
    }
}
ghost = factory_movie('Ghost in the shell');
matrix = factory_movie('Matrix');
 
alert(ghost.get_title());
alert(matrix.get_title());
 
ghost.set_title('공각기동대');
 
alert(ghost.get_title());
alert(matrix.get_title());
{% endhighlight %}

There is some property.

	•	 closure can makes class.
	•	 It can make private declaring way // JS doens't have.
	•	 When outter function is executed, generate new closure.
	•	 So,  It can be independent object.
	•	 In this code, passed title only can be controlled by method.

## Advanced Closure

{% highlight javascript %}
var arr = []
for(var i = 0; i < 5; i++){
    arr[i] = function(){
        return i;
    }
}
for(var index in arr) {
    console.log(arr[index]());
}
{% endhighlight %}

`arr[index]` has just `return i`. So, i=5. <br>
result : repeat 5, 5 times <br>

{% highlight javascript %}
var arr = []
for(var i = 0; i < 5; i++){
    arr[i] = function(id) {
        return id;
    }
}
for(var index in arr) {
    console.log(arr[index]());
}
{% endhighlight %}

This code shows undefined 5 times. <br>
Why? function(id) need a parameter id. <br>
but we didn't give parameter id.

{% highlight javascript %}
var arr = []
for(var i = 0; i < 5; i++){
    arr[i] = function(id) {
		return id;
    }(i); // function(i);
}
for(var index in arr) {
    console.log(arr[index]); // arr[index] is not function.
	// because arr[index] has retuned id value that i.
}
{% endhighlight %}

So, this is correct way. <br>
but we can use closure, too.

{% highlight javascript %}
var arr = []
for(var i = 0; i < 5; i++){
    arr[i] = function(id) {
        return function(){
            return id;
        }
    }(i);
}
for(var index in arr) {
    console.log(arr[index]());
}
{% endhighlight %}

I think this way is no essential. <br>
Just showing possible.

## Hidden varialbe in function

{% highlight javascript %}
function sum(){
    var i, _sum = 0;    
    for(i = 0; i < arguments.length; i++){
        document.write(i+' : '+arguments[i]+'<br />');
        _sum += arguments[i];
    }   
    return _sum;
}
document.write('result : ' + sum(1,2,3,4));
{% endhighlight %}

arguments similar to array and It's values is passed arguments. <br>
So, arguments is `[1,2,3,4]`<br>
arguments is instance of arguments object.
Thus this property, what function need 2 parameters and <br>
we pass 1 parameter, then function.length is 2 and arguments,length is 1  <br>
arguments is number of passed parameter. <br>
function.length is number of variables that function needs.

## Calling the function

JavaScript's function is object. <br>
So, 

{% highlight javascript %}
function sum(arg1, arg2){
    return arg1+arg2;
}
{% endhighlight %}

this function; sum is instance of function object. <br>
So sum can call method of function. <br>
like `sum.apply(null, [1,2])` <br>

{% highlight javascript %}
o1 = {val1:1, val2:2, val3:3}
o2 = {v1:10, v2:50, v3:100, v4:25}
function sum(){
    var _sum = 0;
    for(name in this){
        _sum += this[name];
    }
    return _sum;
}
alert(sum.apply(o1)) // 6
alert(sum.apply(o2)) // 185
{% endhighlight %}

`sum.apply(o1)` makes sum to method of o1 object <br>
and call sum and delete sum. <br>
`o1.sum = sum;` -> function definition

# Objective JavaScript

## Object : Class

{% highlight javascript %}
var person = {
    'name' : 'egoing',
    'introduce' : function(){
        return 'My name is '+this.name;
    }
}
document.write(person.introduce());
{% endhighlight %}

This code can't recycle.

{% highlight javascript %}
function Person(name){
    this.name = name;
    this.introduce = function(){
        return 'My name is '+this.name; 
    }   
}
var p1 = new Person('egoing');
document.write(p1.introduce()+"<br />");
 
var p2 = new Person('leezche');
document.write(p2.introduce());
{% endhighlight %}

Define property of object in constructor 'new'. <br>
So, we can recycle this code. <br><br>
Global object is property of window property. <br>
`window.func();` can execute.

## Special property of this object

{% highlight javascript %}
var funcThis = null; 
function Func(){
    funcThis = this;
}
var o1 = Func();
if(funcThis === window){
    document.write('window <br />');
}
var o2 = new Func();
if(funcThis === o2){
    document.write('o2 <br />');
}
//window
//o2
{% endhighlight %}

This depends on your code that It indicates what. <br>
So when the function called, this indicates window object. <br>
But method of this indicates it's object. <br>

## Function has method from the first

Every function has method that is not written by user. <br>
Note important 3 method.

	•	call
	•	bind
	•	method

{% highlight javascript %}
var example = function (a, b, c) {
  return a + b + c;
};
example(1, 2, 3);
example.call(null, 1, 2, 3);
example.apply(null, [1, 2, 3]);
{% endhighlight %}

These are ways that calls function. <br>
Argument `null` alternate `this` <br>
What is different that calling function is on code.

{% highlight javascript %}
var obj = {
  string: 'zero',
  yell: function() {
    alert(this.string);
  }
};
var obj2 = {
  string: 'what?'
};
obj.yell(); // 'zero';
obj.yell.call(obj2); // 'what?'
{% endhighlight %}

Use call with `obj2`, this of this becomes obj2. <br>
Thus prints what? <br>

### It can use function of the other object.

Where we use it? <br>
When arguments is controlled, we need it. <br>
Arguments is similar to array, explained before.

{% highlight javascript %}
function example3() {
  console.log(Array.prototype.join.call(arguments));
}
example3(1, 'string', true); // '1,string,true'
{% endhighlight %}

It can use this way. <br>
Arguments is not array. So, use this way. <br>
More information : <a href="https://www.zerocho.com/category/JavaScript/post/57433645a48729787807c3fd">Zerocho</a>


<hr>


## Inheritance

### Prototype


{% highlight javascript %}
function Ultra(){}
Ultra.prototype.ultraProp = true; 
function Super(){}
Super.prototype = new Ultra();
function Sub(){}
Sub.prototype = new Super();
 var o = new Sub();
console.log(o.ultraProp); // true
{% endhighlight %}

Prototype is original of object. <br>
It is special property of object. <br>
Saved data in prototype is connected, <br>
when the constructor `new` makes new object. <br>
Prototype is chain that connects between object and the other object.

### Inheritance

{% highlight javascript %}
function Person(name){
    this.name = name;
}
Person.prototype.name=null;
Person.prototype.introduce = function(){
    return 'My name is '+this.name; 
} 
function Programmer(name){
    this.name = name;
}
Programmer.prototype = new Person();
Programmer.prototype.coding = function(){
    return "hello world";
}
 var p1 = new Programmer('egoing');
document.write(p1.introduce()+"<br />"); // My name is egoing
document.write(p1.coding()+"<br />"); // hello world
{% endhighlight %}

Programmer inherited Person. <br>
So, It can use person's method and new own method. <br>
It is different form of `class Person extends Programmer`

## Standard Built-in Object

JavaScript has built-in object.

	•	Object
	•	Function
    •	Array
    •	String
    •	Boolean
    •	Number
    •	Math
    •	Date
    •	RegExp

{% highlight javascript %}
Array.prototype.rand = function(){
    var index = Math.floor(this.length*Math.random());
    return this[index];
}
var arr = new Array('seoul','new york','ladarkh','pusan', 'Tsukuba');
console.log(arr.rand());
{% endhighlight %}

This code is expansion of array. <br>
Output of this function is random value in array.

## Expansion of Object

We can make API that all of object approaches by expanding object.

{% highlight javascript %}
Object.prototype.contain = function(neddle) {
    for(var name in this){
        if(this[name] === neddle){
            return true;
        }
    }
    return false;
}
var o = {'name':'egoing', 'city':'seoul'}
console.log(o.contain('egoing'));
var a = ['egoing','leezche','grapittie'];
console.log(a.contain('leezche'));
{% endhighlight %}

We can make contain method. <br>
But, this way is bad because of confusion of development. <br>
if you want to check this property `contain` is function's own property, <br>
use this `hasOwnProperty(object.what)`


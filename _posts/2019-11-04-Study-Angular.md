---
layout: post
title:  Angular Note
date:   2019-11-04
excerpt: "Note for Angular"
tag:
- Type Script
comments: true
---

# Angular CLI

## Open Server

ng serve
> localhost:4200

## Generating component

ng g c name
<ul>
<li> ng : angular </li>
<li> g : generate </li>
<li> c : component </li>
</ul>

# Angular

This document is just written through my understanding.<br>
So, It is not exact. If you want to learn Angular, please read
<a href="https://angular.kr/">Angular Site</a><br>
Caution : This document is difficult to read.

## Angular has 3 property.

<ul>
<li>component.html : show html </li>
<li>component.css : decorate html </li>
<li>component.ts : for action and define(?) </li>
</ul>

## About .ts

### .ts file: templateUrl -> template (inline)

`<h3>Test</h3> <p>Practice</p>`
It naturally use interpolation. {{variable}}
Caution : backquote! not single quote.

### Also use in HTMl

like this.
{% highlight html %}
<h3>{{ variable + function() }}</h3>
{% endhighlight %}

### ts : Import
from '@angular/...' <- this is node module<br>
from './app/...' <- just file.<br>
<br>
main.ts works angular. Read and understand.

### add component
by hand : modify app.module.ts<br>
 -> in declarations<br>
automatically : use cli

### decorator : @
Special function of TypeScript. <br>
ex) in app.module.ts, @NgModule() function has object type parameters. <br>
<ul>
<li>delarations: [ ], </li>
<li>imports: [ ], </li>
<li>providers: [], </li>
<li>bootstrap: [] </li>
</ul>
Have to add meaning of @ later.

### main.ts
what is main function that start angular.

### app.module.ts
app.module.ts has @NgModule <br>
<ul>
<li> declarations: [] => has what we're component</li>
<li> imports: [] => has angular module </li>
<li> providers: [] => add later </li>
<li> bootstrap: [] => add later </li>
</ul>

### app.component.ts
app.component.ts has @component <br>
<ul>
<li> selector: html tag name </li>
<li> templateUrl: this component's html <= data </li>
<li> styleUrls: Decoration - css </li>
</ul>
then this 3 property(?) construct component(module)<br>


<hr>

## About html

### Angular makes custom html tag

If you make app-test component set, <br>
you can use like this.

{% highlight html %}
<app-test></app-test>
{% endhighlight %}

and this tag is html file that component has.


### Button Event

{% highlight html %}
<button onclick="function()">button name</button>
{% endhighlight %}
just html <br>
and function is in component's ts file. <br>
write function in component's export class in ts file.

### Data Binding

one way data binding : ts -> html or html -> ts
{% highlight html %}
{{ variable }}
{% endhighlight %}
like this. <br>
or button in html. <br>
two way data binding : ts <-> html <br>
ngModel is in FormsModule. <br>
So to use ngModel, add import FormsModule in app.module.ts
{% highlight html %}
<p>{{variable}}</p>
<input type="text" [(ngModel)]="variable" >
{% endhighlight %}

### Directive
Directive usually has '*' mark. <br>
Use any tag <br>
<ul>
<li> *ngIf
{% highlight html %}
<div *ngIf="expession; else otherTmp">contents</div>
<ng-template #otherTmp>not satisfy if</ng-template>
{% endhighlight %}
<br> satisfy if, show div contents
</li>
<li> %ngFor
{% highlight html %}
<div *ngFor="let product of products">
  <h3>
    <a [title]="product.name + ' details'">
      {{ product.name }}
    </a>
  </h3>
    <p *ngIf="product.description">
    Description: {{ product.description }}
  </p>
  <button (click)="share()">
    Share
  </button>

  <app-product-alerts
  [product]="product"
  (notify)="onNotify()">
</app-product-alerts>
</div>
{% endhighlight %}
<br>
Code from <a href="https://angular.kr/start">Angular tutorial</a><br>
[title]="product.name ..." : tooltip:hover <br>
*ngFor="let variable of list" : think foreach <br>
Plus : {{ product | json }} <- show type of product <br>



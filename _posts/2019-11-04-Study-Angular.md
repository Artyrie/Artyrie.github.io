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
* localhost:4200

## Generating component

ng g c name

* ng : angular
* g : generate
* c : component

---

# Angular

This document is just written through my understanding.<br>
So, It is not exact. If you want to learn Angular, please read
<a href="https://angular.kr/">Angular Site</a><br><br>
Caution : This document is difficult to read.

## Angular has 3 property.

* component.html : show html
* component.css : decorate html
* component.ts : for action and define(?)

---

# About .ts

Caution
* use '{' '}' -> q p
* ugly English. (I'm not good english user)

## .ts file: templateUrl -> template (inline)

`<h3>Test</h3> <p>Practice</p>` <br>
backquote is eliminated by markdown grammer. <br>
It naturally use interpolation.<br> `qq variable pp` <br><br>
Caution : backquote! not single quote.

## Also use in HTMl

like this. <br>
`<h3>qq variable + function() pp</h3>`

## ts : Import
from '@angular/...' <- this is module<br>
from './app/...' <- just file.<br>
<br>
main.ts works angular. Read and understand.

## add component
by hand : modify app.module.ts<br>
 -> in declarations<br>
automatically : use cli

## decorator : @
Special function of TypeScript. <br>
I think it is used when moudule is called.<br>
ex) in app.module.ts, @NgModule() function has object type parameters. <br>

* delarations: [ ],
* imports: [ ],
* providers: [ ],
* bootstrap: [ ]

## main.ts
what is main function that start angular.

## app.module.ts
app.module.ts has @NgModule <br>
* declarations: [ ] => has what we're component
* imports: [ ] => has angular module
* providers: [ ] => has maden service
* bootstrap: [ ] => add later

## app.component.ts
app.component.ts has @component <br>
* selector: html tag name
* templateUrl: this component's html <= data
* styleUrls: Decoration - css

then this 3 property(?) construct component(module)

## Service; name.service.ts
It is different to component <br>

Feature

* Dependency Injection <- variable must have service type data for declaring.
* Have one file; TypeSript
* Connected many file.
* Use to extract data for component.

Use

* Import Service file to component file.
* Add constructor in component class that has parameter service type.
* Add app.module.ts in providers <- service file.

Caution

* All of class can be data type.
* Angular class makes 1 instance because 1 instance is used by many component. <- Singleton


<hr>


# About html

## Angular makes custom html tag

If you make app-test component set, <br>
you can use like this. <br>

`<app-test></app-test>`

and this tag is html file that component has.


## Button Event

`<button onclick="function()">button name</button>`

just html <br>
and function is in component's ts file. <br>
write function in component's export class in ts file.

## Data Binding

### one way data binding : ts -> html or html -> ts

`qq variable pp`

like this. <br>
or button in html. <br>

### two way data binding : ts <-> html

ngModel is in FormsModule. <br>
So to use ngModel, add import FormsModule in app.module.ts

`<p>qq variable pp</p>
<input type="text" [(ngModel)]="variable" >`

## Directive
Directive usually has '*' mark. <br>
Use any tag <br>

* *ngIf
{% highlight html %}
<div *ngIf="expession; else otherTmp">contents</div>
<ng-template #otherTmp>not satisfy if</ng-template>
{% endhighlight %}

satisfy if, show div contents

* %ngFor
{% highlight html %}
<div *ngFor="let product of products">
  <h3>
    <a [title]="product.name + ' details'">
      qq product.name pp
    </a>
  </h3>
    <p *ngIf="product.description">
    Description: qq product.description pp
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
Plus : qq product | json pp <- show type of product <br>

## Difference of data calling way

{% highlight html %}
  <p>interpolation : </p>
  <p> - hello, qq name pp!</p>
  <p>property binding : </p>
  <p [textContent]="name">not show this area</p>
  <p>interpolation : </p>
  <img src="{{imgUrl}}" />
  <p>property binding : </p>
  <img [src]="imgUrl" />
{% endhighlight %}

Free to use any way.
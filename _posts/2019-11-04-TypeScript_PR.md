---
layout: post
title:  PR_Type Script
date:   2019-11-03
excerpt: "Just about everything you'll need to style in the theme: headings, paragraphs, blockquotes, tables, code blocks, and more."
tag:
- Type Script
comments: true
---

## Type Script Practice
Use Type Script debugger by <a href="https://github.com/Enterprise-JS/vscode-ts-node-debugging">vscode-ts-code-debugging</a><br>
Code and Explanation is in.

#### Class and Calling
<ul>
<li>Class_Call : index.ts<br>{% highlight typescript %}
import { Person } from './person';

let person = new Person('Bob', 34);

console.log(person.getGreeting());
{% endhighlight %}</li>

<li>Class : person.ts<br>{% highlight typescript %}
export class Person {

    constructor(
        public name: string,
        public age: number) {
    }

    getGreeting() {
        return 'Hi ' + this.name;
    }

}
{% endhighlight %}</li>
</ul>
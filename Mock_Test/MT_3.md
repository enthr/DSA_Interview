# DSA | Mock Test-3 | JavaScript


## 1. Implement a stack using an array in JavaScript. Include the necessary methods such as push, pop, and isEmpty.


### Solution


```javascript
class Stack {
    constructor() {
        this.items = [];
    }

    push(element) {
        this.items.push(element);
    }

    pop() {
        if (this.items.length === 0) return "UNDERFLOW";
        return this.items.pop();
    }

    peek() {
        return this.items[this.items.length - 1];
    }

    isEmpty() {
        return this.items.length === 0;
    }

    size() {
        return this.items.length;
    }

    printStack() {
        let str = "";
        for (let i = 0; i < this.items.length; i++) str += this.items[i] + "| ";
        return str;
    }
}
```


## 2. Implement a queue using an array in JavaScript. Include the necessary methods such as enqueue, dequeue, and isEmpty.


### Solution


```javascript
class Queue {
    constructor() {
        this.items = [];
    }

    enqueue(element) {
        this.items.push(element);
    }

    dequeue() {
        if (this.isEmpty()) return "Underflow";
        return this.items.shift();
    }

    isEmpty() {
        return this.items.length === 0;
    }

    size() {
        return this.items.length;
    }

    display() {
        let str = "";
        for (let i = 0; i < this.items.length; i++) str += this.items[i] + " ";
        return str;
    }
}
```
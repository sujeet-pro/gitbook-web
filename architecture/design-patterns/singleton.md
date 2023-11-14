# Singleton

### TLDR;

It's an anti-pattern in Javascript. For languages that don't allow creating objects directly, it makes sense to have a singleton for JS, you could directly create your object.

```javascript
const yourObject = {
    property: 'value',
    methods() {
        return this.property
    }
}

export const Object.freeze(yourObject)
```



### Mimicking using classes

```
let instance

export class YouClass {
    constructor() {
        if(instance) throw new Error()
    }
    
    static getInstance() {
       if(!instance) {
           instance = new YourClass()
       } 
       return instance
    }
}
```

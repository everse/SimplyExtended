SimplyExtended
==============

#### Define a new object
These are all equivalent. 
```JS

var ObjectLiteral = {
    // Definition
};

var ObjectLiteralExtension = {}.extend({
    // Definition
});

var ObjectExtension = Object.extend({
    // Definition
});
```

#### Initiation methods
Any method in the definition that starts with 'init' will be used to create constructors.

#### Example definition
```JS

var Animal = Object.extend('abstract', {
    name: 'noname',
    eyes: 0,
    
    format: function (num) {
        return "Legs: " + num;
    },
    getLegs: function () {
        return this.format(this.legs);
    }
});

var Dog = Animal.extend({
    legs: 4,
    
    format: function (num) {
        return "This dog has " + num + " legs.";
    },
    init: function () {
        this.eyes = 2;
    },
    initWithName: function (name) {
        this.name = name;
        this.__init__.init.call(this);
    }
});

```

#### Initiation and use
```JS

// Call one of the 'init' methods to create an instance.
var dog = Dog.initWithName('Charlie');

// Call a method defined in the parent with the format method overwritten
dog.getLegs() // Prints: "This dog has 4 legs."
```

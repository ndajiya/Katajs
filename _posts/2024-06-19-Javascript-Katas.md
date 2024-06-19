---
title: "Javascript Katas"
date: 2024-06-19
---

In martial arts, a kata is a predefined sequence of movements that practitioners use to practice techniques and improve their skills. 
The equivalent concept in JavaScript would be a design pattern or a coding pattern. These are structured and repeatable solutions to 
common programming problems, providing a form or blueprint for writing code in a particular style.

Here are some examples of common design patterns in JavaScript that could be considered the "kata" of JavaScript programming:

1. Module Pattern
Description: This pattern is used to create a module, which is a way to encapsulate private and public methods and variables.

Example:
```
var myModule = (function () {
    var privateVariable = 'I am private';
    
    function privateMethod() {
        console.log(privateVariable);
    }
    
    return {
        publicMethod: function () {
            privateMethod();
        }
    };
})();

myModule.publicMethod(); // Outputs: I am private
```

2. Singleton Pattern
Description: This pattern restricts the instantiation of a class to a single instance.

Example:
```
var Singleton = (function () {
    var instance;

    function createInstance() {
        var object = new Object("I am the instance");
        return object;
    }

    return {
        getInstance: function () {
            if (!instance) {
                instance = createInstance();
            }
            return instance;
        }
    };
})();

var instance1 = Singleton.getInstance();
var instance2 = Singleton.getInstance();

console.log(instance1 === instance2); // Outputs: true
```

3. Observer Pattern
Description: This pattern allows an object (subject) to maintain a list of dependents (observers) and notify them of state changes.

Example:
```
function Subject() {
    this.observers = [];
}

Subject.prototype = {
    subscribe: function (fn) {
        this.observers.push(fn);
    },
    unsubscribe: function (fn) {
        this.observers = this.observers.filter(observer => observer !== fn);
    },
    notify: function (data) {
        this.observers.forEach(observer => observer(data));
    }
};

var subject = new Subject();

function Observer1(data) {
    console.log('Observer 1 received data:', data);
}

function Observer2(data) {
    console.log('Observer 2 received data:', data);
}

subject.subscribe(Observer1);
subject.subscribe(Observer2);

subject.notify('Some data'); // Outputs: Observer 1 received data: Some data
                             //          Observer 2 received data: Some data
```

4. Factory Pattern
Description: This pattern is used to create objects without specifying the exact class of object that will be created.

Example:
```
function Car(options) {
    this.make = options.make || 'Default make';
    this.model = options.model || 'Default model';
}

function Truck(options) {
    this.make = options.make || 'Default make';
    this.model = options.model || 'Default model';
}

function VehicleFactory() {}

VehicleFactory.prototype.createVehicle = function (options) {
    switch (options.vehicleType) {
        case 'car':
            return new Car(options);
        case 'truck':
            return new Truck(options);
        default:
            return new Car(options);
    }
};

var factory = new VehicleFactory();

var car = factory.createVehicle({
    vehicleType: 'car',
    make: 'Toyota',
    model: 'Corolla'
});

var truck = factory.createVehicle({
    vehicleType: 'truck',
    make: 'Ford',
    model: 'F-150'
});

console.log(car); // Outputs: Car { make: 'Toyota', model: 'Corolla' }
console.log(truck); // Outputs: Truck { make: 'Ford', model: 'F-150' }
```

5. Prototype Pattern
Description: This pattern is used to create new objects based on a prototype of an existing object.

Example:
```
var vehiclePrototype = {
    init: function (carModel) {
        this.model = carModel;
    },
    getModel: function () {
        console.log('The model of this vehicle is ' + this.model);
    }
};

function vehicle(model) {
    function F() {}
    F.prototype = vehiclePrototype;
    var f = new F();
    f.init(model);
    return f;
}

var car = vehicle('Toyota');
car.getModel(); // Outputs: The model of this vehicle is Toyota
```
These design patterns provide structured ways to solve common programming problems and can be practiced and mastered similarly to how 
martial artists practice katas. By learning and implementing these patterns, JavaScript developers can write more efficient, maintainable, 
and scalable code.

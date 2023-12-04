How to keep Code Decoupled?

Keeping your code decoupled is a core principle in software engineering, particularly relevant in object-oriented programming (OOP). Here's a breakdown of how you can apply this principle to ensure that objects manage their own state:

Encapsulation: Encapsulation is about bundling the data (state) and the methods (behaviors) that operate on the data into a single unit or class. By encapsulating state and behavior, you can ensure that state changes are only done through the object's methods, which can maintain the object's integrity.

Use Getter and Setter Methods: Instead of allowing direct access to object properties, provide getter and setter methods. The setter methods can include validation logic or other constraints, ensuring that the object's state remains valid or consistent.

Responsibility Assignment: Make each object responsible for its own state and behavior. This means that if an object needs to change its state, it should have a method to do so internally rather than allowing external entities to modify its state directly.

Limit External Interactions: Limit how much one object knows about another. Use interfaces or abstract classes to interact with other objects. This way, you rely on contracts defined by interfaces or abstract methods, reducing dependency on the concrete implementation details of other objects.

High Cohesion and Low Coupling: Strive for high cohesion within objects and low coupling between them. High cohesion means that an object's methods and properties are closely related to each other. Low coupling refers to minimizing dependencies between objects, making it easier to change one part of the system without affecting others.

Principle of Least Knowledge (Law of Demeter): Each unit should have only limited knowledge about other units and should only talk to its immediate friends (e.g., objects it directly holds references to).

Use Design Patterns Wisely: Some design patterns like Command, Strategy, or State can help in keeping the code decoupled and managing state changes in a more organized way.

Applying these principles will lead to a more maintainable, scalable, and robust application. It also makes the codebase easier to understand and modify, as changes to the state of an object are localized to the object itself.

Certainly! Let's consider a simple example to illustrate the principle of keeping your code decoupled, especially in the context of changing an object's state. We'll use a Car class in this example.

In a decoupled design, the Car class will encapsulate its state and provide methods to modify it. This ensures that all changes to the car's state go through the car's own methods, maintaining the integrity and consistency of its state.

Here's a basic implementation in TypeScript:

```
class Car {
    private speed: number;

    constructor() {
        this.speed = 0;
    }

    // Getter method for speed
    getSpeed(): number {
        return this.speed;
    }

    // Method to increase speed
    accelerate(increment: number): void {
        if (increment > 0) {
            this.speed += increment;
        }
    }

    // Method to decrease speed
    decelerate(decrement: number): void {
        if (decrement > 0 && this.speed >= decrement) {
            this.speed -= decrement;
        }
    }
}

// Usage
const myCar = new Car();
console.log(`Initial Speed: ${myCar.getSpeed()}`); // 0

myCar.accelerate(20);
console.log(`Speed after acceleration: ${myCar.getSpeed()}`); // 20

myCar.decelerate(5);
console.log(`Speed after deceleration: ${myCar.getSpeed()}`); // 15
```

In this example:

Encapsulation: The speed property is private, which means it cannot be accessed or modified directly from outside the Car class.

Controlled State Change: The methods accelerate and decelerate are the only ways to modify the car's speed. They can include additional logic for validation (like checking for negative increments) and ensure that the car's speed never goes below zero.

Cohesion: The Car class has high cohesion as all its methods and properties are closely related to the concept of a car.

By following this approach, you ensure that the Car object controls its internal state, leading to a more maintainable and robust design.

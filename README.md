# L2-assignment-1
# 🎯 TypeScript Concepts Blog – Interview Ready

This blog covers two essential TypeScript topics that are commonly asked in interviews. Understanding these will not only help in technical discussions but also in writing scalable and maintainable code.

---

## 🔍 1. Interfaces vs. Types in TypeScript

In TypeScript, both `interface` and `type` are used to define the shape of objects. While they may seem interchangeable at first, there are key differences that affect how and when to use them.

### ✅ Interface

- Best used for defining the structure of **objects and classes**
- **Extensible**: You can extend an existing interface using `extends` or by declaring it again
- Ideal for use in **OOP-style architecture**

```ts
interface Person {
  name: string;
  age: number;
}

interface Employee extends Person {
  employeeId: number;
}

const employee: Employee = {
  name: "John",
  age: 30,
  employeeId: 101
};
✅ Type
More flexible than interfaces

Can represent primitives, unions, tuples, and more

Cannot be re-opened or merged once declared


type Car = {
  brand: string;
  model: string;
};

type ElectricCar = Car & { batteryLife: number };

const tesla: ElectricCar = {
  brand: "Tesla",
  model: "Model 3",
  batteryLife: 400
};
🆚 Summary of Differences
Feature	Interface	Type
Extendable	✅ Yes	✅ (via &)
Merging Declarations	✅ Yes	❌ No
Union Types	❌ No	✅ Yes
Use with Primitives	❌ No	✅ Yes

📌 When to use what?

Use interface when working with objects or classes

Use type for complex types, unions, or primitives

🔑 2. Using keyof in TypeScript (with Example)
The keyof keyword is a TypeScript operator used to extract the keys of a given type as a union of string literals.

✅ Why Use keyof?
Enables type-safe access to properties

Useful in generic functions, mappings, and reflections

🔧 Example


type Product = {
  id: number;
  name: string;
  price: number;
};

type ProductKeys = keyof Product; // "id" | "name" | "price"

function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}

const book: Product = {
  id: 1,
  name: "TypeScript Guide",
  price: 30
};

const productName = getProperty(book, "name"); // returns "TypeScript Guide"
🧠 Explanation:
keyof Product gives us a union of the property keys: "id" | "name" | "price"

We use K extends keyof T to ensure the key is valid for the given object type

This pattern ensures compile-time safety and better tooling support

📦 Repo Contents
solutions.ts – Contains all TypeScript examples and solutions

README.md – Blog content (this file)

📁 All code is original and organized inside a single public repository.

📌 Conclusion
Understanding interface vs. type and the keyof keyword will significantly improve how you write, refactor, and scale TypeScript projects. These tools provide strong type safety, flexibility, and expressiveness – essential qualities for building robust applications.
---
{"dg-publish":true,"permalink":"/instance-type/","tags":["TypeScript","dev"]}
---

In TypeScript classes [are both a value and a type](https://www.typescriptlang.org/docs/handbook/declaration-merging.html#basic-concepts).

```ts
class Foo {}
```

When you reference a class variable as a type it effectively references an interface for an instance of that class.

```ts
const foo = new Foo()

function getFoo(): Foo {
  return foo
}

const foo = getFoo() // const foo: Foo
```

If you want to reference the constructor function for that class you must use the `typeof` operator, e.g. in a factory function.

```ts
function createFoo(fooConstructor: typeof Foo): Foo {
	return new fooConstructor();
}

const foo = createFoo(Foo);
```

If for some reason you don't have a reference to the class declaration but you do have a reference to the constructor function then you can use `InstanceType` to get back to the class, e.g. in a *generic* factory function.

```ts
declare function create<T extends new () => any>(c: T): InstanceType<T>

class A { }
class B { }
let a = create(A) // A
let b = create(B) // B
```
*Above courtesy of [this GitHub issue comment](https://github.com/Microsoft/TypeScript/issues/25998#issuecomment-471367329)*
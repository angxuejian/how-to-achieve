# 泛型工具类型（Utility-Types）

皆为 Typescript 提供的内置类型

TS官方文档：[Utility Types](https://www.typescriptlang.org/docs/handbook/utility-types.html)


## Promise<string>
> interface Promise<T>

定义 Promise resolve状态后的类型，reject默认为`any`类型
<!-- Typescript 中 Promise reject 的类型该如何定义？ -->

## Awaited<Type>
> type Awaited<T> = T extends null | undefined ? T : T extends object & { then(onfulfilled: infer F, ...args: infer _): any; } ? F extends (value: infer V, ...args: infer _) => any ? Awaited<...> : never : T

等待promise .then后的类型

```ts
type t1 = Awaited<Promise<string>>
// type t1 = string

type t2 = Awaited<Promise<Promise<{ name: string }>>>
// type t2 = {
//   name: string
//}

type t3 = Awaited<boolean | Promise<string>>
// type t3 = boolean | string
```


## Partial<Type>
> type Partial<T> = { [P in keyof T]?: T[P] | undefined; }

Partial 是 TypeScript 提供的一个内置泛型类型，用于创建一个类型的所有属性都变为可选（optional）的新类型。这个类型在处理对象的部分属性时非常有用，尤其是在函数需要处理对象的部分属性时。

```ts
interface User {
    name: string;
    age: number;
    occupation: string;
}

type PartialUser = Partial<User>;
// type PartialUser = {
//   name?: string;
//   age?: age;
//   occupation?: string;
// }
```

## Exclude<UnionType, ExcludedMembers>
> type Exclude<T, U> = T extends U ? never : T

通过从所有可分配的Type中，排除非赋值类型，来构造一个类型

```ts
type t1 = Exclude<'1' | '2', '2'>
// type t1 = '1'

type t2 = Exclude<string | number | boolean, number>
// type t2 = string | boolean

type user1 = { name: 'yuhua', age: 12 }
type user2 = { name: 'yiye', sex: 'male' }
type t3 = Exclude<user1 | user2, { sex: 'male'}>
// type t3 = {
//   name: 'yuhua'
//   age: 12
// }
```


## Extract<Type, Union>
> type Extract<T, U> = T extends U ? T : never

通过从所有可分配的Type中，寻找可赋值类型，来构造一个类型

```ts
type t1 = Extract<'1' | '2', '2'>
// type t1 = '2'

type t2 = Extract<string | number | boolean, number>
// type t2 = number

type user1 = { name: 'yuhua', age: 12 }
type user2 = { name: 'yiye', sex: 'male' }
type t3 = Extract<user1 | user2, { sex: 'male'}>
// type t3 = {
//   name: 'yiye'
//   sex: 'male'
// }
```
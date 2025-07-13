# 泛型工具类型（Utility-Types）

<!-- https://www.typescriptlang.org/docs/handbook/utility-types.html -->

<!-- # Partial

Partial 是 TypeScript 提供的一个内置泛型类型，用于创建一个类型的所有属性都变为可选（optional）的新类型。这个类型在处理对象的部分属性时非常有用，尤其是在函数需要处理对象的部分属性时。

```
interface User {
    name: string;
    age: number;
    occupation: string;
}

type PartialUser = Partial<User>;

/**
* PartialUser 的结构会如下:
*
* {
*     name?: string;
*     age?: age;
*     occupation?: string;
* }
*/
``` -->

TS官方文档：[Utility Types](https://www.typescriptlang.org/docs/handbook/utility-types.html)

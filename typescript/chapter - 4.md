# 交叉类型 Intersection Types

交叉类型指的是多个类型组成的一个新类型，使用符号``` & ```表示。

交叉类型 A & B，新类型将拥有 A，B的所有类型

```ts
interface User {
    name: string;
    age: number;
}

type General = {
    language: '简体中文' | 'English',
}

// 交叉类型
type Person = User & General

const persons: Person = {
    name: '一也',
    age: 30,
    language: '简体中文'
}
```

TS官方文档：[Intersection Types](https://www.typescriptlang.org/docs/handbook/2/objects.html#intersection-types)
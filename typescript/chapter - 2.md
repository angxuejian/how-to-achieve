# 值类型 Literal Types


(值/字面)类型指的是单个值也是一种类型


```ts
type t1 = '一也' | 123 | true | { age: 20 }

const username: t1 = '一也'
```

上面示例给`t1`设置类型为`'一也'`、`123`、`true`、`{ age: 20 }`后，后续只能赋值四个值类型，否则就出现类型错误



TS官方文档：[Literal Types](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#literal-types)
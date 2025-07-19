# 继承/扩展类型 Extending Types

继承/扩展类型是将多个类型汇总后并新增类型，组成一个新的类型

`interface`可以使用`extends`关键字，继承其他`interface`、`type(object)`、`class`

```ts
interface User {
    name: string;
    age: number
}

type General = {
    language: "简体中文" | "English"
}

interface Person extends User, General {
    sex: boolean
}

const persons: Person = {
    name: '一也',
    age: 30,
    language: '简体中文',
    sex: true
}
```

TS官方文档：[Extending Types](https://www.typescriptlang.org/docs/handbook/2/objects.html#extending-types)
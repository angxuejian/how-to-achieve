# JS / TS类型

## JS
### 基本类型（Primitive Types）

基本类型是不可变的，按值传递，占用内存小

| 类型          | 示例值                         | 说明                     |
| ----------- | --------------------------- | ---------------------- |
| `string`    | `"hello"`                   | 字符串                    |
| `number`    | `42`, `3.14`, `NaN`         | 所有数字（整数和浮点数）           |
| `bigint`    | `123n`, `9007199254740991n` | 超大整数（ES2020）           |
| `boolean`   | `true`, `false`             | 布尔值                    |
| `undefined` | `undefined`                 | 默认未赋值时的值               |
| `null`      | `null`                      | 表示“无”或“空值”             |
| `symbol`    | `Symbol("id")`              | 唯一值，通常用于对象属性的唯一标识（ES6） |


### 引用类型（Reference Types）
引用类型是可变的，按引用传递，占用内存较大：

| 类型         | 示例                           | 说明             |
| ---------- | ---------------------------- | -------------- |
| `Object`   | `{ a: 1 }`                   | 普通对象           |
| `Array`    | `[1, 2, 3]`                  | 数组对象           |
| `Function` | `function() {}` 或 `() => {}` | 函数本质也是对象       |
| `Date`     | `new Date()`                 | 日期对象           |
| `RegExp`   | `/abc/`                      | 正则表达式对象        |
| `Map`      | `new Map()`                  | 键值对集合，键可以是任意类型 |
| `Set`      | `new Set()`                  | 值的集合，不允许重复     |
| `WeakMap`  | `new WeakMap()`              | 弱引用键值对集合       |
| `WeakSet`  | `new WeakSet()`              | 弱引用集合          |
| `Promise`  | `new Promise()`              | 异步处理对象（ES6）    |
| `Error`    | `new Error("msg")`           | 错误对象           |
| `class` 实例 | `new MyClass()`              | 类的实例，本质也是对象    |

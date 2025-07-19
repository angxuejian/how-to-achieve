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



## TS

### 顶层类型（Top type）

| 类型 | 示例 | 说明 |
| ---  | --- | --- |
| `any` | `let test: any;` | 没有任何限制，该类型的变量可以随意赋值。|
| `unknown` | `let test: unknown;` | any 类型的严格版，可以设置任何类型，除 any 和 unknown 类型外不能随意赋值和使用，必须**类型缩小**后才可以使用。 |

### 底层类型（bottom type）

| 类型 | 示例 | 说明 |
| ---  | --- | --- |
| `never` | `let test: never;` | 空类型，不包含任何值，定义never类型后不可以赋任何值，常常用于死循环和抛出异常的函数。 |

示例：

1、函数抛异常（表示永远不会返回）
```ts
function throwError(message: string): never {
  throw new Error(message);
}

// 使用
function getUser(id: number) {
  if (id <= 0) {
    return throwError("Invalid user ID");
  }
  return { id, name: "Alice" };
}

```

2、类型穷尽检查
```ts
function print(value: string | number) {
  if (typeof value === "string") {
    console.log(value.toUpperCase());
  } else if (typeof value === "number") {
    console.log(value.toFixed(2));
  } else {
    // 理论上这里永远不会走到
    const unexpected: never = value;
    throw new Error(`Unexpected value: ${value}`)
  }
}
```
自动防止新增类型但忘了更新逻辑的 bug。

# 类型



<!-- ## 类型保护

使用类型保护来判断对象的类型

1、 in 关键字

使用 in 关键字来区分 User 和 Admin 类型的对象。对于 User 类型的对象，我们输出 occupation 属性；对于 Admin 类型的对象，我们输出 role 属性。

```
// 更新 logPerson 函数以处理 User 和 Admin 类型
export function logPerson(person: Person) {
    if ('occupation' in person) {
        console.log(` - ${person.name}, ${person.age}, ${person.occupation}`);
    } else if ('role' in person) {
        console.log(` - ${person.name}, ${person.age}, ${person.role}`);
    }
}
```

2、is 关键字

使用 is 关键字来定义类型谓词（type predicates），这是一种类型保护的机制。类型谓词是一种特殊的返回值类型，用于在函数中进行类型保护

```
export function isAdmin(person: Person): person is Admin {
    return person.type === 'admin';
}

export function isUser(person: Person): person is User {
    return person.type === 'user';
}

// 更新 logPerson 函数以处理 User 和 Admin 类型
export function logPerson(person: Person) {
    let additionalInformation: string = '';
    if (isAdmin(person)) {
        additionalInformation = person.role;
    } else if (isUser(person)) {
        additionalInformation = person.occupation;
    }
    console.log(` - ${person.name}, ${person.age}, ${additionalInformation}`);
}
``` -->


字段相同，设置name的类型
```typescript
const data = { 
    click: { raycaster: 'click:raycaster' }, 
    dblclick: { raycaster: 'dblclick:raycaster' } 
}

type eventName = keyof typeof Data

(name: eventName) => data[name].raycaster
```

字段不相同，设置name的类型
```typescript
const data = { 
    click: { raycaster: 'click:raycaster' }, 
    dblclick: { raycaster: 'dblclick:raycaster' }, 
    resize: 'resize',
    // ...其他字段
}

type eventName = 'click' | 'dblclick'

(name: eventName) => data[name].raycaster
```

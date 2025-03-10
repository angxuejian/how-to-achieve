# 联合类型 Union types


联合类型指的是多个类型组成的一个新类型，使用符号|表示。

联合类型A|B表示，任何一个类型只要属于A或B，就属于联合类型A|B。

```
interface User {
    name: string;
    age: number;
    occupation: string;
}

interface Admin {
    name: string;
    age: number;
    role: string;
}

// 联合类型
export type Person = User | Admin;

export const persons: Person[] = [
    {
        name: 'Max Mustermann',
        age: 25,
        occupation: 'Chimney sweep'
    },
    {
        name: 'Jane Doe',
        age: 32,
        role: 'Administrator'
    },
    {
        name: 'Kate Müller',
        age: 23,
        occupation: 'Astronaut'
    },
    {
        name: 'Bruce Willis',
        age: 64,
        role: 'World saver'
    }
];

export function logPerson(user: Person) {
    console.log(` - ${user.name}, ${user.age}`);
}

persons.forEach(logPerson);

```

## 类型保护

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
```

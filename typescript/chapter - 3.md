# 联合类型 Union types


联合类型指的是多个类型组成的一个新类型，使用符号``` | ```表示。

联合类型 A | B 表示，任何一个类型只要属于 A 或 B，就属于联合类型 A | B。

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

TS官方文档：[Union Types](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#union-types)


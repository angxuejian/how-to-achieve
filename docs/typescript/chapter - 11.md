

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

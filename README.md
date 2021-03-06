# swnb/event

> event module

## install

```shell
npm install @swnb/event
```

or

```shell
yarn add @swnb/event
```

## example

```typescript

import { SyncEvent } from '@swnb/event'

// define event handler type

type HandlerMap = {
  foo: (x: number, y: number) => void
  bar: (z: string) => void
}

class EventCenter extends SyncEvent<HandlerMap> {}

const ev = new EventCenter()

s.on('bar', z => {
  console.log(z)
})

s.once('foo', (x, y) => {
  console.log(x, y)
})

s.dispatch('bar', 'f')

s.dispatch('foo', 1, 2)

// register or cancel event
const callback = () => {}

s.on('foo' , callback)

s.cancel('foo' , callback)

// async await

;(async () => {
  const a = await s.waitUtil('foo')
  console.log('wait')
  console.log(a[0], a[1]) // 8 0
})()

setTimeout(() => {
  s.dispatch('foo', 8, 0)
}, 1000)

```

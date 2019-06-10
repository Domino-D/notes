#### dependencies & devDependencies

```json
{
  // ...
  "dependencies": {
    "react": "^16.8.6",
    "react-dom": "^16.8.6",
    "react-scripts-ts": "3.1.0"
  },
  "devDependencies": {
    "@types/jest": "^24.0.13",
    "@types/node": "^12.0.7",
    "@types/react": "^16.8.19",
    "@types/react-dom": "^16.8.4",
    "typescript": "^3.5.1"
  }
}
```



#### TypeScript in React

###### import

```typescript
import * as React from 'react'
import * as ReactDOM from 'react-dom'
```

###### console

`Error: Calls to 'console.log' are not allowed`

```typescript
// tslint.json
{
  // ...
  "rules": {
    "no-console": false
  }
  // ...
}
```

###### lifecircle functions

```typescript
// public defined
public componentDidMount() {
  // ...
}

public render() {
  // ...
}
```

###### functions in component

```typescript
// private defined
private getItemDetail() {
  // ...
}
```

###### jsx-no-lambda

`Error: Lambdas are forbidden in JSX attributes due to their rendering performance impact`

```typescript
// tslint.json
{
  // ...
  "rules": {
    "jsx-no-lambda": false
  }
  // ...
}
```

###### state

```typescript
import * as React from 'react'

interface IState {
  list: object[]
}

export default class App extends React.Component<{}, IState> {
  public state: IState = {
    list: [
      { id: 1, name: 'a' },
      { id: 2, name: 'b' },
    ],
  }
  // ...
}
```





#### TypeScript

##### variables

###### Normal

```typescript
let bool: boolean = true

let num: number = 1

let str: str = 'string'

let list1: number[] = [1, 2, 3]
let list2: Array<number> = [4, 5, 6]
```

Tuple

```typescript
let x: [string, number];
x = ['hello', 10]; // OK
x = [10, 'hello']; // Error

console.log(x[0].substr(1)); // OK
console.log(x[1].substr(1)); // Error, 'number' does not have 'substr'

x[3] = 'world'; // OK, (string | number) either of two type
console.log(x[5].toString()); // OK

x[6] = true; // Error, (string | number) nother of two type
```

enum

```typescript
enum letter {a, b, c}
let foo = letter.a
let temp = letter[0]
```

any

```typescript
let foo: any = 1
```

void

```typescript
function func(): void {
  //...
}
```

null

```typescript
let n: null = null
```

undefinde

```typescript
let u: undefinde = undefined
```

assertion

```typescript
let str: any = "string"
let strLength: number = (<string>str).length
// or
let strs: any = "strings"
let strLength: number = (strs as string).length
```

##### interface

```typescript
interface objConfig {
  name?: string
  age?: number
  readonly id: string
}
```


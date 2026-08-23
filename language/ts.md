# Typescript

## Typescript 泛型

## 柯里化

柯里化在类型层面的难点在于：需要将函数参数元组拆开，返回一个递归嵌套的一元函数类型，直到参数耗尽。

```ts
type Curried<F> = F extends (...args: infer A) => infer R
  ? A extends [infer First, ...infer Rest]
    ? (arg: First) => Curried<(...args: Rest) => R>
    : R
  : never;

function curry<F extends (...args: any[]) => any>(fn: F): Curried<F> {
  return function curried(...args: any[]): any {
    if (args.length >= fn.length) {
      return fn(...args);
    }
    return (...nextArgs: any[]) => curried(...args, ...nextArgs);
  } as any;
}
```

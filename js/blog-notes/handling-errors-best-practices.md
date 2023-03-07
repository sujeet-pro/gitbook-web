---
description: Easiest non-cluttering ways to handle errors
---

# Handling Errors - Best Practices

### ## TLDR;

```typescript
function goLike<F extends  (...args: any) => any, E = unknown>(func: F, ctx: unknown = undefined) {
    return (...args: Parameters<F>): [ReturnType<F> | null, E | null] => {
        try {
            const res = func.apply(ctx, args)
            return [res, null]
        } catch (e) {
            return [null, e as E]
        }
    }
}
```

### Identifying the Problems

#### Callbacks

Everyone is aware of the popular "callback hells", but we mostly see those with respect to success responses, what if you need to handle the errors as well.\


```typescript
type cb<T = unknown> = (v: T) => void
type someFun<A = unknown, S = unknown, E = unknown> = (args: A, successCb: cb<S>, errorCb: cb<E>) => void

declare const fun1: someFun
declare const fun2: someFun
declare const fun3: someFun

function fun4(opt: unknown, successCb: cb, errorCb: cb) {
    fun1(opt,
        result1 => {
            fun2(result1, 
                result2 => {
                    fun3(result2, 
                            result3 => {
                                successCb(result3)
                            },
                            error3 => {
                                errorCb(error3)
                            }
                        )
                },
                error2 => {
                    errorCb(error2)
                }
                )
        },
        error1 => {
            errorCb(error1)
        }
        )
}
```



#### Promises

#### Async Await

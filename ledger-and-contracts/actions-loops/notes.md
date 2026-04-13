# Actions & Loops Notes

- `Action` is an applicative typeclass that composes actions sequentially.
- It passes the result from one action into the next.

Example:
```haskell
sequenceA [action1, action2, action3]
```

- A `do` block is equivalent to using the `Action` bind operator `>>=`.

Example:
```haskell
do
  x <- action1
  y <- action2 x
  action3 y
```

is equivalent to:
```haskell
action1 >>= \x -> action2 x >>= \y -> action3 y
```

- When performing effects in a loop, use `mapA` or `forA`.

Example:
```haskell
mapA print items
forA items print
```

- If a return value is not needed, use `mapA_` or `forA_`.

Example:
```haskell
mapA_ print items
forA_ items print
```

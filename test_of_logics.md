# Test of logics

## Working original proposition

The 0 and 1 are in a self-contained domain and -1, 0 and 1 are a close scope.

- Closure properties: `(0, 1)`; `[0, 1)`; `[0, 1]`; `(0, 1]` where `()` denotes
  from and to, exclusively, respectively and `[]` inclusively.
- Binary logic mapping: `and(0, 0) -> 0`; `and(0, 1) -> 0`; `and(1, 0) -> 0`;
  `and(1, 1) -> 1`. `Or(0, 0) -> 0`; `or(0, 1) -> 1`; `or(1, 0) -> 1`;
  `or(1, 1) -> 1` in which the former results in trace and the latter block.
- And: `but(0, 0)`; `but(0, 0)`; `but(0, 0)`; `but(0, 0)`; ladder operator in
  diagonal.
- With: `ror(0, 0)`; `ror(0, 0)`; `ror(0, 0)`; `ror(0, 0)`; in off-diagonal.

For all values of the mapping operators, the result is in the domain range. The
scope is provided with an `i^` operator in `i^(0) -> 0`; `i^(1) -> -1`;
`i^(-1) -> 1`.


## Draft in reduction

The series provided here is linear in finite space.

Summation of series (Sigma)

```math
k =     1, 2, 3,  4,  5, ... , k, ..., n
sum_k = 1, 3, 6, 10, 15, ...         , sum_k = n * (n + 1) / 2
base =  0
```

The summation or acounting in accumulation of positive integers becomes the area
of a triangle. It is the integration in `i^ * i^ = 1/2 i^2 (delta)`. It assumes
here that the differential is in finite while the derivative is infinite.

Product of series (Pi)

```math
k =      0, 1, 2, 3,  4,   5, ... , k, ..., n
prod_k = 1, 1, 2, 6, 24, 120, ...   k!    , for n = 0, prod_n = 1
base =   1                                , for n > 0, prod_n = 1 * 2 * ... n
```

It is called the factorial in accumulation of ratios. In the following equations,
it can be seen of the production of zero.

```math
                        lim_k 1/k = 0                                  [1-a]

                        lim_k 1/sum_k = 0                              [1-b]

                        lim_k 1/prod_k = 0                             [1-c]
```


## Case study of squred dollar

**Quality stars**
```
Linear: 1. very bad; 2. bad; 3. normal; 4. good; 5. very good
```

Ref 1 Google stars; level

**Atmospheric stars**
```
Exponential: 1. nice 2. 3. (cosy) 4. outstanding 5. extradinary
```

Ref 2 Michelin stars; (atmospheric) rank

**References**

Functions and constants:

- `log_10`, `log_2`, `log_n`, `ln`;

- `log_n(0) = -oo`, `log_n(1) = 0`, `log_n(n) = 1` and `epsilon = 2.7(1)`.

- `Pi = 3(02)` denotes the relation of Pi constant with integer 3 in
  approximation.


## Perspective

Coupons by means of squared dollar. The folloing equation is for disignation.

```sdlr
         $^2 100 = $10 * $10 = $n * $(10 - n),  for 0 < n < 10,        [2-a]
                                             ,  for th < n < bd.       [2-b]
```
The `th` is threshold and the `bd` the boundary.

Note: it is not a retro-spec.

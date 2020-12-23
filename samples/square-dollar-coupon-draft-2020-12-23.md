# Square-dollar coupon (draft-2020-12-23)

*(This  is  a standalone document  for  introduction of the methodology  of  the
 square-dollar coupon.)*

The square-dollar coupon in unit of `($^2)` is derrived from square yuan `(圓^2)100`
early this year. This draft is a new intepretation based on it. The following
macro-template demostrates the usage for testing purposes. The test can only be used
to deal it with in trusted third-parties. It is mainly applicable in two parties.
The result of the tests will be treasurable to perspect the value of this coupon.

The **macro-template** is as follows

```sop
                              << deal-with.sop >>
[Define]
  near epsilon := 0.1

[> $ = 20]
  $ => let dollar value
  let square_dollar coupon_value = value^2  || ($^2)100

  || Enumerate the cutoffs for the schema validator.
  let cutoff dis := $10  || discrimination (dis) limit of value (variable)
  let cutoff thr := $30  || threshole (thr) limit of value (variable)
  || ...

  || ...

  [||]
    || Note that the cutoff is not the boundary but a hint.
    || Introduction of a default optimizer:
    || value <= Optimize value and (new-value with a factor).
    value <= Optimize value and new-value with a factor.
    value <= new-value if value near new-value, else value.
    || ...
  [>]
  || ...

  || ...

  || An in-language validator with the predefined schema is provided as below. The
  || user can reset the secondary validator as above. If the principle validator is
  || broken, it is welcome. The limit is to avoid the violation of current legisla-
  || tion. It can certainly be discussed later within plateform(s).

  value => $  || principle validator: $0 <= value <= $40      [1]
              || secondary validator: dis            thr      [2]
              || Equation [1] is strict and equation [2] is a metric which can be
              || violated. The limit of the violation is the legal range.
[[$]]

<<< The new value is $. >>>


[Note]
  1. The dollar and square_dollar are predefined unit types.
  2. The cutoff is a predefined enumeration type.
  3. Keywords: let, const, define, and, and with.
  4. Experssion operators: ^ (powop), v (square root short-cut), and = (open here).
  5. Assignment operator: := (assign the right-value to the left-value.
  6. Mapping operators: => (chuck to), and <= (chuck from).
  7. Quoatation marks: << words >> -- print screen and <<< words >>> print string.
  8. The dollar sign ($) is the lambda value with optional defaults in start [>]
     and [stop]. The leading $ and ($^2) denote the unit.
  9. Terms: [>] play and stop [[]] macro; || inline pause; [||] multiline pause [>]
     ||| manual pause; [Note] an ordered list for notes.
  10. Frontmatters: [Title: title-1], [Subtitle: subtitle-1],
     [Authors: a1\thanks-to-p1, a2 and a3], [Affiliation af-1, af-2 and af3],
     [Macro] and [Function]. (p1 definition to be added)
  11. Backmatters: [References]
  12. Comparison operators: <, =, >, <o=, =o>, ~=, which means lt, eq, gt, le, ge, ne. 
  13. All operators is in keyword boundary and any operator can be within identifier
      execpt |.
```

## Appendix

**System library** in *progress*

```sop
            <<< Collection of system library >>>

|| The following two definitions are in-language library

[Macro Optimize ::= value and new-value with a factor]
  ||| The normalization algorithm
  ||| y => 1/x; x y => 1; v(1 1) => 1 (normalized).
  ||| y => ($^2)400 / x; x y => ($^2)400; v(x y) => $20 (concept unit)

  || value => $  || explanation: explicit lambda (obmited here)
  value := v((value + 1) / new-value)
[[$]]

[Macro operator near ::= expression a ~= b in epsilon := 0.01]
  value := |a - b| <o= epsilon
[[$]]
```

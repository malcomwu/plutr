# Square-dollar coupon (draft-2020-12-23)
This is a short guide to the methodology of the square-dollar coupon.

## Introduction

The square-dollar coupon in unit of `($^2)` is derrived from square yuan `(圓^2)100`
early this year. This draft is a new intepretation based on it. The following
macro-template demostrates the usage for testing purposes. The test can only be used
to deal it with in trusted third-parties. It is mainly applicable in two parties.
The result of the tests will be treasurable to perspect the value of this coupon.


## Sample macro-template

```sop
                              << deal-with.sop >>
[Define]
  near epsilon := 0.1  || to be reset by refactoring (see demo below)

[> $ = 20]
  $ => let dollar value
  let square_dollar coupon_value = value^2  || ($^2)100

  || Enumerate the cutoffs for the schema validator.
  let cutoff dis := $10  || discrimination (dis) limit of value (variable)
  let cutoff thr := $30  || threshole (thr) limit of value (variable)
  || ...
  
  || Descrete analysis
  ||                                food (f)
  ||         f     a
  || amount    cut          area     ^ y ($10)                    $(10, 10) extremely rich at the moment
  || $20 => $10 + $10 => ($^2) 100   ||                   ---------+
  || $20 => $9  + $11 => ($^2) 99    |+-* poverty       ($^2) 100  |
  || $20 => $8  + $12 => ($^2) 96    |\ |
  || $20 => $7  + $13 => ($^2) 91    | \  ------+ $(5, 15)
  || $20 => $6  + $14 => ($^2) 84    |   \      |        normal distribution   $(15, 5)
  || $20 => $5  + $15 => ($^2) 75    |  |   \   |                      ---------+
  || $20 => $4  + $16 => ($^2) 64    |  |      --                     ($^2) 75  |
  || $20 => $3  + $17 => ($^2) 51    |  |           ---    <= optimization (linear regression)
  || $20 => $2  + $18 => ($^2) 36    | --------------------------*    ------ =>
  || $20 => $1  + $19 => ($^2) 19    |      ($^2) 9  $(9, 1)     | poverty      --------
  || $20 => $0  + $20 => ($^2) 0     +-----------------------------------------------------------> x ($10)
  ||                                                  accomodation (a)
  ||
  || The $ unit in x and y axes are normalized.
  || The idea for discrete is in the near operator a ~= b (epsilon = 1).
  || In the above demonstration, the normalization factor is n = f/a = $10 / $100 = 0.1
  || The scaler product: a b, dot product: a * b, and cross product: a x b are the same here because the
  || dimension of a and b is 1.

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

## Appendix A Provided system library

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



## Appendix B Grammar of Inline-math

(Draft)

The definition is limited in scaler number. Some operator such as
mulop is reserved for vector number. The tokens and Grammar are
described below.

(Draft)


```sop
[Define Math ::= language]
  use tokens Math  || ??
  verb 

|| (Draft)
[Define Math.token ::= pattern[vregexp]]  || pattern[option]
  ||| The single quotes such as '$', 'v', etc., are token as lexeme or keywords.
  ||| The [] contains the options of characters.
  ||| The definition of patterns is still vague here.
  ||| The S, SS, ALL and NL are used in the lexer with the default value below.
  ||| The tokens do not have priority. They are maintained by the parser(s).
  S := ' '
  SS := / +/  || pause I make a break and leave something simple for the crowd
  ALL := /.+/
  NL := '\n'
  alphabet(alpha) := [a-zA-Z]
  digit := [0-9]  || or [\d]
  identifier := alpha (alpha digit)*  || queue: $, - and _
  sign := [+-]
  addop := sign  || add and substrate
  mulop := [*x/]  || dot product, cross product and divide
  powop := '^'  || power
  sqrtop := 'v'  || square root
  positive-integer(pint) := [1-9]\d*  || name(abbr.)
  integer(int) := sign (0 | pint)
  decimal := sign pint ('.' pint)
  rational := 'r' int SS '/' SS int


|| (Draft)
[Define Math.expression ::= grammar[vbnf]]  || grammar[option]
  inline-math := '$' (assignment | expression) '$'
  assignment := identifier SS ':=' expression
  expression := term (addop term)*
  term := factor (mulop factor)*
  factor := value (powop value)*
  value := sqrt-expr | function | identifier | number | parantheses
  sqrt-expr := 'v' (number | parantheses)
  function := identifier '(' SS expr-list ')'
  expr-list := '' | expression (',' SS expression)
  number := integer | decimal | rational | real | complex | categorical
          | unit-value
  parantheses := '(' SS expression SS ')'
```




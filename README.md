# Indinero Ruby Styleguide

## Operators

- Spaces around binary operators, except on `**` *(exponent)*.
  ```ruby
  x + y + z
  str = "Hello World"
  sum > 100
  e = M * c**2
  ```
  
- No space after unary operators.
  ```ruby
  !is_dead
  -25
  ```
  
- Space after comma, colon, and semicolon.
  ```ruby
  foo(a, b, c)
  {x: 1, y: 2}
  class FooError < StandardError; end
  ```

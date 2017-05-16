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

## Blocks

- Spaces around block content.
  ```ruby
  Proc.new { puts 'hello' }
  list.each { |item| item.delete }
  ```
  
- Space before opening curly-brace.
  ```ruby
  Proc.new { puts 'hello' }
  list.each { |item| item.delete }
  ```

- Use `do` and `end` for multi-line blocks.
  ```ruby
  # do this
  list.each do |item|
    item.name = 'new name'
    item.save
  end

  # instead of this
  list.each { |item|
    item.name = 'new name'
    item.save
  }
  ```
  
- Do not chain multi-line blocks.
  ```ruby
  #
  # Do this
  #
  result = list.map do |item|
    # do something here
    # evaluate something
  end
  
  result.each do |item|
    # do something here
    # random stuff
  end
  
  #
  # Not this
  #
  list.map do |item|
    # do something here
    # evaluate something
  end.each do |item|
    # do something here
    # random stuff
  end
  ```

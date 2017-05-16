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
  #
  # Bad!
  #
  list.each { |item|
    item.name = 'new name'
    item.save
  }
  
  #
  # Good
  #
  list.each do |item|
    item.name = 'new name'
    item.save
  end
  ```
  
- Do not chain multi-line blocks.
  ```ruby
  #
  # Bad!
  #
  list.map do |item|
    # do something here
    # evaluate something
  end.each do |item|
    # do something here
    # random stuff
  end
  
  #
  # Good
  #
  result = list.map do |item|
    # do something here
    # evaluate something
  end
  
  result.each do |item|
    # do something here
    # random stuff
  end
  ```
  
## Conditionals

- Do not use conditional modifier after multi-line block.
  ```ruby
  #
  # Bad!
  #
  list.each do |item|
    # do something here
    # do another thing
    # do another one again
    # another one
  end if test_condition || another_condition
  
  #
  # Good
  #
  if test_condition || another_condition
    list.each do |item|
      # do something here
      # do another thing
      # do another one again
      # another one
    end
  end
  ```

- Do not use `unless` with negative expressions.
  ```ruby
  #
  # Bad!
  #
  do_something unless list.empty?
  do_another unless text.blank?
  
  #
  # Good
  #
  do_something if list.empty?
  do_another if text.blank?
  ```
  
- Align `when` with `case`.
  ```ruby
  case something
  when 1
    puts 1
  when 2
    puts 2
  end
  ```
  
- Avoid multi-line expressions. Combine expressions into variables as much as possible.
  ```ruby
  #
  # Bad
  #
  if something_boolean || another_boolean_value || some_long_expressions &&
    maybe_true && i_am_not_sure_if_this_is_false
    #
    # do something
    #
  end
  
  #
  # Good
  #
  should_perform = something_boolean || another_boolean || ...
  if should_perform
    #
    # do something
    #
  end
  ```

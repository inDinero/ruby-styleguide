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
  
## Strings

- Always use single-quote `'`, unless when interpolation is needed.
- Use `<<` when concatenation strings.
  ```ruby
  # Bad
  str = 'Hello'
  str += ' World'

  # Good
  str = 'Hello'
  str << ' World'
  ```
  
## Hash

- Always use colon-syntax rather than hash-rockets *(except for non-symbol keys)*.
  ```ruby
  mixed_hash = {foo: 'Foo', baz: :baz, 1 => 'One', 'Bar' => 'Bar Bar'}
  ```
  
- Spaces around contents.
  ```ruby
  { x: 1, y: 2, z: 3 }
  { 'foo' => 1, 'bar' => 2 }
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

## Methods

- Parentheses around method definition arguments.
  ```ruby
  def foo(arg1, arg2, arg3)
    # do something
  end
  ```
  
- Parentheses around method call arguments.
  ```ruby
  foo(1, 2, 3)
  bar('Hello')
  ```
  
- Hash arguments format:
  ```ruby
  object.update(
    prop1: 'Value 01',
    prop2: 'Value 02',
    prop3: 'Value 03',
    prop4: 'Value 04'
  )
  ```
  
- Array arguments format:
  ```ruby
  #
  # Continue up to line-length limit.
  #
  object.add([
    'jack of diamonds', 'two of spades', 'ten of clubs', 'seven of diamonds',
    'king of hearts', 'ace of hearts', 'nine of spades', 'four of diamonds',
    'joker', 'three of clubs', 'joker'
  ])
  ```
  
- 1 method per line when chaining *(if exceeds line-length limit)*.
  ```ruby
  object.
    foo.
    bar(key: 'Bar!').
    baz(:a, :b).
    fizz(x: 1000, y: 2000, z: 3000)
  ```

## Assignment

- Large Array.
  ```ruby
  #
  # Continue up to line-length limit.
  #
  huge_array = [
    ace, king, queen, jack, ten, nine, eight, seven, six, five, four,
    three, two
  ]
  ```
  
- Large Hash.
  ```ruby
  my_big_hash = {
    a: 'Ace of Spades',
    b: 'Two of Spades',
    c: 'Three of Spades',
    d: 'Four of Spades',
    e: 'Five of Spades',
    f: 'Joker'
  }
  ```

- Multi-line Block.
  ```ruby
  output =
    if some_condition
      # do something
    else
      # do another thing
    end

  result =
    collection.map do |record|
      # do something here
    end
  ```

- Long method chain.
  ```ruby
  result =
    my_super_long_variable_name.
      long_public_method_name_something(argument).
      chained_method(arg).
      foo_bar(baz)
  ```

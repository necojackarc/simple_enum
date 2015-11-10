# SimpleEnum [![Build Status](https://travis-ci.org/necojackarc/simple_enum.svg?branch=master)](https://travis-ci.org/necojackarc/simple_enum) [![Code Climate](https://codeclimate.com/github/necojackarc/simple_enum/badges/gpa.svg)](https://codeclimate.com/github/necojackarc/simple_enum) [![Test Coverage](https://codeclimate.com/github/necojackarc/simple_enum/badges/coverage.svg)](https://codeclimate.com/github/necojackarc/simple_enum/coverage)

SimpleEnum provides really simple enumerated type.

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'simple_enum'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install simple_enum

## Usage

Any class can include `SimpleEnum` and you can define an enumerated type like this:

```ruby
require "simple_enum"

class Person
  include SimpleEnum

  simple_enum mood: {
    awesome: 0,
    excellent: 1,
    great: 2,
    good: 3,
    fine: 4
  }

  def initialize(mood: :fine)
    self.mood = mood
  end
end
```

```ruby
[1] pry(main)> Person.moods
=> {:awesome=>0, :excellent=>1, :great=>2, :good=>3, :fine=>4}
[2] pry(main)> necojackarc = Person.new(mood: :awesome)
=> #<Person:0x007fd5cbbf5dd0 @mood=0>
[3] pry(main)> necojackarc.awesome?
=> true
[4] pry(main)> necojackarc.excellent?
=> false
[5] pry(main)> necojackarc.great!
=> :great
[6] pry(main)> necojackarc.awesome?
=> false
[7] pry(main)> necojackarc.great?
=> true
[8] pry(main)> necojackarc.mood = :fine
=> :fine
[9] pry(main)> necojackarc.great?
=> false
[10] pry(main)> necojackarc.fine?
=> true
[11] pry(main)> necojackarc.mood = 1
=> 1
[12] pry(main)> necojackarc.fine?
=> false
[13] pry(main)> necojackarc.excellent?
=> true
[14] pry(main)> necojackarc.mood
=> :excellent
```

## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

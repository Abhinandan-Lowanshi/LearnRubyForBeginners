# Ruby Programming Guide for Beginners

Welcome to Ruby! This guide is designed for absolute beginners to learn Ruby, a simple and fun programming language. Ruby is known for its readable syntax and is widely used for web development (e.g., Ruby on Rails), scripting, and automation. This document covers all essential Ruby topics with clear explanations, detailed code comments, and examples to help you start coding confidently.

---

## Table of Contents
1. [What is Ruby?](#what-is-ruby)
2. [Getting Started](#getting-started)
3. [Basic Syntax and Variables](#basic-syntax-and-variables)
4. [Data Types](#data-types)
5. [Control Structures](#control-structures)
6. [Methods and Blocks](#methods-and-blocks)
7. [Classes and Objects](#classes-and-objects)
8. [Modules](#modules)
9. [Procs and Lambdas](#procs-and-lambdas)
10. [Arrays](#arrays)
11. [Hashes](#hashes)
12. [Sorting and Filtering](#sorting-and-filtering)
13. [Error Handling](#error-handling)
14. [File Input/Output](#file-inputoutput)
15. [Ruby Gems and Libraries](#ruby-gems-and-libraries)
16. [Resources for Learning Ruby](#resources-for-learning-ruby)

---

## What is Ruby?

Ruby is a **dynamic**, **object-oriented**, and **beginner-friendly** programming language created by Yukihiro Matsumoto ("Matz") in the 1990s. It’s designed to be simple, readable, and fun, making it a great choice for beginners.

### Why Learn Ruby?
- **Readable Syntax**: Ruby code looks like plain English, making it easy to understand.
- **Versatile**: Used for web apps, automation, and scripting.
- **Object-Oriented**: Everything in Ruby (even numbers!) is an object, which makes coding intuitive.

---

## Getting Started

### Installing Ruby
1. Download Ruby from [ruby-lang.org](https://www.ruby-lang.org/en/downloads/).
2. For Windows, use RubyInstaller. For macOS/Linux, use Homebrew (`brew install ruby`) or `rbenv`.
3. Check if Ruby is installed by running:
   ```bash
   ruby -v  # Shows the installed Ruby version
   ```

### Running Ruby Code
- **Interactive Ruby (IRB)**: Type `irb` in your terminal to try Ruby code interactively.
- **Ruby Files**: Save code in a file with a `.rb` extension (e.g., `my_script.rb`) and run it with:
  ```bash
  ruby my_script.rb
  ```

---

## Basic Syntax and Variables

### Variables
Ruby uses different types of variables to store data:
- **Local Variables**: Start with a lowercase letter or `_` (e.g., `name`). Used within a method or block.
- **Instance Variables**: Start with `@` (e.g., `@age`). Belong to an object in a class.
- **Class Variables**: Start with `@@` (e.g., `@@count`). Shared across all instances of a class.
- **Global Variables**: Start with `$` (e.g., `$debug`). Accessible everywhere (use sparingly).

```ruby
# Local variable: stores a string
name = "Abhi"
# Instance variable: typically used inside classes
@age = 25
# Class variable: shared across all objects of a class
@@count = 0
# Global variable: can be accessed anywhere (avoid overuse)
$debug = true
# Print the local variable
puts name  # Output: Abhi
```

### Arithmetic Operations
Ruby handles numbers differently based on their type (integers or floats):
- Integer division (`/`) returns a whole number.
- Float division returns a decimal.

```ruby
# Integer variables
a = 2
b = 3
# Float variables
c = 2.0
d = 3
# Float division: returns a decimal result
puts c / d  # Output: 0.6666666666666666
# Integer division: returns a whole number (rounds down)
puts a / b  # Output: 0
```

---

## Data Types

Ruby is dynamically typed, so you don’t need to specify variable types.

### Common Data Types
- **Strings**: Text, enclosed in `""` or `''`.
- **Numbers**: Integers (whole numbers) or Floats (decimals).
- **Symbols**: Immutable identifiers starting with `:` (e.g., `:name`). Used as keys in hashes.
- **Booleans**: `true` or `false`.
- **Nil**: Represents "nothing" (like `null` in other languages).

```ruby
# String: stores text
name = "Ruby"
# Integer: whole number
age = 25
# Float: decimal number
price = 19.99
# Symbol: efficient for constant identifiers
key = :id
# Boolean: true or false
is_active = true
# Nil: represents absence of value
empty = nil
# Print all variables
puts name, age, price, key, is_active, empty
# Output: Ruby, 25, 19.99, id, true, 
```

---

## Control Structures

### Conditionals
Use `if`, `elsif`, `else`, or `unless` to make decisions.

```ruby
# Define a variable for age
age = 20
# If statement: checks if age is 18 or more
if age >= 18
  puts "You are an adult"
# Else-if: checks if age is 13 or more
elsif age >= 13
  puts "You are a teenager"
# Else: runs if no conditions are true
else
  puts "You are a child"
end
# Output: You are an adult

# Unless: runs if the condition is false (opposite of if)
unless age < 18
  puts "Adult"
end
# Output: Adult
```

### Case Statements
A cleaner way to handle multiple conditions.

```ruby
# Define a variable for the day
day = "Monday"
# Case statement: checks the value of day
case day
when "Monday"
  puts "Start of the week"
when "Friday"
  puts "Weekend is near"
else
  puts "Midweek"
end
# Output: Start of the week
```

### Loops
Ruby offers several ways to repeat code:
- **while**: Runs while a condition is true.
- **until**: Runs until a condition is true.
- **each**: Iterates over collections like arrays or hashes.

```ruby
# While loop: runs as long as the condition is true
i = 0
while i < 3
  puts i  # Print current value of i
  i += 1  # Increment i by 1
end
# Output: 0, 1, 2

# Until loop: runs until the condition is true
i = 0
until i >= 3
  puts i  # Print current value of i
  i += 1  # Increment i by 1
end
# Output: 0, 1, 2

# Each loop: iterates over an array
[1, 2, 3].each { |num| puts num }  # Print each number
# Output: 1, 2, 3
```

---

## Methods and Blocks

### Methods
Methods are reusable blocks of code defined with `def`. They can have default parameters or accept variable arguments.

```ruby
# Basic method: no parameters
def greet
  puts "Hello!"  # Print a simple greeting
end
greet  # Output: Hello!

# Method with default parameter
def greet_name(name = "Guest")
  puts "Hello, #{name}!"  # Print greeting with name
end
greet_name         # Output: Hello, Guest!
greet_name("Abhi") # Output: Hello, Abhi!

# Method with variable arguments (accepts any number of arguments)
def print_all(*args)
  args.each { |arg| puts arg }  # Print each argument
end
print_all("A", "B", "C")  # Output: A, B, C
```

### Blocks
Blocks are chunks of code passed to methods using `do ... end` or `{ ... }`. Use `yield` to execute the block.

```ruby
# Method with a block
def demo
  puts "Start"            # Print before the block
  yield if block_given?   # Execute block if provided
  puts "End"              # Print after the block
end
demo { puts "Middle" }    # Pass a block
# Output:
# Start
# Middle
# End

# Block with a parameter
def demo
  yield("Abhi") if block_given?  # Pass "Abhi" to the block
end
demo { |name| puts "Hello, #{name}!" }  # Use the parameter
# Output: Hello, Abhi!
```

---

## Classes and Objects

Ruby is fully object-oriented, and classes define blueprints for objects.

### Example: Basic Class
```ruby
# Define a class named Demo
class Demo
  # attr_reader: creates a getter for @name (read-only)
  attr_reader :name
  # attr_writer: creates a setter for @age (write-only)
  attr_writer :age
  # attr_accessor: creates both getter and setter for @job
  attr_accessor :job

  # Constructor: initializes object with name, age, and job
  def initialize(name, age, job)
    @name = name  # Instance variable for name
    @age = age    # Instance variable for age
    @job = job    # Instance variable for job
  end

  # Instance method: prints the age
  def get_age
    puts @age
  end
end

# Create a new Demo object
demo = Demo.new("Abhi", 30, "Software")
puts demo.name       # Output: Abhi (uses getter)
demo.age = 25        # Set age (uses setter)
demo.get_age         # Output: 25 (uses method)
demo.job = "Teacher" # Set job (uses setter)
puts demo.job        # Output: Teacher (uses getter)
```

### Example: Class with Class Variables
```ruby
# Define a class named Car
class Car
  # Class variable: shared across all Car objects
  @@how_many_cars_sold = 0
  # Global variable: accessible everywhere (avoid overuse)
  $is_running = "False"

  # Constructor: initializes name and year, increments class variable
  def initialize(name, year)
    @@how_many_cars_sold += 1  # Increment car count
    @name = name               # Instance variable for name
    @year = year               # Instance variable for year
  end

  # Instance method: displays car details
  def show_car
    puts "#{@name} #{@year}"
  end

  # Class method: displays total cars sold
  def self.get_how_many_cars_sold
    puts @@how_many_cars_sold
  end
end

# Create Car objects
car1 = Car.new("Mahindra", "2004")
car1.show_car  # Output: Mahindra 2004
car2 = Car.new("Maruti", "2005")
car2.show_car  # Output: Maruti 2005
Car.get_how_many_cars_sold  # Output: 2
puts $is_running  # Output: False
```

### Instance Variables
You can check an object’s instance variables.

```ruby
# Define a simple class
class Demo
  def initialize(name)
    @name = name  # Set instance variable
  end
end
# Create an object
demo = Demo.new("Abhi")
# Print instance variables
puts demo.instance_variables  # Output: [:@name]
```

---

## Modules

Modules group reusable methods and can be mixed into classes using `include` (for instance methods) or `extend` (for class methods).

```ruby
# Define a module with a reusable method
module Greetable
  def say_hello
    puts "Hello from #{self.class}"  # Print class name
  end
end

# Class with instance methods from module
class Person
  include Greetable  # Adds say_hello as instance method
  def initialize(name)
    @name = name
  end
end

# Class with class methods from module
class Robot
  extend Greetable  # Adds say_hello as class method
end

# Create a Person object and call instance method
person = Person.new("Abhi")
person.say_hello  # Output: Hello from Person
# Call class method on Robot
Robot.say_hello   # Output: Hello from Robot
```

---

## Procs and Lambdas

Procs and lambdas store blocks of code for reuse.

### Differences
- **Lambdas**: Strict about the number of arguments (raises an error if incorrect).
- **Procs**: Lenient (ignores extra arguments, sets missing ones to `nil`).

```ruby
# Lambda: strict argument checking
lambda = -> x { x }  # Takes one argument and returns it
puts lambda.call("Nill")  # Output: Nill
# lambda.call("Nill", "Nill2")  # Raises ArgumentError: wrong number of arguments

# Proc: lenient with arguments
proc = Proc.new { |x| x }  # Takes one argument and returns it
puts proc.call("Nill")         # Output: Nill
puts proc.call("Nill", "Nill2")  # Output: Nill (extra argument ignored)
```

### Using Procs with Methods
```ruby
# Method that yields to a block
def demo
  yield("Amit")  # Pass "Amit" to the block
end
# Create a proc
proc = Proc.new { |name| puts name }
demo &proc  # Output: Amit

# Filter even numbers using a proc
check_even = Proc.new { |num| num.even? }  # Returns true if number is even
arr = [1, 2, 3, 4, 5, 6]
puts arr.select(&check_even)  # Output: 2, 4, 6
```

---

## Arrays

Arrays store ordered lists of items (numbers, strings, etc.).

```ruby
# Create an array with mixed types
arr = [1, "Ruby", :symbol]
puts arr[0]    # Output: 1 (access first element)
arr << "New"   # Append "New" to the array
puts arr       # Output: [1, "Ruby", :symbol, "New"]
# Iterate over array
arr.each { |item| puts item }  # Output: 1, Ruby, :symbol, New
```

---

## Hashes

Hashes store key-value pairs, like a dictionary.

```ruby
# Create a hash
data = {"name" => "Abhi", "age" => 30}
puts data["name"]  # Output: Abhi (access value by key)

# Hash with default value (returns 0 if key is missing)
new_data = Hash.new(0)
new_data[:count] = 5  # Set key-value pair
puts new_data[:count]    # Output: 5
puts new_data[:missing]  # Output: 0 (default value)

# Loop through hash
new_data.each { |key, value| puts "#{key}: #{value}" }
# Output: count: 5
```

---

## Sorting and Filtering

### Sorting
Use the spaceship operator `<=>` for custom sorting:
- Returns `0` if equal, `1` if first > second, `-1` if first < second.

```ruby
# Array of names
names = ["Abhinandan", "Abhi", "Yash"]
# Sort in descending order using the spaceship operator
puts names.sort { |a, b| b <=> a }  # Output: Yash, Abhinandan, Abhi

# Array of numbers
numbers = [3, 1, 2]
# Sort in ascending order
puts numbers.sort { |a, b| a <=> b }  # Output: 1, 2, 3
```

### Filtering
Use `select` to filter items based on a condition.

```ruby
# Array of numbers
numbers = [1, 2, 3, 4, 5, 6]
# Select even numbers
evens = numbers.select { |num| num.even? }
puts evens  # Output: 2, 4, 6
```

---

## Error Handling

Handle errors using `begin`, `rescue`, `ensure`, and `end`.

```ruby
# Begin block: code that might raise an error
begin
  num = 10 / 0  # Try to divide by zero
# Rescue: handle specific error
rescue ZeroDivisionError
  puts "Cannot divide by zero!"  # Error message
# Ensure: always runs, error or not
ensure
  puts "This always runs."
end
# Output:
# Cannot divide by zero!
# This always runs.
```

---

## File Input/Output

Read and write files using Ruby’s `File` class.

```ruby
# Write to a file
File.open("example.txt", "w") { |file| file.write("Hello, Ruby!") }  # Create/overwrite file
# Read from a file
content = File.read("example.txt")  # Read entire file
puts content  # Output: Hello, Ruby!
```

**Note**: Ensure the file path is valid and you have write permissions.

---

## Ruby Gems and Libraries

Gems are Ruby libraries that add functionality. Install them with the `gem` command.

```bash
gem install pry  # Installs Pry, an enhanced IRB
```

### Example: Using Pry
```ruby
# Require the Pry library
require 'pry'
# Open an interactive Pry session
binding.pry  # You can type Ruby code here
```

---

## Resources for Learning Ruby

- [Official Ruby Website](https://www.ruby-lang.org/) – Official documentation and downloads.

---

This guide covers all the core Ruby concepts for beginners. Each example includes detailed comments to explain what’s happening. Try running the code in IRB or a `.rb` file, experiment, and have fun learning Ruby!

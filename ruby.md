---
title: Ruby
created_at: 2014-11-03 10:25:18 +0400
kind: article
keywords: ruby, howto
is_draft: true
---

# Ruby

## Front matter

```ruby
#!/usr/bin/env ruby
# encoding: UTF-8
```

## Expressions and Conditions

```ruby
# condition
if rand() < 0.5 then "shave" else "exercise" end

# unless
unless arr.length > 0
  puts 'Not enough parameters'
end

result = nil || 1 # -> 1
entries = timeline.entries || []
options[:country] ||= 'hu' # will default to 'hu' if nothing given

def get_timeline
  user_timeline || sign_in_user
end

a = if b == 5 then c else d end

url = case client_name
  when "web"
    "http://blah.com"
  when "app"
    "http://blah.com/app"
  else
    "http://google.com"
end
```

## Strings and Symbols

```ruby
# string to symbol
"Balta Ceruza".gsub(/\s+/, '_').downcase.to_sym # results in :balta_ceruza

# test if string fits regexp
("something" =~ /.*meth.*/) != nil

# regex from string
Regexp.new "/.*ek.*/"

# use heredoc for multiline strings
puts <<-EOT
Dear #{recipient.name},

I write this,
only to you.
EOT

# or %(), but note the new line handling
puts %(Dear #{recipient.name},

I write this,
only to you.)

# save docs and data _in_ the script file using __END__ and DATA
require 'yaml'

puts YAML.load(DATA)

__END__
---
title: this is actual YAML in the ruby script
```

## Collections

```ruby
arr = [1,2,3,4,5,6,7,8,9,10]

arr.map { |el| el*3 } # returns original array with all elements modified
arr.each { |el| el.to_s+'!' } # acts on each element, returns unmodified array
arr.reduce(10) { |acc, el| acc += el } # accumulate with elements; opt. initial value
arr.select { |el| el%2 == 0 } # returns new array with elements fitting expression
err.reject { |el| el==2 || el==8 } # opposite of select
arr.find { |el| el/2 == 2 } # returns first element that fits the expression
arr.group_by { |el| el.even? } # groups elements into new hash idx. by lamba results
arr.sort { |a,b| a <=> b} # sort; can be used w/o block if elements are sortable

arr.slice(2..4) # returns subset by ids
arr.take(3) # returns first N elements
arr.drop(3) # drop first N elements
arr.concat([4,5,6]) # concatenate
arr.union([4,5,6]) # same as concat, but removes duplicates
arr.uniq # new collection with only the unique elements
arr.max; arr.min # largest/smallest element
arr.flatten # removes nesting
```

## Blocks, Higher Order Functions

```ruby
# creating/using blocks
def hi(name)
  puts "Hi, #{name}!"
  yield(name) if block_given?
end

hi "ati" do |str|
  puts "#{str.length} chars."
end

# Procs
sum = proc { |a,b| a+b }
sum.call 3,4 # => 7

# Simple profiler
def time
  start = Time.now
  yield
  puts Time.now-start
end

time { sleep 2 }
```

## Classes and Modules

```ruby
# Classes
class Thing
  attr_accessor :foo # make var public
  attr_reader :bar # public getter
  attr_writer :baz # public setter
  
  def initialize # constructor
    @bar = "cat" # instance variable
  end
end

# composition with modules
module SomeExtensionModule
  def some_extension
    puts "I do something useful!"
  end
end

class Array
  include SomeExtensionModule
end

# create singletons using modules and extend self
module SomeSingleton
  extend self

  def some_function
  end
end

# use method_missing to extend classes in creative ways
class SomeClass
  def initialize # constructor
    super # super class
  end

  def method_missing(method, *args, &block)
    args.each do |n|
      puts n.to_s
    end

    yield block if block_given?

    method.to_s
  end
end

# autoload is like require, but only loads file when a constant is accessed first
autoload :MyClass "myclass"
```

### Files and Folders

```ruby
# Files
if (File.exist?('filename'))
  # stuff
end

filePath = File.expand_path('relative_path_to_file', File.dirname(__FILE__))
contents = File.open(filePath, 'r').read

# list files in a directory
Dir.chdir 'Work' # cd Work; Dir.pwd contains pwd

Dir.glob 'xv6/*.h' do |f|
  puts f
  puts IO.read f
end
```

## Misc Stuff

```ruby
# ERB
require 'erb'
include ERB::Util # for html_escape, url_encode

puts ERB.new(template).result(binding) # 'binding' == object's context

puts html_escape("a > 0")

# access environment variables
puts ENV['PATH']

# get item YAML front matter
require "safe_yaml/load"

if item =~ /\A(---\s*\n.*?\n?)^((---|\.\.\.)\s*$\n?)/m
  metadata = SafeYAML.load($1)
end

# default parameter
def ls(path='*')
  Dir.glob path
end

# replace ~ with home dir
def cd(path)
  Dir.chdir path.gsub(/^~/, Dir.home)
end
```
# Regular expression

In this project, I learned how to use regular expressions. All my regex is built for the Oniguruma library.

## Tasks :page_with_curl:

_Note: Each Ruby script in the project matches regular expressions based on an argument passed to it via the command line._

0. Simply matching Holberton
```ruby
# 0-simply_match_holberton.rb

require 'oniguruma'

regex = Regexp.new('School')
string = 'Holberton School'

if regex.match?(string)
  puts "Match found!"
else
  puts "No match found."
end
```

1. Repetition Token #0
```ruby
# 1-repetition_token_0.rb

require 'oniguruma'

regex = Regexp.new('hbn{2,5}t')
string = 'Holberton'

if regex.match?(string)
  puts "Match found!"
else
  puts "No match found."
end
```

2. Repetition Token #1
```ruby
# 2-repetition_token_1.rb

require 'oniguruma'

regex = Regexp.new('(h(t|b)){0,1}n')
string = 'Holberton'

if regex.match?(string)
  puts "Match found!"
else
  puts "No match found."
end
```

3. Repetition Token #2
```ruby
# 3-repetition_token_2.rb

require 'oniguruma'

regex = Regexp.new('hbn+')
string = 'Holberton'

if regex.match?(string)
  puts "Match found!"
else
  puts "No match found."
end
```

4. Repetition Token #3
```ruby
# 4-repetition_token_3.rb

require 'oniguruma'

regex = Regexp.new('hbn*')
string = 'Holberton'

if regex.match?(string)
  puts "Match found!"
else
  puts "No match found."
end
```

5. Not quite HBTN yet
```ruby
# 5-beginning_and_end.rb

require 'oniguruma'

regex = Regexp.new('^h.n$')
string = 'Holberton'

if regex.match?(string)
  puts "Match found!"
else
  puts "No match found."
end
```

6. Call me maybe
```ruby
# 6-phone_number.rb

require 'oniguruma'

regex = Regexp.new('\A\d{10}\z')
string = '555-0100'

if regex.match?(string)
  puts "Match found!"
else
  puts "No match found."
end
```

7. OMG WHY ARE YOU SHOUTING?
```ruby
# 7-OMG_WHY_ARE_YOU_SHOUTING.rb

require 'oniguruma'

regex = Regexp.new('[A-Z]+')
string = 'THIS IS IN ALL CAPS'

if regex.match?(string)
  puts "Match found!"
else
  puts "No match found."
end
```

8. Textme
```ruby
# 100-textme.rb

require 'csv'
require 'date'

def parse_date(date_string)
  Date.strptime(date_string, '%m/%d/%y %I:%M %p')
end

def parse_message(message)
  parts = message.split(',')
  sender = parts[0]
  receiver = parts[1]
  flags = parts[2]
  [sender, receiver, flags]
end

def read_messages(file_path)
  messages = []
  CSV.foreach(file_path, headers: false) do |row|
    messages << parse_message(row[0])
  end
  messages
end

def analyze_messages(messages)
  start_date = messages[0][0]
  end_date = messages[-1][0]
  duration = end_date - start_date
  num_messages = messages.length
  [start_date, end_date, duration, num_messages]
end

file_path = 'textme.csv'
messages = read_messages(file_path)
results = analyze_messages(messages)

puts "Start Date, End Date, Duration (in days), Number of Messages"
puts "#{results[0]}, #{results[1]}, #{results[2].to_i}, #{results[3]}"
```
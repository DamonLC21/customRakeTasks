# Custom Rake Tasks

## In this lesson we've built custom rake tasks!

### Tasks Include
  1. rake console
  2. rake speak
  3. rake process_csv

### Remember all rake tasks must have a description to show up in our terminal via rake -T ! 

We write that by specifying...

```ruby 
  desc "This is my description"
  task :task_name do
    puts "Some text"
  end```


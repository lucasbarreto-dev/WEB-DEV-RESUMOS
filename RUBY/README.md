## 1. Reading and Writing Files

```ruby
    # Read file
    File.read('file.txt')

    # Write file
    File.write('file.txt', 'Hello, world!')
```

## 2. Checking If a File Exists

```ruby
    File.exist?('file.txt') # true or false
```

## 3. Creating and Listing Directories

```ruby
    # Create directory
    Dir.mkdir('my_folder') unless Dir.exist?('my_folder')

    # List directory contents
    Dir.entries('.')
```

## 4. Deleting Files and Directories

```ruby
    File.delete('file.txt') if File.exist?('file.txt') # Delete file
    Dir.rmdir('my_folder') if Dir.exist?('my_folder') # Delete directory

```
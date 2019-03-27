require_relative "app.rb"
require "pry"
require "csv"
require "sqlite3"


#Rake tasks must have a description to show up in the available tasks with rake -T
#we write descriptions like so ..

desc "Open a new console"
task :console do
    Pry.start
end

#Create a rake task to run the cat method from app.rb
#app.rb must be required for this to work!

desc "Let the cat do it's thanngggg"
task :speak do
    cat
end

#Create a rake task for automating the processing of a .csv file and seeding a database.

desc "Process a csv"
task :process_csv do
    db = SQLite3::Database.new("db/objective.db")
    db.execute("CREATE TABLE IF NOT EXISTS objectives (
        id INTEGER PRIMARY KEY,
        name,
        rubric_level,
        rubric_item,
        rubric_group,
        rubric_unit
        )")

        csv_text = File.read("objectives.csv")
        csv = CSV.parse(csv_text, :headers => true)
        csv.each do |row|
        db.execute("INSERT INTO objectives (
            name,
            rubric_level,
            rubric_item,
            rubric_group,
            rubric_unit
            ) VALUES (?, ?, ?, ?, ?)",
            row["Name"],row["Rubric Level"],row["Rubric Item"],row["Rubric Group"],row["Rubric Unit"]
        )
    end
    puts "Done!"
end

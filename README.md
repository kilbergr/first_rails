#Console Lab

For this exercise, you will be practicing your Rails console skills. Write out the console commands you would use to execute these queries

##To Start

1. Fork and clone the readme or create your own readme where you will place your answers   
2. Create a new rails application (don't forget to cd into the directory)

		rails new rails_console_lab -TBd   postgresql
Add pry-rails to your Gemfile and run bundle install   

		gem 'pry-rails'
		rails_console_lab
		bundle
3. Make sure you have created your database   

		rake db:create
4. Generate a model called Student, that has a first_name, last_name and age  
		rails generate model Student first_name:string last_name:string age:integer
5. Don't forget to run your migrations  
		rake db:migrate
	
##Tasks to create

1. Using the new/save syntax, create a student with a first and last name and an age    
	
		torey = Student.new(first_name: "Torey", last_name: "Hollingsworth", age: 26)
2.Save the student to the database  
	
		torey.save 
3. Using the find/set/save syntax update the student's first name to Myles  
		torey = Student.find_by_id(1)  
		torey.first_name = "Myles"  
		torey.save  
4. Delete the student (where first_name is Myles)  
	
		torey.destroy
5. In your model, validate that every Student's last name is unique  
	
		validates_uniqueness_of :last_name
	OR
	
		validates :last_name, uniqueness: true
6. In your model, validate that every Student has a first and last name that is longer than 4 characters  

		class Student < ActiveRecord::Base  
			validates :last_name, uniqueness: true, length: {minimum:4}  
			validates :first_name, length: {minimum: 4}  
		end

7. Validate that every first and last name cannot be empty  
	
			validates :last_name, uniqueness: true, length: {minimum:4}, allow_blank: false    
			validates :first_name, length: {minimum: 4}, allow_blank: false
8. Create a migration that adds a column with a type of string called favorite_color to the students table (don't forget to run rake db:migrate after and for this question write the command in terminal to generate this migration)  
	
		rails g migration addFavoriteColorToStudents fav_color:string   
		rake db:migrate  
9. Using the create syntax create a student named John Doe who is 23 years old and has a favorite_color of purple  
		john = Student.create(first_name: "John", last_name: "Doe", age: 23, fav_color: "purple")
10. Show if this new student entry is valid  

		john.valid?
11. Show the number of errors for this student instance  

		john.error.full_message
12. Using update, Change John Doe's name to Martin Fowler  

		student = Student.find_by_first_name("John")  
		john.update_attributes(first_name: "Martin", last_name: "Fowler")

13. Save Martin Fowler  

		student.save
14. Find all of the Students

		Student.all  
15. Find the student with an ID of 128 and if it does not exist, make sure it returns nil and not an error  

		Student.find_by_id(128)
16. Find the first student in the table  
		Student.first
17. Find the last student in the table  

		Student.last
18. Find the student with the last name of Fowler  

		Student.find_by_last_name("Fowler")
19. Find all of students who have the first name of Martin and a favorite color of red  

		Student.where(first_name: "Martin", fav_color: "red")
20. Find all of the students and limit the search to 5 students, starting with the 2nd student and finally, order the students in alphabetical order  

		Student.limit(5)  
		Student.offset(1)  
		Student.order(:last_name)  
		Student.order(:first_name)  
21. Delete Martin Fowler (but first look up who he is!)  

		student = Student.find_by_first_name("Martin")  
		student.destroy
22. Delete all of the students  

		Student.destroy_all
##Bonus

* Use the validates_format_of and regex to only validate names that consist of letters (no numbers or symbols) and start with a capital letter  
* Write a custom validation to ensure that no one named Elie Schoppik, Colt Steele or Tim Garcia is included in the students table.

		NOT_STUDENTS_FN = ["Colt", "Tim"]
		NOT_STUDENTS_LN = ["Steele", "Garcia"]
		class Student < ActiveRecord::Base
			validate :dont_add

			def dont_add
				if NOT_STUDENTS_FN.include?(first_name) && NOT_STUDENTS_LN.include?(last_name)
					errors.add(:first_name, "This is not a student")
				end
			end
		end

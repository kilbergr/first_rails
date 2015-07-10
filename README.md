#Console Lab

For this exercise, you will be practicing your Rails console skills. Write out the console commands you would use to execute these queries

##To Start

1. Fork and clone the readme or create your own readme where you will place your answers   
2. Create a new rails application (don't forget to cd into the directory)
Add pry-rails to your Gemfile and run bundle install  
3. Make sure you have created your database  
4. Generate a model called Student, that has a first_name, last_name and age  
5. Don't forget to run your migrations  

##Tasks to create

1. Using the new/save syntax, create a student with a first and last name and an age  
2.Save the student to the database  
3. Using the find/set/save syntax update the student's first name to Myles  
4. Delete the student (where first_name is Myles)  
5. In your model, validate that every Student's last name is unique  
6. In your model, validate that every Student has a first and last name that is longer than 4 characters  
7. Validate that every first and last name cannot be empty  
8. Create a migration that adds a column with a type of string called favorite_color to the students table (don't forget to run rake db:migrate after and for this question write the command in terminal to generate this migration)  
9. Using the create syntax create a student named John Doe who is 23 years old and has a favorite_color of purple  
10. Show if this new student entry is valid  
11. Show the number of errors for this student instance  
12. Using update, Change John Doe's name to Martin Fowler  
13. Save Martin Fowler  
14. Find all of the Students  
15. Find the student with an ID of 128 and if it does not exist, make sure it returns nil and not an error  
16. Find the first student in the table  
17. Find the last student in the table  
18. Find the student with the last name of Fowler  
19. Find all of students who have the first name of Martin and a favorite color of red  
20. Find all of the students and limit the search to 5 students, starting with the 2nd student and finally, order the students in alphabetical order  
21. Delete Martin Fowler (but first look up who he is!)  
22. Delete all of the students  

##Bonus

* Use the validates_format_of and regex to only validate names that consist of letters (no numbers or symbols) and start with a capital letter  
* Write a custom validation to ensure that no one named Elie Schoppik, Colt Steele or Tim Garcia is included in the students table.
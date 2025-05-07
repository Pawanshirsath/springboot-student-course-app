1.	Entity Relationship Design



The application manages two entities: Student and Course. The relationship between them is Many-to-Many, as a student can enroll in multiple courses, and a course can have multiple students.


Entity: Student

-	id (Long)

-	name (String)

-	email (String)



Entity: Course

-	id (Long)

-	name (String)

-	description (String)



This relationship is mapped using a @ManyToMany annotation in JPA.



2.	Implementation Details



Create Operation:

-	A JSP form is provided for both Student and Course creation.

-	The form data is submitted to the controller, which calls the service and saves the entity using the repository.
 
-	All students and courses are listed in JSP views using JSTL.

-	A custom query is implemented in the repository to perform an inner join and display enrolled students with their courses.


Update Operation:

-	Each entry in the list has an Edit button.

-	Clicking it loads a form pre-filled with data, allowing updates.



Custom Query Example:

@Query("SELECT s FROM Student s JOIN s.courses c WHERE c.name = :courseName") List<Student> findStudentsByCourseName(String courseName);


3.	Challenges and Solutions



-	Challenge: Handling Many-to-Many mapping in JSP forms.

Solution: Used checkboxes in JSP with proper data binding and CascadeType settings in JPA.



-	Challenge: View rendering with JSTL.

Solution: Ensured tag libraries were correctly added in the JSP files and proper paths used.



-	Challenge: Exception handling on duplicate entries.

Solution: Implemented try-catch blocks in service layer and added validation in the form.


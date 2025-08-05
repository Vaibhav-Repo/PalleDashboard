# Models:-
1. In this project, Ive customized Django built-in user model by extending AbstractUser.
I added a role field to distinguish between different user types  like admin and sales.
2. Then I created a Student model that stores student details like name, email, age, gender, place, etc.
Each student is connected to the user who added them using a ForeignKey relation to CustomUser.
3. So this way, I can track which user added which student.
It's useful for role-based access, like showing only the students added by a sales user.
4. This setup supports role-based user access and allows tracking which user added which student,
 making it scalable and secure.

 # Views:-
 1. home – [Login Required]- Loads the homepage only if user is authenticated.
 2. user_login – Handles user authentication.- Checks for username/password, logs the user in.- Shows error messages if login fails.
 3. register – New user registration (only as 'sales' role).- Validates passwords.- Prevents duplicate usernames.- Uses `make_password()` to hash the password.
 4. user_logout – Logs the user out and redirects to login.
 5. employee_list – Admin-only view that lists all CustomUsers.- Uses `values()` to pass data to template.
 6. student_list – Shows different data based on role.- Admin sees all students.- Sales sees only students they added.- Uses `select_related` for performance boost.
 7. add_new_student – Adds new student to DB.- Admin can choose who added the student.- Validates duplicate email.- Joins skillset list into a string.
 8. update_student – Updates existing student.- Checks if email exists for another student.- Preloads skillset & user data.
 9. delete_student – Deletes a student by ID.
 Extras:- @login_required ensures only authenticated users can access certain views.- messages framework is used for friendly error messaging.- Logs are implemented for tracking login attempts

# Templates:-
## Base.html-
 Purpose : This is the base layout template in Django. It provides a reusable structure with Bootstrap, jQuery,
           and common elements like the navbar. It uses Django template tags for block content and includes.
 1.  Declares the document type as HTML5 and Basic structure of the HTML document. ensures proper encoding. title sets the title in the browser tab.
 2.  Makes the page responsive on mobile devices.
 3. Bootstrap and jQuery CDNs:- Includes Bootstrap CSS (v3.4.1) and JavaScript dependencies using CDNs.Enables responsive design and dynamic UI features.
 5. {% include 'navbar.html' %}- Inserts the navbar.html template at this point.Reuses a common navigation bar across pages.
 6. An empty Bootstrap container with top margin. Used for layout spacing. You can move {% block content %} inside it for better structure.
 7. {% block content %}{% endblock %}- Placeholder for child templates to insert their own content. A core feature of Django’s template inheritance and Closes the document properly.
 This template is meant to be extended by other templates using:{% extends 'base.html' %}
 It helps avoid repetition and maintain a consistent look across your Django project.

 # What It actually Does:- 
 1. Role-based authentication (admin vs sales)
 2. Admin can see and manage all student records
 3. Sales users can only view students they have added
 4. Full CRUD functionality for student management
 5. Uses Django's authentication system and decorators like @login_required

 # Technical Highlights:- 
1. CustomUser extends AbstractUser for flexibility
2. Uses select_related for better performance in querying related models
3. Skillset handling using checkboxes, joined into a comma-separated string
4. Implements message framework for better UX
5. Admin and user control over student visibility

 # Why It’s Useful:-
 This app mimics real-world use cases like CRM dashboards, internal employee panels, and
 educational tracking systems. It shows a strong grasp of Django, database modeling, security, and
 user experience.





















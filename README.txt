ExamPrep Hub – A Web-Based Exam Preparation Platform for BCA Students
School of Computer Applications, Graphic Era Hill University · Section C2
Mentor: Amit Juyal

HOW TO RUN (XAMPP)
------------------
1. Install XAMPP (free) from https://www.apachefriends.org
2. Copy the whole "examprep-hub" folder into  C:\xampp\htdocs\
3. Open the XAMPP Control Panel and click START next to Apache and MySQL.
4. Open  http://localhost/examprep-hub/  in Google Chrome.
   The first time, the website creates the MySQL database "examprep_hub"
   with all tables and the sample data by itself.
   (Or import database/examprep_hub.sql in phpMyAdmin → Import.)

If Apache will not start because port 80 is busy, change the port to 8080
(Config → httpd.conf → "Listen 8080") and open http://localhost:8080/examprep-hub/
If your MySQL has a password, write it in api/config.php (DB_PASS).

DEMO LOGINS  (or use the "Demo student" / "Demo teacher" buttons)
-----------
Student : student@examprep.com / student123
Teacher : teacher@examprep.com / teacher123
Teacher registration code: GEHU-TEACH

PAGES
-----
index.html       Home page (Features, How it works, Semesters, For Teachers, Team)
login.html       Log in / Create account (Student or Teacher)
dashboard.html   Student dashboard – average score, subject-wise performance,
                 recent attempts, latest important questions, semester tiles
papers.html      Previous year papers – semester chips, search inside questions,
                 subject / year / exam-type filters, view counts
paper.html       Printable exam paper (Print / Save as PDF), scanned PDF if attached
important.html   Important questions – tags, marks, difficulty, years asked,
                 show/hide answers, save (star) questions, Saved tab
quizzes.html     Practice quizzes list + attempt history
quiz.html        Timed quiz – question palette, mark for review, clear, auto-submit
result.html      Score ring, correct / wrong / skipped / time, answer review
teacher.html     Teacher Panel – Overview, Important Qs, Papers (PDF upload), Quizzes
profile.html     Edit details, change password, dark mode, reset demo data (teacher)

TECHNOLOGIES (as in the proposal)
------------
Front-end : HTML5 (structure), CSS3 (design, dark mode, mobile), JavaScript (logic,
            quiz timer, search, filters, talking to the server with fetch)
Back-end  : PHP (runs in XAMPP's Apache) – login, rules, quiz scoring, PDF upload
Database  : MySQL (XAMPP) – 9 tables: users, papers, paper_sections, paper_questions,
            important_questions, saved_questions, quizzes, quiz_questions, attempts
Passwords are saved with password_hash() (bcrypt). Quiz answers stay on the server
until the student submits. Uploaded PDFs are saved in the uploads/ folder.

FILE STRUCTURE
--------------
*.html            One file per page
css/style.css     All styling (light + dark theme, mobile, print layout)
css/fonts.css     Fonts stored inside the project (work without internet)
js/config.js      Semesters, subjects and question tags (edit the subject list here)
js/api.js         Sends requests to the PHP server, shows "start XAMPP" help if needed
js/core.js        Login check, sidebar layout, icons, popups, helpers
js/<page>.js      One JavaScript file for each page
api/config.php    MySQL login (XAMPP default: root, no password) + teacher code
api/db.php        Database connection, automatic setup, session, helpers
api/auth.php      Log in, sign up, log out, profile, password, reset demo data
api/papers.php    Previous year papers + PDF upload / download
api/important.php Important questions + saved (starred) questions
api/quizzes.php   Quizzes, server-side scoring, results
api/stats.php     Numbers for the home page and dashboards
database/examprep_hub.sql   All tables + sample data
uploads/          Uploaded PDF papers (blocked from direct access)

MODULE-WISE WORK DIVISION
-------------------------
Tanishk Saini   (2421631) – Login system, database & PHP setup, dashboards, home page
Shashank Badoni (2421562) – Previous year papers module (list, viewer, PDF upload)
Taniksha Khanna (2421628) – Important questions module (tags, answers, saved)
Mohini          (2421390) – Quiz module (player, result, quiz builder), UI design

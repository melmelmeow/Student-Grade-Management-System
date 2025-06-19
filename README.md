# Student-Grade-Management-System
 a console-based application that allows users to manage student records, including their  IDs, names, and grades for various subjects. All data will be persistently stored in a text file.


BSIT First Year Final Project in Programming 2 
Python Console Project:  
Student Grade Management System 
Project Goal:  
Create a console-based application that allows users to manage student records, including their 
IDs, names, and grades for various subjects. All data will be persistently stored in a text file. 
Learning Objectives: 
1. File I/O: Reading from, writing to, and updating text files. 
2. Data Structures: Using lists and dictionaries to represent student data in memory. 
3. String Manipulation: Parsing data from text file lines and formatting data for storage. 
4. Functions: Modularizing code into reusable functions. 
5. User Input and Output: Designing a user-friendly console interface. 
6. Error Handling: Gracefully managing potential issues (e.g., file not found, invalid input). 
Project Components: Input, Processes, and Results 
Overall Project Goal: To manage student records (ID, Name, Grades) persistently using a text file. 
NOTES: These components are guides, for the logic flow of the processes (components) 
Component 1: Main Program Loop / User Interface 
 Description: This is the central control of the application, presenting the menu, accepting 
user choices, and dispatching to other functions. 
 Input:  
o User's choice from the displayed menu (e.g., '1', '2', '3', '4', '5'). 
o User pressing Enter to continue. 
 Process/es:  
o Displaying Menu: Prints predefined options to the console. 
o Getting User Choice: Reads input from the console. 
o Choice Validation: Checks if the input choice is valid (e.g., '1' to '5'). 
o Function Dispatch: Calls the appropriate function based on the valid choice (e.g., 
add_student(), update_grade()). 
o Loop Control: Continues displaying the menu until the user chooses to exit. 
o Persistence Trigger: Calls save_students() before exiting. 
 Results:  
o Program continues to operate, displaying menus and prompts. 
BSIT First Year Final Project in Programming 2 
o Appropriate functions are executed. 
o Program exits when the user chooses '5', ensuring data is saved. 
Component 2: Data Loading (load_students) 
 Description: Responsible for reading student data from the persistent storage file 
(grades.txt) into the program's memory. 
 Input:  
o filename (string, e.g., "grades.txt"). 
o The content of the grades.txt file (if it exists), formatted as 
StudentID,StudentName,Subject1:Grade1,.... 
 Process/es:  
o File Existence Check: Determines if the filename exists. 
o File Opening: Opens the specified file in read mode ('r'). 
o Line-by-Line Reading: Iterates through each line of the file. 
o Line Parsing: For each line:  
 Strips whitespace. 
 Splits the line by the comma (,) delimiter. 
 Extracts StudentID and StudentName. 
 Further splits grade entries (e.g., "Math:90") by the colon (:) delimiter. 
 Converts grade strings to integers. 
o Data Structuring: Populates an in-memory dictionary (students_data) where each 
student's information is nested. 
o Error Handling: Catches FileNotFoundError (returns empty data) and ValueError during 
grade conversion (skips invalid grades). 
 Results:  
o An in-memory dictionary students_data populated with all student records from the 
file. 
o Console messages indicating file not found or data loading errors/warnings. 
Component 3: Data Saving (save_students) 
 Description: Responsible for writing the current student data from memory back to the 
persistent storage file (grades.txt). This ensures data changes are not lost when the 
program closes. 
 Input:  
o students_data (the in-memory dictionary containing all student records). 
o filename (string, e.g., "grades.txt"). 
 Process/es:  
o File Opening: Opens the specified file in write mode ('w'), which truncates (clears) 
its content. 
BSIT First Year Final Project in Programming 2 
o Data Serialization: Iterates through the students_data dictionary. For each student:  
 Constructs a single string line following the defined 
StudentID,StudentName,Subject1:Grade1,... format. 
 Converts numeric grades back to strings for writing. 
o Line Writing: Writes each constructed student line, followed by a newline 
character, to the file. 
o Error Handling: Catches potential IOError or other exceptions during writing. 
 Results:  
o An updated grades.txt file reflecting the current state of students_data. 
o Console message confirming successful save or reporting an error. 
Component 4: Adding a Student (add_student) 
 Description: Guides the user to input details for a new student and adds them to the in
memory data. 
 Input:  
o students_data (the current in-memory dictionary). 
o User input for Student ID. 
o User input for Student Name. 
 Process/es:  
o Prompting: Displays prompts for student ID and name. 
o Input Reading: Reads user input from the console. 
o ID Validation: Checks if the entered Student ID is unique within students_data. If not, 
prompts again. 
o Data Addition: Adds a new entry to the students_data dictionary with the provided 
ID and name, and an empty grades dictionary. 
 Results:  
o students_data dictionary is updated with the new student record. 
o Console message confirming the student was added or informing of a duplicate 
ID. 
Component 5: Updating a Grade (update_grade) 
 Description: Allows the user to modify an existing student's grade for a specific subject, 
or add a new subject grade. 
 Input:  
o students_data (the current in-memory dictionary). 
o User input for Student ID. 
o User input for Subject Name. 
o User input for New Grade (numeric). 
 Process/es:  
BSIT First Year Final Project in Programming 2 
o Prompting: Displays prompts for student ID, subject name, and new grade. 
o Input Reading: Reads user input. 
o Student Lookup: Checks if the entered Student ID exists in students_data. 
o Grade Validation:  
 Attempts to convert the New Grade input to an integer. 
 Checks if the grade is within the valid range (0-100). 
 Handles ValueError for non-numeric input. 
o Grade Update: Updates the specific subject's grade in the student's grades 
dictionary within students_data. 
 Results:  
o students_data dictionary is updated with the modified/added grade. 
o Console messages indicating success, student not found, or invalid grade input. 
Component 6: Calculating Average Grade (calculate_average_grade) 
 Description: Computes and displays average grades either for a single student or for a 
single subject across all students. 
 Input:  
o students_data (the current in-memory dictionary). 
o User choice: 'student' or 'subject'. 
o If 'student': User input for Student ID. 
o If 'subject': User input for Subject Name. 
 Process/es:  
o Choice Handling: Determines if calculation is for a student or a subject. 
o Student Average Calculation:  
 Looks up the student by ID. 
 Retrieves all grades for that student. 
 Sums the grades and divides by the count of grades. 
 Handles cases with no grades. 
o Subject Average Calculation:  
 Iterates through all students. 
 Collects grades for the specified subject from each student who has it. 
 Sums these grades and divides by their count. 
 Handles cases where no student has grades for that subject. 
o Error Handling: Checks for non-existent student IDs or subjects. 
 Results:  
o Console output displaying the calculated average grade, formatted to two decimal 
places. 
o Console messages indicating student/subject not found or no grades available. 
Component 7: Generating Report (generate_report) 
BSIT First Year Final Project in Programming 2 
 Description: Displays a comprehensive formatted report of all student records in the 
system. 
 Input:  
o students_data (the current in-memory dictionary). 
 Process/es:  
o Data Iteration: Loops through each student record in students_data. 
o Data Formatting: Structures and prints student ID, name, individual subject 
grades, and their calculated average grade (if available) in a readable format. 
o No Students Check: Handles the case where the students_data dictionary is empty. 
 Results:  
o A neatly formatted, multi-line report printed to the console, detailing each 
student's information. 
o A message indicating "No students to display" if applicable. 
Grading Criteria: 
1. Functionality (50%) 
This is the most crucial part. Your program should work as described in the project instructions. 
 Core Features (30%)  
o Add New Student: Can a user successfully add a new student with a unique ID and 
name? 
o Update Student Grade: Can a user select an existing student and update or add 
grades for specific subjects? Is input validation for grades (0-100) present and 
effective? 
o Calculate Average Grade: Does it correctly calculate the average grade for a 
specific student? Does it correctly calculate the average for a specific subject 
across all students? 
o Generate Report: Does it display a clear, well-formatted report of all students, 
their IDs, names, and individual subject grades? Does it include individual student 
averages in the report? 
 File Handling (15%)  
o Load Data: Does the program correctly load existing student data from grades.txt 
when it starts? 
o Save Data: Are all changes (adding students, updating grades) correctly saved back 
to grades.txt when the program exits? Is the data format maintained accurately? 
o File Not Found: Does the program gracefully handle cases where grades.txt doesn't 
exist initially (e.g., creating it or starting with an empty dataset)? 
 Error Handling & Edge Cases (5%)  
o Invalid Input: Does the program handle non-numeric input for grades or choices 
gracefully (e.g., using try-except blocks)? 
BSIT First Year Final Project in Programming 2 
o Student/Subject Not Found: Does it provide helpful messages if a user tries to 
update a non-existent student or calculate an average for a non-existent subject? 
o Duplicate Student ID: Does it prevent adding students with IDs that already exist? 
o No Grades/Students: Does it handle scenarios where a student has no grades, or 
when there are no students in the system yet? 
2. Code Quality & Structure (30%) 
This section assesses how well your code is written and organized. 
 Modularity (10%)  
o Functions: Is the code broken down into logical, well-defined functions (e.g., 
load_students, save_students, add_student, update_grade, display_menu, etc.)? 
o Responsibility: Does each function have a clear, single responsibility? 
 Readability (10%)  
o Meaningful Names: Are variable, function, and parameter names clear and 
descriptive (e.g., student_id instead of x)? 
o Comments: Is the code adequately commented where necessary to explain 
complex logic or non-obvious parts? 
o Whitespace & Indentation: Is the code consistently indented and spaced 
according to Python best practices (PEP 8)? 
 Efficiency (5%)  
o File Operations: Are file operations performed efficiently (e.g., opening files only 
when needed, writing all data at once instead of line-by-line in a loop if not 
required)? 
o Data Structures: Are appropriate data structures used (e.g., dictionaries for quick 
student lookup by ID)? 
 Adherence to Pythonic Principles (5%)  
o Uses with open(...) for file handling. 
o Appropriate use of f-strings for output. 
o Avoids unnecessary global variables. 
3. User Experience (UX) (20%) 
A good program isn't just functional; it's also easy and pleasant to use. 
 Clear Instructions: Are menu options and input prompts clear and easy for the user to 
understand? 
 Informative Feedback: Does the program provide clear messages about what it's doing, 
success/failure of operations, and any errors encountered? 
 Navigation: Is it easy to navigate through the menu and perform desired actions? 
BSIT First Year Final Project in Programming 2 
 Output Formatting: Are reports and other output clearly formatted and readable in the 
console? 
Total Score: 100% 
Reminders:  
Important Project Guidelines 
Here's a clearer approach to using AI in your project: 
 AI as a Learning Tool: You're welcome to use AI tools (like ChatGPT, Gemini, etc.) to help you 
develop and understand your project. This can be a great way to explore different coding 
approaches, debug issues, or clarify concepts.  
 Understand Your Code: While AI can assist, it's crucial that you understand every line of code 
you submit. Don't just copy and paste; take the time to learn why the code works and how it 
solves the problem. Your understanding will be assessed.  
 Presentation & Debugging: During your project presentation, you'll have dedicated time to 
explain your code and demonstrate its functionality. This is also when you might be asked to 
debug or modify parts of your program on the spot, so a deep understanding of your code is 
key. 
Team Task Documentation and Grading 
Here's a clearer and more comprehensive way to approach documenting tasks, 
accomplishments, and grading for your team project: 
 Documenting Tasks and Accomplishments 
It's vital to maintain clear records of your team's work. For each team member, 
document the specific tasks they were assigned and list their accomplishments. This 
isn't just about what they said they'd do, but what they actually delivered. 
To do this effectively, consider: 
 Task Assignment: Clearly state who was responsible for what. Be specific (e.g., 
"Juan Dela Cruz: Implement add_student function and unit tests for it"). 
 Accomplishment Details: Provide concrete examples of what each member 
achieved. Don't just say "Helped with code." Instead, specify " Juan Dela Cruz: 
Successfully implemented save_students and load_students functions, 
ensuring data persistence." 
 Contribution to Deliverables: How did each person's work directly contribute 
to the final project components? 
 Collaboration: Note instances of effective teamwork or support provided to 
other members. 
BSIT First Year Final Project in Programming 2 
 Grading Team Member Accomplishments 
Once tasks and accomplishments are documented, you can assign grades based on 
their contributions. Consider the following when evaluating each member: 
 Task Completion: Did the member complete all assigned tasks? 
 Quality of Work: Was the code (or other deliverable) well-written, functional, and 
efficient? 
 Timeliness: Were tasks completed by agreed-upon deadlines? 
 Problem-Solving: How effectively did they identify and resolve issues or 
challenges? 
 Initiative & Proactiveness: Did they go beyond what was expected, offer 
solutions, or take ownership of unexpected problems? 
 Teamwork: Did they actively participate, communicate effectively, and support 
their teammates? 
You might use a simple rubric (e.g., a scale of 1-5 or percentages) for each of these 
criteria, or assign an overall grade based on a holistic assessment. The key is to be fair 
and transparent, backing up your grades with the documented accomplishments. 
Project Presentation Slides Content Outline 
Target Audience: Your instructor/evaluators and potentially classmates. 
Goal of Presentation: To clearly demonstrate your project's functionality, explain its technical 
implementation, highlight key learning, and assess team contributions. 
Slide 1: Title Slide 
 Title: Student Grade Management System 
 Subtitle: A Console-Based Grade Management Application 
 Course/Subject: [Your Course Name/Code, e.g., COMP 009] 
 Team Name: [Your Team Name, if applicable] 
 Team Members:  
o [Member 1 Name] 
o [Member 2 Name] 
o [Member 3 Name] 
o [Add more as needed] 
 Date: July 1, 2025 
Slide 2: Project Overview & Motivation 
 What is it?  
 Why did we build it?  
 Key Features: (Briefly list 3-4 main features, detailed later)  
Slide 3: System Requirements & Setup 
BSIT First Year Final Project in Programming 2 
 Software Requirements 
 Project Files 
 How to Run 
Slide 4: Data Storage Format (grades.txt) 
 Explanation: How we store data persistently. 
 Format 
 Example from grades.txt:  
 Why this format? (Briefly explain advantages)  
Slide 5: Core Functionality - Add & Update 
 Feature 1: Add New Student  
o Input:  
o Process:  
o Output:  
 Feature 2: Update Student Grade  
o Input:  
o Process:  
o Output:  
Slide 6: Core Functionality - Averages & Reports 
 Feature 3: Calculate Average Grade  
o Input:  
o Process:  
o Output:  
 Feature 4: Generate Report  
o Input:  
o Process:  
o Output:  
Slide 7: File Handling & Persistence 
 Loading Data (load_students function)  
o Process:  
o Key Aspect:  
 Saving Data (save_students function)  
o Process:  
o Key Aspect:  
 Importance:  
Slide 8: Data Structures & Modularity 
 In-Memory Data Structure:  
o How:  
o Example Structure:  
o Why:  
BSIT First Year Final Project in Programming 2 
 Modular Design (Functions):  
o Approach:  
o Benefits:  
Slide 9: Error Handling & Robustness 
 Key Scenarios Handled:  
o File Not Found:  
o Invalid Numeric Input:  
o Grade Range:  
o Duplicate Student ID:  
o Non-existent Student/Subject:  
o No Grades Recorded:  
 Why it's important:  
Slide 10: Challenges & Learnings 
 Challenges Faced:  
 Key Learnings:  
Slide 11: Future Enhancements (Optional) 
 Possible Additions:  
Slide 12: Team Contributions & Grading 
 Transparency: [State that you followed the outlined criteria for task documentation and 
grading.] 
 [Member 1 Name]:  
o Assigned Tasks: [Specific tasks] 
o Key Accomplishments: [What they delivered] 
o Contribution Grade: [Your assigned grade / rationale] 
 [Member 2 Name]:  
o Assigned Tasks: [Specific tasks] 
o Key Accomplishments: [What they delivered] 
o Contribution Grade: [Your assigned grade / rationale] 
 [Member 3 Name]:  
o Assigned Tasks: [Specific tasks] 
o Key Accomplishments: [What they delivered] 
o Contribution Grade: [Your assigned grade / rationale] 
 [Add more as needed] 
 Self-Reflection: Briefly mention how the team collaborated. 
Slide 13: Live Demonstration 
 Transition Slide: "Let's see the system in action!" 
 Instructions:  
o Open main.py in your editor for code review if requested. 
o Run the script from the terminal. 
BSIT First Year Final Project in Programming 2 
o Demonstrate each core feature:  
 Loading data (mention if grades.txt is empty or pre-filled). 
 Adding a new student (show ID validation). 
 Updating a grade (show grade validation). 
 Calculating an average (student and subject). 
 Generating the report. 
 Exiting and re-running to show persistence. 
 Speak through your actions! Explain what you're doing and why. 
Slide 14: Q&A / Thank You 
 Title: Questions & Discussion 
 Content:  
o "Thank you for your time!" 
o "Any questions?" 
o [Your contact information, if appropriate] 
o Reiterate willingness to debug/explain code. 
Presentation Tips: 
 Keep it concise: Use bullet points, not long paragraphs. 
 Visuals: If using PowerPoint/Google Slides, use clean design, consistent fonts, and 
appropriate colors. 
 Practice: Rehearse your presentation, especially the live demo! 
 Time Management: Allocate time for each slide and the demo. 
 Confidence: Present your work with confidence and clarity. 
Presentation Instructions 
Here's what you need to know for your upcoming presentation: 
Dress Code 
Please adhere to a formal corporate dress code. This means professional attire such as suits, 
blazers, dress shirts, blouses, dress pants, or skirts. 
Presentation Setup 
You will have 5 minutes for setup prior to your presentation. Please ensure all necessary files 
and equipment are ready within this timeframe. 
Presentation Duration 
The presentation itself is 1 hour. Be prepared to cover all your material (20 minutes) and allow 
time for questions (40 minutes). 

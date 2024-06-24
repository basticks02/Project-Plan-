# Project-Plan
Project Plan Link: https://docs.google.com/document/d/1qVpVUWfpK19PLDRcP0QqXiVbzNUfehxs9ig6wsnwLv4/edit


Meta University Eng Project Plan Template     
Fill in blanks (enclosed by brackets []) and remove red text as you work through writing your project plan. Your project plan should be a living document and can be changed as you progress through the internship. Make sure to work on this document together with your manager to get feedback, as well as ensuring your project meets the requirements and expectations in the Project Guide.
Synchronize
Intern: Praise Ekanem
Intern Manager: Cherie Liu
Intern Director: Vicky Wang
Peer(s): Christina Chen, Matthew Wang
GitHub Repository Link: https://github.com/Synchronize-X/synchronize.git
Overview
Synchronize is a cutting-edge web application designed for EnoObong Memorial Medical Services in Nigeria. This comprehensive platform aims to streamline and enhance the clinic's operations by facilitating efficient interactions between patients and the resident  physician. The app is tailored to manage health records, appointments, and provide vital medical resources, thereby improving the overall healthcare experience.
Category: Health and Medical Services
Story: The goal of this project is to build a comprehensive web application for EnoObong Memorial Medical Services, a clinic in Nigeria. The app will enhance the clinic’s operations by facilitating patient and physician interactions through a seamless digital platform.
Market: This app is aimed at patients and physicians of EnoObong Memorial Medical Services. It targets both existing and potential patients who need an efficient way to manage their health records, appointments, and access medical resources.
Habit: The app is expected to be used frequently by both patients and physicians. Patients will use it to manage their profiles, view COVID-19 resources, find directions to the clinic, and receive notifications about their health. Physicians will use it to manage patient profiles, schedule appointments, and provide updates.
Scope: The initial scope includes a landing page, user authentication, profile management for patients, a COVID-19 resource section, a locate page with Google Maps integration, and a notification system. Future stretch goals include an AI chatbot for health diagnosis and additional interactive features.

Product Spec
Landing Page
Header: Contains links to login/signup, general information about the clinic (about, history, what's new).
Body: Displays general information about the clinic.
Footer: Contact information, social media links, etc.

User Authentication
Login/Signup: Separate options for patients and physicians.
Redirection: After login/signup, users are redirected back to the landing page (Which contains Welcome ‘first name’).

Patient Features
My Profile: A separate page where patients can enter and edit their personal information such as name, date of birth, height, weight, occupation, phone number, and complaints and upload headshots(stretch).
Google Calendar Integration: Embedded calendar to manage appointments, updated by physicians.
COVID-19 Resources: A page or section on the landing page displaying important updates and precautions using the Open Disease Data API.
Locate Page: Embedded Google Maps to help patients find directions to the clinic.
Notifications: Updates from physicians regarding appointments, prescriptions, etc. (Stretch feature).
AI Chatbot (Stretch): Using the Infermedica API for NLP-based symptom checking and patient triage. Implementing a conversational interface within the app to interact with the chatbot.

Physician Features
Patients Component: A page listing all patient profiles with editable details.
Profile Editing: The Physician can view and edit patient profiles, manage appointments, and set prescription reminders. These changes will be reflected in the  patients' calendars.

User Stories
User stories are actions that the user should be able to perform in your app.

First, focus and identify functionality that is required for your MVP (Minimum Viable Product) that conforms to all the project requirements and expectations. Make sure your technical challenges are part of your MVP.

You should also identify optional / nice-to-have functionalities that would be done as stretch goals during MU Week 8 and 9. Remember, technical challenges should not be optional features, they must be code complete before the end of Week 8!

These are a few user stories for my MVP:
As a patient, I want to log in to my account, so that I can access my health records.
As a patient, I want to update my profile information, so that my physician has my latest details.
As a patient, I want to view my upcoming appointments on a calendar, so that I can keep track of them.
As a patient, I want to access COVID-19 resources, so that I stay informed about the latest updates and precautions.
As a patient, I want to locate the clinic using a map, so that I can easily find directions.
As a patient, I want to receive notifications about my appointments and prescriptions, so that I stay updated on my health status. (Stretch feature)
As a physician, I want to view all my patients’ profiles, so that I can manage their health records efficiently.
As a physician, I want to edit patient profiles, so that I can update their medical information and appointments.
As a physician, I want to set reminders for prescriptions, so that my patients are reminded to take their medication.

Screen Archetypes

Landing Page:

Description: The entry point of the app that provides general information about EnoObong Memorial Medical Services. It includes sections such as About, History, What's New, and Contact Information.
Components: Header with navigation links (Login/Signup), body with general information, and footer with contact details.

Login/Signup Page:

Description: The page where users can log in or create an account. Separate options are available for patients and physicians.
Components: Login form, Signup form, role selection (patient or physician), and redirection to the landing page upon successful authentication.

Patient Profile Page:

Description: A page where patients can enter and edit their personal information. It also includes an embedded Google Calendar for managing appointments.
Components: Profile form fields (name, date of birth, height, weight, occupation, phone number, complaints, headshot upload), Google Calendar integration, and a section for COVID-19 resources.

Physician Dashboard

Description: A dashboard for physicians to manage patient profiles, view and edit patient details, and update appointments.
Components: List of patient profiles, editable patient details, appointment management (Google Calendar integration), and prescription reminder settings.

COVID-19 Resources Page:

Description: A dedicated page providing up-to-date information and precautions regarding COVID-19.
Components: Display of the latest COVID-19 updates and precautions using the Open Disease Data API.

Locate Page:

Description: A page to help patients find directions to the clinic using Google Maps.
Components: Embedded Google Map with directions to the clinic.


AI Chatbot Page (Stretch):

Description: A conversational interface for patients to interact with an AI chatbot for health diagnosis.
Components: Chat interface, integration with Infermedica API for symptom checking and patient triage.




Data Model
Database: PostgreSQL using Prisma ORM for managing the database schema and interactions.

User Table:**

Fields: id, firstName, lastName, email, password, role, createdAt, updatedAt
Relationships:
One-to-One with Patient Profile Table: A user can have one patient profile.
One-to-One with Physician Profile Table: A user can have one physician profile.
One-to-Many with Notification Table: A user can receive multiple notifications.
One-to-Many with Appointment Table (as a patient or physician): A user can have multiple appointments.

Patient Profile Table:

Fields: id, userId, dateOfBirth, placeOfBirth, height, weight, occupation, phone, complaints, headshotUrl, calendarId, createdAt, updatedAt
Relationships:
One-to-One with User Table: Each patient profile is associated with a single user.
One-to-Many with Appointment Table: A patient can have multiple appointments with physicians.
One-to-Many with Calendar Table: A patient can have multiple calendar events.

Physician Profile Table:

Fields: id, userId, specialization, phone, createdAt, updatedAt
Relationships:
One-to-One with User Table: Each physician profile is associated with a single user.
One-to-Many with Appointment Table: A physician can have multiple appointments with patients.

Appointment Table:**

Fields: id, patientId, physicianId, title, description, startTime, endTime, createdAt, updatedAt
Relationships:
Many-to-One with Patient Profile Table: Each appointment is associated with one patient.
Many-to-One with Physician Profile Table: Each appointment is associated with one physician.

Notification Table:

Fields: id, userId, message, read, createdAt, updatedAt
Relationships:
Many-to-One with User Table: Each notification is associated with one user.

Calendar Table:**

Fields: id, patientId, eventTitle, eventDescription, eventStartTime, eventEndTime, createdAt, updatedAt
Relationships:
Many-to-One with Patient Profile Table: Each calendar event is associated with one patient.


Server Endpoints
Authentication Endpoints

POST /api/auth/signup: User signup
Parameters: firstName, lastName, email, password, role

Patient Endpoints

GET /api/patients/
: Get patient profile by ID
POST /api/patients: Create or update patient profile
Parameters: userId, dateOfBirth, placeOfBirth, height, weight, occupation, phone, complaints, headshotUrl, calendarId
PATCH /api/patients/
/calendar: Update patient's calendar
Parameters: calendarData (Details of the calendar updates made by the physician)

Physician Endpoints

GET /api/physicians/
: Get physician profile by ID
POST /api/physicians: Create or update physician profile
Parameters: userId, specialization, phone

Appointment Endpoints:

GET /api/appointments: Get all appointments
POST /api/appointments: Create a new appointment
Parameters: patientId, physicianId, title, description, startTime, endTime
PUT /api/appointments/
: Update appointment by ID

Notification Endpoints:

GET /api/notifications: Get all notifications for the logged-in user
POST /api/notifications: Create a new notification
Parameters: userId, message
PUT /api/notifications/
: Mark notification as read


Navigation




Project Requirements
Based on the Project Guide, here is how Synchronize will fulfill each of the base project requirements:

GO BEYOND CODEPATH: TECHNICAL CHALLENGES
The Web App  provides multiple opportunities to solve technical challenges. (However they are yet to be confirmed)

DATABASE & API INTEGRATION
The Web App interacts with a database and integrates with at least one API that you didn’t learn about in CodePath – free APIs only.

Database: 
Using PostgreSQL for storing user profiles, appointments, and other data, in conjunction with Prisma ORM for object data modeling and database management.

APIs:
Google Calendar API: For embedding and managing appointment calendars.
Google Maps API: For the locate page to provide directions to the clinic.
Open Disease Data API: For updating COVID-19 resources and precautions.
Infermedica API (Stretch feature): For the AI chatbot integration.

USER AUTHENTICATION
You can log in/log out of the Web App as a user. You can sign up with a new user profile.

Implementing a login/signup system with role-based access for patients and physicians. After login/signup, users are redirected to the landing page containing a welcome message (e.g., "Welcome, [First Name]").

VISUALS & INTERACTIONS
The Web App will have multiple views, interesting cursor interaction, demonstrates at least one component with complex visual styling, and uses a loading state to create visual polish.

Multiple Views: The Web App will include multiple pages such as the landing page, patient profile page, physician dashboard, COVID-19 resources, and locate page.
Interesting Cursor Interaction: Implementing custom cursor styles and animations (e.g., changing cursor to a hand icon over editable fields, ripple effects on buttons).
Custom Visual Styling: Creating unique UI components such as custom buttons, forms, and profile cards with tailored CSS styling.
Loading State: Using loading spinners or progress bars during data fetching and submission processes to enhance user feedback.



Technical Challenges
For your project, you should demonstrate that you can apply what you’ve learned so far and expand on that knowledge to write code and implement features that go beyond the scope of the projects you worked on during CodePath.

Based on the general idea and direction of your project requirements, your intern manager will create at least two (2) Technical Challenges for you. This section is all about explaining what they are and how you’re planning to tackle them - you’ll work together with your manager to fill it out. 

Technical Challenge #1 - [Name/Small Description]
What
What problem are you solving, and what parts go beyond what you learned in CodePath? 
How
Explain in words how you’ll solve this problem. 

You’re encouraged to expand on this section with pseudo-code, links to external frameworks, architecture / design diagrams, anything that you can use to explain this to others!
Technical Challenge #2
What
How

Database Integration
I will be using Postgres along with the Prisma (ORM) tool.

External APIs
Google Calendar API: For embedding and managing appointment calendars.
Google Maps API: For the locate page to provide directions to the clinic.
Open Disease Data API: For updating COVID-19 resources and precautions.
Infermedica API (Stretch feature): For the AI chatbot integration.

Authentication
[Describe how user authentication is handled for your project, including logging in and signing up. Also describe any kind of cookie / session management you’re doing and how you’re implementing it, and how this affects navigation between different screens by the same user.]

Visuals and Interactions

Interesting Cursor Interaction: 
When a patient hovers over editable profile fields, the cursor changes to a hand icon.
Use JavaScript to add a ripple effect when buttons are clicked, giving visual feedback to the user.
UI Component with Custom Visual Styling: 
Design custom buttons with a unique color scheme and rounded edges to match the clinic's branding.
Create a visually appealing profile card for patients, including their headshot, name, and contact information, styled with custom CSS.
Loading State: 
Implement a loading spinner that appears when data is being fetched from the database, such as when loading patient profiles or updating appointments.
Display a progress bar at the top of the page during data submission processes, ensuring users know their action is being processed.

Timeline
Project execution will start in Week 4 of MU. Based on the previously defined requirements, user stories and technical challenges, use the following table to scope out and plan a timeline for deliverables over Week 4 - 9. You can be as detailed as you need, ranging from simply mentioning the user stories, or dividing them into sub-tasks.

You are free to modify the table, add / remove rows or columns, whatever fits your style! The important thing here is that you focus and prioritize certain aspects of your project so you don’t get behind and are ready to deliver the MVP - remember your required features should be code complete before the end of Week 8, including both technical challenges!

We also encourage you to leverage project tracking tools such as GitHub Issues or Meta’s internal Tasks / GSD tooling to keep manage individual units of work.

MU Week
Project Week
Focus
User Stories
4
1
Focus on the components that will serve as the skeleton of your project. You will probably be using most of what you learned in CodePath to set up things like the client and server repositories, initial routing, login / registration, creating a database with object models, etc.
Setup the repositories
Setup the pages and initial routing on the frontend.
Create a patient database + object model.
Stretch (if there’s time): work on user authentication and login
5
2
Week 5 and 6 should be where you focus on the specific requirements of your project.
Finish up authentication work from Week 4.
Setup feature to create a new and edit existing patient profile.
Pull information from Open Disease Data API for Covid-19 resources and Google Maps API for location services.
6
3
By this point, you should be getting started with your technical challenges as well.
Setup appointment making feature, getting and posting from calendar database.
Get started on Technical Challenge #1 (to be filled out later).
7
4
You should focus on finishing your MVP and core requirements. By this point, you should be done with at least one of your technical challenges.
Finish Technical Challenge #1.
Get started on Technical Challenge #2.
8
5
Continue work on finishing touches and stretch goals for your MVP. By this point, your core functionality and both TAPs should all be in place. It is also a good point to start working on stretch goals that could further expand on the functionality (and technical complexity) of your project.

This week you also have to submit your self-review, make sure you allocate enough time for this alongside your final submission for your project!
Finish Technical Challenge #2
Stretch: AI Chatbot
Write final self-review.
9
6
It’s time to show others what you have built! Work on a presentation and demo that you will present to other interns to showcase your work. You are also free to continue polishing and expanding on your project!
Polishing up UI/other features in the project.
10
7
For this week, we have a bunch of extra activities prepared to give you a quick dive of what it is to work at Meta. You will find activities around using internal tools and frameworks, and even committing code to our internal repositories.
Bootcamp tasks in Meta repos.




# DSAtool  
## Technical Manual

---

## Table of Contents

1. [Introduction](#1-introduction)  
   1.1. [Overview](#11-overview)  
   1.2. [Glossary](#12-glossary)

2. [System Architecture](#2-system-architecture)  
   2.1. [User Browser](#21-user-browser)  
   2.2. [Django Web Application](#22-django-web-application)  
   2.3. [SQLite Database](#23-sqlite-database)  
   2.4. [Static Files and Libraries](#24-static-files-and-libraries)  
   2.5. [Deployment and Hosting](#25-deployment-and-hosting)

3. [High-Level Design](#3-high-level-design)  
   3.1. [Overview of Components](#31-overview-of-components)  
   3.2. [High-Level Diagrams](#32-high-level-diagrams)

4. [Problems and Resolution](#4-problems-and-resolution)  
   4.1. [Animation Performance](#41-animation-performance)  
   4.2. [Browser Responsiveness Issues](#42-browser-responsiveness-issues)  
   4.3. [Collision of Animation and User Input](#43-collision-of-animation-and-user-input)  
   4.4. [Often Merge Conflicts](#44-often-merge-conflicts)  
   4.5. [PyScratch Drag-and-drop Inconsistency](#45-pyscratch-drag-and-drop-inconsistency)  
   4.6. [Unknown Developer Console Errors](#46-unknown-developer-console-errors)  
   4.7. [Database Inconsistencies](#47-database-inconsistencies)

5. [Installation Guide](#5-installation-guide)  
   5.1. [Prerequisites](#51-prerequisites)  
   5.2. [Installation Steps](#52-installation-steps)

---

## 1. Introduction

### 1.1. Overview
This technical manual presents the detailed design of DSAtool, reflecting both the initial design and the current implemented design. This system was developed to enhance the learning of data structures and algorithms (DSA) through interactive visualisation, algorithm simulation, and coding puzzles.

Since the initial design proposal, the system’s core architecture and key features — including the sorting algorithm visualiser, drag-and-drop coding environment (PyScratch), algorithm simulator (Become The Algorithm), and the side-by-side algorithm comparison — have been refined and expanded. The application is designed to be web-based, integrating a Django backend, a user-friendly front end, and various interactive components to create a comprehensive learning tool.

### 1.2. Glossary
- **DSA**: Data structures and algorithms.  
- **UI**: User Interface.  
- **Drag-and-drop**: A graphical user interaction where elements are selected with a mouse and moved to a new position.  
- **Django**: A high-level Python web framework used for the development of web-based applications.  
- **Front-end**: The client-facing portion of the application, encompassing HTML, CSS, and JavaScript.  
- **Back-end**: The server-side application logic, handling data access, authentication, and validation.  
- **SQLite**: A lightweight relational database used for storing user information and progress data, embedded within the Django application.  
- **Pyodide**: A Python interpreter that allows Python code to run directly in the browser.

---

## 2. System Architecture

**Figure 1 - System Architecture Diagram**
![High Level Diagram](./sys-arch.JPG)


The system architecture for DSAtool has largely retained the same foundational components as outlined in the Functional Specification, but a number of changes were introduced during implementation to ensure scalability, modularity, maintainability, and efficient data handling—particularly in regard to the PyScratch feature. Below is a high-level overview of the system architecture as it is completed:

### 2.1. User Browser
- Users interact with the web interface through a modern web browser such as Google Chrome.  
- JavaScript works in-browser to power many of the interactive features, such as the drag-and-drop interface found in PyScratch and the playbar controls found in the Visualiser.

### 2.2. Django Web Application
- Serves as the core back-end framework.  
- Manages user authentication, handles the creation and retrieval of user data, and acts as an intermediary between the client and the database and static files.  
- Generates and returns the HTML pages along with dynamic data when required.

### 2.3. SQLite Database
- Stores user credentials, profile information, and learning progress.  
- This allows users to track their progress for both **Become The Algorithm** and **PyScratch**.  
- Contained in the Django back-end, allowing for easy retrieval of updated user data.

### 2.4. Static Files and Libraries
- Also found within the Django back-end.  
- A set of static assets (CSS stylesheets, images, and JavaScript files) are served by Django.  
- Notably, it contains files that use the Pyodide interpreter to enable Python code execution directly in the browser for the PyScratch feature.

### 2.5. Deployment and Hosting
- The final system can be deployed on Heroku (as proposed in the Functional Specification) or on any compatible cloud platform.  
- The system requires minimal resource allocation given the lightweight nature of SQLite and the mostly client-side animations.

---

## 3. High-Level Design

The high-level design focuses on module interactions and core data flow. The system is divided into modular components, each responsible for specific functionalities. This section details how the final system is structured and communicates.

### 3.1. Overview of Components

1. **User Account Module**  
   - **Sign Up/Login/Logout**: Provides all user management activities. Uses Django’s authentication system with hashed passwords stored in SQLite.  
   - **Profile & Progress Tracking**: Displays relevant user details, including any recorded learning progress.

2. **Landing Page Module**  
   - **System Overview**: The landing page is the user’s first point of contact. It provides a high-level introduction to the Data Structures and Algorithms Learning Tool, outlining its core features and benefits.  
   - **Quick Access**: Offers prominent links to the three main features of the project — Visualiser, Become The Algorithm, and PyScratch. Also has links to profile, sign in, and the dev blog.  
   - **Navigation Hub**: Serves as a central navigation point, allowing both registered and unregistered users to easily jump between the key modules.

3. **Visualiser Module**  
   - **Data Structure Creation**: Users can specify custom values to populate the array with.  
   - **Algorithm Visualiser**: Uses JavaScript and CSS to animate sorting algorithm execution.  
   - **Playbar**: Offers users the ability to pause, slow down, and speed up single algorithm execution.  
   - **Side-by-Side Comparison**: Executes two algorithms in parallel on the same input data, visually demonstrating performance differences.

4. **PyScratch Module**  
   - **Drag-and-drop coding environment**: Users build algorithmic puzzles from code blocks.  
   - **In-browser code generation**: As blocks are added to the code area, they can be run and the equivalent textual code is read by the interpreter, displaying any relevant visualisation or output.

5. **Become The Algorithm Module**  
   - **Manual algorithm execution**: The user “becomes the algorithm,” performing each algorithmic step according to their chosen algorithm.  
   - **Learning Reinforcement**: As they attempt to sort the data structure according to their chosen algorithm, feedback is displayed to the user. This approach helps users understand these algorithms at a more fundamental level.

6. **Database Module**  
   - **Data storage**: Stores user credentials and any progress data.  
   - **Django ORM**: Simplifies read/write operations with Python-based queries to SQLite.

7. **Static Files**  
   - **Static resources**: Includes the project’s CSS, JavaScript, images, and other front-end assets. These are served by Django’s static file handling system.  
   - **Integration with Modules**: All three of the main features rely on JavaScript, CSS, and images stored as static files to ensure consistent styling and behavior across the application.

### 3.2. High-Level Diagrams

This high-level diagram illustrates the typical flow when a user interacts with DSAtool. First, the user’s browser sends a request to the Django back-end (for example, to load a new visualization). Django then verifies any authentication needs, accesses or updates the SQLite database as required, and returns an HTML response or partial data to the client. Finally, JavaScript in the user’s browser handles all interactive and visual components such as animations, block-based coding, and manual algorithm simulations, providing a responsive, dynamic user experience.

**Figure 2 - High Level Diagram**
![High Level Diagram](./high-level.JPG)


---

## 4. Problems and Resolution

During the design and implementation phases, we encountered several challenges. Below are the major problems and their resolutions:

### 4.1. Animation Performance
- **Issue**: Initial visualiser animations lagged sometimes, causing delayed frames and inconsistent movement of bars.  
- **Resolution**: Separated the JavaScript logic from HTML files into static JavaScript files. This resulted in better performance and a more modular code base. Additionally, we reduced the frequency of DOM updates during animation.

### 4.2. Browser Responsiveness Issues
- **Issue**: The platform’s UI elements were inconsistent on much larger or much smaller screens than those used in development, leading to difficulty in usage and a lack of UI harmony.  
- **Resolution**: Introduced responsive CSS layouts for the affected pages, ensuring consistent UI elements regardless of screen size.

### 4.3. Collision of Animation and User Input
- **Issue**: Users could trigger the visualisation animation and then change the chosen algorithm or press the randomise button, causing overlapping operations and inconsistent state.  
- **Resolution**: Implemented strict state checks and disabled UI inputs while a visualisation animation was in progress, ensuring sequential and stable execution.

### 4.4. Often Merge Conflicts
- **Issue**: Multiple developers working on the same features at the same time led to frequent merge conflicts.  
- **Resolution**: Adopted a more structured development workflow using feature branches, significantly reducing merge conflicts.

### 4.5. PyScratch Drag-and-drop Inconsistency
- **Issue**: Converting the blocks to valid code occasionally produced syntax errors when blocks were placed in disallowed configurations.  
- **Resolution**: Introduced rule-based constraints to prevent certain block connections and added robust error handling to alert users of misplaced blocks.

### 4.6. Unknown Developer Console Errors
- **Issue**: Errors of unknown origin would appear in the console, sometimes causing algorithm execution to pause in the Visualiser.  
- **Resolution**: Implemented robust unit testing for the Visualiser’s JavaScript logic to pinpoint the source of errors. Expanded these tests to the rest of the code base and created a comprehensive test suite.

### 4.7. Database Inconsistencies
- **Issue**: Merging would occasionally overwrite the database, leading to inconsistencies in user profiles.  
- **Resolution**: Added the database to `.gitignore` and ensured that “makemigrations templates” was run after each change to `models.py` to properly manage database schema changes.

---

## 5. Installation Guide

This section provides a step-by-step guide to install and deploy DSAtool on a local machine for development or testing purposes.

### 5.1. Prerequisites
- **Python 3.8+**  
  Ensure Python is installed and added to your PATH. Verify by running `python --version`.  
- **pip**  
  Ensure you have pip installed to manage Python packages.  
- **Git**  
  Used to clone the repository directly from the project repository.  
- **Web Browser**  
  A modern browser (e.g., Chrome, Firefox, Edge) for testing and using the application.


### 5.2. Installation Steps

1. **Obtain the Project**  
   - Clone the project via Git using SSH or HTTPS from this link:  
     ```
     https://gitlab.computing.dcu.ie/donnelt6/2025-csc1049-tdonnelly-dsatool
     ```

2. **Install Django**  
   - Install Django using the command:
     ```
     pip install Django
     ```

3. **Apply Migrations and Initialize the Database**  
   - After completing steps 1 and 2, navigate to the project folder at:
     ```
     2025-csc1049-tdonnelly-dsatool\code\src\backend-django\dsatool
     ```
   - Run the following commands to set up the SQLite database:
     ```bash
     python manage.py makemigrations
     python manage.py makemigrations templates
     python manage.py migrate
     ```

4. **Run the development server**  
   - Still in the project folder (containing `manage.py`), start Django’s built-in server using the command:
     ```bash
     python manage.py runserver
     ```
   - By default, the application will be accessible at:
     ```
     http://127.0.0.1:8000/
     ```

You should now have DSAtool installed locally and are ready for use.


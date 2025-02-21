# Introduction

**Table of Contents**  
1. [Landing Page](#landing-page)  
2. [Visualiser](#visualiser)  
3. [PyScratch](#pyscratch)  
4. [Become The Algorithm](#become-the-algorithm)  
5. [Navigation Bar](#navigation-bar)  
6. [Profile, Register, Sign in, Log out](#profile-register-sign-in-log-out)  
7. [FAQs and Support](#faqs-and-support)

---

## Introduction

![Figure 1 - Landing Page Header](./hero.JPG)  
*Figure 1 - Landing Page Header*

This is a user manual for **DSAtool**, a data structures and algorithms (DSA) learning tool aimed at coders who are interested in learning DSA in a visual and interactive environment. This manual is intended for users of all technical levels. It provides step-by-step instructions on using the system’s major components, including the landing page, visualiser, PyScratch, and Become The Algorithm features.

---

## Landing Page

![Figure 2 - Landing Page](./landing.JPG)  
*Figure 2 - Landing Page*

The landing page serves as the start point for any user visiting the site. It clearly informs the user of the purpose of the site, the intended user, and the features available. In the top right corner of the landing page, a profile icon is displayed. This highlights the ability to create and view a profile within the site. 

- If a user clicks this icon while logged in, they will be directed to their profile page.  
- Conversely, if the user is logged out, they will be redirected to a page where they can register / log in.

Also found in the top right corner is a link to the devblog, containing general information about the project and its goal, alongside the technologies used to build the site and a timeline highlighting development stages.

At a focal point on the landing page are three large, uniquely colored banners. Each banner provides a brief description of one of the three main features of the site and contains a link to access that feature. The three possible branching points from these banners are:

### 1.1 Visualiser
- Watch the execution of various sorting algorithms, control their execution speed, and compare two algorithms side by side.

### 1.2 PyScratch
- Build data structures and algorithms in an interactive drag and drop coding interface.

### 1.3 Become The Algorithm
- Step inside the mind of the algorithm and sort arrays according to the rules of said algorithm.

---

## Visualiser

### 2.1 Single Visualiser

![Figure 3.1 - Single Visualiser](./visualiser.JPG)  
*Figure 3.1 - Single Visualiser*

Upon clicking the visualiser on the landing page, you are greeted with the screen above.

Four main components comprise the visualiser (as illustrated by the arrows in the figure):

1. **Algorithm heading and arrow controls**  
   - The algorithm heading displays the currently selected algorithm.  
   - The arrows allow the user to change which algorithm they would like to select.

2. **Bars**  
   - These are a visual representation of the data structure (array).  
   - They dynamically change based on user input and move during the sorting process. Key bars are highlighted during swaps or changes.

3. **Bar controls**  
   - **Text Box**: Allows a user to enter custom values for the array (up to 15 values, max size = 200). Values must be separated by commas.  
   - **Randomise**: Randomises the array values.  
   - **Unsort**: Returns the bars to their original order following a sort.  
   - **Sort**: Sorts the array depending on the chosen algorithm.

4. **Playbar**  
   - Provides speed and pause/play controls for the sorting animation.  
   - Also contains a button that links to a page for side-by-side comparison of two algorithms.

From left to right on the playbar:

- **Double chevron left**: Slows down the algorithm to 0.25× speed.  
- **Single chevron left**: Slows down the algorithm to 0.5× speed.  
- **Reset button**: Returns speed to 1× and resumes execution at 1× speed if paused.  
- **Pause button**: Pauses the algorithm.  
- **Play button**: Resumes at the speed specified before pause.  
- **Single chevron right**: Sets speed to 1.5×.  
- **Double chevron right**: Sets speed to 2×.  
- **Compare button**: Links to the compare visualiser page.

---

### 2.2 Compare Visualiser

![Figure 3.2 - Compare Visualiser](./compare.JPG)  
*Figure 3.2 - Compare Visualiser*

The compare visualiser allows you to view the simultaneous execution of two chosen algorithms.

- Users can change algorithms via the arrows. The two chosen algorithms **cannot** be the same.  
- Users can enter up to 10 custom values via a text input box. Both algorithms operate on the same array of values.  
- The time taken to sort in milliseconds is displayed below each set of bars. A tooltip clarifies that both algorithms are slowed down by the same amount to keep the sorting process visible.  
- At the bottom middle of the screen, **Randomise**, **Unsort**, and **Sort** buttons are available with the same functionality as in the single visualiser, except they apply to both arrays simultaneously.

---

## PyScratch

![Figure 4 - PyScratch](./pyscratch.JPG)  
*Figure 4 - PyScratch*

PyScratch is an interactive drag and drop coding interface. It can be accessed via the large banner on the landing page or the link on the navigation bar. Upon accessing PyScratch, users see an alert asking if they would like a brief tutorial. 

- **New users** are recommended to complete this tutorial to understand the layout and functionality.  
- If a user clicks "No," they can re-do the tutorial later by clicking the blue question mark in the top right corner.

The goal of PyScratch is to let users drag code blocks from the Block Palette into the Code Area to complete data structures and algorithms puzzles of increasing complexity. Users may also experiment with custom code blocks.

The interface can be broken down into six main areas:

1. **Block Palette**  
   - Contains the blocks of code needed to solve each puzzle.  
   - Includes a text box for entering custom code for custom blocks.

2. **Puzzle Header**  
   - Displays the current puzzle.  
   - Includes a button to check if the code in the Code Area solves the puzzle.  
   - Upon progressing to the next puzzle, the Block Palette updates accordingly.

3. **Code Area**  
   - Where blocks of code are dragged.  
   - These blocks are translated into actual Python code by the site’s embedded interpreter.

4. **Code Buttons**  
   - **Run Code**: Attempts to execute the code in the Code Area.  
   - **Clear Code**: Clears all code blocks from the Code Area.  
   - **Reset Puzzles**: Resets puzzle progress back to puzzle 1.

5. **Data Visualisation**  
   - Allows users to visualise certain aspects of built data structures (e.g., array indices and values).  
   - Updates when **Run Code** is clicked.

6. **Code Output**  
   - Displays any output of the code in the Code Area after clicking **Run Code**.  
   - Also displays errors if they occur.

---

## Become The Algorithm

![Figure 5 - Become The Algorithm](./become-the-algorithm.JPG)  
*Figure 5 - Become The Algorithm*

**Become The Algorithm** is an interactive simulation feature that puts users in the shoes of a chosen algorithm.  

- The user can select their chosen algorithm using arrow controls.  
- Users may click the arrow icon to view brief information about each algorithm, including a description and its time complexity.

Once the algorithm is chosen:

1. **Choose a difficulty**: Easy, Medium, or Hard — each increasing the number of bars.  
2. **Randomise or Reset**: Users can shuffle bars or reset them to their original positions.  
3. **Perform the sort**:  
   - Drag the bar you believe should move first to its new position, following the rules of the chosen algorithm.  
   - A success/failure message will appear to guide you.  
   - If stuck, the **Hint** button highlights the two bars to be moved next.  
   - Continue until bars are sorted (success) or until a wrong move is made (progress resets).

---

## Navigation Bar

![Figure 6 - The navigation bar](./nav-bar.JPG)  
*Figure 6 - The navigation bar*

Above is the navigation bar displayed along the top of all pages on DSAtool, except for the landing page (which has its own unique navigation bar). Its purpose is to provide users with easy access to all areas of the website.

- The **left side** shows the name of the project, which also links to the landing page.  
- The **right side** consists of five buttons:  
  1. **Home**: Links to the landing page.  
  2. **PyScratch**: Links to the PyScratch feature.  
  3. **Visualiser**: Links to the single visualiser page.  
  4. **Become The Algorithm**: Links to that feature.  
  5. **Profile Icon**: 
     - If signed in, redirects to the profile page.  
     - If not signed in, redirects to the login page (which also links to registration).

---

## Profile, Register, Sign In, Log Out

The Profile section serves as a personal hub for DSAtool users, providing access to account management and progress tracking. It is accessed via the profile icon in the top-right corner of the navigation bar.

### 6.1 Profile Page
Once signed in, clicking the profile icon redirects to a personalized profile page, which includes:

- **Progress Tracker**: Displays user progress in Become The Algorithm and PyScratch.  
- **User Information**: Displays profile info such as username.  
- **Log Out Button**: Allows users to securely end their session.

### 6.2 Register and Sign In
For users without an account, accessing the profile icon while logged out redirects them to the authentication interface:

- **Sign In Form**: Prompt for existing users.  
- **Registration Link**: For new users to create an account.

**Registration** requires:  
- A unique username  
- A valid password

### 6.3 Log Out
Accessible from both the profile page and navigation bar:

- Immediately ends the current user session.  
- Redirects the user to the login page.

---

## FAQs and Support

![Figure 7.1 - Devblog “About” section](./about-section.JPG)  
*Figure 7.1 - Devblog “About” section*

Above is an extract from the devblog, accessible via the navigation bar on the landing page. It contains general information about the project — similar to a Frequently Asked Questions (FAQ) section — and includes:

- Information about the project’s features  
- The overall goal of the project

![Figure 7.2 - Devblog timeline](./timeline.JPG)  
*Figure 7.2 - Devblog timeline*

The devblog timeline can also be found here, highlighting different stages of the project’s development.

---

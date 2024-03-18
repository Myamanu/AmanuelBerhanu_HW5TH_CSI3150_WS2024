# Quiz App Demo

This project is a simple quiz application built with [HTML](https://www.w3schools.com/Html/), [CSS](https://www.w3schools.com/Css/), and [JavaScript](https://www.w3schools.com/Js/).

# Problem Statement
- The [Quiz App](https://martysen.github.io/DemoQuizApp/) is an innovative web-based platform that revolutionizes the way users engage with quizzes. It’s not just a test of knowledge; it’s a race against time. With each question timed at 15 seconds, the app challenges users to think quickly and accurately. It’s designed to cater to a wide audience, from students looking to test their knowledge to trivia enthusiasts seeking a quick challenge. The app’s core lies in its simplicity and the instant gratification of knowing whether you’ve answered correctly. It’s a tool for learning, self-assessment, and entertainment, all rolled into one. The Quiz App stands out by providing a seamless user experience, from the moment the <kbd> Start Quiz </kbd> button is clicked to the display of the final score. It’s an engaging way to learn and a fun twist on traditional quizzes, pushing the boundaries of what educational tools can be. This app is a step towards making learning addictive and accessible to everyone, everywhere.

## Features

- <kbd> Start Quiz </kbd> button to begin the quiz.
- Information box with rules and instructions for the quiz.
- Quiz box with timed questions with a 15-second limit
- Dynamic question and option generation from a JavaScript file, and navigation.
- Countdown timer for each question and question number tracking and display
- Immediate feedback on answer selection with visual cues for correct and incorrect answers.
- Result box to display the final score and options to replay or quit the quiz.

## Technologies Used

- [HTML](https://www.w3schools.com/Html/)
- [CSS](https://www.w3schools.com/Css/)
- [JavaScript](https://www.w3schools.com/Js/)

## Directory Structure
The Quiz App is divided into several directories and files, each serving a specific purpose:

- **Root Directory:** Contains the main HTML file `index.html` and two subdirectories for CSS and JavaScript files.
- **CSS Directory:** Holds the `style.css` file, which contains all the styling rules for the application.
- **JavaScript Directory:** Contains two JavaScript files, `questions.js` for storing quiz questions and `quizApp.js` for the main quiz logic.

## Setup

To set up this project, first, clone the repository to your local machine. Then, open the index.html file in a web browser. Alternatively, you can deploy the project to a GitHub page and access it through the provided link for a similar outcome.

## Usage

1. Click on the <kbd> Start Quiz </kbd> button to begin.
2. Read the rules in the information box and click <kbd> Continue </kbd> button to proceed.
3. Answer the questions within the given time limit and use <kbd> Next Que </kbd> to move on to the next question.
4. After answering all questions, your score will be displayed in the result box.
5. You can choose to replay the quiz or quit.
## How Files Are Linked and Work Together
1. **`index.html`**
    + The `index.html` file is the entry point of the Quiz App. It includes links to the CSS and JavaScript files, ensuring that the styling and functionality are applied to the app.
The HTML file structures the content of the app, defining areas like the start button, info box, quiz box, and result box.
2. **`style.css`**
    + The style.css file is linked within the `index.html` head section using the `<link>` tag. It applies visual styles to the HTML elements, such as colors, layouts, and fonts. CSS selectors target HTML elements by class or id, and apply styles defined within the `style.css` file.
3. **`questions.js` and `quizApp.js`**
    + Both JavaScript files are linked at the end of the `index.html` head section using the `<script>` tag with the `defer` attribute, which ensures that the scripts are executed after the HTML document has been parsed.
    + The `questions.js` defines an array of question objects, each containing a question, options, and the correct answer.
    + The `quizApp.js` contains the main logic of the app. It interacts with the HTML document by selecting elements and manipulating them based on user actions, such as starting the quiz, selecting answers, and displaying results.

## Interaction Flow

#### Starting the Quiz:  
  -  When the user clicks the <kbd> Start Quiz </kbd> button, `quizApp.js` responds by displaying the quiz instructions. Below these instructions, it provides buttons for the user to either quit or continue with the quiz.

#### Displaying Questions: 
  - As the user proceeds, `quizApp.js` fetches questions and their options from `questions.js` and displays them one by one.

#### User Interaction: 
  - The user interacts with the quiz by selecting answers. The `quizApp.js` processes these interactions, provides feedback, and updates the score.

#### Ending the Quiz: 
  - Once the user completes the quiz, `quizApp.js` presents the final score and options to restart or quit the quiz.

## Codebase Explanation

 ### 1. `index.html`
The `index.html` file serves as the entry point for the Quiz App. It structures the content and links the external CSS and JavaScript files necessary for the app's functionality and styling.

#### 1.1 Key Sections of `index.html`

- **Document Declaration and Head Section:**
This section sets up the document type and the metadata for the HTML document. It includes the title of the app and links to the external CSS file for styling. The Font Awesome script is used for icons throughout the app, and the JavaScript files are loaded with the defer attribute to ensure they execute after the document has been parsed.

  ```html
  <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz App Demo</title>

    <!-- CSS FILE -->
    <link rel="stylesheet" href="css/style.css">
    <!-- This is my personal font awesome kit code. you will have to add your own after you register with email-->
    <script src="https://kit.fontawesome.com/4a4f4b55b0.js" crossorigin="anonymous"></script>

     <!-- Add questions list -->
    <script src="js/questions.js" defer></script>

    <!-- Main logic of the app -->
    <script src="js/quizApp.js" defer></script>
</head>
```

- **Start Button:**
This div contains the button that users click to start the quiz. It’s styled to be visually appealing and is the first interactive element users engage with.
```HTML
**Code:**
<!-- Quiz START Button -->
<div class="start_btn"><button>Start Quiz</button></div>
```

- **Instruction Box:**
The instruction box provides users with the rules of the quiz and contains buttons for starting or exiting the quiz. It appears after the user clicks the <kbd> Start Quiz </kbd> button.


**Code:**
```HTML
<!-- Instruction box wrapper -->
    <div class="info_box">
        <div class="info-title"><span>Some Rules of this Quiz</span></div>
        <div class="info-list">
            <div class="info">1. You will have only <span>15 seconds</span> per each question.</div>
            <div class="info">2. Once you select your answer, it can't be undone.</div>
            <div class="info">3. You can't select any option once time goes off.</div>
            <div class="info">4. You can't exit from the Quiz while you're playing.</div>
            <div class="info">5. You'll get points on the basis of your correct answers.</div>
        </div>
        <div class="buttons">
            <button class="quit">Exit Quiz</button>
            <button class="restart">Continue</button>
        </div>
    </div>

```

- **Quiz Box:**
The quiz box is the main area where questions are displayed. It includes a header with a timer, a section for the current question and answer options, and a footer for navigation.

**Code:**
```HTML
<!-- Quiz Box -->
    <div class="quiz_box">
        <header>
            <div class="title">Demo Quiz App in JavaScript</div>
            <div class="timer">
                <div class="time_left_txt">Time Left</div>
                <div class="timer_sec">15</div>
            </div>
            <div class="time_line"></div>
        </header>
        <section>
            <div class="que_text">
                <!-- Insert questions from ./js/questions.js -->
            </div>
            <div class="option_list">
                <!-- Insert options to questions from ./js/questions.js -->
            </div>
        </section>
        <!-- footer of Quiz Box -->
        <footer>
            <div class="total_que">
                <!-- insert Question Count Number dynamically from JavaScript App logic -->
            </div>
            <button class="next_btn">Next Que</button>
        </footer>
    </div>
```

- **Result Box:**
After the quiz is completed, the result box displays the user’s score and provides options to replay the quiz or exit.

**Code:**
```HTML
<!-- Result Box -->
<div class="result_box">
    <!-- Result Box -->
    <div class="result_box">
        <div class="icon">
            <i class="fas fa-crown"></i>
        </div>
        <div class="complete_text">You've completed the Quiz!</div>
        <div class="score_text">
            <!-- insert dynamic user score as Result from JavaScript -->
        </div>
        <div class="buttons">
            <button class="restart">Replay Quiz</button>
            <button class="quit">Quit Quiz</button>
        </div>
    </div>
```
Each of these sections is styled by the style.css file and made interactive through the questions.js and quizApp.js files. 

### 2. `style.css`
The `style.css` file contains all the styling rules for the Quiz App, defining how elements look and feel. It includes styles for the layout, colors, fonts, and transitions.

#### 2.1 Key Sections of `style.css`
- **Typography and Basic Layout:**
This section sets up the base typography and layout styles. It imports the [Poppins font family](https://fonts.google.com/specimen/Poppins?query=poppin) from Google Fonts and applies it to all elements. The body rule sets the background color for the entire app, and the ::selection rule changes the text selection color.

```css
/* Importing Google fonts */
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@200;300;400;500;600;700&display=swap');

/* Universal base styles */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Poppins', sans-serif;
}

/* Body background */
body {
    background: #a020f0;
}

/* Text selection color */
::selection {
    color: #fff;
    background: #a020f0;
}
```

- **Quiz Components Styling:**
This section defines the styles for the main components of the quiz: the start button, info box, quiz box, and result box. It centers these elements on the screen and adds a shadow for depth. The '.activeInfo', '.activeQuiz', and '.activeResult' classes are used to make the elements visible and interactive when active.

```CSS
/* Common styles for start button, info box, quiz box, and result box */
.start_btn, .info_box, .quiz_box, .result_box {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
}

/* Active state styles for info box, quiz box, and result box */
.info_box.activeInfo, .quiz_box.activeQuiz, .result_box.activeResult {
    opacity: 1;
    z-index: 5;
    pointer-events: auto;
    transform: translate(-50%, -50%) scale(1);
}

/* Start button styling */
.start_btn button {
    font-size: 25px;
    font-weight: 500;
    color: #a020f0;
    padding: 15px 30px;
    outline: none;
    border: none;
    border-radius: 5px;
    background: #fff;
    cursor: pointer;
}
```

- **Interactive Elements and Feedback:**
This section styles the options that users can click on during the quiz. It includes a hover effect to improve user interaction and visual feedback styles for correct and incorrect answers. The '.disabled' class prevents further interaction with options after an answer is selected.

```CSS
/* Option list and options styling */
.option_list .option {
    background: aliceblue;
    border: 1px solid #84c5fe;
    border-radius: 5px;
    padding: 8px 15px;
    font-size: 17px;
    margin-bottom: 15px;
    cursor: pointer;
    transition: all 0.3s ease;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

/* Hover effect for options */
.option_list .option:hover {
    color: #601391;
    background: #cce5ff;
    border: 1px solid #b8daff;
}

/* Correct and incorrect answer feedback styles */
.option_list .option.correct {
    color: #155724;
    background: #d4edda;
    border: 1px solid #c3e6cb;
}

.option_list .option.incorrect {
    color: #721c24;
    background: #f8d7da;
    border: 1px solid #f5c6cb;
}

/* Disabled state for options */
.option_list .option.disabled {
    pointer-events: none;
}
```

- **Result Box and Buttons:**
The result box and buttons are styled to display the user’s score at the end of the quiz. The '.buttons' class styles the <kbd> replay </kbd> and <kbd> quit </kbd> buttons, including hover effects to indicate interactivity.

```CSS
/* Result box styling */
.result_box {
    background: #fff;
    border-radius: 5px;
    display: flex;
    padding: 25px 30px;
    width: 450px;
    align-items: center;
    flex-direction: column;
    justify-content: center;
    transform: translate(-50%, -50%) scale(0.9);
    opacity: 0;
    pointer-events: none;
    transition: all 0.3s ease;
}

/* Button styling for replay and quit */
.buttons button {
    margin: 0 10px;
    height: 45px;
    padding: 0 20px;
    font-size: 18px;
    font-weight: 500;
    cursor: pointer;
    border: none;
    outline: none;
    border-radius: 5px;
    border: 1px solid #a020f0;
    transition: all 0.3s ease;
}

/* Hover effects for buttons */
.buttons button.restart:hover {
    background: #8304d1;
}

.buttons button.quit:hover {
    color: #fff;
    background: #8604d6;
}
```
> [!NOTE]
> This detailed explanation of the `style.css` file provides insight into how the Quiz App’s visual elements are styled and how they interact with the user. 


### 3. `questions.js`
The `questions.js` file is crucial for the Quiz App as it contains the data structure for the quiz questions and answers.

#### 3.1 Key Section of `questions.js`
- **Structure of the Questions Array:**
It is structured as an array of objects, where each object represents a single question with its associated options and the correct answer.
```javascript
// Array of question objects
let questions = [
    {
        numb: 1,
        question: "What does HTML stand for?",
        answer: "Hyper Text Markup Language",
        options: [
            "Hyper Text Preprocessor",
            "Hyper Text Markup Language",
            "Hyper Text Multiple Language",
            "Hyper Tool Multi Language"
        ]
    },
    // More question objects...
];
```
> [!IMPORTANT]
> This array holds multiple question objects. Each object has a 'numb' property indicating the question number, a 'question' property containing the question text, a 'answer' property for the correct answer, and an 'options' array with all possible answers.

### 4. `quizApp.js`
The `quizApp.js` file is the heart of the Quiz App, where the main logic and functionality resides. It manages the quiz flow, handles user interactions, and updates the UI based on the user’s actions and quiz progress.

#### 4.1 Key Sections of `questions.js`
- **Initialization and Event Listeners:**
This section sets up the initial state of the quiz by selecting essential HTML elements using the 'document.querySelector' method. These elements are then used to manage the quiz’s state and respond to user interactions. Event listeners are attached to buttons like the <kbd> Start Quiz </kbd> button. When clicked, it triggers the display of the information box by adding the 'activeInfo' class, making it visible to the user. Also, adds event listeners to <kbd> Exit </kbd>, and <kbd> Continue </kbd> buttons to control the quiz flow.
```javascript
// Selecting all required elements
const start_btn = document.querySelector(".start_btn button");
const info_box = document.querySelector(".info_box");
const exit_btn = info_box.querySelector(".buttons .quit");
const continue_btn = info_box.querySelector(".buttons .restart");
// ...additional selections goes here

// if startQuiz button clicked
start_btn.addEventListener("click", (e) => {
  info_box.classList.add("activeInfo"); //show info box
});

// if exitQuiz button clicked
exit_btn.addEventListener("click", (e) => {
  info_box.classList.remove("activeInfo"); //hide info box
});

// if continueQuiz button clicked
continue_btn.addEventListener("click", (e) => {
  info_box.classList.remove("activeInfo"); //hide info box
  quiz_box.classList.add("activeQuiz"); //show quiz box
  showQuetions(0); //calling showQestions function
  queCounter(1); //passing 1 parameter to queCounter
  startTimer(15); //calling startTimer function
  startTimerLine(0); //calling startTimerLine function
});
```
- **Event Handlers for Quiz Navigation:**
In this section variables are declared to keep track of the quiz state, such as the time left for each question '(timeValue)' and the current question index '(que_count)'. Also, event listeners are added to the <kbd> Next </kbd>, <kbd> Restart </kbd>, and <kbd> Quit </kbd> buttons to allow the user to navigate through the quiz, restart it, or quit at any time. As an example, event handlers that set up for navigating through the question will trigger the quiz to proceed to the following question when the <kbd>Next Que </kbd> button clicked.
```JavaScript
// Variables to control quiz operations
let timeValue = 15;
let que_count = 0;
let que_numb = 1;
let userScore = 0;
// ...additional variables goes here

// if restartQuiz button clicked
restart_quiz.addEventListener("click", (e) => {
  quiz_box.classList.add("activeQuiz"); //show quiz box
  result_box.classList.remove("activeResult"); //hide result box
  timeValue = 15;
  que_count = 0;
  que_numb = 1;
  userScore = 0;
  widthValue = 0;
  showQuetions(que_count); //calling showQestions function
  queCounter(que_numb); //passing que_numb value to queCounter
  clearInterval(counter); //clear counter
  clearInterval(counterLine); //clear counterLine
  startTimer(timeValue); //calling startTimer function
  startTimerLine(widthValue); //calling startTimerLine function
  timeText.textContent = "Time Left"; //change the text of timeText to Time Left
  next_btn.classList.remove("show"); //hide the next button
});

// if quitQuiz button clicked
quit_quiz.addEventListener("click", (e) => {
  window.location.reload(); //reload the current window
});

// if Next Question button is clicked
next_btn.addEventListener("click", (e) => {
  //check if it does not exceed max questions
  if (que_count < questions.length - 1) {
    que_count++; //increment the que_count value
    que_numb++; //increment the que_numb value
    showQuetions(que_count); //calling showQestions function
    queCounter(que_numb); //passing que_numb value to queCounter
    clearInterval(counter); //clear counter
    clearInterval(counterLine); //clear counterLine
    startTimer(timeValue); //calling startTimer function
    startTimerLine(widthValue); //calling startTimerLine function
    timeText.textContent = "Time Left"; //change the timeText to Time Left
    next_btn.classList.remove("show"); //hide the next button
  } else {
    clearInterval(counter); //clear counter
    clearInterval(counterLine); //clear counterLine
    showResult(); //calling showResult function
  }
});
```

- **Quiz Operations:**
This section contains the core functions that manage the quiz questions and timer. The 'showQuestions' function is responsible for displaying the current question and its options. It dynamically updates the content based on the question index provided. Moreover, the 'startTimer' function manages the countdown for each question. It updates the UI to reflect the time remaining and handles the case when the time runs out. 

```JavaScript
// getting questions and options from array
// If you have lesser or more number of options you need to change this code
function showQuetions(index) {
  const que_text = document.querySelector(".que_text");

  //creating a new span and div tag for question and option and passing the value using array index
  // self exercise: re-write the following using backtick syntax for string in JS instead of concatenation operator
  let que_tag =
    "<span>" +
    questions[index].numb +
    ". " +
    questions[index].question +
    "</span>";
  let option_tag =
    '<div class="option"><span>' +
    questions[index].options[0] +
    "</span></div>" +
    '<div class="option"><span>' +
    questions[index].options[1] +
    "</span></div>" +
    '<div class="option"><span>' +
    questions[index].options[2] +
    "</span></div>" +
    '<div class="option"><span>' +
    questions[index].options[3] +
    "</span></div>";
  que_text.innerHTML = que_tag; //adding new (child) span tag inside que_tag
  option_list.innerHTML = option_tag; //adding new (child) div tag inside option_tag

  const option = option_list.querySelectorAll(".option");

  // set onclick attribute to all available options
  for (i = 0; i < option.length; i++) {
    option[i].setAttribute("onclick", "optionSelected(this)");
  }
}

// Function to control the timer
function startTimer(time) {
  counter = setInterval(timer, 1000);
  function timer() {
    timeCount.textContent = time; //change the value of timeCount with time value
    time--; //decrement the time value
    if (time < 9) {
      //if timer is less than 9
      let addZero = timeCount.textContent;
      timeCount.textContent = "0" + addZero; //add a 0 before time value
    }
    if (time < 0) {
      //if timer is less than 0
      clearInterval(counter); //clear counter
      timeText.textContent = "Time Off"; //change the time text to time off
      const allOptions = option_list.children.length; //get all option items
      let correcAns = questions[que_count].answer; //get correct answer from array
      for (i = 0; i < allOptions; i++) {
        if (option_list.children[i].textContent == correcAns) {
          //if there is an option which is matched to an array answer
          option_list.children[i].setAttribute("class", "option correct"); //add green color to matched option
          option_list.children[i].insertAdjacentHTML("beforeend", tickIconTag); //add tick icon to matched option
          console.log("Time Off: Auto selected correct answer.");
        }
      }
      for (i = 0; i < allOptions; i++) {
        option_list.children[i].classList.add("disabled"); //once user select an option then disabled all options
      }
      next_btn.classList.add("show"); //show the next button if user selected any option
    }
  }
}

```
- **Answer Validation, Scoring, and result display**
This section contains the core functions that manage the answer validation and results display. In particular, when a user selects an answer, the 'optionSelected' function validates the answer against the correct one and updates the score accordingly. It also provides visual feedback to the user. Furthermore, after the quiz is completed, the 'showResult' function calculates and displays the user’s final score. It also offers options to restart or quit the quiz. Plus, in this section, new div tags for right or wrong tick icons are created.
```JavaScript
// create new div tags for right or wrong tick icons
let tickIconTag = '<div class="icon tick"><i class="fas fa-check"></i></div>';
let crossIconTag = '<div class="icon cross"><i class="fas fa-times"></i></div>';

//if user clicked on option
function optionSelected(answer) {
  clearInterval(counter); //clear counter
  clearInterval(counterLine); //clear counterLine
  let userAns = answer.textContent; //getting user selected option
  let correcAns = questions[que_count].answer; //getting correct answer from array
  const allOptions = option_list.children.length; //getting all option items

  //if user selected option is equal to array's correct answer
  if (userAns == correcAns) {
    userScore += 1; //update total score value increment by 1
    answer.classList.add("correct"); //add green color to correct selected option
    answer.insertAdjacentHTML("beforeend", tickIconTag); //add tick icon to correct selected option
    console.log("Correct Answer");
    console.log("Your correct answers = " + userScore);
  } else {
    answer.classList.add("incorrect"); //add red color to correct selected option
    answer.insertAdjacentHTML("beforeend", crossIconTag); //add cross icon to correct selected option
    console.log("Wrong Answer");

    for (i = 0; i < allOptions; i++) {
      if (option_list.children[i].textContent == correcAns) {
        //if there is an option which is matched to an array answer
        option_list.children[i].setAttribute("class", "option correct"); //add green color to matched option
        option_list.children[i].insertAdjacentHTML("beforeend", tickIconTag); //add tick icon to matched option
        console.log("Auto selected correct answer.");
      }
    }
  }
  for (i = 0; i < allOptions; i++) {
    option_list.children[i].classList.add("disabled"); //once user select an option, disable all options
  }
  next_btn.classList.add("show"); //show the next button if user selected any option
}

// Function to show results
function showResult() {
  info_box.classList.remove("activeInfo"); //hide info box
  quiz_box.classList.remove("activeQuiz"); //hide quiz box
  result_box.classList.add("activeResult"); //show result box
  const scoreText = result_box.querySelector(".score_text");
  if (userScore > 3) {
    // if user scored more than 3
    //create a new span tag and pass the user score number and total question number
    let scoreTag =
      "<span>and congrats! , You got <p>" +
      userScore +
      "</p> out of <p>" +
      questions.length +
      "</p></span>";
    scoreText.innerHTML = scoreTag; //add new span tag inside score_Text
  } else if (userScore > 1) {
    // if user scored more than 1
    let scoreTag =
      "<span>and nice , You got <p>" +
      userScore +
      "</p> out of <p>" +
      questions.length +
      "</p></span>";
    scoreText.innerHTML = scoreTag;
  } else {
    // if user scored less than 1
    let scoreTag =
      "<span>and sorry , You got only <p>" +
      userScore +
      "</p> out of <p>" +
      questions.length +
      "</p></span>";
    scoreText.innerHTML = scoreTag;
  }
}
```
- **Progress Bar and question counter:**
These functions visualize the time left with a progress bar and update the question counter as the user progresses through the quiz. For instance, the 'startTimer' function manages the countdown for each question. It updates the UI to reflect the time remaining and handles the case when the time runs out.

```JavaScript
// Function to control the progress bar
function startTimerLine(time) {
    counterLine = setInterval(timer, 29);
  function timer() {
    time += 1; //upgrading time value with 1
    time_line.style.width = time + "px"; //increasing width of time_line with px by time value
    if (time > 549) {
      //if time value is greater than 549
      clearInterval(counterLine); //clear counterLine
    }
  }
}

// Function to update question counter
function queCounter(index) {
//creating a new span tag and passing the question number and total question
  let totalQueCounTag =
    "<span><p>" +
    index +
    "</p> of <p>" +
    questions.length +
    "</p> Questions</span>";
  bottom_ques_counter.innerHTML = totalQueCounTag; //adding new span tag inside bottom_ques_counter
}
```

> [!NOTE]
> This file orchestrates the entire quiz experience, from starting the quiz to displaying the final results. It ensures that the quiz is interactive and responsive to user actions.

## License

This project is open source and available under the [MIT License](LICENSE).

## Acknowledgments

- Font Awesome for icons
- Google Fonts for typography

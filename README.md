# quiz-cli

An interactive command-line quiz game for learning JavaScript.

## Overview

`quiz-cli` is a terminal-based quiz application built with Node.js. Users can select a quiz category and question count, answer numbered questions, receive immediate feedback and explanations, and review their final performance.

## Features

- Interactive terminal-based quiz experience
- Categories for:
  - JavaScript Basics
  - Node.js Fundamentals
  - General Programming
- Configurable question counts
- Fisher–Yates question shuffling
- Immediate answer feedback
- Explanations for questions
- Progress and score tracking
- Performance messages
- Review of incorrect answers
- Option to replay the quiz
- ANSI color and style helpers for terminal output
- Input validation for numbered choices and yes/no confirmations

## Prerequisites

- Node.js `18.0.0` or later

The project does not declare runtime dependencies and uses Node.js built-in functionality together with local project files.

## Installation and Setup

From the project directory, run:

```bash
npm install
```

There are currently no declared package dependencies, so no external runtime packages are installed by this command.

## Usage

Start the quiz with:

```bash
npm start
```

This runs:

```bash
node index.js
```

During the quiz, you can:

1. Select a category.
2. Select the number of questions.
3. Answer questions using numbered choices.
4. View immediate feedback and explanations.
5. Review your final score and incorrect answers.
6. Choose whether to play again.

Available question-count choices depend on the selected category:

- All questions
- Three questions, when the category contains at least three
- Five questions, when the category contains at least five

## Question Data

Quiz questions are stored in:

```text
data/questions.json
```

The data is organized by category. Each question contains:

- A question prompt
- Four answer options
- A zero-based index identifying the correct answer
- An explanation shown after answering

The currently included categories each contain five questions:

- JavaScript Basics
- Node.js Fundamentals
- General Programming

## Project Structure

```text
.
├── data/
│   └── questions.json   # Quiz categories and questions
├── src/
│   ├── colors.js        # ANSI color and style helpers
│   ├── input.js         # Terminal input and validation helpers
│   └── quiz.js          # Quiz flow, scoring, feedback, and results
├── index.js             # Application entry point
├── package.json         # Project metadata and npm scripts
└── README.md            # Project documentation
```

The `.DS_Store` file is repository metadata and is not part of the application.

## Technologies

- Node.js
- JavaScript
- ECMAScript modules
- Node.js built-in terminal input functionality
- Node.js built-in test runner
- JSON question data

The project uses ES modules through the `"type": "module"` setting in `package.json`.

## Testing

Run the configured test command with:

```bash
npm test
```

This invokes:

```bash
node --test
```

No test files are currently present in the repository, so the test command runs Node.js's test runner without repository-provided test cases.

## License

This project is licensed under the MIT License, as specified in `package.json`.

## Limitations and Notes

- The application is designed for interactive terminal use.
- No hosted demo or graphical user interface is provided in the repository.
- Quiz content must be maintained in `data/questions.json`.
- No external runtime services or databases are configured.
- No continuous integration workflow or deployment configuration is present.
- No contribution process or authorship details are defined in the repository.
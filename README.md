# Quiz CLI

An interactive command-line quiz game for learning and reviewing programming fundamentals.

## Overview

Quiz CLI is a Node.js ES module application that presents multiple-choice programming questions in the terminal. Users select a category, choose the number of questions, answer interactively, and receive a scored results summary with explanations and a review of incorrect answers.

The application loads its question data from `data/questions.json` and uses only Node.js built-in modules; there are no external runtime dependencies.

## Features

- Interactive terminal-based menus and prompts
- Three quiz categories:
  - JavaScript Basics
  - Node.js Fundamentals
  - General Programming
- Choice of all available questions, three questions, or five questions when supported by the selected category
- Randomized question order for each quiz
- Progress bar and question counter
- Immediate correct/incorrect feedback
- Explanations for questions
- Score percentage and performance feedback
- Incorrect-answer review at the end of a quiz
- Option to play multiple quizzes in one session
- ANSI-colored terminal output without an external color library

## Technology Stack

- **Language:** JavaScript
- **Runtime:** Node.js 18 or later
- **Module system:** ECMAScript modules (ESM)
- **Input handling:** Node.js built-in `readline` module
- **File access:** Node.js built-in `fs/promises`, `path`, and `url` modules
- **Question data:** JSON
- **Testing:** Node.js built-in test runner configuration

## Prerequisites

- Node.js `>=18.0.0`
- A terminal capable of displaying standard ANSI escape sequences for colored output

No database, environment variables, external services, or package installation from npm are required by the application.

## Project Structure

```text
.
├── data/
│   └── questions.json   # Quiz categories, questions, answer indexes, and explanations
├── src/
│   ├── colors.js        # ANSI color and text-style helpers
│   ├── input.js         # Readline interface and interactive prompt helpers
│   └── quiz.js          # Quiz class, scoring, shuffling, progress, and results logic
├── index.js             # Application entry point and main quiz loop
├── package.json         # Project metadata, scripts, and Node.js engine requirement
└── README.md            # Project documentation
```

## Installation and Setup

Clone the repository and enter the project directory:

```bash
git clone <repository-url>
cd test-app
```

This project has no declared npm dependencies, so there is no dependency-installation step required. If you prefer to initialize the local npm project metadata, the repository's scripts can be run directly with Node.js after cloning.

## Running the Application

Start the quiz with:

```bash
npm start
```

This executes `node index.js`.

You can also run the entry point directly:

```bash
node index.js
```

### Interactive workflow

1. Choose a quiz category.
2. Choose to answer all available questions, three questions, or five questions when that option is available.
3. Press Enter to begin.
4. Select each answer by entering its displayed option number.
5. Review immediate feedback and the explanation for each question.
6. View the final score and incorrect-answer review.
7. Choose whether to play again.

Invalid menu selections are rejected until a valid option number is entered. The application exits after the user chooses not to play again.

## Question Data

Questions are stored in `data/questions.json` under the top-level `categories` object. Each category has a display `name` and a `questions` array. A question entry contains:

- `question`: The question text
- `options`: An array of answer choices
- `answer`: The zero-based index of the correct option
- `explanation`: Optional explanatory text shown after answering

For example, a question follows this structure:

```json
{
  "question": "What keyword is used to declare a constant in JavaScript?",
  "options": ["var", "let", "const", "define"],
  "answer": 2,
  "explanation": "The 'const' keyword declares a block-scoped constant that cannot be reassigned."
}
```

When changing question data, ensure that `answer` points to an existing zero-based position in the `options` array.

## Testing

The project defines the following test command:

```bash
npm test
```

This runs Node.js's built-in test runner with `node --test`. No test files are currently included in the repository, so the command does not currently execute a project test suite.

## Architecture

The application is divided into a small set of focused modules:

- `index.js` loads the question JSON, displays the banner, manages category and question-count selection, and controls the application loop.
- `src/input.js` wraps Node's `readline` interface in promise-based helpers for menus, confirmations, and pause prompts.
- `src/quiz.js` contains the `Quiz` class. It shuffles questions, tracks progress and answers, evaluates selections, calculates the score, and displays results.
- `src/colors.js` provides ANSI escape-code helpers used for styled terminal output.
- `data/questions.json` keeps quiz content separate from the application logic.

The application uses asynchronous functions and promises for file loading and terminal input. Question arrays are copied and shuffled using the Fisher-Yates algorithm when a `Quiz` instance is created.

## Configuration

There are no environment variables or configuration files required to run the application. Quiz categories and content are configured in `data/questions.json`.

## Development Notes

The project uses native ECMAScript module syntax, enabled by the following setting in `package.json`:

```json
"type": "module"
```

The available npm scripts are:

| Command | Description |
| --- | --- |
| `npm start` | Starts the interactive quiz application |
| `npm test` | Runs Node.js's built-in test runner |

The source code uses only Node.js built-in modules and local project modules, so a `node_modules` directory is not required for normal execution.

## Troubleshooting

### `node` or `npm` is not recognized

Install Node.js 18 or later and ensure both `node` and `npm` are available on your system `PATH`.

### The application cannot load questions

Run the application from a complete repository checkout and verify that `data/questions.json` exists and contains valid JSON. The entry point resolves this file relative to `index.js`.

### Colors do not appear

The application writes ANSI escape sequences directly to the terminal. Use a terminal that supports ANSI color and styling escape sequences.

### The test command reports no tests

`npm test` is configured to use Node's built-in test runner, but the repository currently contains no test files.

## Deployment and CI/CD

No Dockerfiles, Docker Compose files, Kubernetes manifests, deployment scripts, or GitHub Actions workflows are present in the repository. The application is intended to run locally or in an interactive terminal environment.

## Contributing

To contribute:

1. Create a branch for your change.
2. Make the change while preserving the existing ESM structure.
3. Run `npm start` to check the interactive application behavior.
4. Run `npm test` to execute the configured test command.
5. Submit a pull request describing the change.

When adding questions, update `data/questions.json` and verify that every answer index matches its corresponding option.

## License

This project is licensed under the MIT License, as declared in `package.json`.
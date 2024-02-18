# Data Summarization

## Assigned: Monday, 19 Feb 2024

## Due: Monday, 26 Feb 2024

## Expiration Date: Monday 4 March 2024, 2:30pm

## Project Goals

This lab assignment invites you to combine what you learned about the basics
of Python programming and data analysis to implement a useful program that can
summarize a list of floating-point data values stored in a file. However, the
first step towards summarizing the data correctly requires the program to
transform the input data values from a text-based format to a numerical
representation. Along with learning more about how to implement data
transformation and summarization routines you will also explore the basics of
writing your own test cases. As you enhance your technical
skills, you will continue to program with tools such as VS Code and
a terminal window and both the Python programming language and the Poetry package manager.

## Project Access

You can access this assignment by clicking the link provided to you in Discord or in the course schedule. Once you click this link it will create a GitHub repository that you can clone to your computer by using the `git clone` command to download the project from GitHub to your computer. Now you are ready to add source code and documentation to the project!

## Expected Output

This project invites you to implement a data summarization program called
`datasummarizer`. The `datasummarizer` program takes as input a file of floating
point values and computes their arithmetic mean. Here is an excerpt from the
`input/data.txt` file that contains the floating-point values that the
`datasummarizer` must summarize:

```
2.5169521900e+0
1.8703141360e+0
-3.4505452520e-2
2.3580068020e+0
1.5516879500e+0
```

As this example indicates, these numbers are floating-point values. Can you
explain why these floating point numbers are written as, for instance,
`2.5169521900e+0`?

## Executing the Code
After you have studied and understood the contents of this
file, you are ready to install the project's dependencies with the command
`poetry install` and then run it with the command `poetry run datasummarizer
--data-file input/data.txt`. Specifically, you will know that your
`datasummarizer` works correctly when it outputs the computed mean as
`0.9919614640914002`. If you did not get this answer, then please confirm the
correctness of your functions for data transformation and summarization.

```
🔬 The data file contains 100 data values in it! Let's get summarizing!

🧮 The computed mean is 0.9919614640914002!
```

Don't forget that if you want to run the `datasummarizer` you must use your
terminal to first go into the GitHub repository containing this project and
then go into the `datasummarizer` directory that contains the project's
code. Finally, remember that before running the program you must run `poetry
install` to add the dependencies.

## Adding Functionality

If you study the file `datasummarizer/datasummarizer/main.py` you will see that
it has many `TODO` markers that designate the parts of the program that you need
to implement before `datasummarizer` will produce correct output. If you run the
provided test suite with the command `poetry run task test` or you try to run
the program with the command `poetry run datasummarizer --data-file
input/data.txt` you will see an error message in your terminal window. This is
due to the fact that there are key parts of this program that are missing! In
addition to implementing the program's main functions you also need to correctly
`import` the correct modules and objects, like `typer`.

Since the `datasummarizer` program takes as input textual values from an input
file, you will need to implement a data transformation function that can take as
input a string that contains a numerical value on each line and returns a list
of floating-point values suitable for input into a mathematical computation. For
your reference, here is the signature of the `transform_string_to_number_list`
function:

`def transform_string_to_number_list(data_text: str) -> List[float]`

You program also needs to contain a data summarization function that can take as
input a list of floating-point values and then return a single floating-point
value that corresponds to the arithmetic mean of the values in the list. As you
are implementing this function, please ensure that your function can handle
without crashing an empty list of numerical values, returning a "not a number"
(i.e., `NaN`) designator in this situation. Here is the signature of the
`compute_mean` function that you must implement:

`def compute_mean(numbers: List[float]) -> float`

In summary, you must follow all of the instructions next to the `TODO` markers
in the provided source code to implement a program that can correctly compute
the arithmetic mean of the provided data values in the
`datasummarizer/input/data.txt` file. In addition to ensuring that your program
is adequately documented, has the correct industry-standard format, and adheres
to the industry best practices Python programming, you must implement functions
that pass a provided Pytest test suite.

If you look in the files called `test_transform.py` and `test_summarize.py` you
will find the test suites for the `transform` and `summarize` modules. As you
complete your implementation of `datasummarizer` you should run these tests, as
explained in the next subsection, to confirm that your program's functions are
working correctly. Ultimately, it is important for both your program to produce
the correct output and the test suite to pass!

When you are adding functionality to the `datasummarizer` program, make sure
that you work in an incremental fashion, adding a small feature to the
system and then confirming that it works correctly through linting, testing,
and running the program. Once you have added this feature and confirmed that
it works correctly, you should commit your source code to your GitHub
repository and confirm that you have improved the build status of your
project. As you are committing your source code, please pay careful
attention to the commit message that you write! Specifically, you should
make sure that your commit message features a sentence with an active verb
and a clear description of the way in which you changed the source code. You
can read the article [How to Write a Git Commit
Message](https://cbea.ms/git-commit/) by [Chris Beams](https://cbea.ms/) to
learn some suggestions for ways to improve the quality of your Git commit
messages.

## Running Checks

If you study the source code in the `pyproject.toml` file you will see that it
includes the following section section of tasks that use
[taskipy](https://github.com/illBeRoy/taskipy):

```toml
[tool.taskipy.tasks]
black = { cmd = "black datasummarizer tests --check", help = "Run the black checks for source code format" }
flake8 = { cmd = "flake8 datasummarizer tests", help = "Run the flake8 checks for source code documentation" }
mypy = { cmd = "poetry run mypy datasummarizer", help = "Run the mypy type checker for potential type errors" }
pydocstyle = { cmd = "pydocstyle datasummarizer tests", help = "Run the pydocstyle checks for source code documentation" }
pylint = { cmd = "pylint datasummarizer tests", help = "Run the pylint checks for source code documentation" }
test = { cmd = "pytest -x -s", help = "Run the pytest test suite" }
test-silent = { cmd = "pytest -x --show-capture=no", help = "Run the pytest test suite without showing output" }
all = "task black && task flake8 && task pydocstyle && task pylint && task mypy && task test"
lint = "task black && task flake8 && task pydocstyle && task pylint"
```

This section makes it easy to run commands like `poetry run task lint` to
automatically run all of the linters designed to check the Python source code in
your program and its test suite. You can also use the command `poetry run task
black` to confirm that your source code adheres to the industry-standard format
defined by the `black` tool. If it does not adhere to the standard then you can
run the command `poetry run black datasummarizer tests` and it will automatically
reformat the source code.

Along with running tasks like `poetry run task list`, you can leverage the
relevant instructions in the [technical
skills](/proactive-skills/introduction-proactive-skills/) to enter into a Docker
container and run the command `gradle grade` to check your work. If `gradle
grade` shows that all checks pass, you will know that you made progress towards
correctly implementing and writing about `datasummarizer`. If your program has
all of the anticipated functionality, you can run the command `poetry run task
test` and see that the test suite produces output like the following. It is
important to note that `datasummarizer` comes with two test suites, both of
which should pass so as to establish a confidence in the correctness of the
program.

```
collected 6 items

tests/test_summarize.py ....
tests/test_transform.py ..
```

## Project Reflection

Once you have finished both of the previous technical tasks, you can use a text
editor to answer all of the questions in the `writing/reflection.md` file. For
instance, you should provide the output of the Python program in a fenced code
block, explain the meaning of the Python source code segments that you
implemented, and answer all of the other questions about your experiences in
completing this project. The reflection's objective is to invite you to explain
the Python functions for data summarization and transformation.

## Submission

As you are working on your lab, you are to commit and push regularly. The commands are the following.

```bash
git add -A
git commit -m ``Your notes about commit here''
git push
```

After you have pushed your work to your repository, please visit the repository at the GitHub website (you may have to log-in using your browser) to verify that your files were correctly sent.

## Project Assessment

The grade that a student receives on this assignment will have the following components.

- **GitHub Actions CI Build Status [up to 50%]:**: For the lab01 repository associated with this assignment students will receive a checkmark grade if their last before-the-deadline build passes. This is only checking some baseline writing and commit requirements as well as correct running of the program. An additional reduction will given if the commit log shows a cluster of commits at the end clearly used just to pass this requirement. An addition reduction will also be given if there is no commit during lab work times. All other requirements are evaluated manually.

- **Mastery of Technical Writing [up to 25%]:**: Students will also receive a checkmark grade when the responses to the writing questions presented in the `reflection.md` reveal a proficiency of both writing skills and technical knowledge. To receive a checkmark grade, the submitted writing should have correct spelling, grammar, and punctuation in addition to following the rules of Markdown and providing conceptually and technically accurate answers.

- **Mastery of Technical Knowledge and Skills [up to 25%]**: Students will receive a portion of their assignment grade when their program implementation reveals that they have mastered all of the technical knowledge and skills developed during the completion of this assignment. As a part of this grade, the instructor will assess aspects of the programming including, but not limited to, the completeness and the correctness of the program and the use of effective source code comments.

## GatorGrade

### Checks for GatorGrade

For immediate feedback on submissions, we will be using Gator Grade to inform the of missing components in the submission. As you submit, you will notice that there is a thick red X that will change to a green check mark when all components have been included in the submission. You are encouraged to click on the red X to find a listing of the components to address.

You can check the baseline writing and commit requirements for this lab assignment by running department's assignment checking `gatorgrade` tool. To use `gatorgrade`, you first need to make sure you have Python3 installed (type `python --version` to check). If you do not have Python installed, please see:

- [Setting Up Python on Windows](https://realpython.com/lessons/python-windows-setup/)
- [Python 3 Installation and Setup Guide](https://realpython.com/installing-python/)
- [How to Install Python 3 and Set Up a Local Programming Environment on Windows 10](https://www.digitalocean.com/community/tutorials/how-to-install-python-3-and-set-up-a-local-programming-environment-on-windows-10)

Then, if you have not done so already, you need to install `gatorgrade`:

- First, [install `pipx`](https://pypa.github.io/pipx/installation/)
- Then, install `gatorgrade` with `pipx install gatorgrade`

Finally, you can run `gatorgrade`: `gatorgrade --config config/gatorgrade.yml`

## Seeking Assistance

* Extra resources for using markdown include;
  + [Markdown Tidbits](https://www.youtube.com/watch?v=cdJEUAy5IyA)
  + [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
* Do not forget to use the above git commands to push your work to the cloud for the instructor to grade your assignment. You can go to your GitHub repository using your browser to verify that your files have been submitted. Please see the TL’s or the instructor if you have any questions about assignment submission.

Students who have questions about this project outside of the lab time are invited to ask them in the course's Discord channel or during instructor's or TL's office hours.

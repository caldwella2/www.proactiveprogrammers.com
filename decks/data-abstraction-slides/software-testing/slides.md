---
# try also 'default' to start simple
theme: default
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: prism
colorSchema: light
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
---

[//]: # (Slide Start {{{)

# Data Abstraction

## Software Testing

<div class="container my-5">
  &nbsp;
</div>

### Gregory M. Kapfhammer

### www.proactiveprogrammers.com

[//]: # (Slide End }}})

---

[//]: # (Slide Start {{{)

# <em>Okay</em>, what is this about?

<style>
  h2 {
    font-size: 36px;
    @apply text-orange-600 mb-4;
  }
</style>

<div v-click>

## Key Question

> How can I use the processes of software testing and debugging to establish a
> confidence in the correctness of a Python program?

</div>

<br>

<div v-click>

## Learning Objectives

> To **remember** and **understand** the principles of software testing and
> debugging so as to implement test suites, using Pytest, for programs that find
> bugs and establish a confidence in correctness.


</div>

<div v-click>

<div class="flex row">

<uim-rocket class="text-5xl ml-8 mt-5 text-blue-600" />

<div class="text-3xl font-bold mt-8 ml-4">
Let's explore the practice of software testing!
</div>

</div>

</div>


[//]: # (Slide End }}})

---

[//]: # (Slide Start {{{)

<div class="flex row">

<div class="text-7xl text-orange-600 font-bold mt-5 ml-4 mb-4">
What are foundations of testing and debugging?
</div>

</div>

<div v-click>

<div class="flex row">

<mdi-tooltip-check class="text-6xl ml-8 mt-6 text-blue-600" />

<div class="text-3xl font-bold mt-10 ml-4">
Testing: run a program to try to see if it works
</div>

</div>

</div>

<div v-click>

<div class="flex row">

<mdi-tooltip-check class="text-6xl ml-8 mt-6 text-blue-600" />

<div class="text-3xl font-bold mt-10 ml-4">
Debugging: fix a program that is currently broken
</div>

</div>

</div>

<div v-click>

<div class="flex row">

<mdi-tooltip-check class="text-6xl ml-8 mt-6 text-blue-600" />

<div class="text-3xl font-bold mt-10 ml-4">
Design for testability ensures testing is possible
</div>

</div>

</div>

[//]: # (Slide End }}})

---

[//]: # (Slide Start {{{)

# Software Testing in Python

<v-clicks>

-   Python program must be in an **executable state**!

-   Python source code must be **free** of **syntactical errors**

-   Python source code must be **free** of **static semantic errors**

- Key insights about software testing in Python:

    - Purpose of testing is to show that **bugs exists**

    - Testing **cannot prove** the **absence of defects**

    - **Exhaustive testing** of trivial functions is **not possible**

    - A **test suite** is a collection of useful program inputs

    - **Partition testing** divides the input space into groups

</v-clicks>

[//]: # (Slide End }}})

---

[//]: # (Slide Start {{{)

<div class="flex row">

<div class="text-7xl text-orange-600 font-bold mt-5 ml-4 mb-4">
What are key strategies for software testing?
</div>

</div>

<div v-click>

<div class="flex row">

<mdi-tooltip-check class="text-6xl ml-8 mt-6 text-blue-600" />

<div class="text-3xl font-bold mt-10 ml-4">
Keys: What is the focus? <b>and</b> What is the scope?
</div>

</div>

</div>

<div v-click>

<div class="flex row">

<mdi-tooltip-check class="text-6xl ml-8 mt-6 text-blue-600" />

<div class="text-3xl font-bold mt-10 ml-4">
Closed-box testing focuses on the specification
</div>

</div>

</div>

<div v-click>

<div class="flex row">

<mdi-tooltip-check class="text-6xl ml-8 mt-6 text-blue-600" />

<div class="text-3xl font-bold mt-10 ml-4">
Glass-box testing focuses on the source code
</div>

</div>

</div>

[//]: # (Slide End }}})

---

[//]: # (Slide Start {{{)

# Closed-Box Software Testing

<v-clicks>

- Consider the **specification** of the program under test

- Specifications may exist in a **variety of forms**:

    - Docstring for a function
    - Type annotations for a function
    - Informal specification for a program unit
    - Formal specification for a program unit

- Specifications should explain **what** the program unit should do

- You can use a **specification** to write a **test case** in Pytest

- Divide the **input space** into **partitions** and make input for each

- Ultimately, use the **specification** to **guide** your **testing** effort!

</v-clicks>

[//]: # (Slide End }}})

---

# Glass-Box Software Testing

<v-clicks>

- Consider the **implementation** of the program under test

- Attempt to **cover** a **representation** of a program:

    - Function coverage
    - Statement coverage
    - Branch coverage
    - Condition-decision coverage
    - Multiple condition-decision coverage
    - All paths coverage

- Organize **test adequacy criteria** into a **subsumption hierarchy**

- Why is it practically impossible to achieve certain strong criteria?

- Use `coverage.py` and `codecov.io` to track and report coverage

</v-clicks>

[//]: # (Slide End }}})

---

[//]: # (Slide Begin {{{)

# Squaring a Number with a `while` Loop

<div class="ml-1">

```python {all|1|2-3|4-6|7|all}
def compute_square_while(value: int) -> int:
    num_iterations = 0
    answer = 0
    while num_iterations < abs(value):
        answer = answer + abs(value)
        num_iterations = num_iterations + 1
    return answer
```

</div>

<br>

<v-clicks>

<p class = "bold">
What are the <b>expected outputs</b> for this function?
</p>

<p class = "bold">
How can we implement a <b>Pytest test case</b> for this function?
</p>

<p class = "bold">
How <b>challenging</b> is full path coverage for this function?
</p>

</v-clicks>

[//]: # (Slide End }}})

---

[//]: # (Slide Begin {{{)

# Squaring a Number with a `for` Loop

<div class="ml-1">

```python {all|1|2|3-4|5|all}
def compute_square_for(value: int) -> int:
    answer = 0
    for _ in range(abs(value)):
        answer = answer + abs(value)
    return answer
```

</div>

<br>

<v-clicks>

<p class = "bold">
What are the <b>expected outputs</b> for this function?
</p>

<p class = "bold">
How can we implement a <b>Pytest test case</b> for this function?
</p>

<p class = "bold">
How <b>challenging</b> is full path coverage for this function?
</p>

<p class = "bold">
How is testing this function <b>similar</b> to the previous function?
</p>

</v-clicks>

[//]: # (Slide End }}})

---

[//]: # (Slide Begin {{{)

# Test Cases for the `while` Loop Method

<div class="-ml-5">

```python {all|1-4|6-9|all}
def test_compute_square_while_loop_positive():
    value = 3
    square_value = main.compute_square_while(value)
    assert square_value == 9

def test_compute_square_while_loop_negative():
    value = -3
    square_value = main.compute_square_while(value)
    assert square_value == 9
```

</div>

<v-click>

Where is the **assertion** for these test cases?

What are the **inputs** and **outputs** of the test case?

</v-click>

[//]: # (Slide End }}})

---

[//]: # (Slide Begin {{{)

# Test Cases for the `for` Loop Method

<div class="-ml-5">

```python {all|1-4|6-9|all}
def test_compute_square_for_loop_positive():
    value = 3
    square_value = main.compute_square_for(value)
    assert square_value == 9

def test_compute_square_for_loop_negative():
    value = -3
    square_value = main.compute_square_for(value)
    assert square_value == 9
```

</div>

<v-click>

Where is the **assertion** for these test cases?


</v-click>

[//]: # (Slide End }}})

---

[//]: # (Slide Begin {{{)

# Test Assertions for Data Containers

<div class="-ml-8">

```python {all}
def test_compute_square_iterative_for_loop():
    number_list = """-72
        29
        61
        -42
        44"""
    square_function = main.compute_square_for
    square_list = main.
    compute_square_iterative(number_list,
                           square_function)
    assert square_list ==
       [72 * 72, 29 * 29, 61 * 61, 42 * 42, 44 * 44]
```

</div>

[//]: # (Slide End }}})

---

[//]: # (Slide Start {{{)

<div class="flex row">

<div class="text-7xl text-orange-600 font-bold mt-5 ml-4 mb-4">
What are the key parts of a Pytest test case?
</div>

</div>

<div v-click>

<div class="flex row">

<mdi-tooltip-check class="text-6xl ml-8 mt-6 text-blue-600" />

<div class="text-3xl font-bold mt-10 ml-4">
Input: the value(s) provided to function under test
</div>

</div>

</div>

<div v-click>

<div class="flex row">

<mdi-tooltip-check class="text-6xl ml-8 mt-6 text-blue-600" />

<div class="text-3xl font-bold mt-10 ml-4">
Output: the value(s) created by function under test
</div>

</div>

</div>

<div v-click>

<div class="flex row">

<mdi-tooltip-check class="text-6xl ml-8 mt-6 text-blue-600" />

<div class="text-3xl font-bold mt-10 ml-4">
Assertions: checks that the output is as expected
</div>

</div>

</div>

[//]: # (Slide End }}})

---

[//]: # (Slide Start {{{)

# Defect Detection with Pylance

```python {all|1-3|4|5-8|9-10|all}
def create_results_zip_file(
    results_dir: Path, results_files: List[str]
 ) -> None:
    """Make a .zip file of all results."""
    with zipfile.ZipFile(
        "results/All-WorkKnow-Results.zip",
        "w",
    ) as results_zip_file:
        for results_file in results_files:
            results_zip_file.write(results_files)
```

<v-click>

<mdi-message-question-outline class="text-8xl absolute top-108 left-8 text-orange-600" />
<mdi-bug class="text-8xl absolute top-105 left-34 text-orange-600" />

</v-click>

[//]: # (Slide End }}})

---

[//]: # (Slide Start {{{)

<v-click>

## Pylance Feedback in VS Code

<style>
  h2 {
    font-size: 42px;
    @apply text-orange-600 mb-4;
  }
  li {
    font-size: 28px;
    margin-top: 4px;
    margin-bottom: 9px;
    }
  pre {
    @apply text-3xl
  }
</style>

<div class="border-3 rounded-2xl border-gray-700 bg-true-gray-300 p-5 mb-6">

<pre>
Argument of type "List[str]" cannot be
assigned to parameter "filename" of
type "StrPath" in function "write"
</pre>

</div>

</v-click>

<v-click>

```python
with zipfile.ZipFile(
    "results/All-WorkKnow-Results.zip",
    "w",
) as results_zip_file:
    for results_file in results_files:
        results_zip_file.write(results_files)
```

</v-click>

<v-click>

<mdi-bug class="text-8xl absolute top-99 left-215 text-orange-600" />

</v-click>

<v-click>

<mdi-arrow-up class="text-6xl absolute top-118 left-175 text-orange-600" />

</v-click>

<v-click >

<div class="text-8xl ml-100 mt-5">

<code>results_file</code>

</div>

</v-click>

[//]: # (Slide End }}})

---

[//]: # (Slide Start {{{)

<div class="flex row">

<div class="text-7xl text-orange-600 font-bold mt-5 ml-4 mb-4">
What are the trade-offs of static analysis?
</div>

</div>

<div v-click>

<div class="flex row">

<mdi-tooltip-check class="text-6xl ml-8 mt-6 text-blue-600" />

<div class="text-3xl font-bold mt-10 ml-4">
Does not require the execution of the program
</div>

</div>

</div>

<div v-click>

<div class="flex row">

<mdi-tooltip-check class="text-6xl ml-8 mt-6 text-blue-600" />

<div class="text-3xl font-bold mt-10 ml-4">
Integrate with widely used text editors like VS Code
</div>

</div>

</div>

<div v-click>

<div class="flex row">

<mdi-tooltip-check class="text-6xl ml-8 mt-6 text-blue-600" />

<div class="text-3xl font-bold mt-10 ml-4">
Can surface false positives and false negatives
</div>

</div>

</div>

[//]: # (Slide End }}})
---

[//]: # (Slide Start {{{)

# Debugging Complex Software

<v-clicks>

- Complex software fails in complex and confusing ways! 😬

- Once the program fails we need to find and fix the fault

- A fault manifests itself in a failure through the stages of:

    - **Execute**: a test case must execute the fault
    - **Infect**: the fault must change the value of a variable
    - **Propagate**: the incorrect value must appear in output

- Faults (or "bugs" or "defects") often take different forms:

    - **Overt**: has an obvious manifestation
    - **Covert**: has no obvious manifestation
    - **Persistent**: occurs every time the program runs with same input
    - **Transient**: occurs only some of the time when program runs with the same input

</v-clicks>

[//]: # (Slide End }}})

---

[//]: # (Slide Start {{{)

<div class="flex row">

<div class="text-7xl text-orange-600 font-bold mt-5 ml-4 mb-4">
What are the key tasks during debugging?
</div>

</div>

<div v-click>

<div class="flex row">

<mdi-tooltip-check class="text-6xl ml-8 mt-6 text-blue-600" />

<div class="text-3xl font-bold mt-10 ml-4">
Document an undesired behavior of a program
</div>

</div>

</div>

<div v-click>

<div class="flex row">

<mdi-tooltip-check class="text-6xl ml-8 mt-6 text-blue-600" />

<div class="text-3xl font-bold mt-10 ml-4">
Develop a hypothesis for why this behavior occurs
</div>

</div>

</div>

<div v-click>

<div class="flex row">

<mdi-tooltip-check class="text-6xl ml-8 mt-6 text-blue-600" />

<div class="text-3xl font-bold mt-10 ml-4">
Find and fix the problem without making new ones
</div>

</div>

</div>

[//]: # (Slide End }}})

---

[//]: # (Slide Start {{{)

# Investigating Software Testing

<v-clicks>

- Software testing can **accomplish** these **goals**:

    - Find bugs in a Python program by running it
    - Establish a confidence in a Python program's correctness
    - Support confident refactoring of a Python program

-   Importance of software testing for Python programs:

    -   **Q1**: What are the **benefits** of software testing?

    -   **Q2**: What are the **limitations** of software testing?

    -   **Q3**: What are the **trade-offs** associated with software testing?

    -   **Q4**: How do you write a test suite using **Pytest**?

    -   **Q5**: How do you know when you are **finished** testing software?

</v-clicks>

[//]: # (Slide End }}})

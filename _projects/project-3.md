---
title: Project 3 Multithreading
navbar: Guides
layout: guides
key: 3.0
bump: false

project: 3

#tags:
#  - text: 'New'
#    type: 'is-primary'

subsections:
  - text: 'Requirements'
    link: '#requirements'

  - text: 'Grading'
    link: '#grading'

  - text: 'Getting Started'
    link: '#getting-started'

tests: 'project3_tests'
review1: 'project3_review1'
review2: 'project3_review2'
design: 'project3_design'

review0: 'project2_review1'

---

For this project, you will extend your [previous project](project-{{ page.project | minus: 1 }}.html) to support **multithreading**. In addition to meeting the previous project requirements, your code must make a **thread-safe inverted index**, and use **work queues** to build and search an inverted index using multiple threads.

## Requirements
{: .page-header }

The following detail the functionality requirements that must be implemented for this project.

### Input Requirements

Your `main` method must be placed in a class named `Driver` and must process the following command-line arguments:

Pending

### Other Headings

Pending

### Output Requirements

Pending

### Run Examples

Pending

## Grading
{: .page-header }

This project grade is split into the following assignments:

| Assignment | Points | Deadline | Release | Prerequisites |
|:-----------|-------:|---------:|:-------:|:--------------|
| [{{ site.data.projects[page.tests].text }}]({{ site.data.projects[page.tests].canvas }}) | {{ site.data.projects[page.tests].points }} | {{ site.data.projects[page.tests].date | date: "%b %d, %Y" }} | `v{{ page.project }}.0.Z` | `Project{{ page.project }}Test.java`, [{{ site.data.projects[page.review0].text }}]({{ site.data.projects[page.review1].canvas }}), [Test Checks](grading.html#project-tests) |
| [{{ site.data.projects[page.review1].text }}]({{ site.data.projects[page.review1].canvas }}) (30 min) | {{ site.data.projects[page.review1].points }} | {{ site.data.projects[page.review1].date | date: "%b %d, %Y" }} | `v{{ page.project }}.1.Z` | [{{ site.data.projects[page.tests].text }}]({{ site.data.projects[page.tests].canvas }}), [Review Checks](grading.html#project-reviews) |
| [{{ site.data.projects[page.review2].text }}]({{ site.data.projects[page.review2].canvas }}) (15 min)<sup>1</sup> | {{ site.data.projects[page.review2].points }} | {{ site.data.projects[page.review2].date | date: "%b %d, %Y" }} | `v{{ page.project }}.2.Z` | [{{ site.data.projects[page.review1].text }}]({{ site.data.projects[page.review1].canvas }}), [Review Checks](grading.html#project-reviews) |
| Project {{ page.project }} Review Y (15 min)<sup>2</sup> | 0 | {{ site.data.projects[page.design].date | date: "%b %d, %Y" }} | `v{{ page.project }}.Y.Z` | [{{ site.data.projects[page.review2].text }}]({{ site.data.projects[page.review2].canvas }}), [Review Checks](grading.html#project-reviews) |
| [{{ site.data.projects[page.design].text }}]({{ site.data.projects[page.design].canvas }}) | {{ site.data.projects[page.design].points }} | {{ site.data.projects[page.design].date | date: "%b %d, %Y" }} | `v{{ page.project }}.Y.Z` | [{{ site.data.projects[page.review2].text }}]({{ site.data.projects[page.review2].canvas }}), [Review Checks](grading.html#project-reviews), Passing Pull Request |
{: .table .is-auto .is-hoverable :}

<sup>1</sup> You should start on [project {{ page.project | plus: 1 }}](project-{{ page.project | plus: 1 }}.html) after receiving a grade for [{{ site.data.projects[page.review2].text }}]({{ site.data.projects[page.review2].canvas }})---do NOT wait to finish this project to start the next one!

<sup>2</sup> It takes approximately 3 to 4 code reviews to pass the design of this project. Keep in mind you may have only 30 minutes worth of code review appointments every 5 days. Due to weekends, that works out to approximately 3 weeks or more of code reviews.

See the [Project Grading](grading.html) guide for details on how projects are graded. 

## Getting Started
{: .page-header }

The following sections may be useful for getting started on this project.

### Related Homework

The following homework assignments may be useful for this project:

  - Pending


You can modify homework assignments as necessary for this project. However, make sure your code is passing all of the tests before using.

**You should NOT wait until you have completed all of the associated homework assignments to start the project.**{: .has-text-danger :} You should develop the project *iteratively* as you progress throughout the semester, integrating assignments one at a time into your project code.

### Related Content

The following lecture content may be useful for this project:

  - Pending


You can use and modify lecture code as necessary for this project. However, make sure you understand the concepts *before* using the code.

**You should NOT wait until you have covered all of the associated lecture content to start the project.**{: .has-text-danger :} You should develop the project *iteratively* as you progress throughout the semester, integrating concepts one at a time into your project code.

### Suggestions

Your goal should be to get to **testable code** as quickly as possible first, and then **developing iteratively** to pass the functionality tests.

  - Pending

It is important to **get started early** so you have plenty of time to think about how you want to approach the project *and* start coding iteratively. Planning to complete the code in too large of a chunk is a recipe to get stuck and fall behind!

<i class="fas fa-info-circle"></i>&nbsp;These hints may or may not be useful depending on your approach. Do not be overly concerned if you do not find these hints helpful for your approach for this project.
{: .notification }

{% comment %}
## Functionality
{: .page-header }

The core functionality of your project must satisfy the following requirements:

  - Maintain the functionality of the [previous project](project-{{ page.project | minus: 1 }}.html).

  - Process **additional** command-line arguments to determine the input to process and output to produce. See the "Input" and "Output" sections below for specifics.

  - Create a simple **conditional read/write lock** class that allows multiple concurrent read operations. See below for specifics.

  - Create a new **thread-safe inverted index** using the simple conditional read/write lock *in addition to* the inverted index created for previous projects.

  - Create a **work queue** class with finish and shutdown functionality. See below for specifics.

  - Use a work queue to support **multithreaded building** of the inverted index from a path. Each worker should process one file at a time (i.e. create one task per file).

  - Use a work queue to support **multithreaded searching** of the inverted index from a query file. Each worker should process one query line at a time (i.e. create one task per line).

  - Exit *gracefully* shutting down all worker threads without calling `System.exit()` when all of the building and searching operations are complete.

  - Create new classes (or extend existing classes) to support multithreading. **DO NOT REMOVE YOUR SINGLE THREADING CODE**, as you still need to support single threaded building and searching the index.

  - Do *NOT* use any of the classes in the `java.util.concurrent` package and do *NOT* use the `Stream.parallel` method for the multithreaded code.

See the following sections for additional details.

### Simple Read/Write Lock

The inverted index must be made thread-safe using a simple conditional read/write lock. The conditional read/write lock must support concurrent read operations, non-concurrent write and read/write operations, and allow an active writer to acquire additional read or write locks as necessary (i.e. reentrant write lock).

**The thread-safe inverted index should not be used unless multithreading is enabled.** The original version without locking must be used when single threading.

### Simple Work Queue

The work queue must support the ability to automatically track unfinished (or pending) work (or tasks), and provide a method that waits until there is no more pending work. The work queue should also support the ability to shutdown gracefully.

**The work queue should not be initialized unless multithreading is enabled.** It is possible to reuse the same work queue for both building and searching if multithreading is enabled.

### Input

Your `main` method must be placed in a class named `Driver`. The `Driver` class should accept the following additional command-line arguments:

  - `-threads [num]` threads where the flag `-threads`  indicates the next argument `[num]` is the number of worker threads to use. If the `[num]` argument is not provided or an invalid number, use `5` as the default number of worker threads.

    If the `-threads` flag is not provided, then a work queue should *not* be initialized, no worker threads should be created, and the project should execute with a single main thread *exactly* as previous projects.

The command-line flag/value pairs may be provided in any order, and the order provided is not the same as the order the code should perform the operations (i.e. always build the index before performing search, even if the flags are provided in the other order).

Your code should support all of the command-line arguments from the [previous project](project-{{ page.project | minus: 1 }}.html) as well.

### Output

The output of your inverted index and search results should be the same from the [previous project](project-{{ page.project | minus: 1 }}.html).

As before, your code should **only generate output files if the necessary flags are provided**. If the correct flags are provided, your code should perform the indexing and search operations even if file output is not being generated.

## Grading
{: .page-header }

The following sections detail how to earn credit for this project. The project grade is separated into one "functionality" or "test" grade worth 100 points, and a series of "design" or "code review" grades that together are worth another 100 points.

<article class="message is-warning">
  <div class="message-body"><i class="far fa-exclamation-triangle"></i>&nbsp;The tests for project 3 are handled slightly differently than other projects. Pay close attention to the sections below!</div>
</article>

#### Multithreading Tests

The project tests primarily check the file output of your code. Therefore, it is difficult to detect whether your code is actually multithreading as required. The tests can only detect is whether your code initializes a work queue, not whether that work queue is properly used.

Submitting code for a test grade that is not multithreading using a work queue and conditional read/write lock will result in a **one-time 10 to 20 point deduction** to the test score. It is up to you to manually verify that:

  - Your code is creating tasks as required (one per file for building, one per line for searching) and adding those tasks to a work queue to be executed.

  - Your code is utilizing a conditional read/write lock to protect access to your inverted index data structure.

You are strongly encouraged to use logging to verify tasks are being created and run as intended.

#### Benchmarking Tests

Unlike previous projects, the tests for this project are broken in two: `Project3aTest.java` and `Project3bTest.java`.

For the test grade and first code review, your code only needs to pass the tests in the `Project3aTest.java` group of JUnit tests. These tests verify your code still produces the correct file output.

For the following code reviews and the final release of this project, your code must also pass the `Project3bTest.java` group of JUnit tests. These tests benchmark your single-threaded versus multithreaded code and make sure your multithreaded version is faster.

For code reviews, this includes getting a speedup of at least `1.1x` faster on average using multithreading. For the final release, the speedup should be at least `1.5x` faster.

<article class="message is-warning">
  <div class="message-body"><i class="far fa-stopwatch"></i>&nbsp;Be patient. The tests for project 3 can take some time to complete, even if you have an efficient approach.</div>
</article>

#### Project Tests

To be eligible for the "Project {{ page.project }} Tests" grade, you must meet the following criteria:

  - Your code must pass the first `Project{{ page.project }}aTest.java` group of JUnit tests.

  - Your code must be multithreaded. See the "Multithreading Tests" section for details.

As with previous projects, you must also meet the following criteria for the test grade:

  - Your code must pass the tests for the previous project, [project {{ page.project | minus: 1 }}](project-{{ page.project | minus: 1 }}.html).

  - Your code must *not* pass the tests for the future project, [project {{ page.project | plus: 1 }}](project-{{ page.project | plus: 1 }}.html).

  - You must have non-zero grades for the "Project {{ page.project | minus: 1 }} Tests" and "Project {{ page.project | minus: 1 }} Review 1" assignments in Canvas.

See the [`project-tests`]({{ site.github.owner_url }}/project-tests) repository for the test code and the [Project Testing](project-testing.html) guide for additional details.

#### Project Reviews

To be eligible for the "Project {{ page.project }} Review 1" grade, you must meet the following criteria:

  - Your code must pass the `Project{{ page.project }}aTest.java` group of JUnit tests.

  - Your code must also pass the `Project{{ page.project }}bTest.java` group of JUnit benchmark tests with at least a `1.1x` speedup for `v3.1.x` or higher releases.

  - Your code must also pass the `Project{{ page.project }}bTest.java` group of JUnit benchmark tests with at least a `1.5x` speedup for the final release.

As with previous projects, you must also meet the following criteria for code reviews:

  - You must have a non-zero grade for the "Project {{ page.project | minus: 1 }} Final Release" assignment in Canvas.

  - You must have a non-zero grade for the "Project {{ page.project }} Tests" assignment in Canvas and your code must still pass the associated tests.

  - Your code must additionally pass the code review checks, such as being free of compile warnings and `TODO` comments.

See the [Project Reviewing](project-reviewing.html) guide for additional details, including how to earn the subsequent "Project {{ page.project }} Review 2" and "Project {{ page.project }} Final Release" grades.

## Getting Started
{: .page-header }

The following sections may be useful for getting started on this project.

### Examples

The following are a few examples (non-comprehensive) to illustrate the usage of the command-line arguments that can be passed to your `Driver` class via a "Run Configuration" in Eclipse, assuming you set the working directory to the `project-tests` directory.

Consider the following example:

```
-text "input/text/simple/" -query "input/query/simple.txt" -results actual/search-exact-simple.json -threads 3
```

The above arguments behave the same as [project {{ page.project | minus: 1 }}](project-{{ page.project | minus: 1 }}.html), except use `3` worker threads in a work queue to multithread both the building and search.

```
-text "input/text/simple/" -query "input/query/simple.txt" -results actual/search-exact-simple.json -threads
```

The above arguments are nearly the same, except use the default of `5` worker threads.


```
-text "input/text/simple/" -query "input/query/simple.txt" -results actual/search-exact-simple.json
```

This should behave *exactly* the same as [project {{ page.project | minus: 1 }}](project-{{ page.project | minus: 1 }}.html), using single-threading without any worker threads.

### Related Content

The following homework assignments and lecture code may be useful to complete as part of this project:

  - The `LoggerSetup` homework is useful for learning how to set up and configure `log4j2`, which will be helpful when it comes to debugging multithreaded code.

  - The `ReadWriteLock` homework is useful for creating a  simple conditional read/write lock. The conditional lock class can be used directly for your project. It also illustrates how to use a conditional lock to make a data structure class thread-safe.

  - The `PrimeFinder` homework is useful for creating a work queue that tracks pending work. This work queue class can be used directly for your project. It also illustrates how to use this work queue and create tasks for non-recursive problems.

  - The `Synchronization` lecture code illustrates how to use a conditional read/write lock to make a data structure class thread-safe.

  - The `WorkQueues` lecture code illustrates how to use a work queue and create tasks for recursive problems. If your approach is not recursive, this example might not be helpful for this project.

You can modify homework assignments and lecture code as necessary for this project. However, for homework, make sure your code is passing all of the tests before using.

You should *not* wait until you have completed all of the associated homework assignments or covered all of the related lecture content to start the project. You should **develop the project iteratively** as you progress throughout the semester, integrating assignments and concepts one at a time into your project code.

### Hints

**Do not start on this project until you understand the multithreading code shown in class.** If you are stuck on the code shown in class, we are here to help!

Your goal should be to get to testable code as quickly as possible first, and then to focus on passing the functionality tests. One possible breakdown of tasks are:

  - Configure `log4j2` add debug messages in your code. Once you are certain a class is working, disable debug messages for that class in your `log4j2.xml` file.

  - Extend your previous inverted index to create a thread-safe version using a conditional read/write lock.

  - Create new code to build the index using a work queue (creating one task per file). Make sure your code still passes the tests.

  - Create new code to process the query file using a work queue (creating one task per query line). Make sure your code still passes the tests.

  - Test your code in a multitude of settings and with different numbers of threads. Some issues will only come up occasionally, or only on certain systems.

  - Test your code with logging enabled. Then, test your code with logging completely disabled. Your code will run faster without logging, which sometimes causes some concurrency problems.

**Do not worry about efficiency until after your first code review.** However, if you have had one code review and are running into issues, look for the following common issues:

  - Make sure the code does not over-notify (e.g. wake up threads more often than necessary).

  - Make sure the code does not over-finish (e.g. call finish more often than necessary).

  - Make sure the code does not over-block (e.g. perform blocking operations within a loop).

  - Make sure the code does not over-synchronize (e.g. preventing operations that could occur at the same time).

These issues are best detected using logging.

It is important to **get started early** so you have plenty of time to think about how you want to approach the project *and* start coding iteratively. Planning to complete the code in too large of a chunk is a recipe to get stuck and fall behind!

<i class="fas fa-info-circle"></i>&nbsp;These hints may or may not be useful depending on your approach. Do not be overly concerned if you do not find these hints helpful for your approach for this project.
{: .notification }
{% endcomment %}
---
title: Exam 1 Review
navbar: Guides
layout: default
key: 1.1
bump: true

tags:
#  - text: 'New'
#    type: 'is-primary'

topics:
  - text: 'Exception Handling'
    tags: 'exceptions'
    code: 'ExceptionHandling'

  - text: 'File Input/Output (IO)'
    tags: 'files'
    code: 'FileIO'

  - text: 'Data Structures'
    tags: 'data'
    code: 'DataStructures'

  - text: 'Exploring Objects'
    tags: 'objects'
    code: 'ExploringObjects'

  - text: 'Inheritance'
    tags: 'inheritance'
    code: ['InheritanceBasics', 'InheritanceTopics']

  - text: 'Lambda Expressions'
    tags: 'lambdas'
    code: 'LambdaExpressions'

  - text: 'Stream Pipelines'
    tags: 'streams'
    code: 'StreamPipelines'

  - text: 'Regular Expressions'
    tags: 'regexes'
    code: 'RegularExpressions'

---

The exam will cover topics on the lecture content, homework assignments, and quizzes covered up thus far in class. This includes the following topics:

{% for topic in page.topics -%}
  - {{ topic.text }}
{% endfor %}

See below for resources and additional details.

<style>
ul.icons {
  list-style-type: none;
  margin-left: 1.5em;
  margin-top: 0em;
}

ul.icons > li {
  position: relative;
}

ul.icons > li > i {
  width: 1.25em;
  left: -1.5em;
  position: absolute;
  text-align: center;
  line-height: inherit;
}
</style>

## Resources

{% assign columns = 'slides,quizzes,homework' | split: ',' %}
<table class="table is-hoverable">
<thead>
  <tr>
    <th width="20%">Topic and Code</th>
    <th width="30%">Lecture Slides</th>
    <th width="30%">Practice Quizzes</th>
    <th width="20%">Homework</th>
  </tr>
</thead>

<tbody>

{% for topic in page.topics %}
<tr>
  <td>
    <ul class="icons">
      {% if topic.code %}
      {% for repo in topic.code %}
      <li><i class="{{ site.data.icons.code.class }}"></i> <a href="{{ site.data.info.links.github.link }}/lectures/tree/main/{{ repo }}">{{ repo }}</a></li>
      {% endfor %}
      {% else %}
      <li><i class="{{ site.data.icons.pending.class }}"></i> {{ topic.text }}</li>
      {% endif %}
    </ul>
  </td>

  {% for column in columns %}
  {% assign data = site.data[column] %}
  {% assign filtered = data | where_exp:"item", "item.tags contains topic.tags" %}
  <td>
    <ul class="icons">
      {% for item in filtered -%}
      <li>
        <i class="{{ site.data.icons[item.icon].class }}"></i>
        {% if column == "homework" %}
        <a href="{{ site.data.info.links.github.link }}/homework-{{ item.text }}-template/">{{ item.text }}</a>
        {% elsif column == "quizzes" %}
        {% if item.test %}<a href="{{ item.test }}">{{ item.text }}</a>{% else %}{{ item.text }}{% endif %}
        {% else %}
        <a href="{{ item.link }}">{{ item.text }}</a>
        {% endif %}
        {% if item.save -%}
        <a href="/files/{{ item.text }}.pdf"><i class="fas fa-download"></i></a>
        {%- endif %}
        {% if item.tube -%}
        <a href="{{ item.tube }}"><i class="fab fa-youtube"></i></a>
        {%- endif %}
      </li>
      {% endfor %}
      {% if filtered.size < 1 %}
      <li type="none">(None)</li>
      {% endif %}
    </ul>
  </td>
  {% endfor %}
</tr>
{% endfor %}

</tbody>
</table>

Note that homework is often associated with multiple topics and appears multiple times in the table.

See the [Schedule](/schedule.html) for links to the many videos and recordings made for this content.

## Example Topics

The following are some example topics that you may want to make sure you understand. This is a non-comprehensive list. Some of these topics may not appear on the exam and some topics not covered here may appear on the exam.

- You should understand what each **keyword** in Java means, including: `public`, `private`, `static`, `final`, `class`, `abstract`, and `interface`.

- You should understand the difference between a **primitive type** and an **object**.

- You should understand how to use different control-flow statements, such as `if`, `else if`, `else` statements, `for` and enhanced `for` loops, `while` and `do-while` loops, `switch` statements, and how to use related keywords such as `break`, `continue`, and `return`.

- You should understand how to create and use `String` objects.

- You should be familiar with the `Object` class and all of its methods.

- You should understand how to use the `new` keyword and its significance when it comes to memory allocation and the `final` keyword.

- You should understand when it is appropriate to use the `static` keyword with members, methods, and classes.

- You should understand the difference between **mutable** versus **immutable** objects, and when it is safe to pass a reference of an object.

- You should understand the difference between the abstract data types **list**, **set**, and **map**.

- You should understand how and when to use different **built-in data structures**, such as `ArrayList`, `LinkedList`, `HashSet`, `TreeSet`, `HashMap`, and `TreeMap`.

- You should understand how to create, access, and efficiently iterate through a **nested data structure**, and understand how to compare the pros/cons of different approaches to iteration.

- You should understand how to create and use classes, including the meaning of terms like **constructors**, **methods**, and **members**.

- You should understand how to design a class to be both **generalized** and **encapsulated**.

- You should understand how to **overload** and **override** methods.

- You should understand the difference between **identifiers** and **instances**.

- You should understand how to **catch and throw** exceptions.

- You should understand how to use a **try-with-resources block**, as well as a traditional `try`/`catch`/`finally` block.

- You should understand the difference between a **relative path** and **absolute path**.

- You should understand how to **read and write to files** line-by-line and traverse directories using the Java "new IO" package and the `Path`, `Paths`, `Files`, `BufferedReader`, `BufferedWriter`, and `DirectoryStream` classes.

- You should understand inheritance-related terms such as **superclass**, **subclass**, **direct**, and **indirect**, as well as keywords such as `this` and `super`.

- You should understand the difference between an **interface** and an **abstract class**.

- You should understand how to create a **nested class**, and the difference between different types of nested classes.

- You should understand how to create an **anonymous inner class**, and the inheritance relationships that class has to its outer class and its superclass.

- You should understand concepts such as **upcasting** and **downcasting**, as well as how they are useful.

- You should understand how to extend the `Comparator` and `Comparable` interfaces to allow for custom sorting using `Collections.sort()`.

- You should understand how to create **functional interfaces** using the `@FunctionalInterface` annotation.

- You should understand how to create and use **lambda expressions**, and the difference between lambda expressions and anonymous inner classes and interfaces.

- You should understand how to create and use **streams** and stream pipelines, and the differences between a stream and a collection.

- You should understand terminology with respect to stream operations, including **intermediate** versus **terminal** operations, **lazy** versus **eager** operations, and what it means for an operation to be **non-interfering**, **stateless**, and without **side-effects**.

- You should understand how to use the `Pattern` and `Matcher` classes in Java to handle regular expressions, and the difference between the `find()` versus `matches()` methods.

- You should understand how to create **character classes**, such as `[a-z]` and `[^0-9]`, in regular expressions.

- You should understand how to use **predefined character classes** such as `\w`, `\W`, `\s`, `\S`, and `.` in regular expressions.

- You should understand how to use the `?`, `*`, and `+` **quantifiers** in regular expressions.

- You should understand the difference between a **greedy versus reluctant quantifier** in regular expressions.

- You should understand how to create and use **capturing groups** and non-capturing groups in regular expressions.

- You should understand how to use the `i`, `m`, and `s` **flags**.

- You should understand how to use the `^`, `$`, `\A`, `\z`, and `\b` **boundary matchers**.

- You should understand the different ways to use the **`?` character** in a regular expression. For example: `(?i)` to turn on the `i` flag, `(?:i)` to create a non-capturing group that matches the `i` character, `[?!]` to create a character class that matches the `?` and `!` characters, `i?` to match the `i` character 0 or 1 times (greedy), and `i+?` to match the `i` character 1 or more times (reluctant).
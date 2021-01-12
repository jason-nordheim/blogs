# Jest + React

Ensuring a software product is reliable and preformat is critical to the success of any software product.

While there are perfectly valid reasons for performing manual tests, automated tests provide a multitude of benefits and is one of the most valuable skills a developers can possess to improve the quality and reliability of their code by:

- Documentation - test provide specifications for how code should be used (how it supposed to work)
- Consistency - testing ensures that code follows best-practices and meets teams naming conventions
- Confidence - testing provides confidence that software works as expected and that new code doesn't break existing functionality

All of this center's around increasing **productivity**. Through automated tests software can be released faster, with less bugs than manually tested software.

> Automated testing is the process of writing code to verify behavior of an application

## Types of Automated Tests

There are three primary categories of tests (listed from lowest complexity to highest):

1. Unit Tests
2. Integration Tests
3. End-to-end Tests

The "lowest level" of testing is known as **unit testing**. Unit tests are the simplest form of automated tests, and typically the shortest to write. The goal of _unit testing_ is to validate that isolated units of work (e.g. functions/services) behave as expected. A test that validates more than one unit of work, or the behavior of related units of work is known as "integration testing". **Integration** tests validate that related units or components work together as expected. The highest level of testing is known as "end-to-end testing". In **end-to-end** tests, the full application is running and user actions are simulated to see if the produce the expected behavior.

In Summary:

| Test                | Complexity | Purpose                                                           | Execution Time |
| ------------------- | ---------- | ----------------------------------------------------------------- | -------------- |
| Unit Testing        | Low        | Verify behavior of individual units of work                       | Very fast      |
| Integration Testing | Medium     | Verify behavior of operations involving multiple units/components | Pretty Quick   |
| End-to-end Testing  | High       | Verify user-actions produce expected behavior                     | Long           |

---

---

# Archive

The highest level of testing, we have "end-to-end tests". **End-to-end** testing involves running automating (simulating) actions a user would take in the application, then verifying that those actions produce the expected behavior and functionality. In the context of web applications like React, an _end-to-end test_ involves the full-stack (server, client, database, etc.) supporting the application to be configured and running.

At the other end of testing, **unit tests** verify that individual "units" of code behave as expected. These tests ensure that a single operation operates as expected.

In between _unit tests_ and _end-to-end tests_ are "integration tests". **Integration tests** are like a hybrid of

**Integration** tests verify that related units/components that work together work as expected.

**Unit** tests verify the functionality of a single function or component in an application.

The highest level of testing is referred to as "end-to-end" testing and is the most closely related to the manual process of testing software products.

In end-to-end tests:

- the application is running
- user behavior (clicking, typing, etc.) is simulated via the automated tests

> End-to-end tests execute more slowly than any other form of automated testing since the application (including all components) must be running

- Saves time
  - faster feedback cycle
    - does a function return
    - does a component display what you think it will?
    - does bad input break a function
- Quality

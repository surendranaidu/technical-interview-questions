# Testing Interview questions

* **Why test is necessary ?**

Software Testing is necessary because we all make mistakes. Some of those mistakes are unimportant, but some of them are expensive or dangerous. We need to check everything and anything we produce because things can always go wrong – humans make mistakes all the time.

Benefit of testing:

    - Cost-effectiveness
    - Add security
    - Product Quality
    - customer satisfaction.

* **List some kinds of testing ?**


Functional Testing types include:

    Unit Testing
    Integration Testing
    System Testing
    Sanity Testing
    Smoke Testing
    Interface Testing
    Regression Testing
    Beta/Acceptance Testing

Non-functional Testing types include:

    Performance Testing
    Load Testing
    Stress Testing
    Volume Testing
    Security Testing
    Compatibility Testing
    Install Testing
    Recovery Testing
    Reliability Testing
    Usability Testing
    Compliance Testing
    Localization Testing

* **Compare Unit Test vs Integration Test ?**

When a module is developed by a developer and it is tested for functionality then it is known as Unit testing. Once all modules are developed and integrated with other modules then Integration testing is to be carried out to discover the issues arise when different modules are interacting with each other to build overall system.

More detail [here](https://www.softwaretestingclass.com/what-is-difference-between-unit-testing-and-integration-testing/)

* **What is mocking, When we apply and Why ?**

In short, mocking is creating objects that simulate the behavior of real objects.

Mocking is primarily used in unit testing. An object under test may have dependencies on other (complex) objects. To isolate the behavior of the object you want to replace the other objects by mocks that simulate the behavior of the real objects. This is useful if the real objects are impractical to incorporate into the unit test.


* **List some testing framework**

C++: Boost.test, Aeryn, FRUCTOSE, CxxTest, GoogleTest, ..

Python: Robot Framework, Pytest, Uninitest(PyUnit), Behave, Lettuce

JS/TS: MochaJS, JEST, Jasmine, Karma

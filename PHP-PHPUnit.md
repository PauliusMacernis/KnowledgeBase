## PHP (testing with PHPUnit)
- ~Explain how PHPUnit executes tests (when/how often creates test objects, when/how often invokes test methods).
<a href="#" title="...">⌘</a>

- ~How does the PHPUnit test runner work?
<a href="#" title="...">⌘</a>

- **How should the test classes be named?**  
The tests for a class `Example` go into a class `ExampleTest`.  
Read more:  
https://phpunit.readthedocs.io/en/7.1/writing-tests-for-phpunit.html  

- **How should test class methods (aka. tests) be named?**  
Methods are named `test*`. For example, `testSomething`  
Read more:  
https://phpunit.readthedocs.io/en/7.1/writing-tests-for-phpunit.html  

- **Is there a way of having a test class method (aka. test) named by not following method naming convention (`test*`) and still treat this method as a test?**  
Alternatively, you we use the `@test` annotation in a method's docblock to mark it as a test method.  
Read more:  
https://phpunit.readthedocs.io/en/7.1/writing-tests-for-phpunit.html  

- **What should the visibility of test class methods (aka. tests) be?**  
The tests are `public` methods.  
Read more:  
https://phpunit.readthedocs.io/en/7.1/writing-tests-for-phpunit.html  

- **What is `PHPUnit\Framework\TestCase` class for?**  
The test class (for example, `ExampleTest`) inherits (most of the time) from `PHPUnit\Framework\TestCase`.  
Read more:  
https://phpunit.readthedocs.io/en/7.1/writing-tests-for-phpunit.html  

- **What are assertion methods for?**  
Inside the test methods, assertion methods such as `assertSame()` are used to assert that an actual value matches an expected value. For example:  
```
<?php
use PHPUnit\Framework\TestCase;

class StackTest extends TestCase
{
    public function testPushAndPop()
    {
        $stack = [];
        $this->assertSame(0, count($stack));

        array_push($stack, 'foo');
        $this->assertSame('foo', $stack[count($stack)-1]);
        $this->assertSame(1, count($stack));

        $this->assertSame('foo', array_pop($stack));
        $this->assertSame(0, count($stack));
    }
}
```
Read more:  
https://phpunit.readthedocs.io/en/7.1/writing-tests-for-phpunit.html  
https://phpunit.readthedocs.io/en/7.1/assertions.html#appendixes-assertions  

- **Why should we write tests instead of `print`, `print_r`, `echo`, `var_dump` statements and a debugger expressions instead?**  
Because we are expecting some value to be dumped after the print (`print`, `print_r`, `echo`, `var_dump`, etc.) and it is better to have this kind of expectations to be saved as tests than just printing the value, checking if it matches the expectation, and removing just after.  
Read more:  
https://phpunit.readthedocs.io/en/7.1/writing-tests-for-phpunit.html  

- **Why Unit Tests are treated as a good practice?**  
Because these:
    - helps to identify and fix bugs,
    - helps to refactor code, 
    - helps to serve as documentation for a unit of software under test,
    - reduces the cost of the bug, profit loss because of the bug, etc. Finding a bug in a local develop environment is much cheeper in value loss than finding the same on production.
Read more:  
https://phpunit.readthedocs.io/en/7.1/writing-tests-for-phpunit.html  

- **May Unit tests have implicit dependencies between test methods?**  
One unit test usually covers one specific path in one function or method. However a test method is not necessarily an encapsulated, independent entity. Often there are implicit dependencies between test methods, hidden in the implementation scenario of a test.  
Read more:  
https://phpunit.readthedocs.io/en/7.1/writing-tests-for-phpunit.html  

- **Is it ok for Unit tests to have implicit dependencies between test methods?**  
???  
Read more:  
https://phpunit.readthedocs.io/en/7.1/writing-tests-for-phpunit.html  


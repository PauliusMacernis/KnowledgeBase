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


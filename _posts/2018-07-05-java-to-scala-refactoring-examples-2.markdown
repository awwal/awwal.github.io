---
published: true 
---

##  Java to Scala Refactoring examples 2

Say we have an expected failure test

```
    @Test
    public void testFailureScenario() {

        String s = "1;";
        try {
            Integer.parseInt(s);
            fail(s + " should not be convertable to int");
        } catch (Exception e) {
            //expected
        }

    }
```


Using the intellij scala plugin, a refactor produces this

```
    @Test
    def testFailureScenario(): Unit = {
    val s = "1;"
    try {
      s.toInt
      fail(s + " should not be convertable to int")
    } catch {
      case e: Exception =>

      //expected
    }
  }

```


That works. But we can do better. We can create a method like assertThrowsException that can be re-used.

```
    @Test
    def testFailureScenario(): Unit = {
      val s = "1;"
      assertThrowsException(s+" should not be convertable to int", s){ str=>
        str.toInt

      }
    }


    def assertThrowsException[A](message:String, a:A)(f: A=> Any) : Unit ={
      Try(f(a)) match {
        case Success(_) =>  fail(message);
        case Failure(_) => ()
      }

    }
``` 


The assertThrowsException takes two parameter set.

First parameter set (msg:String, a:A)  and the second parmaeter set (f: A => Any) 

The second parameter set has only one parameter. `A` function that takes an A and returns Any. 
The first parameter set include the `a` that the function that f will work on.

Ultimately, we can move to functional scala friendly testing library. Such as [scala test](http://www.scalatest.org).

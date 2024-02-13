# JavaSE-BiPredicate

See the Udemy course: https://www.udemy.com/course/curso-certificacion-profesional-desarrollador-java-se-11

In Java, a BiPredicate is a functional interface that represents a predicate (a boolean-valued function) that takes two arguments.

It's a part of the java.util.function package introduced in Java 8, specifically designed to work with functional programming concepts.

The BiPredicate interface has a single method called test, which takes two parameters and returns a boolean. 

Here's the definition of the BiPredicate interface:

```java
@FunctionalInterface
public interface BiPredicate<T, U> {
    boolean test(T t, U u);
}
```

Let's look at a simple example to illustrate how you might use a BiPredicate. 

Suppose you want to check if two strings have the same length. You can use a BiPredicate for this:

```java
import java.util.function.BiPredicate;

public class BiPredicateExample {
    public static void main(String[] args) {
        BiPredicate<String, String> sameLengthPredicate = (s1, s2) -> s1.length() == s2.length();

        String str1 = "hello";
        String str2 = "world";

        if (sameLengthPredicate.test(str1, str2)) {
            System.out.println("The two strings have the same length.");
        } else {
            System.out.println("The two strings have different lengths.");
        }
    }
}
```

In this example, sameLengthPredicate is a BiPredicate that checks if two strings have the same length. 

The test method is called with the strings str1 and str2, and the result is printed based on whether the strings have the same length or not.

# More examples of using BiPredicate in Java.

## Example 1: Comparing Numbers

Here, the BiPredicate areEqual checks if two integers are equal.

```java
import java.util.function.BiPredicate;

public class BiPredicateExample {
    public static void main(String[] args) {
        BiPredicate<Integer, Integer> areEqual = (num1, num2) -> num1.equals(num2);

        int a = 5;
        int b = 5;
        
        if (areEqual.test(a, b)) {
            System.out.println("The numbers are equal.");
        } else {
            System.out.println("The numbers are not equal.");
        }
    }
}
```

## Example 2: Checking Pair Properties

In this example, the BiPredicate isValidPair checks if a key is not null or empty and if the associated value is greater than 0.

```java
Copy code
import java.util.function.BiPredicate;

public class BiPredicateExample {
    public static void main(String[] args) {
        BiPredicate<String, Integer> isValidPair = (key, value) -> key != null && value != null && !key.isEmpty() && value > 0;

        String key = "example";
        int value = 42;

        if (isValidPair.test(key, value)) {
            System.out.println("The pair is valid.");
        } else {
            System.out.println("The pair is not valid.");
        }
    }
}
```

These examples demonstrate how you can use BiPredicate to create boolean conditions based on two input parameters.

# More advanced topics and use cases for BiPredicate in Java.

## 1. Combining Predicates with and, or, and negate:

You can combine BiPredicate instances using logical operations like and, or, and negate. 

In this example, combinedPredicate is a combination of two predicates using the and method. 

The conditions check if the sum is even and the product is positive.

```java
import java.util.function.BiPredicate;

public class BiPredicateExample {
    public static void main(String[] args) {
        BiPredicate<Integer, Integer> isSumEven = (a, b) -> (a + b) % 2 == 0;
        BiPredicate<Integer, Integer> isProductPositive = (a, b) -> (a * b) > 0;

        BiPredicate<Integer, Integer> combinedPredicate = isSumEven.and(isProductPositive);

        int num1 = 4;
        int num2 = 3;

        if (combinedPredicate.test(num1, num2)) {
            System.out.println("The sum is even, and the product is positive.");
        } else {
            System.out.println("Conditions not met.");
        }
    }
}
```

## 2. Using Method References:

You can use method references to make your code more concise. 

In this example, areEqualIgnoreCase is a BiPredicate that uses a method reference to equalsIgnoreCase method of the String class.

```java
import java.util.function.BiPredicate;

public class BiPredicateExample {
    public static void main(String[] args) {
        BiPredicate<String, String> areEqualIgnoreCase = String::equalsIgnoreCase;

        String str1 = "Java";
        String str2 = "java";

        if (areEqualIgnoreCase.test(str1, str2)) {
            System.out.println("The strings are equal ignoring case.");
        } else {
            System.out.println("The strings are not equal ignoring case.");
        }
    }
}
```

## 3. Custom BiPredicate:
You can create your own custom BiPredicate implementation. 

For example, a predicate that checks if the difference between two numbers is within a certain range:

```java
import java.util.function.BiPredicate;

public class BiPredicateExample {
    public static void main(String[] args) {
        BiPredicate<Integer, Integer> isDifferenceInRange = (a, b) -> Math.abs(a - b) <= 10;

        int num1 = 15;
        int num2 = 25;

        if (isDifferenceInRange.test(num1, num2)) {
            System.out.println("The difference is within the specified range.");
        } else {
            System.out.println("The difference is outside the specified range.");
        }
    }
}
```

Here, isDifferenceInRange checks if the absolute difference between two numbers is less than or equal to 10.

These advanced examples showcase the versatility of BiPredicate in creating complex conditions and promoting code readability.

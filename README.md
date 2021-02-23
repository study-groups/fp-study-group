# fp-study-group
Collection of links for studying the functional programming.

## Thinking in type, shape and function signature

- https://hackmd.io/CBQPxR3ySpSc5ALiIkac0w

## Functional programming with vanilla Java

Modern functional programming semantics were added to the Java
language in version 8, around 2014. This is shows the native 
way before Java 8 to the modern way in Java 8 and after.

- https://www.oracle.com/java/technologies/javase-downloads.html

- From https://mkyong.com/java8/java-8-filter-a-map-examples/

```java
TestMapFilter.java
package com.mkyong;

import java.util.HashMap;
import java.util.Map;
import java.util.stream.Collectors;

public class TestMapFilter {

    public static void main(String[] args) {

        Map<Integer, String> HOSTING = new HashMap<>();
        HOSTING.put(1, "linode.com");
        HOSTING.put(2, "heroku.com");
        HOSTING.put(3, "digitalocean.com");
        HOSTING.put(4, "aws.amazon.com");

        // Before Java 8
        String result = "";
        for (Map.Entry<Integer, String> entry : HOSTING.entrySet()) {
            if ("aws.amazon.com".equals(entry.getValue())) {
                result = entry.getValue();
            }
        }
        System.out.println("Before Java 8 : " + result);

        //Map -> Stream -> Filter -> String
        result = HOSTING.entrySet().stream()
                .filter(map -> "aws.amazon.com".equals(map.getValue()))
                .map(map -> map.getValue())
                .collect(Collectors.joining());

        System.out.println("With Java 8 : " + result);

        // filter more values
        result = HOSTING.entrySet().stream()
                .filter(x -> {
                    if (!x.getValue().contains("amazon") && !x.getValue().contains("digital")) {
                        return true;
                    }
                    return false;
                })
                .map(map -> map.getValue())
                .collect(Collectors.joining(","));

        System.out.println("With Java 8 : " + result);

    }
}
```

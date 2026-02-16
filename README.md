# Java Stack–Heap Memory Diagram

## Overview

This repository contains a Stack–Heap memory diagram illustrating the runtime behavior of a Java program.  
The diagram demonstrates how the JVM manages stack frames, local variables, object references, and heap-allocated objects during method execution.

---

## Source Code

```java
public class Main {
    public static void main(String[] args) {
        String name = "Kevin";
        List<String> list = new ArrayList<>();
        int times = 10;
        System.out.println(times + fill(list, name + name, times));
    }

    public static int fill(Collection<String> collection, String str, int times) {
        String shrunk = shrink(str);
        times = (times + shrunk.length()) / 2;
        for (int i = 0; i < times / 2; i++) {
            collection.add(shrunk);
        }
        return times;
    }

    public static String shrink(String str) {
        int newLength = str.length() / 2 + str.length() % 2;
        char[] chars = new char[newLength];
        for (int i = 0; i < str.length(); i += 2) {
            chars[i / 2] = str.charAt(i);
        }
        return new String(chars);
    }
}


```

## Solution Description

The Stack–Heap diagram illustrates the runtime memory behavior of the program during its execution in the Java Virtual Machine (JVM).

# Stack Memory

Represents the method call hierarchy

Contains stack frames for:

main

fill

shrink

Each stack frame stores:

Local primitive variables

References to heap objects

Stack frames are shown in the correct order of method invocation and are removed after method completion

# Heap Memory

Stores all dynamically created objects, including:

String instances

ArrayList<String> and its internal storage

char[] array created in the shrink method

All heap objects are correctly linked to their corresponding stack references

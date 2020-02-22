---
layout: page
title: Static vs. Non-Static
---

## Static vs. Dynamic Bound Classes
- What's the difference between:
`public static void drive(){}`
and
`public void drive(){}`

### Static:
- When calling a static method, we do not instantiate an object. 
- A static method can be accessed directly or by using class name as mentioned in the comments.
- Static methods can access static variables without any objects
- Static methods can be accessed directly in static and non-static methods

### Non-Static/Dynamic:
- A non-static (dynamic) method is always accessed using the object of a class
- Non-static methods and non-static variables can only be accessed using objects


**TL;DR:**
You can call static classes without having to have an object of that class

ex. `Car1.drive()` 

- Uses the `drive` method from the `Car1` class in the main class without needing an object of Car1

### Static vs. Dynamic Binding:
- Static binding in Java occurs during Compile time while Dynamic binding occurs during Runtime.
- `private`, `final`, and `static` methods and variables uses static binding and bonded by compiler 
- Dynamic (non-static) methods are bonded during runtime based upon runtime object


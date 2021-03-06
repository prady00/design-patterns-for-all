Singleton
==========
Real world example
> There can only be one president of a country at a time. The same president has to be brought to action, whenever duty calls. President here is singleton.

In plain words
> Ensures that only one object of a particular class is ever created.

Wikipedia says
> In software engineering, the singleton pattern is a software design pattern that restricts the instantiation of a class to one object. This is useful when exactly one object is needed to coordinate actions across the system.

Singleton pattern is actually considered an anti-pattern and overuse of it should be avoided. It is not necessarily bad and could have some valid use-cases but should be used with caution because it introduces a global state in your application and change to it in one place could affect in the other areas and it could become pretty difficult to debug. The other bad thing about them is it makes your code tightly coupled plus mocking the singleton could be difficult.

**Programmatic Example**

To create a singleton, make the constructor private, disable cloning, disable extension and create a static variable to house the instance
```java
package com.prady00.dp.creational.singleton;
final class President
{
    private static President instance = null;

    private President()
    {
        // Hide the constructor
    }

    public static President getInstance()
    {
        if (President.instance == null) {
        	President.instance = new President();
        }

        return President.instance;
    }

}
```
Then in order to use
```java
package com.prady00.dp.creational.singleton;

public class SingletonRunner {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		President president1 = President.getInstance();
		President president2 = President.getInstance();
		
		// here president1 and president2 are same instances

	}

}

```
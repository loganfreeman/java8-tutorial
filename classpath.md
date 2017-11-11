[How To add an External jar File to the ClassPath Dynamically at runtime?
](https://stackoverflow.com/questions/15204913/how-to-add-an-external-jar-file-to-the-classpath-dynamically-at-runtime)
```
URLClassLoader child = new URLClassLoader (myJar.toURL(), this.getClass().getClassLoader());
Class classToLoad = Class.forName ("com.MyClass", true, child);
Method method = classToLoad.getDeclaredMethod ("myMethod");
Object instance = classToLoad.newInstance ();
Object result = method.invoke (instance);
```

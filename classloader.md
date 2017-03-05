load jar file
---
```java
private static void addSoftwareLibrary(File file) throws Exception {
    Method method = URLClassLoader.class.getDeclaredMethod("addURL", new Class[]{URL.class});
    method.setAccessible(true);
    method.invoke(ClassLoader.getSystemClassLoader(), new Object[]{file.toURI().toURL()});
}
```

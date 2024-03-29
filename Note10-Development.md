# Note10 Development
## Using javac and java
- Sử dụng `-d` để thay đổi đường dẫn của file khi lần đầu tạo bởi javac cammand.
- 
❑ The -d option can build package-dependent destination classes on-the-fly if
the root package directory already exists.
❑ Use the -D option in conjunction with the java command when you want to
set a system property.
❑ System properties consist of name=value pairs that must be appended directly
behind the -D, for example, java -Dmyproperty=myvalue.
❑ Command-line arguments are always treated as Strings.
❑ The java command-line argument 1 is put into array element 0, argument 2
is put into element 1, and so on.
Searching with java and javac (Objective 7.5)
❑ Both java and javac use the same algorithms to search for classes.
❑ Searching begins in the locations that contain the classes that come standard
with J2SE.
❑ Users can define secondary search locations using classpaths.
❑ Default classpaths can be defined by using OS environment variables.
❑ A classpath can be declared at the command line, and it overrides the default
classpath.
❑ A single classpath can define many different search locations.
❑ In Unix classpaths, forward slashes (/) are used to separate the directories
that make up a path. In Windows, backslashes (\) are used.

❑ In Unix, colons (:) are used to separate the paths within a classpath. In Windows, semicolons (;) are used.
❑ In a classpath, to specify the current directory as a search location, use a dot (.)
❑ In a classpath, once a class is found, searching stops, so the order of locations
to search is important.
Packages and Searching (Objective 7.5)
❑ When a class is put into a package, its fully qualified name must be used.
❑ An import statement provides an alias to a class's fully qualified name.
❑ In order for a class to be located, its fully qualified name must have a tight
relationship with the directory structure in which it resides.
❑ A classpath can contain both relative and absolute paths.
❑ An absolute path starts with a / or a \.
❑ Only the final directory in a given path will be searched.
JAR Files (Objective 7.5)
❑ An entire directory tree structure can be archived in a single JAR file.
❑ JAR files can be searched by java and javac.
❑ When you include a JAR file in a classpath, you must include not only the
directory in which the JAR file is located, but the name of the JAR file too.
❑ For testing purposes, you can put JAR files into .../jre/lib/ext, which is
somewhere inside the Java directory tree on your machine.
Static Imports (Objective 7.1)
❑ You must start a static import statement like this: import static
❑ You can use static imports to create shortcuts for static members (static
variables, constants, and methods) of any class.

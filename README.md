# bazel-poc
This document is based on my understanding on Bazel.
Bazel is a build tool for java based application like maven.
It will create a BUILD and WORKSPACE file.
BUILD file is blueprint for java_binary created with src package and main file name.
```java_binary(
    name = "TestApp",
    srcs = glob(["src/main/java/com/poc/*.java"]),
}
```
Thi is root package and all file under /poc will be scan and build by Bazel.
It will also create a target directory.
This rule will tell bazel to run a jar file.
glob(include, exclude=[], exclude_directories=1, allow_empty=True)
glob is a helper function to match all nested package directory to build jar.
We can exclude directory to be scan on runtime. Using exclude_directories =1.

# bazel build glob
It can have a pattern matcher like
```java_library(
    name = "mylib",
    srcs = glob(
        ["**/*.java"],
        exclude = ["**/testing/**"],
    ),
)
```
To exclude package /testing.
In Bazel we can specify multiple target folder to build.
This will create multi-module project.
```deps = [":greeter"],
```
is helps to inject dependent library while build.
For each sub-module a separate BUILD file will create.

In this example I create a simple Bazel project with 2 module so separate BUILD file created.

Happy Bazel!!

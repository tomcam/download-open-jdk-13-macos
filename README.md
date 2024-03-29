# How to download Open JDK 13 for MacOS and run a "hello world" program in Java

I'm not a Java developer but I was given a utility and needed fix a bug in it.
Here's how to get Open JDK working on your Mac in just a few minutes, because
Java SE may no longer be free for you.

Oracle [changed its license terms for Java](https://www.oracle.com/technetwork/java/javase/overview/oracle-jdk-faqs.html)
in April 2019 and it seems that
restrictions on commercial use have increased. It seems like the standard
Java distribution may require payment now if you're a developer. I'm not totally 
sure, but I decided to download and install
[OpenJDK 13](https://openjdk.java.net), which is still free,
on my MacOS machine. The Oracle instructions
don't seem to cover MacOS, so here's my method.

## Go to openjdk.java.net and download the MacOS version

* Visit [OpenJDK 13](https://openjdk.java.net) and download the **macOS/x64** option. 
It's big, over 300MB.

I assume this leaves the file `openjdk-13_osx-x64_bin.tar` in your `~/Downloads` directory.

## Extract the contents of the archive

* Double-click the file `openjdk-13_osx-x64_bin.tar`.

It gets extracted into a directory named `jdk-13.jdk`.

## Move the directory to /Library/Java/JavaVirtualMachines/

Drop into your terminal:

* In Finder, choose **Applications > Utilities > Terminal**.

The terminal prompt appears.

* Change to the Downloads directory:

```bash
$ cd ~/Downloads
```

* And move the newly created `jdk-13.jdk` directory to the `/Library/Java/JavaVirtualMachines/` directory. 
You'll be asked for your system password:

```bash
$ sudo mv jdk-13.jdk /Library/Java/JavaVirtualMachines/
```

That's it! You may want to ensure it's been copied to the right place.

## Ensure the Java compiler and interpreter run

* Run `java` to check the version of the bytecode interpreter:

```bash
$ java -version
```

You should get something like this:

```bash
openjdk version "13" 2019-09-17
```

* Run `javac` to check the version of the compiler:

```bash
$ javac -version
```

And you'll get a terser message:

```
javac 13
```

## Bonus task: compile and run a program

Just to make sure the toolchain is all there, I wrote a hello world
program, compiled it, and executed i:

* Create the following text file named `hello.java`:

```java
class hello {
	public static void main(String args[]){
	System.out.println("hello, world");
 }
}
```

* Run javac on it to produce an executable:

```bash
$ javac hello.java
```

There's no output from the compiler if all goes well.

* Execute the program:

Now run it:

```bash
$ java hello
```

And get the evergreen response:

```
hello, world.
```


## Exit terminal

Now feel free to close the the Terminal window or 
just type `exit` at the prompt.

```
$ exit
```

## Other things I've learned

* To learn where JAVA_HOME is:

```bash
$ /usr/libexec/java_home
```

Result will look something like this:

```
/Library/Java/JavaVirtualMachines/jdk-13.jdk/Contents/Home
```

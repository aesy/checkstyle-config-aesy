# Aesys Checkstyle Configuration

[![maven-central][maven-central-image]][maven-central-url]
[![MIT license][license-image]][license-url]

[maven-central-image]: https://img.shields.io/maven-central/v/io.aesy.checkstyle/checkstyle-config-aesy.svg
[maven-central-url]: https://search.maven.org/#search%7Cga%7C1%7Cg%3A%22io.aesy.checkstyle%22%20checkstyle-config-aesy

[license-image]: https://img.shields.io/github/license/aesy/checkstyle-config-aesy.svg
[license-url]: https://github.com/aesy/checkstyle-config-aesy/blob/master/LICENSE

This is my personal Java style configuration. It's very opiniated in terms of styling, but 
more lenient when it comes to code smells whilst not ignoring them. It is designed to aid nitpicky 
programmers in code reviews to maintain beautiful codebases and at the same time maintain good 
inter-personal relations by removing the need to make annoying comments about minor inconsistencies. 
I use it in my personal projects, but have made it public so that any lost souls out there that 
may find this and are brave enough to try something new can do so (and maybe, maaaybe, be 
pleasantly surprised).

This is a (eternal) work in progress and will most likely change based on feedback and experience.

## The though process behind the checks 

The checks are chosen based on the fact that you are not stupid. Programming means making 
decisions and you are free to use any feature available to you to achieve what want. 
You are free to use native, volatile, assert, labels, fallthroughs, even *emojis* :flushed: - 
you know what you are doing! However, unusual behaviour is harder to reason about and should 
therefore be documented, and this is enforced as much as possible. 

Everyone make mistakes and may benefit from a helpful reminder of edge cases, inconsistencies, 
and bad practices. Metrics such as class/method/file length are warnings (they are pretty forgiving
). TODO comments, redundant code blocks and overridden clone methods are warnings. Even a generic 
`throw Exception` is a warning, because in all these cases you've made the active choice of writing 
them, and they may very well stay with the project - though hopefully just for a while. The 
warnings are there to remind you they still exist (read: they are there to torment you).

Often we don't write code to be read solely by ourselves, which make readability a concern. 
Consistent code means less mental overhead when reading, but nobody likes to point out missing 
spaces or additional linebreaks in reviews, so let the linter do it for you! These checks are 
*very* strict when it comes to styling. A style violation is an **error**, because there really 
is no good reason to violate it. The styling used isn't far from the sun standard, so it isn't 
that big of a deal. It's usually no harder than running a reformat/fix command and you're done, 
given you have that set up. If there are two ways of achieving the same task, only one will 
be valid. That means, for example, that all optional braces are no longer optional. 

Unlike other strict configurations, this configuration will not require you to add extra cruft
such as default cases to all switch statements, or adding the `final` modifier to every single 
parameter and all local variables that are never reassigned (so, most...). It yields too much 
clutter for too little gain.

## TL;DR?

* No feature is forbidden.
* Code smells are warnings, talk about them in reviews.
* Style inconsistencies are errors, don't talk about them - fix them!
* There is only one way.
* No extra cruft.

## Usage

Add the following plugin to your maven `pom.xml`:

```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-checkstyle-plugin</artifactId>
    <version>3.0.0</version>
    
    <dependencies>
        <dependency>
            <groupId>io.aesy.checkstyle</groupId>
            <artifactId>checkstyle-config-aesy</artifactId>
            <version>1.0.0-SNAPSHOT</version>
        </dependency>
        <dependency>
            <groupId>com.puppycrawl.tools</groupId>
            <artifactId>checkstyle</artifactId>
            <version>8.10.1</version>
        </dependency>
    </dependencies>

    <configuration>
        <configLocation>aesy_checks.xml</configLocation>
        
        <!-- The following parameters are optional: -->
        <consoleOutput>true</consoleOutput>
        <failsOnError>true</failsOnError>
        <failOnViolation>false</failOnViolation>
        <logViolationsToConsole>true</logViolationsToConsole>
        <violationSeverity>warning</violationSeverity>
    </configuration>
    
    <executions>
        <execution>
            <id>validate</id>
            <phase>validate</phase>
            <goals>
                <goal>check</goal>
            </goals>
        </execution>
    </executions>
</plugin>
```

## IntelliJ IDEA

A IDEA configuration file will be included soon™.

## Eclipse

A Eclipse configuration fille will be included sometime™.

## Contribute
Use the [issue tracker](https://github.com/aesy/checkstyle-config-aesy/issues) to report bugs or 
make feature requests. Pull requests are welcome, but it may be a good idea to create an issue to 
discuss any changes beforehand.

## License
MIT, see [LICENSE](/LICENSE) file.

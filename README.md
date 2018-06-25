# Aesys Checkstyle Configuration

[![maven-central][maven-central-image]][maven-central-url]
[![MIT license][license-image]][license-url]

[maven-central-image]: https://img.shields.io/maven-central/v/org.aesy.checkstyle/checkstyle-config-aesy.svg
[maven-central-url]: https://search.maven.org/#search%7Cga%7C1%7Cg%3A%22org.aesy.checkstyle%22%20checkstyle-config-aesy

[license-image]: https://img.shields.io/github/license/aesy/checkstyle-config-aesy.svg
[license-url]: https://github.com/aesy/checkstyle-config-aesy/blob/master/LICENSE

This is my personal Java style configuration. I use it in my personal projects, but have made it 
public so that any lost souls out there that are brave enough to try something new can do so (and 
maybe, maaaybe, be pleasantly surprised).

## The though process behind the checks 

The checks are chosen based on the fact that you are not stupid. Programming means making 
decisions and you are free to use any feature available to you to achieve what want. But everyone 
make mistakes and may benefit from a helpful reminder of edge cases, inconsistencies, and 
bad practices.

Metrics such as class/method/file length are warnings (they are pretty forgiving). TODO comments, 
empty JavaDoc comments and overridden clone methods are warnings. Even a ignored `Exception` is a 
warning, because in all these cases you've made an active choice of writing it, even though they 
are likely temporary. The warnings are there to remind you they exist (read: torment you).

Unusual behaviour should be documented. You are free to use fallthroughs if you want to, as long as 
you document it. 

Often we don't write code to be read solely by ourselves, which make readability a big concern. 
Consistent code means less mental overhead when reading and thus these checks are *very* 
strict when it comes to styling. Style violations are ERRORS, because there really is no good 
reason to violate it. The styling used isn't far from the sun standard, so it isn't that big of a 
deal. It's usually no harder than running a reformat command and you're done, given you have that 
set up. If there are two ways of achieving the same task, only one will be valid.

This is an eternal work in progress and will most likely change based on feedback and experience.

## Usage

Add the following plugin to your `pom.xml`:

```xml
<plugin>
	<groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-checkstyle-plugin</artifactId>
    <version>3.0.0</version>
    
    <dependencies>
        <dependency>
            <groupId>org.aesy.checkstyle</groupId>
            <artifactId>checkstyle-config-aesy</artifactId>
            <version>0.0.1</version>
        </dependency>
    </dependencies>

    <configuration>
        <configLocation>aesy_checks.xml</configLocation>
        
        <!-- The following parameters are optional: -->
        <consoleOutput>true</consoleOutput>
        <failOnViolation>true</failOnViolation>
        <logViolationsToConsole>true</logViolationsToConsole>
        <violationSeverity>error</violationSeverity>
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

## Contribute
Use the [issue tracker](https://github.com/aesy/checkstyle-config-aesy/issues) to report bugs or 
make feature requests. Pull requests are welcome, but it may be a good idea to create an issue to 
discuss any changes beforehand.

## License
MIT, see [LICENSE](/LICENSE) file.

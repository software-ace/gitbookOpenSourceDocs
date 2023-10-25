---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# 🚀 Getting Started with Rest Assured

Now that you have the prerequisites for REST ASSURED, you are ready to start

* The official Getting Started documentation [https://github.com/rest-assured/rest-assured/wiki/GettingStarted](https://github.com/rest-assured/rest-assured/wiki/GettingStarted), I will quote what I will use from it down below

***

* Create a maven project
* Add the following dependency to your pom.xml file:

```xml
<dependency>
    <groupId>io.rest-assured</groupId>
    <artifactId>rest-assured</artifactId>
    <version>5.3.2</version>
    <scope>test</scope>
</dependency>
<dependency>
    <groupId>org.testng</groupId>
    <artifactId>testng</artifactId>
    <version>7.8.0</version>
    <scope>test</scope>
</dependency>
```

{% hint style="warning" %}
1. You should place rest-assured before the TestNG dependency declaration in your pom.xml / build.gradle in order to make sure that the correct version of Hamcrest is used.
2. REST Assured includes JsonPath and XmlPath as transitive dependencies
{% endhint %}

* Standalone `JsonPath` (included if you depend on the `rest-assured` artifact). Makes it easy to parse JSON documents.
* Stand-alone `XmlPath` (included if you depend on the `rest-assured` artifact). Makes it easy to parse XML documents.
*   If you want to validate that a JSON response conforms to a [Json Schema](http://json-schema.org/) you can use the `json-schema-validator` module:

    Maven:

    ```xml
    <dependency>
          <groupId>io.rest-assured</groupId>
          <artifactId>json-schema-validator</artifactId>
          <version>5.3.2</version>
          <scope>test</scope>
    </dependency>
    ```

Refer to the [documentation](https://github.com/rest-assured/rest-assured/wiki/Usage#json-schema-validation) for more info.

*   #### Java 9+ <a href="#user-content-java-9" id="user-content-java-9"></a>

    When using Java 9+ and find yourself having problems with [split packages](https://www.logicbig.com/tutorials/core-java-tutorial/modules/split-packages.html) you can depend on:

    ```xml
    <dependency>
       <groupId>io.rest-assured</groupId>
       <artifactId>rest-assured-all</artifactId>
       <version>5.3.2</version>
       <scope>test</scope>
    </dependency>
    ```

    instead of just `rest-assured`.

***

### Static Imports

* In order to use REST assured effectively it's recommended to statically import methods from the following classes like this:

```java
import static io.restassured.RestAssured.*
import static io.restassured.matcher.RestAssuredMatchers.*
import static org.hamcrest.Matchers.*
```

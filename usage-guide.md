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

# 👨💻 Usage Guide

## [Static imports](https://github.com/rest-assured/rest-assured/wiki/Usage#static-imports) <a href="#user-content-static-imports" id="user-content-static-imports"></a>

In order to use REST assured effectively it's recommended to statically import methods from the following classes:

```
io.restassured.RestAssured.*
io.restassured.matcher.RestAssuredMatchers.*
org.hamcrest.Matchers.*
```

***

## Parameters in RESTful APIs

Let's take a quick look at the parameters in RESTful APIs. Basically, there are two types of parameters.

* **Path Parameters**

where the parameter value is simply part of the URL that you call when you invoke the API.

* http://api.zippopotam.us/**us**/**90210**
* http://api.zippopotam.us/**ca**/**B2R**

So, for example, US and 90210 are path parameters. But also, in the last example that we saw in the previous slide, CA and B2R are different values for the same path parameters.

* **Query Parameters**

which we can recognize by the question mark (?) followed by key/value tuples separated by an equal sign.

So, for example:

* https://duckduckgo.com/?**q=cats**
* https://www.google.com/search?**q=cats**

For this specific API, you specify query parameters with a key `q` and a value that can contain any sort of thing like `cats`

***

## Simple HTTP request examples

Here are examples of all the common HTTP request methods (GET, POST, PUT, PATCH, DELETE) using Rest-Assured

<figure><img src="https://miro.medium.com/max/4318/1*6cjGAevnut9YuDmprV1Qmw.png" alt=""><figcaption></figcaption></figure>

### Get Request:

```java
import static io.restassured.RestAssured;
import org.testng.annotations.Test;

public class GetRequestExample {

    @Test
    public void getRequestExample() {
             given()
            .when()
            .get("https://jsonplaceholder.typicode.com/posts/1")
            .then()
            .statusCode(200)
            .log().all();  // Log the response
    }
}
```

### POST Request:

```java
import static io.restassured.RestAssured;
import io.restassured.http.ContentType;
import org.testng.annotations.Test;

public class PostRequestExample {

    @Test
    public void postRequestExample() {
        String requestBody = "{ \"title\": \"foo\", \"body\": \"bar\", \"userId\": 1 }";
             given()
            .contentType(ContentType.JSON)            
            .body(requestBody)
            .when()
            .post("https://jsonplaceholder.typicode.com/posts")
            .then()
            .statusCode(201)
            .log().all();  // Log the response
    }
}
```

{% hint style="info" %}
Remember: the `PUT` request updates the whole object, but the `PATCH` request updates a specific key value in the object
{% endhint %}

### PUT Request:

```java
import static io.restassured.RestAssured;
import io.restassured.http.ContentType;
import org.testng.annotations.Test;

public class PutRequestExample {

    @Test
    public void putRequestExample() {
 
 String requestBody = "{ \"id\": 1, \"title\": \"updated title\", \"body\": \"updated body\", \"userId\": 1 }";

             given()
            .contentType(ContentType.JSON)
            .body(requestBody)
            .when()
            .put("https://jsonplaceholder.typicode.com/posts/1")
            .then()
            .statusCode(200)
            .log().all();  // Log the response
    }
}
```

### PATCH Request:

```java
import static io.restassured.RestAssured;
import io.restassured.http.ContentType;
import org.testng.annotations.Test;

public class PatchRequestExample {

    @Test
    public void patchRequestExample() {
        String requestBody = "{ \"title\": \"updated title\" }";

            given()
            .contentType(ContentType.JSON)
            .body(requestBody)
            .when()
            .patch("https://jsonplaceholder.typicode.com/posts/1")
            .then()
            .statusCode(200)
            .log().all();  // Log the response
    }
}
```

### DELETE Request:

```java
import static io.restassured.RestAssured;
import org.testng.annotations.Test;

public class DeleteRequestExample {

    @Test
    public void deleteRequestExample() {
            given()
            .when()
            .delete("https://jsonplaceholder.typicode.com/posts/1")
            .then()
            .statusCode(200)
            .log().all();  // Log the response
    }
}
```

***

## Using TestNG Data Provider

Imagine you write a separate test code for every test you need to do :scream: because you know, you have different inputs for the same test most of the time &#x20;

here comes TestNG to save the day! :superhero: with its Data Provider feature.


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

# 📖 Usage Guide

## Simple HTTP request examples

Here are examples of all the common HTTP request methods (GET, POST, PUT, PATCH, DELETE) using Rest-Assured

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


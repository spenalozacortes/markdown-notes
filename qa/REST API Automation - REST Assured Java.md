# REST API basics and terminology

## Understanding GET, POST, PUT, DELETE HTTP CRUD operations of API

**End point/Base URI**
Address where API is hosted on the server.

HTTP methods which are commonly used to communicate with REST APIs are GET, POST, PUT, and DELETE.

**GET**
The GET method is used to extract information from the given server using a given URI. While using GET request, it should only extract data and should have no other effect on the data. No payload/body required.

**How to send input data in GET?** Using query parameters.

**POST**
A POST request is used to send data to the server, for example, customer information, file upload, etc. using HTML forms.

**How to send input data in POST?** Using form parameters/body payload.

**PUT**
Replaces all current representations of the target resource with the uploaded content.

**DELETE**
Removes all current representations of the target resource given by a URI.

## What are path, query parameters & headers in REST API

**Resources**
Resources represent API/Collection which can be accessed from the server.

google.com/maps
google.com/search
google.com/images

**Path parameters**
Path parameters are variable parts of a URL path. They are typically used to point to a specific resource within a collection, such as a user identified by ID.

google.com/images/1123343
amazon.com/orders/112

**Query parameters**
Query parameters is used to sort/filter the resources. 

Query parameters are identified with ?

amazon.com/orders?sort_by=2/20/2020

**Headers/Cookies**
Headers represent the metadata associated with the API request and response. In layman terms, we were sending additional details to API to process our request.

Example: authorization details.

**End point request can be constructed as below**
Base URL/resource/(query/path) parameters

# REST Assured setup for API automation testing

## Setting up Java with system variables

**What is REST Assured?**
REST Assured is a Java based library that is used to test RESTful web services/APIs.

```bash
/usr/libexec/java_home -V

export JAVA_HOME=

source .bashrc
```

## Setting up REST Assured Maven project with Eclipse

1. Automatic standard project skeleton creation
2. Ease of adding project dependencies -> mvnrepository.com
3. Seamless integration with CI/CD

**Hamcrest**

## Build REST API automation test to add place and validate status codes

1. **Given**. All input details.
2. **When**. Submit the API. Resource, HTTP method.
3. **Then**. Validate the response.

```java
import static io.restassured.RestAssured.*;
```
 
```java
public class Basics {
    public static void main(String[] args) {
        // Validate if Add Place API is working as expected

        RestAssured.baseURI = "https://rahulshettyacademy.com";
        given().log().all()
            .queryParam("key", "qaclick123")
            .header("Content-Type", "application/json")
            .body("{\n" +
                "  \"location\": {\n" +
                "    \"lat\": -38.383494,\n" +
                "    \"lng\": 33.427362\n" +
                "  },\n" +
                "  \"accuracy\": 50,\n" +
                "  \"name\": \"Frontline house\",\n" +
                "  \"phone_number\": \"(+91) 983 893 3937\",\n" +
                "  \"address\": \"29, side layout, cohen 09\",\n" +
                "  \"types\": [\n" +
                "    \"shoe park\",\n" +
                "    \"shop\"\n" +
                "  ],\n" +
                "  \"website\": \"https://rahulshettyacademy.com\",\n" +
                "  \"language\": \"French-IN\"\n" +
                "}\n")
        .when()
            .post("maps/api/place/add/json")
        .then().log().all()
            .assertThat().statusCode(200);
    }
}
```

# Validating the REST API responses

## Assertions on JSON response body and headers through automated code

```java
.body("scope", equalTo("APP"))
.header("server", "Apache/2.4.52 (Ubuntu)")
```

```java
// Payload.java
public class Payload {

    public static String addPlace() {
        return "{\n" +
                "  \"location\": {\n" +
                "    \"lat\": -38.383494,\n" +
                "    \"lng\": 33.427362\n" +
                "  },\n" +
                "  \"accuracy\": 50,\n" +
                "  \"name\": \"Frontline house\",\n" +
                "  \"phone_number\": \"(+91) 983 893 3937\",\n" +
                "  \"address\": \"29, side layout, cohen 09\",\n" +
                "  \"types\": [\n" +
                "    \"shoe park\",\n" +
                "    \"shop\"\n" +
                "  ],\n" +
                "  \"website\": \"https://rahulshettyacademy.com\",\n" +
                "  \"language\": \"French-IN\"\n" +
                "}\n";
    }
}
```

```java
// Basics.java
public static void main(String[] args) {
    // Validate if Add Place API is working as expected

    RestAssured.baseURI = "https://rahulshettyacademy.com";
    given().log().all()
        .queryParam("key", "qaclick123")
        .header("Content-Type", "application/json")
        .body(Payload.addPlace())
    .when()
        .post("maps/api/place/add/json")
    .then().log().all()
        .assertThat()
            .statusCode(200)
            .body("scope", equalTo("APP"))
            .header("server", "Apache/2.4.52 (Ubuntu)");
}
```

## Parsing the JSON response body using JsonPath class

```java
.extract().response().asString()
```

```java
JsonPath js = new JsonPath(response);
String placeId = js.getString("place_id");
```

```java
public static void main(String[] args) {
    // Validate if Add Place API is working as expected

    RestAssured.baseURI = "https://rahulshettyacademy.com";
    String response =
        given().log().all()
            .queryParam("key", "qaclick123")
            .header("Content-Type", "application/json")
            .body(Payload.addPlace())
        .when()
            .post("maps/api/place/add/json")
        .then()
            .assertThat()
                .statusCode(200)
                .body("scope", equalTo("APP"))
                .header("server", "Apache/2.4.52 (Ubuntu)")
                .extract().response().asString();

    JsonPath js = new JsonPath(response);
    String placeId = js.getString("place_id");
    System.out.println(placeId);
}
```

## Integrating the multiple APIs with common JSON response values

```java
given().log().all()
    .queryParam("key", "qaclick123")
    .header("Content-Type", "application/json")
    .body("{\n" +
        "\"place_id\":\"" + placeId + "\",\n" +
        "\"address\":\"70 winter walk, USA\",\n" +
        "\"key\":\"qaclick123\"\n" +
        "}")
.when()
    .put("maps/api/place/update/json")
.then().assertThat().log().all()
    .statusCode(200)
    .body("msg", equalTo("Address successfully updated"));
```

## Building end to end automation using GET, POST and PUT HTTP methods

```java
String getPlaceResponse = given().log().all()
	    .queryParam("key", "qaclick123")
	    .queryParam("place_id", placeId)
    .when()
        .get("maps/api/place/get/json")
    .then().assertThat().log().all()
        .statusCode(200).extract().response().asString();
```

## Importance of JUnit / TestNG assertions in validating the responses

```java
Assert.assertEquals(actualAddress, newAddress);
```

```java
// ReusableMethods.java
public class ReusableMethods {

    public static JsonPath rawToJson(String response) {
        JsonPath js1 = new JsonPath(response);
        return js1;
    }
}
```

```java
// Basics.java
public class Basics {
    public static void main(String[] args) {

        RestAssured.baseURI = "https://rahulshettyacademy.com";
        String response =
            given().log().all()
                .queryParam("key", "qaclick123")
                .header("Content-Type", "application/json")
                .body(Payload.addPlace())
            .when()
                .post("maps/api/place/add/json")
            .then()
                .assertThat()
                    .statusCode(200)
                    .body("scope", equalTo("APP"))
                    .header("server", "Apache/2.4.52 (Ubuntu)")
                    .extract().response().asString();

        JsonPath js = new JsonPath(response);
        String placeId = js.getString("place_id");
        System.out.println(placeId);

        String newAddress = "Summer walk, Africa";

        given().log().all()
            .queryParam("key", "qaclick123")
            .header("Content-Type", "application/json")
            .body("{\n" +
                "\"place_id\":\"" + placeId + "\",\n" +
                "\"address\":\"" + newAddress + "\",\n" +
                "\"key\":\"qaclick123\"\n" +
                "}")
        .when()
            .put("maps/api/place/update/json")
        .then().assertThat().log().all()
            .statusCode(200)
            .body("msg", equalTo("Address successfully updated"));

        String getPlaceResponse = 
	        given().log().all()
                .queryParam("key", "qaclick123")
                .queryParam("place_id", placeId)
            .when()
                .get("maps/api/place/get/json")
            .then().assertThat().log().all()
                .statusCode(200).extract().response().asString();

        JsonPath js1 = ReusableMethods.rawToJson(getPlaceResponse);
        String actualAddress = js1.getString("address");

        Assert.assertEquals(actualAddress, newAddress);
    }
}
```

# Diving in depth - Automating REST APIs

## Retrieving the JSON array size and its elements using JsonPath

```json
{
	"dashboard": {
		"purchaseAmount": 910,
		"website": "rahulshettyacademy.com"
	},

	"courses": [
		{
			"title": "Selenium Python",
			"price": 50,
			"copies": 6
		},
		{
			"title": "Cypress",
			"price": 40,
			"copies": 4
		},
		{
			"title": "RPA",
			"price": 45,
			"copies": 10
		}
	]
}
```

```java
// ComplexJsonParse.java
public static void main(String[] args) {
    JsonPath js = new JsonPath(Payload.coursePrice());
    int count = js.getInt("courses.size()");
    System.out.println(count);

    int totalAmount = js.getInt("dashboard.purchaseAmount");
    System.out.println(totalAmount);

    String titleFirstCourse = js.get("courses[0].title");
    System.out.println(titleFirstCourse);
}
```

## Iterating over every element of JSON array and accessing elements in it

```java
for (int i = 0; i < count; i++) {
    String courseTitle = js.get("courses[" + i + "].title");
    System.out.println(courseTitle);
    System.out.println(js.get("courses[" + i + "].price").toString());
}
```

## Retrieving JSON nodes on condition logic using JsonPath

```java
for (int i = 0; i < count; i++) {
    String courseTitle = js.get("courses[" + i + "].title");
    if (courseTitle.equalsIgnoreCase("RPA")) {
        int copies = js.get("courses[" + i + "].copies");
        System.out.println(copies);
        break;
    }
}
```

## Real time example to solve business logic through JSON response

```java
int sum = 0;
for (int i = 0; i < count; i++) {
    int price = js.get("courses[" + i + "].price");
    int copies = js.get("courses[" + i + "].copies");
    int amount = price * copies;
    System.out.println(amount);
    sum += amount;
}
System.out.println(sum);
int purchaseAmount = js.getInt("dashboard.purchaseAmount");
System.out.println(purchaseAmount);
```

# Handling dynamic JSON payloads with parameterization

## Sending parameters to payload from test

```java
@Test
public void addBook() {
    RestAssured.baseURI = "http://216.10.245.166";
    String response = given().header("Content-Type", "application/json").body(Payload.addBook("asfde", "646"))
        .when().post("Library/Addbook.php")
        .then().assertThat().statusCode(200)
        .extract().response().asString();
    JsonPath js = ReusableMethods.rawToJson(response);
    String id = js.get("ID");
    System.out.println(id);
}
```

## Understanding TestNG data provider for parameterization

```java
// DynamicJson.java
@DataProvider(name = "BooksData")
public Object[][] getData() {
    return new Object[][] {{"ojfwyt", "9363"}, {"cwetee", "4253"}, {"okmfet", "533"}};
}
```

## Example on parameterization API tests with multiple data sets

```java
// DynamicJson.java
@Test(dataProvider = "BooksData")
public void addBook(String isbn, String aisle) {
    RestAssured.baseURI = "http://216.10.245.166";
    String response = given().header("Content-Type", "application/json").body(Payload.addBook(isbn, aisle))
        .when().post("Library/Addbook.php")
        .then().assertThat().statusCode(200)
        .extract().response().asString();
    JsonPath js = ReusableMethods.rawToJson(response);
    String id = js.get("ID");
    System.out.println(id);
}
```

## How to handle with static JSON payloads

```java
// Basics.java
RestAssured.baseURI = "https://rahulshettyacademy.com";
String response =
    given().log().all()
        .queryParam("key", "qaclick123")
        .header("Content-Type", "application/json")
        .body(new String(Files.readAllBytes(Paths.get("C:\\Users\\Stephan\\Dropbox\\documentos\\trabajo\\a1qa\\projects\\RestAssuredBasics\\src\\test\\java\\data\\addPlace.json"))))
    .when()
        .post("maps/api/place/add/json")
    .then().assertThat()
        .statusCode(200)
        .body("scope", equalTo("APP"))
        .header("server", "Apache/2.4.52 (Ubuntu)")
        .extract().response().asString();
```

# Real world example - Automating Jira APIs

## Defining path parameters in REST Assured code using Add comment API

```java
// JiraTest.java
RestAssured.baseURI = "http://localhost:8080";

given().pathParam("id", "10100").log().all()
    .header("Content-Type", "application/json").body("{\n" +
                "    \"body\": \"Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque eget venenatis elit. Duis eu justo eget augue iaculis fermentum. Sed semper quam laoreet nisi egestas at posuere augue semper.\",\n" +
                "    \"visibility\": {\n" +
                "        \"type\": \"role\",\n" +
                "        \"value\": \"Administrators\"\n" +
                "    }\n" +
                "}")
    .when().post("/rest/api/2/issue/{id}/comment");
```

## Importance of session filter cookie in REST Assured code

```java
// JiraTest.java

RestAssured.baseURI = "http://localhost:8080";

SessionFilter session = new SessionFilter();

String response = given().header("Content-Type", "application/json").body("{ \"username\": \"miestasfanjo\", \"password\": \"Abita1.618\" }")
    .log().all()
    .filter(session)
    .when().post("/rest/auth/1/session")
    .then().log().all().extract().response().asString();

given().pathParam("id", "10100").log().all()
    .header("Content-Type", "application/json").body("{\n" +
                "    \"body\": \"Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque eget venenatis elit. Duis eu justo eget augue iaculis fermentum. Sed semper quam laoreet nisi egestas at posuere augue semper.\",\n" +
                "    \"visibility\": {\n" +
                "        \"type\": \"role\",\n" +
                "        \"value\": \"Administrators\"\n" +
                "    }\n" +
                "}")
    .filter(session)
    .when().post("/rest/api/2/issue/{id}/comment")
    .then().log().all().assertThat().statusCode(201);
```

## Sending attachments to REST API using multipart method in REST Assured

From Jira page, on top right, Select Settings Icon > System > Attachments (under Advanced): Set **Allow Attachments** to **ON**

```shell
curl -D- -u admin:admin -X POST -H "X-Atlassian-Token: no-check" -F "file=@myfile.txt" http://myhost/rest/api/2/issue/TEST-123/attachments
```

```java
// JiraTest.java
given().header("X-Atlassian-Token", "no-check").filter(session).pathParam("id", "10100")
    .header("Content-Type", "multipart/form-data")
    .multiPart("file", new File("jira.txt"))
    .when().post("/rest/api/2/issue/{id}/attachments")
    .then().log().all().assertThat().statusCode(200);
```

## Integrating query params and path params in single test to restrict results

```java
// JiraTest.java
String issueDetails = given().filter(session).pathParam("id", "10100")
    .queryParam("fields", "comment")
    .when().get("/rest/api/2/issue/{id}")
    .then().log().all().extract().response().asString();
```

## Parsing complex Jira JSON response to retrieve the added comment with code logic

```java
// JiraTest.java
JsonPath js1 = new JsonPath(issueDetails);
int commentsCount = js1.getInt("fields.comment.comments.size()");
for (int i = 0; i < commentsCount; i++) {
    String commentIdIssue = js1.get("fields.comment.comments[" + i + "].id").toString();
    if(commentIdIssue.equalsIgnoreCase(commentId)) {
        String message = js1.get("fields.comment.comments[" + i + "].body").toString();
    }
}
```

## Importance of assertions and HTTP validations on REST APIs

```java
// JiraTest.java
Assert.assertEquals(message, expectedMessage);
```

```java
// JiraTest.java
String response = given().relaxedHTTPSValidation()
```

```java
// JiraTest.java
public class JiraTest {
    public static void main(String[] args) {

        RestAssured.baseURI = "http://localhost:8080";

        SessionFilter session = new SessionFilter();

        String response = given().relaxedHTTPSValidation()
                .header("Content-Type", "application/json").body("{ \"username\": \"miestasfanjo\", \"password\": \"Abita1.618\" }")
                .log().all()
                .filter(session)
                .when().post("/rest/auth/1/session")
                .then().log().all().extract().response().asString();

        String expectedMessage = "Hi how are you?";

        String addCommentResponse = given().pathParam("id", "10100").log().all()
                .header("Content-Type", "application/json").body("{\n" +
                "    \"body\": \"" + expectedMessage + "\",\n" +
                "    \"visibility\": {\n" +
                "        \"type\": \"role\",\n" +
                "        \"value\": \"Administrators\"\n" +
                "    }\n" +
                "}")
                .filter(session)
                .when().post("/rest/api/2/issue/{id}/comment")
                .then().log().all().assertThat().statusCode(201)
                .extract().response().asString();

        JsonPath js = new JsonPath(addCommentResponse);
        String commentId = js.getString("id");

        given().header("X-Atlassian-Token", "no-check").filter(session).pathParam("id", "10100")
                .header("Content-Type", "multipart/form-data")
                .multiPart("file", new File("jira.txt"))
                .when().post("/rest/api/2/issue/{id}/attachments")
                .then().log().all().assertThat().statusCode(200);

        String issueDetails = given().filter(session).pathParam("id", "10100")
                .queryParam("fields", "comment")
                .when().get("/rest/api/2/issue/{id}")
                .then().log().all().extract().response().asString();

        JsonPath js1 = new JsonPath(issueDetails);
        int commentsCount = js1.getInt("fields.comment.comments.size()");
        for (int i = 0; i < commentsCount; i++) {
            String commentIdIssue = js1.get("fields.comment.comments[" + i + "].id").toString();
            if(commentIdIssue.equalsIgnoreCase(commentId)) {
                String message = js1.get("fields.comment.comments[" + i + "].body").toString();
                Assert.assertEquals(message, expectedMessage);
            }
        }

    }
}
```

# Handling OAuth 2.0 authorization grant type - Client credentials

## Practical example on OAuth 2.0 with its contract details for testing

**Authorization server endpoint**

Form parameters:
- client_id
- client_secret
- grant_type: client_credentials
- scope: trust

**API endpoint (secured by OAuth)**

Query parameter:
- access_token

## REST Assured automation script for OAuth end to end API test

```java
public class OAuthCredentials {

    @Test
    public void test() {
        String response = given()
                .formParam("client_id", "692183103107-p0m7ent2hk7suguv4vq22hjcfhcr43pj.apps.googleusercontent.com")
                .formParam("client_secret", "erZOWM9g3UtwNRj340YYaK_W")
                .formParam("grant_type", "client_credentials")
                .formParam("scope", "trust")
                .when().log().all()
                .post("https://rahulshettyacademy.com/oauthapi/oauth2/resourceOwner/token")
                .asString();
        JsonPath js = new JsonPath(response);
        String accessToken = js.getString("access_token");

        String response2 = given()
                .queryParam("access_token", accessToken)
                .when().log().all()
                .get("https://rahulshettyacademy.com/oauthapi/getCourseDetails?access_token=UniCqQcOlislWWKvOFAnUQ==")
                .asString();
        System.out.println(response2);
    }
}
```

# Handling Google/Facebook OAuth 2.0 authorization Grant types

## Understand Grant type authorization flow with real time example

**Why applications rely on other (Google or Facebook) authentications**
- No data breach headaches for application
- Need not maintain user profile data
- This also allows richer websites by allowing disparate applications to talk to each other
 
Grant types: authorization code or client credentials
## Flow procedure in achieving OAuth 2.0 authentication mechanism

**Get code**
- scope
- auth_url
- client_id
- response_type: code
- redirect_uri
- state

**Exchange code**
- code
- client_id
- client_secret
- redirect_uri
- grant_type: authorization_code

**Actual request**
- access_token

## Details on practise OAuth 2.0 project to retrieve courses list

**Contract details**
- Grant type
- redirect URL / callback URL
- authorization server URL
- access token URL
- client ID
- client secret
- scope
- state
- how to pass oauth in request

**Mandatory fields for GetAuthorization code request**
**End point**: authorization server URL
**Query params**: scope, auth_url, client_id, response_type, redirect_uri
This operation should be performed on browser
**Output**: code

**Mandatory fields for GetAccessToken request**
**End point**: access token URL
**Query params**: code, client_id, client_secret, redirect_uri, grant_type
**Output**: access token

# REST Assured automation for OAuth 2.0 authorization code

## Building up REST Assured automation test for the OAuth project

```java
// OAuthTest.java
String accessTokenResponse = given().queryParams("code", "")
    .queryParams("client_id", "692183103107-p0m7ent2hk7suguv4vq22hjcfhcr43pj.apps.googleusercontent.com")
    .queryParams("client_secret", "erZOWM9g3UtwNRj340YYaK_W")
    .queryParams("redirect_uri", "https://rahulshettyacademy.com/getCourse.php")
    .queryParams("grant_type", "authorization_code")
    .when().log().all().post("https://www.googleapis.com/oauth2/v4/token").asString();

JsonPath js = new JsonPath(accessTokenResponse);
String accessToken = js.getString("access_token");

String response = given().queryParam("access_token", accessToken)
    .when().log().all().get("https://rahulshettyacademy.com/getCourse.php")
                .asString();
System.out.println(response);
```

## Integration Web UI automation to generate authorization code

```java
// OAuthTest.java
WebDriver driver = new ChromeDriver();
driver.get("https://accounts.google.com/o/oauth2/v2/auth?scope=https://www.googleapis.com/auth/userinfo.email&auth_url=https://accounts.google.com/o/oauth2/v2/auth&client_id=692183103107-p0m7ent2hk7suguv4vq22hjcfhcr43pj.apps.googleusercontent.com&response_type=code&redirect_uri=https://rahulshettyacademy.com/getCourse.php");
driver.findElement(By.cssSelector("input[type='email']")).sendKeys("srinath19830");
driver.findElement(By.cssSelector("input[type='email']")).sendKeys(Keys.ENTER);
Thread.sleep(3000);
driver.findElement(By.cssSelector("input[type='password']")).sendKeys("password");
driver.findElement(By.cssSelector("input[type='email']")).sendKeys(Keys.ENTER);
Thread.sleep(4000);
String url = driver.getCurrentUrl();
```

## Formatting URL string to retrieve code using Java methods

```java
// OAuthTest.java
String partialCode = url.split("code=")[1];
String code = partialCode.split("&scope")[0];

String accessTokenResponse = given().queryParams("code", code)
    .urlEncodingEnabled(false)
```

# Deserialization using POJO classes with REST Assured

## What is serialization and deserialization in REST Assured

**Serialization** in REST Assured context is a process of converting a Java object into request body (payload).

REST Assured also supports **deserialization** by converting response body back to Java object.

**Advantages**
- Easy to parse and extract response (JSON/XML) values if they are wrapped as Java object.
- User friendly methods can be created which makes code more readable.

**Design approach**
- Java object is constructed with the support of POJO classes.
- POJO classes are created base on the request/response payload.

**What additional libraries required**
For JSON you need to have either Jackson, Jackson2, Gson or Johnzon in the classpath and for XML you need JAXB.

## Strategies in parsing complex nested JSON using POJO classes

```json
{ 
	"instructor": "RahulShetty", 
	"url": "rahulshettycademy.com", 
	"services": "projectSupport", 
	"expertise": "Automation", 
	"courses": { 
		"webAutomation": [ 
			{ 
				"courseTitle": "Selenium Webdriver Java", "price": "50" 
			}, 
			{ 
				"courseTitle": "Cypress",
                "price": "40"
            },
            {
                "courseTitle": "Protractor",
                "price": "40"
            }
        ],
        "api": [
            {
                "courseTitle": "Rest Assured Automation using Java",
                "price": "50"
            },
            {
                "courseTitle": "SoapUI Webservices testing",
                "price": "40"
            }
        ],
        "mobile": [
            {
                "courseTitle": "Appium-Mobile Automation using Java",
                "price": "50"
            }
        ]
    },
    "linkedIn": "https://www.linkedin.com/in/rahul-shetty-trainer/"
}
```

```java
// Courses.java
public class Courses {
    private String webAutomation;
    private String api;
    private String mobile;

    public String getWebAutomation() {
        return webAutomation;
    }

    public void setWebAutomation(String webAutomation) {
        this.webAutomation = webAutomation;
    }

    public String getApi() {
        return api;
    }

    public void setApi(String api) {
        this.api = api;
    }

    public String getMobile() {
        return mobile;
    }

    public void setMobile(String mobile) {
        this.mobile = mobile;
    }
}
```

```java
// GetCourse.java
public class GetCourse {
    private String url;
    private String services;
    private String expertise;
    private Courses courses;
    private String instructor;
    private String linkedIn;

    public String getUrl() {
        return url;
    }

    public void setUrl(String url) {
        this.url = url;
    }

    public String getServices() {
        return services;
    }

    public void setServices(String services) {
        this.services = services;
    }

    public String getExpertise() {
        return expertise;
    }

    public void setExpertise(String expertise) {
        this.expertise = expertise;
    }

    public Courses getCourses() {
        return courses;
    }

    public void setCourses(Courses courses) {
        this.courses = courses;
    }

    public String getInstructor() {
        return instructor;
    }

    public void setInstructor(String instructor) {
        this.instructor = instructor;
    }

    public String getLinkedIn() {
        return linkedIn;
    }

    public void setLinkedIn(String linkedIn) {
        this.linkedIn = linkedIn;
    }
}
```

## Creating POJO classes for the real time nested array JSON

```java
// WebAutomation.java
public class WebAutomation {

    private String courseTitle;
    private String price;

    public String getCourseTitle() {
        return courseTitle;
    }

    public void setCourseTitle(String courseTitle) {
        this.courseTitle = courseTitle;
    }

    public String getPrice() {
        return price;
    }

    public void setPrice(String price) {
        this.price = price;
    }
}
```

```java
// Courses.java
public class Courses {
    private List<WebAutomation> webAutomation;
    private List<Api> api;
    private List<Mobile> mobile;

    public List<WebAutomation> getWebAutomation() {
        return webAutomation;
    }

    public void setWebAutomation(List<WebAutomation> webAutomation) {
        this.webAutomation = webAutomation;
    }

    public List<Api> getApi() {
        return api;
    }

    public void setApi(List<Api> api) {
        this.api = api;
    }

    public List<Mobile> getMobile() {
        return mobile;
    }

    public void setMobile(List<Mobile> mobile) {
        this.mobile = mobile;
    }
}
```

## End to end automation examples using POJO deserialization

```java
// OAuthTest.java
GetCourse gc = given().queryParam("access_token", accessToken)
    .expect().defaultParser(Parser.JSON) //  text/html
    .when().get("https://rahulshettyacademy.com/getCourse.php")
    .as(GetCourse.class);

System.out.println(gc.getLinkedIn());
System.out.println(gc.getInstructor());
```

## Solving complex queries from JSON with simple POJO methods

```java
// OAuthTest.java
System.out.println(gc.getCourses().getApi().get(1).getCourseTitle());

List<Api> apiCourses = gc.getCourses().getApi();
for (int i = 0; i < apiCourses.size() ; i++) {
    if(apiCourses.get(i).getCourseTitle().equalsIgnoreCase("SoapUI Webservices testing")) {
        System.out.println(apiCourses.get(i).getPrice());
    }
}
```

```java
// OAuthTest.java
String[] courseTitles = {"Selenium Webdriver Java", "Cypress", "Protractor"};
ArrayList<String> a = new ArrayList<>();
List<WebAutomation> webAutomationCourses = gc.getCourses().getWebAutomation();
for(WebAutomation course : webAutomationCourses) {
    a.add(course.getCourseTitle());
}
List<String> expectedList = Arrays.asList(courseTitles);
Assert.assertTrue(a.equals(expectedList));
```

# Serialization of input payload using Google Maps API example

## Complete end to end test case with serialization implementation

```java
// Serialize.java
RestAssured.baseURI = "https://rahulshettyacademy.com";

AddPlace p = new AddPlace();
p.setAccuracy(50);
p.setAddress("29, side layout, cohen 09");
p.setLanguage("French-IN");
p.setPhone_number("(+91) 983 893 3937");
p.setWebsite("https://rahulshettyacademy.com");
p.setName("Frontline house");
List<String> myList = new ArrayList<>();
myList.add("shoe park");
myList.add("shop");
p.setTypes(myList);
Location l = new Location();
l.setLat(-38.383494);
l.setLng(33.427362);
p.setLocation(l);

Response res = given().log().all().queryParam("key", "qaclick123")
    .body(p)
    .when().post("/maps/api/place/add/json")
    .then().assertThat().statusCode(200)
    .extract().response();
```

# Understand request and response spec builders in REST Assured

## Practical example in implementing spec builders and optimize code

```java
// SpecBuilder.java
RequestSpecification req = new RequestSpecBuilder().setBaseUri("https://rahulshettyacademy.com")
    .addQueryParam("key", "qaclick123")
    .setContentType(ContentType.JSON)
    .build();

ResponseSpecification resspec = new ResponseSpecBuilder().expectStatusCode(200)
    .expectContentType(ContentType.JSON)
    .build();

RequestSpecification res = given().spec(req).body(p);

Response response = res.when().post("/maps/api/place/add/json")
    .then().spec(resspec)
    .extract().response();
```

# End to end ecommerce API example with automation concepts

## Create REST Assured automation for login call to generate Auth token

```java
// ECommerceAPI.java
RequestSpecification req = new RequestSpecBuilder().setBaseUri("https://rahulshettyacademy.com")
    .setContentType(ContentType.JSON).build();
LoginRequest loginRequest = new LoginRequest();
loginRequest.setUserEmail("prueba@gmail.com");
loginRequest.setUserPassword("Abita123");
RequestSpecification reqLogin = given().log().all().spec(req).body(loginRequest);
LoginResponse loginResponse = reqLogin.when().post("/api/ecom/auth/login")
    .then().log().all().extract().response().as(LoginResponse.class);
```

## Automate post calls which has form parameters and attachments using REST Assured

```java
// ECommerceAPI.java
RequestSpecification addProductBaseReq = new RequestSpecBuilder().setBaseUri("https://rahulshettyacademy.com")
    .addHeader("authorization", token)
    .build();
RequestSpecification reqAddProduct = given().log().all().spec(addProductBaseReq)
    .param("productName", "Laptop")
    .param("productAddedBy", userId)
    .param("productCategory", "fashion")
    .param("productSubCategory", "shirts")
    .param("productPrice", "11500")
    .param("productDescription", "Lenovo")
    .param("productFor", "men")
    .multiPart("productImage", new File("C:\\Users\\Stephan\\Downloads\\jenkinsmalvado.png"));
String addProductResponse = reqAddProduct.when().post("/api/ecom/product/add-product")
    .then().log().all().extract().response().asString();
JsonPath js = new JsonPath(addProductResponse);
String productId = js.get("productId");
```

## Implement POJO classes to build nested JSON for create order for product added

```java
// ECommerceAPI.java
// Create order
RequestSpecification createOrderBaseReq = new RequestSpecBuilder().setBaseUri("https://rahulshettyacademy.com")
    .addHeader("authorization", token)
    .setContentType(ContentType.JSON)
    .build();
OrderDetail orderDetail = new OrderDetail();
orderDetail.setCountry("Mexico");
orderDetail.setProductOrderedId(productId);
List<OrderDetail> orderDetailList = new ArrayList<>();
orderDetailList.add(orderDetail);
Orders orders = new Orders();
orders.setOrders(orderDetailList);
RequestSpecification createOrderReq = given().log().all().spec(createOrderBaseReq).body(orders);
String responseAddOrder = createOrderReq.when().post("/api/ecom/order/create-order")
    .then().log().all()
    .extract().response().asString();
System.out.println(responseAddOrder);
```

## Script implementation with Delete product using path parameters & HTTPs relaxed

```java
// ECommerceAPI.java
RequestSpecification reqLogin = given().relaxedHTTPSValidation().log().all().spec(req).body(loginRequest);
```

```java
// ECommerceAPI.java
// Delete product
RequestSpecification deleteProdBaseReq = new RequestSpecBuilder().setBaseUri("https://rahulshettyacademy.com")
    .addHeader("authorization", token)
    .setContentType(ContentType.JSON)
    .build();
RequestSpecification deleteProdReq = given().log().all().spec(deleteProdBaseReq)
    .pathParam("productId", productId);
String deleteProdResponse = deleteProdReq.when()
    .delete("/api/ecom/product/delete-product/{productId}")
    .then().log().all()
    .extract().response().asString();
JsonPath js1 = new JsonPath(deleteProdResponse);
Assert.assertEquals(js1.get("message"), "Product Deleted Successfully");
```

```java
// ECommerceAPI.java
public class ECommerceAPI {
    public static void main(String[] args) {
        RequestSpecification req = new RequestSpecBuilder().setBaseUri("https://rahulshettyacademy.com")
                .setContentType(ContentType.JSON).build();
        LoginRequest loginRequest = new LoginRequest();
        loginRequest.setUserEmail("prueba@gmail.com");
        loginRequest.setUserPassword("Abita123");
        RequestSpecification reqLogin = given().relaxedHTTPSValidation().log().all().spec(req).body(loginRequest);
        LoginResponse loginResponse = reqLogin.when().post("/api/ecom/auth/login")
                .then().log().all().extract().response().as(LoginResponse.class);
        String token = loginResponse.getToken();
        String userId = loginResponse.getUserId();

        // Add product
        RequestSpecification addProductBaseReq = new RequestSpecBuilder().setBaseUri("https://rahulshettyacademy.com")
                .addHeader("authorization", token)
                .build();
        RequestSpecification reqAddProduct = given().log().all().spec(addProductBaseReq)
                .param("productName", "Laptop")
                .param("productAddedBy", userId)
                .param("productCategory", "fashion")
                .param("productSubCategory", "shirts")
                .param("productPrice", "11500")
                .param("productDescription", "Lenovo")
                .param("productFor", "men")
                .multiPart("productImage", new File("C:\\Users\\Stephan\\Downloads\\jenkinsmalvado.png"));
        String addProductResponse = reqAddProduct.when().post("/api/ecom/product/add-product")
                .then().log().all().extract().response().asString();
        JsonPath js = new JsonPath(addProductResponse);
        String productId = js.get("productId");

        // Create order
        RequestSpecification createOrderBaseReq = new RequestSpecBuilder().setBaseUri("https://rahulshettyacademy.com")
                .addHeader("authorization", token)
                .setContentType(ContentType.JSON)
                .build();
        OrderDetail orderDetail = new OrderDetail();
        orderDetail.setCountry("Mexico");
        orderDetail.setProductOrderedId(productId);
        List<OrderDetail> orderDetailList = new ArrayList<>();
        orderDetailList.add(orderDetail);
        Orders orders = new Orders();
        orders.setOrders(orderDetailList);
        RequestSpecification createOrderReq = given().log().all().spec(createOrderBaseReq).body(orders);
        String responseAddOrder = createOrderReq.when().post("/api/ecom/order/create-order")
                .then().log().all()
                .extract().response().asString();
        System.out.println(responseAddOrder);

        // Delete product
        RequestSpecification deleteProdBaseReq = new RequestSpecBuilder().setBaseUri("https://rahulshettyacademy.com")
                .addHeader("authorization", token)
                .setContentType(ContentType.JSON)
                .build();
        RequestSpecification deleteProdReq = given().log().all().spec(deleteProdBaseReq)
                .pathParam("productId", productId);
        String deleteProdResponse = deleteProdReq.when()
                .delete("/api/ecom/product/delete-product/{productId}")
                .then().log().all()
                .extract().response().asString();
        JsonPath js1 = new JsonPath(deleteProdResponse);
        Assert.assertEquals(js1.get("message"), "Product Deleted Successfully");
    }
}
```

# Maven and Cucumber basics

## Importance of Maven in framework development
Apache Maven is a software project management tool for Java frameworks.

**Why Maven?**
- Central repository to get dependencies
- Maintaining common structure across the organization
- Flexibility in integrating with CI tools
- Plugins for test framework execution

**Understanding Maven terminologies**
- **Artifact**: An artifact is a file, usually a JAR, that gets deployed to a Maven repository
- **GroupId**: GroupId will identify your project uniquely across all projects
- **archetype:generate**: Generates a new project from an archetype

## Understanding terminologies of Maven

```shell
mvn archetype:generate -DgroupId=Qaclickacademy -DartifactId=Mavenjava -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
```

```shell
mvn eclipse:eclipse
```

## Introduction to Cucumber

**What is framework?**
In any real time project whenever automation scripts are developed, one should come up with an execution system called framework to run and maintain automated tests.

**What is cucumber?**
Cucumber is the BDD framework for running automated tests.
Cucumber does not automate your test cases!

**When my tests are already automated and can run, what Cucumber does?**
Data driven, parameterization, execution controls, hooks, reports, automation utilities and many more.

**When you say automated tests, what type of automation test cases does Cucumber support?**
Any test (web, mobile, API, unit testing) which is written in Java/Ruby supported by Cucumber.

**How Cucumber is unique and best from other test frameworks (keyword, data driven, hybrid) in the market?**
Because test cases/requirements are defined with on BDD methodology (Gherkin syntax). No coding is required to implement framework functionalities.

## Understanding Cucumber dependencies

cucumber-java
cucumber-junit

## Understand the terminologies of automation

Feature
Step definition
JUnit Test runner

```gherkin
Feature: Application Login  
    
  Scenario: Home page default login  
    Given User is on NetBanking landing page  
    When User login into application with username and password  
    Then Home page is populated  
    And Cards are displayed
```

## Mapping step definition to feature file

```java
// StepDefinition.java
public class StepDefinition {

    @Given("^User is on NetBanking landing page$")
    public void user_is_on_NetBanking_landing_page() {

    }
    
    @When("^User login into application with username and password$")
    public void user_login_into_application_with_username_and_password() {
        
    }
}
```

## Running the tests with Test Runner

```java
// TestRunner.java
@RunWith(Cucumber.class)
@CucumberOptions(
    features = "src/test/java/features",
    glue = "stepDefinitions")
public class TestRunner {
}
```

## How to reuse functions with different data

```gherkin
Feature: Application Login

  Scenario: Home page default login
    Given User is on NetBanking landing page
    When User login into application with "jin" and "1234"
    Then Home page is populated
    And Cards displayed are "true"
```

```java
// StepDefinition.java
@When("User login into application with {string} and {string}")
public void user_login_into_application_with_and(String string, String string2) {
    System.out.println(string);
    System.out.println(string2);
}

@Then("Cards displayed are {string}")
public void cards_displayed_are(String string) {
    System.out.println(string);
}
```

# Cucumber BDD API framework development from scratch - 1

## Creating Maven project with Cucumber REST Assured dependencies

Cucumber Java
Cucumber JUnit
REST Assured
Jackson Databind
## Building Cucumber Feature file for REST Assured API tests

```gherkin
Feature: Validating Place APIs

  Scenario: Verify if Place is being successfully added using AddPlaceAPI
    Given Add Place Payload
    When user calls "AddPlaceAPI" with Post http request
    Then the API call got success with status code 200
    And "status" in response body is "OK"
    And "scope" in response body is "APP"
```

## Building Test Runner and step definition files for Add Place API feature test

```java
@RunWith(Cucumber.class)
@CucumberOptions(features = "src/test/java/features", glue = {"stepDefinitions"})
public class TestRunner {
}
```

## Running the test in Cucumber standards with necessary configuration changes

```java
public class Utils {

    RequestSpecification req;

    public RequestSpecification requestSpecification() {
        req = new RequestSpecBuilder().setBaseUri("https://rahulshettyacademy.com")
                .addQueryParam("key", "qaclick123")
                .setContentType(ContentType.JSON).build();
        return req;
    }
}
```

```java
public class TestDataBuild {

    public AddPlace addPlacePayload() {
        AddPlace p = new AddPlace();
        p.setAccuracy(50);
        p.setAddress("29, side layout, cohen 09");
        p.setLanguage("French-IN");
        p.setPhone_number("(+91) 983 893 3937");
        p.setWebsite("https://rahulshettyacademy.com");
        p.setName("Frontline house");
        List<String> myList = new ArrayList<>();
        myList.add("shoe park");
        myList.add("shop");
        p.setTypes(myList);
        Location l = new Location();
        l.setLat(-38.383494);
        l.setLng(33.427362);
        p.setLocation(l);

        return p;
    }
}
```

```java
// StepDefinition.java
@Given("Add Place Payload")
public void add_Place_Payload() {
    resspec = new ResponseSpecBuilder().expectStatusCode(200)
        .expectContentType(ContentType.JSON).build();

    res = given().spec(requestSpecification()).body(data.addPlacePayload());
}
```

## Building utility files and implement logging feature in framework

```java
// Utils.java
public RequestSpecification requestSpecification() throws FileNotFoundException {
    PrintStream log = new PrintStream(new FileOutputStream("logging.txt"));
    req = new RequestSpecBuilder().setBaseUri("https://rahulshettyacademy.com")
        .addQueryParam("key", "qaclick123")
        .addFilter(RequestLoggingFilter.logRequestTo(log))
        .addFilter(ResponseLoggingFilter.logResponseTo(log))
        .setContentType(ContentType.JSON)
        .build();
    return req;
}
```

## Implement mechanism to drive global property values from Properties file

```java
// Utils.java
public RequestSpecification requestSpecification() throws IOException {
    PrintStream log = new PrintStream(new FileOutputStream("logging.txt"));
    req = new RequestSpecBuilder().setBaseUri(getGlobalValue("baseUrl"))
        .addQueryParam("key", "qaclick123")
        .addFilter(RequestLoggingFilter.logRequestTo(log))
        .addFilter(ResponseLoggingFilter.logResponseTo(log))
        .setContentType(ContentType.JSON)
        .build();
    return req;
}

public static String getGlobalValue(String key) throws IOException {
    Properties prop = new Properties();
    FileInputStream fis = new FileInputStream("src/test/java/resources/global.properties");
    prop.load(fis);
    return prop.getProperty(key);
}
```

## Data driven testing mechanism for API tests using Cucumber example

```gherkin
Feature: Validating Place APIs

  Scenario Outline: Verify if Place is being successfully added using AddPlaceAPI
    Given Add Place Payload with "<name>" "<language>" "<address>"
    When user calls "AddPlaceAPI" with Post http request
    Then the API call got success with status code 200
    And "status" in response body is "OK"
    And "scope" in response body is "APP"

    Examples:
      | name    | language | address            |
      | AAhouse | English  | World cross center |
```

```java
// StepDefinition.java
@Given("Add Place Payload with {string} {string} {string}")
public void add_place_payload_with(String name, String language, String address) throws IOException {
    resspec = new ResponseSpecBuilder().expectStatusCode(200)
                .expectContentType(ContentType.JSON).build();
    res = given().spec(requestSpecification()).body(data.addPlacePayload(name, language, address));
}
```

```java
// TestDataBuild.java
public AddPlace addPlacePayload(String name, String language, String address) {
    AddPlace p = new AddPlace();
    p.setAccuracy(50);
    p.setAddress(address);
    p.setLanguage(language);
    p.setPhone_number("(+91) 983 893 3937");
    p.setWebsite("https://rahulshettyacademy.com");
    p.setName(name);
    List<String> myList = new ArrayList<>();
    myList.add("shoe park");
    myList.add("shop");
    p.setTypes(myList);
    Location l = new Location();
    l.setLat(-38.383494);
    l.setLng(33.427362);
    p.setLocation(l);

    return p;
}
```

## Parameterize API test with multiple data sets using Cucumber framework features

```gherkin
Feature: Validating Place APIs

  Scenario Outline: Verify if Place is being successfully added using AddPlaceAPI
    Given Add Place Payload with "<name>" "<language>" "<address>"
    When user calls "AddPlaceAPI" with Post http request
    Then the API call got success with status code 200
    And "status" in response body is "OK"
    And "scope" in response body is "APP"

    Examples:
      | name    | language | address            |
      | AAhouse | English  | World cross center |
      | BBhouse | Spanish  | Sea cross center   |
```

```java
// Utils.java
public static RequestSpecification req;

public RequestSpecification requestSpecification() throws IOException {
    if (req == null) {
        PrintStream log = new PrintStream(new FileOutputStream("logging.txt"));
        req = new RequestSpecBuilder().setBaseUri(getGlobalValue("baseUrl"))
            .addQueryParam("key", "qaclick123")
            .addFilter(RequestLoggingFilter.logRequestTo(log))
            .addFilter(ResponseLoggingFilter.logResponseTo(log))
            .setContentType(ContentType.JSON)
            .build();
        return req;
    }
    return req;
}
```

## Removing hardcoded resource details with Enum class methods

```gherkin
Feature: Validating Place APIs

  Scenario Outline: Verify if Place is being successfully added using AddPlaceAPI
    Given Add Place Payload with "<name>" "<language>" "<address>"
    When user calls "AddPlaceAPI" with "Post" http request
    Then the API call got success with status code 200
    And "status" in response body is "OK"
    And "scope" in response body is "APP"

    Examples:
      | name    | language | address            |
      | AAhouse | English  | World cross center |
      | BBhouse | Spanish  | Sea cross center   |
```

```java
// ApiResources.java
public enum ApiResources {
    AddPlaceAPI("/maps/api/place/add/json"),
    GetPlaceAPI("/maps/api/place/get/json"),
    DeletePlaceAPI("/maps/api/place/delete/json");

    private String resource;

    ApiResources(String resource) {
        this.resource = resource;
    }

    public String getResource() {
        return resource;
    }
}
```

```java
// StepDefinitions.java
@When("user calls {string} with {string} http request")
public void user_calls_with_Post_http_request(String resource, String method) {
    ApiResources resourceApi = ApiResources.valueOf(resource);
    System.out.println(resourceApi.getResource());

    if (method.equalsIgnoreCase("POST")) {
        response = res.when().post(resourceApi.getResource());
    } else if (method.equalsIgnoreCase("GET")) {
        response = res.when().get(resourceApi.getResource());
    }
}
```

## Build end to end testcase with Add and Delete Place in framework standards

```gherkin
Feature: Validating Place APIs

  Scenario Outline: Verify if Place is being successfully added using AddPlaceAPI
    Given Add Place Payload with "<name>" "<language>" "<address>"
    When user calls "AddPlaceAPI" with "Post" http request
    Then the API call got success with status code 200
    And "status" in response body is "OK"
    And "scope" in response body is "APP"
    And verify place_id created maps to "<name>" using "GetPlaceAPI"

    Examples:
      | name    | language | address            |
      | AAhouse | English  | World cross center |
#     | BBhouse | Spanish  | Sea cross center   |
```

```java
// Utils.java
public String getJsonPath(Response response, String key) {
    String resp = response.asString();
    JsonPath js = new JsonPath(resp);
    return js.get(key).toString();
}
```

```java
// StepDefinition.java
@Then("{string} in response body is {string}")
public void in_response_body_is(String key, String expectedValue) {
    assertEquals(expectedValue, getJsonPath(response, key));
}

@Then("verify place_id created maps to {string} using {string}")
public void verify_place_id_created_maps_to_using(String expectedName, String resource) throws IOException {
    String placeId = getJsonPath(response, "place_id");
    res = given().spec(requestSpecification())
            .queryParam("place_id", placeId);
    user_calls_with_http_request(resource, "GET");
    String actualName = getJsonPath(response, "name");
    assertEquals(expectedName, actualName);
}
```

## Creating additional scenarios in framework to reuse existing step definitions

```gherkin
Scenario: Verify if Delete Place functionality is working
	Given DeletePlace Payload
    When user calls "DeletePlaceAPI" with "Post" http request
    Then the API call got success with status code 200
    And "status" in response body is "OK"
```

```java
// StepDefinition.java
static String placeId;

@Given("DeletePlace Payload")
public void deleteplace_Payload() throws IOException {
    res = given().spec(requestSpecification())
        .body(data.deletePlacePayload(placeId));
}
```

```java
// TestDataBuild.java
public String deletePlacePayload(String placeId) {
    return "{\r\n \"place_id\":\"" + placeId + "\"\r\n}";
}
```

## Importance of Cucumber hooks in setting up preconditions for API tests

```gherkin
@DeletePlace
Scenario: Verify if Delete Place functionality is working
    Given DeletePlace Payload
    When user calls "DeletePlaceAPI" with "Post" http request
    Then the API call got success with status code 200
    And "status" in response body is "OK"
```

```java
// TestRunner.java
@RunWith(Cucumber.class)
@CucumberOptions(features = "src/test/java/features", glue = {"stepDefinitions"}, tags = "@DeletePlace")
public class TestRunner {
}
```

```java
public class Hooks {

    @Before("@DeletePlace")
    public void beforeScenario() throws IOException {
        StepDefinition stepDefinition = new StepDefinition();
        stepDefinition.add_place_payload_with("Shetty", "French", "Asia");
        stepDefinition.user_calls_with_http_request("AddPlaceAPI", "POST");
        stepDefinition.verify_place_id_created_maps_to_using("Shetty", "GetPlaceAPI");
    }
}
```

## Optimizing the framework tests with all necessary validations

```java
// Hooks.java
@Before("@DeletePlace")
public void beforeScenario() throws IOException {
    StepDefinition stepDefinition = new StepDefinition();
    if (StepDefinition.placeId == null) {
        stepDefinition.add_place_payload_with("Shetty", "French", "Asia");
        stepDefinition.user_calls_with_http_request("AddPlaceAPI", "POST");
        stepDefinition.verify_place_id_created_maps_to_using("Shetty", "GetPlaceAPI");
    }
}
```

## Running the complete framework using Maven commands

```shell
mvn test
```

```shell
mvn test -Dcucumber.options="--tags @AddPlace"
```

## Generate excellent Cucumber HTML reporting with additional plugins

https://github.com/damianszczepanik/maven-cucumber-reporting

```java
// TestRunner.java
@RunWith(Cucumber.class)
@CucumberOptions(features = "src/test/java/features", plugin = "json:target/jsonReports/cucumber-report.json", glue = {"stepDefinitions"}, tags = "@DeletePlace")
public class TestRunner {
}
```

target/cucumber-html-reports/overview-features.html

# Learn GraphQL from scratch and testing with REST Assured

## What is GraphQL? How different it is from REST APIs?
GraphQL is a query language and server-side runtime for fulfilling those queries on your existing data. GraphQL isn't tied to any specific database or storage engine and is instead backed by your existing code and data.

## Understanding GraphQL schema and its query language

https://rahulshettyacademy.com/gq/graphql

## Learn how to write GraphQL queries to test GraphQL APIs

```GraphQL
query {
  character(characterId: 47) {
    name
    gender
    status
    id
  }
  location(locationId: 3) {
    name
    dimension
  }
  episode(episodeId: 1) {
    name
    air_date
    episode
  }
  characters(filters: { name: "Tom" }) {
    info {
      count
    }
    result {
      name
      type
    }
  }
}
```

## Testing GraphQL queries with Postman and Explorer

```GraphQL
query($characterId : Int!, $episodeId: Int!) {
  character(characterId: $characterId) {
    name
    gender
    status
    id
  }
  location(locationId: 3) {
    name
    dimension
  }
  episode(episodeId: $episodeId) {
    name
    air_date
    episode
  }
  characters(filters: { name: "Tom" }) {
    info {
      count
    }
    result {
      name
      type
    }
  }
  episodes(filters: { episode: "hulu" }) {
    result {
      id
      name
      air_date
      episode
    }
  }
}
```

```
{
  "characterId": 47,
  "episodeId": 1
}
```

## What are GraphQL mutations? How to test mutations

```GraphQL
mutation {
  createLocation(location: {name: "Aus", type: "Southzone", dimension: "234"}) {
    id
  }
  
  createCharacter(character: {name: "Robin", type: "macho", status: "dead", species: "fantasy", gender: "male", image: "png", originId: 4845, locationId: 4845}) {
    id
  }
  
  createEpisode(episode: {name: "Raw and rust", air_date: "1950 June", episode: "Prime"}) {
    id
  }
  
  deleteLocations(locationIds: [4847, 4845]) {
    locationsDeleted
  }
}
```

## Test multiple GraphQL mutations with query variables in Postman

```GraphQL
mutation($locationName: String!, $characterName: String!, $episodeName: String!) {
  createLocation(location: {name: $locationName, type: "Southzone", dimension: "234"}) {
    id
  }
  
  createCharacter(character: {name: $characterName, type: "macho", status: "dead", species: "fantasy", gender: "male", image: "png", originId: 4855, locationId: 4855}) {
    id
  }
  
  createEpisode(episode: {name: $episodeName, air_date: "1950 June", episode: "Prime"}) {
    id
  }
  
  deleteLocations(locationIds: [4847, 4845]) {
    locationsDeleted
  }
}
```

```
{
  "locationName": "South Africa",
  "characterName": "Baskin Robber",
  "episodeName": "Manifest 2"
}
```

## Automate GraphQL queries & mutations using REST Assured automation

```java
public class GraphQL {
    public static void main(String[] args) {

        int characterId = 47;
        String response = given().log().all()
                .header("Content-Type", "application/json")
                .body("{\"query\":\"query($characterId : Int!, $episodeId: Int!) {\\n  character(characterId: $characterId) {\\n    name\\n    gender\\n    status\\n    id\\n  }\\n  location(locationId: 3) {\\n    name\\n    dimension\\n  }\\n  episode(episodeId: $episodeId) {\\n    name\\n    air_date\\n    episode\\n  }\\n  characters(filters: { name: \\\"Tom\\\" }) {\\n    info {\\n      count\\n    }\\n    result {\\n      name\\n      type\\n    }\\n  }\\n  episodes(filters: { episode: \\\"hulu\\\" }) {\\n    result {\\n      id\\n      name\\n      air_date\\n      episode\\n    }\\n  }\\n}\\n\",\"variables\":{\"characterId\":" + characterId + ",\"episodeId\":1}}")
                .when().post("https://rahulshettyacademy.com/gq/graphql")
                .then().extract().response().asString();
        System.out.println(response);
        JsonPath js = new JsonPath(response);
        String characterName = js.getString("data.character.name");
        System.out.println(characterName);

        String newCharacter = "Abita";
        String mutationResponse = given().log().all()
                .header("Content-Type", "application/json")
                .body("{\"query\":\"mutation($locationName: String!, $characterName: String!, $episodeName: String!) {\\n  createLocation(location: {name: $locationName, type: \\\"Southzone\\\", dimension: \\\"234\\\"}) {\\n    id\\n  }\\n  \\n  createCharacter(character: {name: $characterName, type: \\\"macho\\\", status: \\\"dead\\\", species: \\\"fantasy\\\", gender: \\\"male\\\", image: \\\"png\\\", originId: 4855, locationId: 4855}) {\\n    id\\n  }\\n  \\n  createEpisode(episode: {name: $episodeName, air_date: \\\"1950 June\\\", episode: \\\"Prime\\\"}) {\\n    id\\n  }\\n  \\n  deleteLocations(locationIds: [4847, 4845]) {\\n    locationsDeleted\\n  }\\n}\\n\",\"variables\":{\"locationName\":\"New Zealand\",\"characterName\":\"" + newCharacter + "\",\"episodeName\":\"Manifest\"}}")
                .when().post("https://rahulshettyacademy.com/gq/graphql")
                .then().extract().response().asString();
        System.out.println(mutationResponse);
    }
}
```

# Cucumber BDD API framework development from scratch - 2

## Integrating the API framework into Jenkins and triggering with new job 

```gherkin
Feature: Validating Place APIs

  @AddPlace @Regression
  Scenario Outline: Verify if Place is being successfully added using AddPlaceAPI
    Given Add Place Payload with "<name>" "<language>" "<address>"
    When user calls "AddPlaceAPI" with "Post" http request
    Then the API call got success with status code 200
    And "status" in response body is "OK"
    And "scope" in response body is "APP"
    And verify place_id created maps to "<name>" using "GetPlaceAPI"

    Examples:
      | name    | language | address            |
      | AAhouse | English  | World cross center |
#     | BBhouse | Spanish  | Sea cross center   |
```

# Understanding Version Control System Git

## Creating git config and repositories

```shell
git config --global user.name "name"
```

```shell
git config --global user.email "email@email.com"
```

## Understanding staging and commit in Git

```shell
git init
```

```shell
git add *
```

```shell
git status
```

```shell
git commit -m "first commit"
```

## Add remote repository and push the committed code

```shell
git remote add origin <server>
```

```shell
git push origin master
```

## End to end working example on Git commands

```shell
git clone <server>
```

```shell
git pull origin master
```

## Importance of branching in Git

```shell
git checkout -b <branchname>
```

```shell
git branch
```

```shell
git push origin <branchname>
```

```shell
git pull origin <branchname>
```

```shell
git checkout <branchname>
```

```shell
git merge <branchname>
```

# Excel integration with REST Assured test

## What is Apache POI API

poi-ooxml
poi

## Strategy to access Excel data

- Create object for XSSFWorkbook class
- Get access to sheet
- Get access to all rows of sheet
- Access to specific row from all rows
- Get access to all cells of row
- Access the data from Excel into arrays

```java
// Excel.java
FileInputStream fis = new FileInputStream("C:\\Users\\Stephan\\Dropbox\\projects\\RestAssuredBasics\\src\\test\\resources\\data.xlsx");
XSSFWorkbook workbook = new XSSFWorkbook(fis);
int sheets = workbook.getNumberOfSheets();
for (int i = 0; i < sheets; i++) {
    if (workbook.getSheetName(i).equalsIgnoreCase("testdata")) {
        XSSFSheet sheet = workbook.getSheetAt(i);
    }
}
```

## Getting rows and its cells from sheet

```java
// Excel.java
for (int i = 0; i < sheets; i++) {
    if (workbook.getSheetName(i).equalsIgnoreCase("testdata")) {
        XSSFSheet sheet = workbook.getSheetAt(i);
        Iterator<Row> rows = sheet.iterator();
        Row firstRow = rows.next();
        Iterator<Cell> cells = firstRow.cellIterator();
        while (cells.hasNext()) {
            Cell cell = cells.next();
            if (cell.getStringCellValue().equalsIgnoreCase("testcases")) {

            }
        }
    }
}
```

## Retrieving data from Excel based on condition

```java
// Excel.java
int k = 0;
int column = 0;
while (cells.hasNext()) {
    Cell cell = cells.next();
    if (cell.getStringCellValue().equalsIgnoreCase("testcases")) {
        column = k;
    }
    k++;
}
System.out.println(column);
```

## Practice exercise 1

```java
// Excel.java
while (rows.hasNext()) {
	Row row = rows.next();
    if (row.getCell(column).getStringCellValue().equalsIgnoreCase("purchase")) {
        Iterator<Cell> data = row.cellIterator();
        while (data.hasNext()) {
            System.out.println(data.next().getStringCellValue());
        }
    }
}
```

## Practice exercise 2

```java
// Excel.java
ArrayList<String> array = new ArrayList<>();

while (data.hasNext()) {
    array.add(data.next().getStringCellValue());
}
```

## Practice exercise 3

```java
// Excel.java
while (data.hasNext()) {
	Cell cell = data.next();
    if (cell.getCellType() == CellType.STRING) {
        array.add(cell.getStringCellValue());
    } else {
        array.add(NumberToTextConverter.toText(cell.getNumericCellValue()));
    }
}
```

```java
public class Excel {

    public ArrayList<String> getData(String testCaseName) throws IOException {
        ArrayList<String> array = new ArrayList<>();

        FileInputStream fis = new FileInputStream("C:\\Users\\Stephan\\Dropbox\\projects\\RestAssuredBasics\\src\\test\\resources\\data.xlsx");
        XSSFWorkbook workbook = new XSSFWorkbook(fis);

        int sheets = workbook.getNumberOfSheets();
        for (int i = 0; i < sheets; i++) {
            if (workbook.getSheetName(i).equalsIgnoreCase("testdata")) {
                XSSFSheet sheet = workbook.getSheetAt(i);
                Iterator<Row> rows = sheet.iterator();
                Row firstRow = rows.next();
                Iterator<Cell> cells = firstRow.cellIterator();
                int k = 0;
                int column = 0;
                while (cells.hasNext()) {
                    Cell cell = cells.next();
                    if (cell.getStringCellValue().equalsIgnoreCase("testcases")) {
                        column = k;
                    }
                    k++;
                }

                while (rows.hasNext()) {
                    Row row = rows.next();
                    if (row.getCell(column).getStringCellValue().equalsIgnoreCase(testCaseName)) {
                        Iterator<Cell> data = row.cellIterator();
                        while (data.hasNext()) {
                            Cell cell = data.next();
                            if (cell.getCellType() == CellType.STRING) {
                                array.add(cell.getStringCellValue());
                            } else {
                                array.add(NumberToTextConverter.toText(cell.getNumericCellValue()));
                            }
                        }
                    }
                }
            }
        }
        return array;
    }
}
```
## Conversion of HashMap into JSON

```java
// ExcelDriven.java
HashMap<String, Object> jsonAsMap = new HashMap<>();
jsonAsMap.put("name", "Rest Assured");
jsonAsMap.put("isbn", "sjkfdksjd12");
jsonAsMap.put("aisle", "333");
jsonAsMap.put("author", "Aba");

RestAssured.baseURI = "http://216.10.245.166";
String resp = given()
        .header("Content-Type", "application/json")
        .body(jsonAsMap)
```

## Excel integration with REST Assured test

```java
// ExcelDriven.java
Excel excel = new Excel();
ArrayList data = excel.getData("RestAddBook", "RestAssured");

HashMap<String, Object> jsonAsMap = new HashMap<>();
jsonAsMap.put("name", data.get(1));
jsonAsMap.put("isbn", data.get(2));
jsonAsMap.put("aisle", data.get(3));
jsonAsMap.put("author", data.get(4));
```

```java
public class ExcelDriven {

    @Test
    public void test() throws IOException {
        Excel excel = new Excel();
        ArrayList data = excel.getData("RestAddBook", "RestAssured");

        HashMap<String, Object> jsonAsMap = new HashMap<>();
        jsonAsMap.put("name", data.get(1));
        jsonAsMap.put("isbn", data.get(2));
        jsonAsMap.put("aisle", data.get(3));
        jsonAsMap.put("author", data.get(4));

        RestAssured.baseURI = "http://216.10.245.166";
        String resp = given()
                .header("Content-Type", "application/json")
                .body(jsonAsMap)
                .when()
                .post("Library/Addbook.php")
                .then()
                .assertThat()
                .statusCode(200)
                .extract()
                .response()
                .asString();
        JsonPath js = ReusableMethods.rawToJson(resp);
        String id = js.get("ID");
        System.out.println(id);
    }
}
```

# Core Java basics

## How Java classes can take advantage of interface?

```java
public interface CentralTraffic {
    int a = 4;

    public void greenGo();
    public void redStop();
    public void flashYellow();
}
```

```java
public interface ContinentalTraffic {
    public void trainSymbol();
}
```

```java
public class AustralianTraffic implements CentralTraffic, ContinentalTraffic {

    public static void main(String[] args) {
        CentralTraffic a = new AustralianTraffic();
        a.redStop();
        a.greenGo();
        a.flashYellow();

        AustralianTraffic at = new AustralianTraffic();
        at.walkOnSymbol();

        ContinentalTraffic ct = new AustralianTraffic();
        ct.trainSymbol();
    }

    public void walkOnSymbol() {
        System.out.println("Walking");
    }

    @Override
    public void greenGo() {
        System.out.println("Green go implementation");
    }

    @Override
    public void redStop() {
        System.out.println("Red stop implementation");
    }

    @Override
    public void flashYellow() {
        System.out.println("Yellow implementation");
    }

    @Override
    public void trainSymbol() {
        System.out.println("Train symbol implementation");
    }
}
```

## Usage of inheritance in Java

```java
public class ParentClass {
    String color = "red";

    public void gear() {
        System.out.println("Gear code is implemented");
    }

    public void brakes() {
        System.out.println("Brakes code is implemented");
    }

    public void audioSystem() {
        System.out.println("Audio system code is implemented");
    }
}
```

```java
public class ChildClass extends ParentClass {

    public void engine() {
        System.out.println("New engine");
    }

    public void color() {
        System.out.println(color);
    }

    public static void main(String[] args) {
        ChildClass childClass = new ChildClass();
        childClass.color();
        childClass.brakes();
    }
}
```


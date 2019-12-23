# mars-sdk-android

Users
- API version: 0.1.0
  - Build date: 2019-12-20T11:49:25.649Z[GMT]

API to register user device

## Requirements

Building the API client library requires:
1. Java 1.7+
2. Maven/Gradle

## Installation

To install the API client library to your local Maven repository, simply execute:

```shell
mvn clean install
```

To deploy it to a remote Maven repository instead, configure the settings of the repository and execute:

```shell
mvn clean deploy
```

Refer to the [OSSRH Guide](http://central.sonatype.org/pages/ossrh-guide.html) for more information.

### Maven users

Add this dependency to your project's POM:

```xml
<dependency>
  <groupId>io.swagger</groupId>
  <artifactId>swagger-java-client</artifactId>
  <version>1.0.0</version>
  <scope>compile</scope>
</dependency>
```

### Gradle users

Add this dependency to your project's build file:

```groovy
compile "io.swagger:swagger-java-client:1.0.0"
```

### Others

At first generate the JAR by executing:

```shell
mvn clean package
```

Then manually install the following JARs:

* `target/swagger-java-client-1.0.0.jar`
* `target/lib/*.jar`

## Getting Started

Please follow the [installation](#installation) instruction and execute the following Java code:

```java
import io.swagger.client.*;
import io.swagger.client.auth.*;
import io.swagger.client.model.*;
import io.swagger.client.api.UserApi;

import java.io.File;
import java.util.*;

public class UserApiExample {

    public static void main(String[] args) {
        
        UserApi apiInstance = new UserApi();
        Body2 body = new Body2(); // Body2 | 
        try {
            InlineResponse2002 result = apiInstance.registerDeviceToken(body);
            System.out.println(result);
        } catch (ApiException e) {
            System.err.println("Exception when calling UserApi#registerDeviceToken");
            e.printStackTrace();
        }
    }
}
import io.swagger.client.*;
import io.swagger.client.auth.*;
import io.swagger.client.model.*;
import io.swagger.client.api.UserApi;

import java.io.File;
import java.util.*;

public class UserApiExample {

    public static void main(String[] args) {
        
        UserApi apiInstance = new UserApi();
        Body1 body = new Body1(); // Body1 | 
        try {
            InlineResponse2001 result = apiInstance.updateDeviceToken(body);
            System.out.println(result);
        } catch (ApiException e) {
            System.err.println("Exception when calling UserApi#updateDeviceToken");
            e.printStackTrace();
        }
    }
}
```

### Firebase Integration
Add following code to your firebase messaging service  class and overide the onNewToken method
```
import com.google.firebase.iid.FirebaseInstanceId;
import io.swagger.client.ApiException;
import io.swagger.client.api.UserApi;
import io.swagger.client.model.Body2;
import io.swagger.client.model.InlineResponse2002;

    @Override
    public void onNewToken(String token) {
        sendRegistrationToServer(token);
    }
```
Implement the sendRegistrationToServer()
```
private void sendRegistrationToServer(String token) {
        UserApi userInstance = new UserApi();
        Body2 newUserBody = new Body2();
        newUserBody.setToken(token);
        newUserBody.setDeviceId(FirebaseInstanceId.getInstance().getId());

        try {
            InlineResponse2002 res = userInstance.registerDeviceToken(newUserBody);

        } catch (ApiException e) {
            System.err.println("");
            e.printStackTrace();
        }

    }

```

## Documentation for API Endpoints

All URIs are relative to *https://sdk-test.marax.ai/sdk/v1*

Class | Method | HTTP request | Description
------------ | ------------- | ------------- | -------------
*UserApi* | [**registerDeviceToken**](docs/UserApi.md#registerDeviceToken) | **POST** /user/firebase/android | Register a new device
*UserApi* | [**updateDeviceToken**](docs/UserApi.md#updateDeviceToken) | **PUT** /user/firebase/android | Update the firebase token for a device
*UserOffersApi* | [**fetchOffer**](docs/UserOffersApi.md#fetchOffer) | **GET** /user-offer/{offerId}/{userId} | Fetch a single offer for user by offer id
*UserOffersApi* | [**paintOffer**](docs/UserOffersApi.md#paintOffer) | **GET** /user-offer/template/{templateId}/{userId} | 
*UserOffersApi* | [**updateOffer**](docs/UserOffersApi.md#updateOffer) | **PUT** /user-offer/{offerId}/{userId} | Update the offer details for the user

## Documentation for Models

 - [Body](docs/Body.md)
 - [Body1](docs/Body1.md)
 - [Body2](docs/Body2.md)
 - [InlineResponse200](docs/InlineResponse200.md)
 - [InlineResponse2001](docs/InlineResponse2001.md)
 - [InlineResponse2002](docs/InlineResponse2002.md)
 - [InlineResponse2002Data](docs/InlineResponse2002Data.md)
 - [User](docs/User.md)
 - [UserAttributes](docs/UserAttributes.md)
 - [UserCompliances](docs/UserCompliances.md)
 - [UserCompliancesGdpr](docs/UserCompliancesGdpr.md)
 - [UserOfferObject](docs/UserOfferObject.md)
 - [UserSdk](docs/UserSdk.md)
 - [UserSdkAndroid](docs/UserSdkAndroid.md)
 - [UserSdkFirebase](docs/UserSdkFirebase.md)

## Documentation for Authorization

All endpoints do not require authorization.
Authentication schemes defined for the API:

## Recommendation

It's recommended to create an instance of `ApiClient` per thread in a multithreaded environment to avoid any potential issues.

## Author

dev@marax.ai


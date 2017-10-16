# v3-bot-client

```
  ____              _       _           _   _
 |  _ \            | |     | |         | | | |
 | |_) | __ _ _ __ | | __  | |_ ___    | |_| |__   ___
 |  _ < / _` | '_ \| |/ /  | __/ _ \   | __| '_ \ / _ \
 | |_) | (_| | | | |   <   | || (_) |  | |_| | | |  __/
 |____/ \__,_|_| |_|_|\_\   \__\___/    \__|_| |_|\___|
      __
      \ \        ________  __________  ______  ______
  _____\ \      / ____/ / / /_  __/ / / / __ \/ ____/
 |______> >    / /_  / / / / / / / / / / /_/ / __/
       / /    / __/ / /_/ / / / / /_/ / _, _/ /__
      /_/    /_/    \____/ /_/  \____/_/ |_/_____/

```

## Background

Implements MS Bot v3 rest api via swagger codegen:

```shell
java -jar /swagger-codegen-cli-2.2.1.jar generate -i https://docs.botframework.com/en-us/restapi/directline3/swagger.json -l java --library okhttp-gson -c java-config.json -o v3client-okhttp
```

Config:

```
{
  "modelPackage" : "org.bttf.v3client.model",
  "apiPackage"   : "org.bttf.v3client.api",
  "invokerPackage" : "org.bttf.v3client",
  "groupId" : "org.bttf.v3",
  "artifactId"  : "v3client",
  "dateLibrary" : "java8"
}
```

## Requirements

Building the API client library requires [Maven](https://maven.apache.org/) to be installed.

## Installation

To install the API client library to your local Maven repository, simply execute:

```shell
mvn install
```

To deploy it to a remote Maven repository instead, configure the settings of the repository and execute:

```shell
mvn deploy
```

Refer to the [official documentation](https://maven.apache.org/plugins/maven-deploy-plugin/usage.html) for more information.

### Maven users

Add this dependency to your project's POM:

```xml
<dependency>
    <groupId>org.bttf.v3</groupId>
    <artifactId>v3-bot-client</artifactId>
    <version>1.0.0</version>
    <scope>compile</scope>
</dependency>
```

### Gradle users

Add this dependency to your project's build file:

```groovy
compile "org.bttf.v3:v3-bot-client:1.0.0"
```

### Others

At first generate the JAR by executing:

    mvn package

Then manually install the following JARs:

* target/v3-bot-client-1.0.0.jar
* target/lib/*.jar

## Getting Started

Please follow the [installation](#installation) instruction and execute the following Java code:

```java

import org.bttf.v3client.*;
import org.bttf.v3client.auth.*;
import org.bttf.v3client.model.*;
import org.bttf.v3client.api.ConversationsApi;

import java.io.File;
import java.util.*;

public class ConversationsApiExample {

    public static void main(String[] args) {
        
        ConversationsApi apiInstance = new ConversationsApi();
        String conversationId = "conversationId_example"; // String | Conversation ID
        String watermark = "watermark_example"; // String | (Optional) only returns activities newer than this watermark
        try {
            ActivitySet result = apiInstance.conversationsGetActivities(conversationId, watermark);
            System.out.println(result);
        } catch (ApiException e) {
            System.err.println("Exception when calling ConversationsApi#conversationsGetActivities");
            e.printStackTrace();
        }
    }
}

```

## Documentation for API Endpoints

All URIs are relative to *https://directline.botframework.com*

Class | Method | HTTP request | Description
------------ | ------------- | ------------- | -------------
*ConversationsApi* | [**conversationsGetActivities**](docs/ConversationsApi.md#conversationsGetActivities) | **GET** /v3/directline/conversations/{conversationId}/activities | Get activities in this conversation. This method is paged with the &#39;watermark&#39; parameter.
*ConversationsApi* | [**conversationsPostActivity**](docs/ConversationsApi.md#conversationsPostActivity) | **POST** /v3/directline/conversations/{conversationId}/activities | Send an activity
*ConversationsApi* | [**conversationsReconnectToConversation**](docs/ConversationsApi.md#conversationsReconnectToConversation) | **GET** /v3/directline/conversations/{conversationId} | Get information about an existing conversation
*ConversationsApi* | [**conversationsStartConversation**](docs/ConversationsApi.md#conversationsStartConversation) | **POST** /v3/directline/conversations | Start a new conversation
*ConversationsApi* | [**conversationsUpload**](docs/ConversationsApi.md#conversationsUpload) | **POST** /v3/directline/conversations/{conversationId}/upload | Upload file(s) and send as attachment(s)
*TokensApi* | [**tokensGenerateTokenForNewConversation**](docs/TokensApi.md#tokensGenerateTokenForNewConversation) | **POST** /v3/directline/tokens/generate | Generate a token for a new conversation
*TokensApi* | [**tokensRefreshToken**](docs/TokensApi.md#tokensRefreshToken) | **POST** /v3/directline/tokens/refresh | Refresh a token


## Documentation for Models

 - [Activity](docs/Activity.md)
 - [ActivitySet](docs/ActivitySet.md)
 - [AnimationCard](docs/AnimationCard.md)
 - [Attachment](docs/Attachment.md)
 - [AudioCard](docs/AudioCard.md)
 - [CardAction](docs/CardAction.md)
 - [CardImage](docs/CardImage.md)
 - [ChannelAccount](docs/ChannelAccount.md)
 - [Conversation](docs/Conversation.md)
 - [ConversationAccount](docs/ConversationAccount.md)
 - [ConversationReference](docs/ConversationReference.md)
 - [Entity](docs/Entity.md)
 - [Error](docs/Error.md)
 - [ErrorResponse](docs/ErrorResponse.md)
 - [Fact](docs/Fact.md)
 - [GeoCoordinates](docs/GeoCoordinates.md)
 - [HeroCard](docs/HeroCard.md)
 - [MediaUrl](docs/MediaUrl.md)
 - [Mention](docs/Mention.md)
 - [Object](docs/Object.md)
 - [Place](docs/Place.md)
 - [ReceiptCard](docs/ReceiptCard.md)
 - [ReceiptItem](docs/ReceiptItem.md)
 - [ResourceResponse](docs/ResourceResponse.md)
 - [SigninCard](docs/SigninCard.md)
 - [SuggestedActions](docs/SuggestedActions.md)
 - [Thing](docs/Thing.md)
 - [ThumbnailCard](docs/ThumbnailCard.md)
 - [ThumbnailUrl](docs/ThumbnailUrl.md)
 - [TokenParameters](docs/TokenParameters.md)
 - [VideoCard](docs/VideoCard.md)


## Documentation for Authorization

All endpoints do not require authorization.
Authentication schemes defined for the API:

## Recommendation

It's recommended to create an instance of `ApiClient` per thread in a multithreaded environment to avoid any potential issue.

## Author

botframework@microsoft.com


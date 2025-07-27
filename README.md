# openapi

Developer-friendly & type-safe Java SDK specifically catered to leverage *openapi* API.

<div align="left">
    <a href="https://www.speakeasy.com/?utm_source=openapi&utm_campaign=java"><img src="https://custom-icon-badges.demolab.com/badge/-Built%20By%20Speakeasy-212015?style=for-the-badge&logoColor=FBE331&logo=speakeasy&labelColor=545454" /></a>
    <a href="https://mit-license.org/">
        <img src="https://img.shields.io/badge/License-MIT-blue.svg" style="width: 100px; height: 28px;" />
    </a>
</div>


<br /><br />
> [!IMPORTANT]
> This SDK is not yet ready for production use. To complete setup please follow the steps outlined in your [workspace](https://app.speakeasy.com/org/vartana/qwerty). Delete this section before > publishing to a package manager.

<!-- Start Summary [summary] -->
## Summary

Authlete API Explorer: <div class="min-h-screen bg-gray-100 dark:bg-gray-900 text-gray-900 dark:text-gray-100 p-6">
  <div class="flex justify-end mb-4">
    <label for="theme-toggle" class="flex items-center cursor-pointer">
      <div class="relative">Dark mode:
        <input type="checkbox" id="theme-toggle" class="sr-only" onchange="toggleTheme()">
        <div class="block bg-gray-600 w-14 h-8 rounded-full"></div>
        <div class="dot absolute left-1 top-1 bg-white w-6 h-6 rounded-full transition"></div>
      </div>
    </label>
  </div>
  <header class="bg-green-500 dark:bg-green-700 p-4 rounded-lg text-white text-center">
    <p>
      Welcome to the <strong>Authlete API documentation</strong>. Authlete is an <strong>API-first service</strong>
      where every aspect of the platform is configurable via API. This explorer provides a convenient way to
      authenticate and interact with the API, allowing you to see Authlete in action quickly. 🚀
    </p>
    <p>
      At a high level, the Authlete API is grouped into two categories:
    </p>
    <ul class="list-disc list-inside">
      <li><strong>Management APIs</strong>: Enable you to manage services and clients. 🔧</li>
      <li><strong>Runtime APIs</strong>: Allow you to build your own Authorization Servers or Verifiable Credential (VC)
        issuers. 🔐</li>
    </ul>
    <p>All API endpoints are secured using access tokens issued by Authlete's Identity Provider (IdP). If you already
      have an Authlete account, simply use the <em>Get Token</em> option on the Authentication page to log in and obtain
      an access token for API usage. If you don't have an account yet, <a href="https://console.authlete.com/register">sign up
        here</a> to get started.</p>
  </header>
  <main>
    <section id="api-servers" class="mb-10">
      <h2 class="text-2xl font-semibold mb-4">🌐 API Servers</h2>
      <p>Authlete is a global service with clusters available in multiple regions across the world.</p>
      <p>Currently, our service is available in the following regions:</p>
      <div class="grid grid-cols-2 gap-4">
        <div class="p-4 bg-white dark:bg-gray-800 rounded-lg shadow">
          <p class="text-center font-semibold">🇺🇸 US</p>
        </div>
        <div class="p-4 bg-white dark:bg-gray-800 rounded-lg shadow">
          <p class="text-center font-semibold">🇯🇵 JP</p>
        </div>
        <div class="p-4 bg-white dark:bg-gray-800 rounded-lg shadow">
          <p class="text-center font-semibold">🇪🇺 EU</p>
        </div>
        <div class="p-4 bg-white dark:bg-gray-800 rounded-lg shadow">
          <p class="text-center font-semibold">🇧🇷 Brazil</p>
        </div>
      </div>
      <p>Our customers can host their data in the region that best meets their requirements.</p>
      <a href="#servers" class="block mt-4 text-green-500 dark:text-green-300 hover:underline text-center">Select your
        preferred server</a>
    </section>
    <section id="authentication" class="mb-10">
      <h2 class="text-2xl font-semibold mb-4">🔑 Authentication</h2>
      <p>The API Explorer requires an access token to call the API.</p>
      <p>You can create the access token from the <a href="https://console.authlete.com">Authlete Management Console</a> and set it in the HTTP Bearer section of Authentication page.</p>
      <p>Alternatively, if you have an Authlete account, the API Explorer can log you in with your Authlete account and
        automatically acquire the required access token.</p>
      <div class="theme-admonition theme-admonition-warning admonition_o5H7 alert alert--warning">
        <div class="admonitionContent_Knsx">
          <p>⚠️ <strong>Important Note:</strong> When the API Explorer acquires the token after login, the access tokens
            will have the same permissions as the user who logs in as part of this flow.</p>
        </div>
      </div>
      <a href="#auth" class="block mt-4 text-green-500 dark:text-green-300 hover:underline text-center">Setup your
        access token</a>
    </section>
    <section id="tutorials" class="mb-10">
      <h2 class="text-2xl font-semibold mb-4">🎓 Tutorials</h2>
      <p>If you have successfully tested the API from the API Console and want to take the next step of integrating the
        API into your application, or if you want to see a sample using Authlete APIs, follow the links below. These
        resources will help you understand key concepts and how to integrate Authlete API into your applications.</p>
      <div class="mt-4">
        <a href="https://www.authlete.com/developers/getting_started/"
          class="block text-green-500 dark:text-green-300 font-bold hover:underline mb-2">🚀 Getting Started with
          Authlete</a>
          </br>
        <a href="https://www.authlete.com/developers/tutorial/signup/"
          class="block text-green-500 dark:text-green-300 font-bold hover:underline">🔑 From Sign-Up to the First API
          Request</a>
      </div>
    </section>
    <section id="support" class="mb-10">
      <h2 class="text-2xl font-semibold mb-4">🛠 Contact Us</h2>
      <p>If you have any questions or need assistance, our team is here to help.</p>
      <a href="https://www.authlete.com/contact/"
        class="block mt-4 text-green-500 dark:text-green-300 font-bold hover:underline">Contact Page</a>
    </section>
  </main>
</div>
<!-- End Summary [summary] -->

<!-- Start Table of Contents [toc] -->
## Table of Contents
<!-- $toc-max-depth=2 -->
* [openapi](#openapi)
  * [SDK Installation](#sdk-installation)
  * [SDK Example Usage](#sdk-example-usage)
  * [Authentication](#authentication)
  * [Available Resources and Operations](#available-resources-and-operations)
  * [Error Handling](#error-handling)
  * [Server Selection](#server-selection)
  * [Debugging](#debugging)
* [Development](#development)
  * [Maturity](#maturity)
  * [Contributions](#contributions)

<!-- End Table of Contents [toc] -->

<!-- Start SDK Installation [installation] -->
## SDK Installation

### Getting started

JDK 11 or later is required.

The samples below show how a published SDK artifact is used:

Gradle:
```groovy
implementation 'org.openapis:openapi:0.1.0'
```

Maven:
```xml
<dependency>
    <groupId>org.openapis</groupId>
    <artifactId>openapi</artifactId>
    <version>0.1.0</version>
</dependency>
```

### How to build
After cloning the git repository to your file system you can build the SDK artifact from source to the `build` directory by running `./gradlew build` on *nix systems or `gradlew.bat` on Windows systems.

If you wish to build from source and publish the SDK artifact to your local Maven repository (on your filesystem) then use the following command (after cloning the git repo locally):

On *nix:
```bash
./gradlew publishToMavenLocal -Pskip.signing
```
On Windows:
```bash
gradlew.bat publishToMavenLocal -Pskip.signing
```
<!-- End SDK Installation [installation] -->

<!-- Start SDK Example Usage [usage] -->
## SDK Example Usage

### Example

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.ServiceGetApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ServiceGetApiResponse res = sdk.serviceManagement().get()
                .serviceId("<id>")
                .call();

        if (res.service().isPresent()) {
            // handle response
        }
    }
}
```
<!-- End SDK Example Usage [usage] -->

<!-- Start Authentication [security] -->
## Authentication

### Per-Client Security Schemes

This SDK supports the following security schemes globally:

| Name       | Type   | Scheme       |
| ---------- | ------ | ------------ |
| `authlete` | oauth2 | OAuth2 token |
| `bearer`   | http   | HTTP Bearer  |

You can set the security parameters through the `security` builder method when initializing the SDK client instance. The selected scheme will be used by default to authenticate with the API for all operations that support it. For example:
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.ServiceGetApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ServiceGetApiResponse res = sdk.serviceManagement().get()
                .serviceId("<id>")
                .call();

        if (res.service().isPresent()) {
            // handle response
        }
    }
}
```
<!-- End Authentication [security] -->

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

<details open>
<summary>Available methods</summary>


### [authorization()](docs/sdks/authorization/README.md)

* [issue](docs/sdks/authorization/README.md#issue) - Issue Authorization Response
* [issueForm](docs/sdks/authorization/README.md#issueform) - Issue Authorization Response
* [processPushedRequest](docs/sdks/authorization/README.md#processpushedrequest) - Process Pushed Authorization Request
* [processPushedRequestForm](docs/sdks/authorization/README.md#processpushedrequestform) - Process Pushed Authorization Request
* [getTicketInfo](docs/sdks/authorization/README.md#getticketinfo) - Get Ticket Information
* [getTicketInfoForm](docs/sdks/authorization/README.md#getticketinfoform) - Get Ticket Information

### [authorizationEndpoint()](docs/sdks/authorizationendpoint/README.md)

* [process](docs/sdks/authorizationendpoint/README.md#process) - Process Authorization Request
* [processForm](docs/sdks/authorizationendpoint/README.md#processform) - Process Authorization Request
* [updateTicket](docs/sdks/authorizationendpoint/README.md#updateticket) - Update Ticket Information
* [updateTicketForm](docs/sdks/authorizationendpoint/README.md#updateticketform) - Update Ticket Information

### [authorizationEndpoints()](docs/sdks/authorizationendpoints/README.md)

* [failAuthRequest](docs/sdks/authorizationendpoints/README.md#failauthrequest) - Fail Authorization Request
* [failAuthRequestForm](docs/sdks/authorizationendpoints/README.md#failauthrequestform) - Fail Authorization Request

### [ciba()](docs/sdks/ciba/README.md)

* [process](docs/sdks/ciba/README.md#process) - Process Backchannel Authentication Request
* [processForm](docs/sdks/ciba/README.md#processform) - Process Backchannel Authentication Request
* [issue](docs/sdks/ciba/README.md#issue) - Issue Backchannel Authentication Response
* [issueForm](docs/sdks/ciba/README.md#issueform) - Issue Backchannel Authentication Response
* [fail](docs/sdks/ciba/README.md#fail) - Fail Backchannel Authentication Request
* [failForm](docs/sdks/ciba/README.md#failform) - Fail Backchannel Authentication Request
* [completeBackchannelAuth](docs/sdks/ciba/README.md#completebackchannelauth) - Complete Backchannel Authentication
* [completeBackchannelAuthForm](docs/sdks/ciba/README.md#completebackchannelauthform) - Complete Backchannel Authentication

### [clientManagement()](docs/sdks/clientmanagement/README.md)

* [list](docs/sdks/clientmanagement/README.md#list) - List Clients
* [create](docs/sdks/clientmanagement/README.md#create) - Create Client
* [update](docs/sdks/clientmanagement/README.md#update) - Update Client
* [delete](docs/sdks/clientmanagement/README.md#delete) - Delete Client ⚡

### [clients()](docs/sdks/clients/README.md)

* [getById](docs/sdks/clients/README.md#getbyid) - Get Client
* [updateLock](docs/sdks/clients/README.md#updatelock) - Update Client Lock
* [updateLockForm](docs/sdks/clients/README.md#updatelockform) - Update Client Lock
* [refreshSecret](docs/sdks/clients/README.md#refreshsecret) - Rotate Client Secret
* [updateSecret](docs/sdks/clients/README.md#updatesecret) - Update Client Secret
* [updateSecretForm](docs/sdks/clients/README.md#updatesecretform) - Update Client Secret
* [getAuthorizedApplications](docs/sdks/clients/README.md#getauthorizedapplications) - Get Authorized Applications
* [updateAuthorization](docs/sdks/clients/README.md#updateauthorization) - Update Client Tokens
* [updateAuthorizationForm](docs/sdks/clients/README.md#updateauthorizationform) - Update Client Tokens
* [deleteAuthorization](docs/sdks/clients/README.md#deleteauthorization) - Delete Client Tokens
* [getGrantedScopes](docs/sdks/clients/README.md#getgrantedscopes) - Get Granted Scopes
* [deleteGrantedScopes](docs/sdks/clients/README.md#deletegrantedscopes) - Delete Granted Scopes
* [register](docs/sdks/clients/README.md#register) - Register Client
* [registerForm](docs/sdks/clients/README.md#registerform) - Register Client
* [get](docs/sdks/clients/README.md#get) - Get Client
* [updateRegistration](docs/sdks/clients/README.md#updateregistration) - Update Client
* [updateRegistrationForm](docs/sdks/clients/README.md#updateregistrationform) - Update Client
* [getRequestableScopes](docs/sdks/clients/README.md#getrequestablescopes) - Get Requestable Scopes
* [updateRequestableScopes](docs/sdks/clients/README.md#updaterequestablescopes) - Update Requestable Scopes
* [deleteRequestableScopes](docs/sdks/clients/README.md#deleterequestablescopes) - Delete Requestable Scopes

### [credentials()](docs/sdks/credentials/README.md)

* [issueJwt](docs/sdks/credentials/README.md#issuejwt) - /api/{serviceId}/vci/jwtissuer API
* [issueJwtForm](docs/sdks/credentials/README.md#issuejwtform) - /api/{serviceId}/vci/jwtissuer API
* [issueBatch](docs/sdks/credentials/README.md#issuebatch) - /api/{serviceId}/vci/batch/issue API

### [deviceFlow()](docs/sdks/deviceflow/README.md)

* [verify](docs/sdks/deviceflow/README.md#verify) - Process Device Verification Request
* [verifyForm](docs/sdks/deviceflow/README.md#verifyform) - Process Device Verification Request
* [complete](docs/sdks/deviceflow/README.md#complete) - Complete Device Authorization
* [completeForm](docs/sdks/deviceflow/README.md#completeform) - Complete Device Authorization

### [devices()](docs/sdks/devices/README.md)

* [authorize](docs/sdks/devices/README.md#authorize) - Process Device Authorization Request
* [authorizeForm](docs/sdks/devices/README.md#authorizeform) - Process Device Authorization Request

### [dynamicClientRegistration()](docs/sdks/dynamicclientregistration/README.md)

* [delete](docs/sdks/dynamicclientregistration/README.md#delete) - Delete Client
* [deleteForm](docs/sdks/dynamicclientregistration/README.md#deleteform) - Delete Client

### [federation()](docs/sdks/federation/README.md)

* [register](docs/sdks/federation/README.md#register) - Process Federation Registration Request
* [registerForm](docs/sdks/federation/README.md#registerform) - Process Federation Registration Request

### [federations()](docs/sdks/federations/README.md)

* [postConfiguration](docs/sdks/federations/README.md#postconfiguration) - Process Entity Configuration Request

### [grantManagementEndpoints()](docs/sdks/grantmanagementendpoints/README.md)

* [processRequest](docs/sdks/grantmanagementendpoints/README.md#processrequest) - Process Grant Management Request

### [hardwareSecurityKey()](docs/sdks/hardwaresecuritykey/README.md)

* [delete](docs/sdks/hardwaresecuritykey/README.md#delete) - Delete Security Key

### [hardwareSecurityKeys()](docs/sdks/hardwaresecuritykeys/README.md)

* [create](docs/sdks/hardwaresecuritykeys/README.md#create) - Create Security Key
* [createForm](docs/sdks/hardwaresecuritykeys/README.md#createform) - Create Security Key
* [list](docs/sdks/hardwaresecuritykeys/README.md#list) - List Security Keys

### [introspectionEndpoint()](docs/sdks/introspectionendpoint/README.md)

* [process](docs/sdks/introspectionendpoint/README.md#process) - Process Introspection Request
* [processForm](docs/sdks/introspectionendpoint/README.md#processform) - Process Introspection Request

### [introspections()](docs/sdks/introspections/README.md)

* [process](docs/sdks/introspections/README.md#process) - Process OAuth 2.0 Introspection Request
* [processForm](docs/sdks/introspections/README.md#processform) - Process OAuth 2.0 Introspection Request

### [joseObject()](docs/sdks/joseobject/README.md)

* [verify](docs/sdks/joseobject/README.md#verify) - Verify JOSE
* [verifyForm](docs/sdks/joseobject/README.md#verifyform) - Verify JOSE

### [jwkSetEndpoint()](docs/sdks/jwksetendpoint/README.md)

* [get](docs/sdks/jwksetendpoint/README.md#get) - Get JWK Set

### [securityKeys()](docs/sdks/securitykeys/README.md)

* [get](docs/sdks/securitykeys/README.md#get) - Get Security Key

### [serviceManagement()](docs/sdks/servicemanagement/README.md)

* [get](docs/sdks/servicemanagement/README.md#get) - Get Service
* [list](docs/sdks/servicemanagement/README.md#list) - List Services
* [getConfiguration](docs/sdks/servicemanagement/README.md#getconfiguration) - Get Service Configuration

### [services()](docs/sdks/services/README.md)

* [create](docs/sdks/services/README.md#create) - Create Service
* [update](docs/sdks/services/README.md#update) - Update Service
* [delete](docs/sdks/services/README.md#delete) - Delete Service ⚡

### [tokenEndpoint()](docs/sdks/tokenendpoint/README.md)

* [process](docs/sdks/tokenendpoint/README.md#process) - Process Token Request
* [processForm](docs/sdks/tokenendpoint/README.md#processform) - Process Token Request
* [issue](docs/sdks/tokenendpoint/README.md#issue) - Issue Token Response
* [issueForm](docs/sdks/tokenendpoint/README.md#issueform) - Issue Token Response

### [tokenOperations()](docs/sdks/tokenoperations/README.md)

* [delete](docs/sdks/tokenoperations/README.md#delete) - Delete Access Token
* [revoke](docs/sdks/tokenoperations/README.md#revoke) - Revoke Access Token
* [revokeForm](docs/sdks/tokenoperations/README.md#revokeform) - Revoke Access Token

### [tokens()](docs/sdks/tokens/README.md)

* [fail](docs/sdks/tokens/README.md#fail) - Fail Token Request
* [failForm](docs/sdks/tokens/README.md#failform) - Fail Token Request
* [revoke](docs/sdks/tokens/README.md#revoke) - Process Revocation Request
* [revokeForm](docs/sdks/tokens/README.md#revokeform) - Process Revocation Request
* [reissueId](docs/sdks/tokens/README.md#reissueid) - Reissue ID Token
* [list](docs/sdks/tokens/README.md#list) - List Issued Tokens
* [create](docs/sdks/tokens/README.md#create) - Create Access Token
* [createForm](docs/sdks/tokens/README.md#createform) - Create Access Token
* [update](docs/sdks/tokens/README.md#update) - Update Access Token
* [updateForm](docs/sdks/tokens/README.md#updateform) - Update Access Token

### [userinfo()](docs/sdks/userinfo/README.md)

* [get](docs/sdks/userinfo/README.md#get) - Process UserInfo Request
* [getForm](docs/sdks/userinfo/README.md#getform) - Process UserInfo Request
* [issue](docs/sdks/userinfo/README.md#issue) - Issue UserInfo Response
* [issueForm](docs/sdks/userinfo/README.md#issueform) - Issue UserInfo Response

### [utilityEndpoints()](docs/sdks/utilityendpoints/README.md)

* [getInfo](docs/sdks/utilityendpoints/README.md#getinfo) - Get Server Metadata
* [echo](docs/sdks/utilityendpoints/README.md#echo) - Echo

### [vci()](docs/sdks/vci/README.md)

* [parseSingle](docs/sdks/vci/README.md#parsesingle) - /api/{serviceId}/vci/single/parse API
* [parseSingleForm](docs/sdks/vci/README.md#parsesingleform) - /api/{serviceId}/vci/single/parse API

### [verifiableCredentialIssuer()](docs/sdks/verifiablecredentialissuer/README.md)

* [getMetadata](docs/sdks/verifiablecredentialissuer/README.md#getmetadata) - /api/{serviceId}/vci/metadata API
* [getMetadataForm](docs/sdks/verifiablecredentialissuer/README.md#getmetadataform) - /api/{serviceId}/vci/metadata API
* [postJwks](docs/sdks/verifiablecredentialissuer/README.md#postjwks) - /api/{serviceId}/vci/jwks API
* [postJwksForm](docs/sdks/verifiablecredentialissuer/README.md#postjwksform) - /api/{serviceId}/vci/jwks API
* [createOffer](docs/sdks/verifiablecredentialissuer/README.md#createoffer) - /api/{serviceId}/vci/offer/create API
* [createOfferForm](docs/sdks/verifiablecredentialissuer/README.md#createofferform) - /api/{serviceId}/vci/offer/create API
* [getOfferInfo](docs/sdks/verifiablecredentialissuer/README.md#getofferinfo) - /api/{serviceId}/vci/offer/info API
* [getOfferInfoForm](docs/sdks/verifiablecredentialissuer/README.md#getofferinfoform) - /api/{serviceId}/vci/offer/info API
* [issueSingle](docs/sdks/verifiablecredentialissuer/README.md#issuesingle) - /api/{serviceId}/vci/single/issue API
* [batchParse](docs/sdks/verifiablecredentialissuer/README.md#batchparse) - /api/{serviceId}/vci/batch/parse API
* [batchParseForm](docs/sdks/verifiablecredentialissuer/README.md#batchparseform) - /api/{serviceId}/vci/batch/parse API
* [parseDeferred](docs/sdks/verifiablecredentialissuer/README.md#parsedeferred) - /api/{serviceId}/vci/deferred/parse API
* [parseDeferredForm](docs/sdks/verifiablecredentialissuer/README.md#parsedeferredform) - /api/{serviceId}/vci/deferred/parse API
* [issueDeferred](docs/sdks/verifiablecredentialissuer/README.md#issuedeferred) - /api/{serviceId}/vci/deferred/issue API

</details>
<!-- End Available Resources and Operations [operations] -->

<!-- Start Error Handling [errors] -->
## Error Handling

Handling errors in this SDK should largely match your expectations. All operations return a response object or raise an exception.

By default, an API error will throw a `models/errors/APIException` exception. When custom error responses are specified for an operation, the SDK may also throw their associated exception. You can refer to respective *Errors* tables in SDK docs for more details on possible exception types for each operation. For example, the `get` method throws the following exceptions:

| Error Type                                                                   | Status Code | Content Type     |
| ---------------------------------------------------------------------------- | ----------- | ---------------- |
| models/errors/1api1infoGetResponses400Exception                              | 400         | application/json |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 401, 403    | application/json |
| models/errors/1api1infoGetResponses400ContentApplication1jsonSchemaException | 500         | application/json |
| models/errors/APIException                                                   | 4XX, 5XX    | \*/\*            |

### Example

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.ServiceGetApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ServiceGetApiResponse res = sdk.serviceManagement().get()
                .serviceId("<id>")
                .call();

        if (res.service().isPresent()) {
            // handle response
        }
    }
}
```
<!-- End Error Handling [errors] -->

<!-- Start Server Selection [server] -->
## Server Selection

### Select Server by Index

You can override the default server globally using the `.serverIndex(int serverIdx)` builder method when initializing the SDK client instance. The selected server will then be used as the default on the operations that use it. This table lists the indexes associated with the available servers:

| #   | Server                    | Description         |
| --- | ------------------------- | ------------------- |
| 0   | `https://us.authlete.com` | 🇺🇸 US Cluster     |
| 1   | `https://jp.authlete.com` | 🇯🇵 Japan Cluster  |
| 2   | `https://eu.authlete.com` | 🇪🇺 Europe Cluster |
| 3   | `https://br.authlete.com` | 🇧🇷 Brazil Cluster |

#### Example

```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.ServiceGetApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .serverIndex(3)
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ServiceGetApiResponse res = sdk.serviceManagement().get()
                .serviceId("<id>")
                .call();

        if (res.service().isPresent()) {
            // handle response
        }
    }
}
```

### Override Server URL Per-Client

The default server can also be overridden globally using the `.serverURL(String serverUrl)` builder method when initializing the SDK client instance. For example:
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Authelete;
import org.openapis.openapi.models.components.Security;
import org.openapis.openapi.models.errors.1api1infoGetResponses400ContentApplication1jsonSchemaException;
import org.openapis.openapi.models.errors.1api1infoGetResponses400Exception;
import org.openapis.openapi.models.operations.ServiceGetApiResponse;

public class Application {

    public static void main(String[] args) throws 1api1infoGetResponses400Exception, 1api1infoGetResponses400ContentApplication1jsonSchemaException, 1api1infoGetResponses400ContentApplication1jsonSchemaException, Exception {

        Authelete sdk = Authelete.builder()
                .serverURL("https://br.authlete.com")
                .security(Security.builder()
                    .authlete(System.getenv().getOrDefault("AUTHLETE", ""))
                    .build())
            .build();

        ServiceGetApiResponse res = sdk.serviceManagement().get()
                .serviceId("<id>")
                .call();

        if (res.service().isPresent()) {
            // handle response
        }
    }
}
```
<!-- End Server Selection [server] -->

<!-- Start Debugging [debug] -->
## Debugging

### Debug
You can setup your SDK to emit debug logs for SDK requests and responses.

For request and response logging (especially json bodies), call `enableHTTPDebugLogging(boolean)` on the SDK builder like so:
```java
SDK.builder()
    .enableHTTPDebugLogging(true)
    .build();
```
Example output:
```
Sending request: http://localhost:35123/bearer#global GET
Request headers: {Accept=[application/json], Authorization=[******], Client-Level-Header=[added by client], Idempotency-Key=[some-key], x-speakeasy-user-agent=[speakeasy-sdk/java 0.0.1 internal 0.1.0 org.openapis.openapi]}
Received response: (GET http://localhost:35123/bearer#global) 200
Response headers: {access-control-allow-credentials=[true], access-control-allow-origin=[*], connection=[keep-alive], content-length=[50], content-type=[application/json], date=[Wed, 09 Apr 2025 01:43:29 GMT], server=[gunicorn/19.9.0]}
Response body:
{
  "authenticated": true, 
  "token": "global"
}
```
__WARNING__: This should only used for temporary debugging purposes. Leaving this option on in a production system could expose credentials/secrets in logs. <i>Authorization</i> headers are redacted by default and there is the ability to specify redacted header names via `SpeakeasyHTTPClient.setRedactedHeaders`.

__NOTE__: This is a convenience method that calls `HTTPClient.enableDebugLogging()`. The `SpeakeasyHTTPClient` honors this setting. If you are using a custom HTTP client, it is up to the custom client to honor this setting.

Another option is to set the System property `-Djdk.httpclient.HttpClient.log=all`. However, this second option does not log bodies.
<!-- End Debugging [debug] -->

<!-- Placeholder for Future Speakeasy SDK Sections -->

# Development

## Maturity

This SDK is in beta, and there may be breaking changes between versions without a major version update. Therefore, we recommend pinning usage
to a specific package version. This way, you can install the same version each time without breaking changes unless you are intentionally
looking for the latest version.

## Contributions

While we value open-source contributions to this SDK, this library is generated programmatically. Any manual changes added to internal files will be overwritten on the next generation. 
We look forward to hearing your feedback. Feel free to open a PR or an issue with a proof of concept and we'll do our best to include it in a future release. 

### SDK Created by [Speakeasy](https://www.speakeasy.com/?utm_source=openapi&utm_campaign=java)

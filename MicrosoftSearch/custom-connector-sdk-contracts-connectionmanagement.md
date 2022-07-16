---
title: "Microsoft Graph connectors SDK contracts connection management API and models"
ms.author: rchanda
author: rchanda1392
manager: harshkum
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.date: 06/29/2022
description: "Microsoft Graph connectors SDK contracts connection management API and models"
---

# Microsoft Graph connectors SDK contracts connection management API and models

The Microsoft Graph connectors SDK contracts connection management API and models are called during the process of **custom connector connection creation** on the [Microsoft 365 admin center](https://admin.microsoft.com/adminportal/home#/MicrosoftSearch/Connectors/add).

## Connection management APIs

|Method |Parameters |Return Type |Description |
|:----------|:-------------|:----------|:-------------|
|ValidateAuthentication |[ValidateAuthenticationRequest](#validateauthenticationrequest) |[ValidateAuthenticationResponse](#validateauthenticationresponse) |Validates the credentials and data source path provided by the admin in the connection settings step. |
|ValidateCustomConfiguration |[ValidateCustomConfigurationRequest](#validatecustomconfigurationrequest) |[ValidateCustomConfigurationResponse](#validatecustomconfigurationresponse) |Validates the optional configuration provided by the admin in the connection configuration step. If no configuration is required for the connector, this API can return a success response. |
|GetDataSourceSchema |[GetDataSourceSchemaRequest](#getdatasourceschemarequest) |[GetDataSourceSchemaResponse](#getdatasourceschemaresponse) |Gets the data source schema in a format that can be understood by Microsoft Graph. |

### Connection management API Models

The following are the connection management API models:

#### ValidateAuthenticationRequest

Request model to validate the authentication request to the data source.

|Property |Type |Description |
|:----------|:-------------|:----------|
|authenticationData |[AuthenticationData](/microsoftsearch/custom-connector-sdk-contracts-common#authenticationdata) |Holds the data source access URL and the credentials to access it. |

#### ValidateAuthenticationResponse

Response model to validate the authentication response to the data source.

|Property |Type |Description |
|:----------|:-------------|:----------|
|status |[OperationStatus](/microsoftsearch/custom-connector-sdk-contracts-common#operationstatus) |Shows the status of the operation and details like error messages. |
|oAuth2ClientCredentialResponse |[OAuth2ClientCredentialResponse](/microsoftsearch/custom-connector-sdk-contracts-common#oauth2clientcredentialresponse) |Credential information to be sent to the connector during the crawl if OAuth flow is used (access token, refresh token etc., sent by the auth server).|

#### ValidateCustomConfigurationRequest

Request model to validate custom configuration request information.

|Property |Type |Description |
|:----------|:-------------|:----------|
|customConfiguration |[CustomConfiguration](/microsoftsearch/custom-connector-sdk-contracts-common#customconfiguration) |Provides configuration data for the connector. |
|authenticationData |[AuthenticationData](/microsoftsearch/custom-connector-sdk-contracts-common#authenticationdata) |Holds the data source access URL and the credentials to access it. |

#### ValidateCustomConfigurationResponse

Request model to validate custom configuration response information.

|Property |Type |Description |
|:----------|:-------------|:----------|
|status |[OperationStatus](/microsoftsearch/custom-connector-sdk-contracts-common#operationstatus) |Shows the status of the operation and details like error messages. |

#### GetDataSourceSchemaRequest

Request model to get the schema request of the data source.

|Property |Type |Description |
|:----------|:-------------|:----------|
|customConfiguration |[CustomConfiguration](/microsoftsearch/custom-connector-sdk-contracts-common#customconfiguration) |Provides configuration data for the connector. |
|authenticationData |[AuthenticationData](/microsoftsearch/custom-connector-sdk-contracts-common#authenticationdata) |Holds the data source access URL and the credentials to access it. |

#### GetDataSourceSchemaResponse

Request model to get the schema response of the data source.

|Property |Type |Description |
|:----------|:-------------|:----------|
|status |[OperationStatus](/microsoftsearch/custom-connector-sdk-contracts-common#operationstatus) |Shows the status of the operation and details like error messages. |
|dataSourceSchema |[DataSourceSchema](/microsoftsearch/custom-connector-sdk-contracts-common#datasourceschema) |Shows the data source schema.|

## See also

* [Microsoft Graph connectors API v1.0 reference for the schema resource type](/graph/api/resources/externalconnectors-schema)
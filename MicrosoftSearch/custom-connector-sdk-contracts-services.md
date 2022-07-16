---
title: "Microsoft Graph connectors SDK contract services"
ms.author: rchanda
author: rchanda1392
manager: harshkum
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.date: 06/29/2022
description: Microsoft Graph connectors SDK contract services
---

# Microsoft Graph connectors SDK contract services

In this article, you can see the services that are part of the contract protocol buffer files. These services should be implemented as part of the connector.

|Services |Description |
|:----------|:-------------|
|[ConnectorInfo](/microsoftsearch/custom-connector-sdk-contracts-connectorinfo) |Includes APIs to get information about the connector. If you're using the Visual Studio extension, you can use the default implementation for this service without changes. |
|[ConnectionManagement](/MicrosoftSearch/custom-connector-sdk-contracts-connectionmanagement) |Contains APIs that are called during the process of **custom connector connection creation** on the Microsoft 365 admin center. |
|[ConnectorCrawl](/MicrosoftSearch/custom-connector-sdk-contracts-connectorcrawler) |Includes APIs that are called during a crawl. |
|[ConnectorOAuth](/MicrosoftSearch/custom-connector-sdk-contracts-connectoroauth) |Service for OAuth flows like refreshing access token during crawls. |

You can download the contract protocol buffer files from the Microsoft Graph connectors SDK [contracts](https://github.com/microsoftgraph/msgraph-connectors-sdk/tree/main/Contracts) page in GitHub.

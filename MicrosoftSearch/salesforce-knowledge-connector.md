--- 
title: "Salesforce Knowledge Connector for Microsoft Search and Copilot" 
ms.author: rerabo
author: vivg
manager: igala
audience: Admin
ms.audience: Admin 
ms.topic: article 
ms.service: mssearch 
ms.localizationpriority: medium 
search.appverid: 
- BFB160 
- MET150 
- MOE150 
description: "Set up the Salesforce Knowledge Microsoft Graph connector for Microsoft Search and Microsoft 365 Copilot" 
ms.date: 12/05/2024
---

# Salesforce Knowledge Microsoft Graph connector

The Salesforce Knowledge Graph connector allows your organization to index articles from Salesforce Knowledge. After you configure the connector, end users can search for Knowledge articles from Salesforce in Microsoft Copilot and from any Microsoft Search client. 

This documentation is for Microsoft 365 administrators or anyone who configures, runs, and monitors a Salesforce Knowledge Graph connector. 

>[!NOTE]
>The Salesforce Knowledge Graph connector is in preview. If you wish to get early access to try it, sign up using [this form](https://forms.office.com/r/JniPmK5bzm).

## Capabilities
- Index Salesforce Knowledge articles.
- Enable users within the company to ask questions in natural language using Copilot and receive answers based on articles in Salesforce. Examples:
   - What are the steps for processing a refund?
   - What is the escalation procedure for high-priority cases?
   - What are the latest updates to our product warranty policy?
- Use [Semantic search in Copilot](semantic-index-for-copilot.md) to enable users to find relevant content based on keywords, personal preferences, and social connections.

## Limitations
- The connector doesn't support ACLs (access control lists). All the data indexed using the Salesforce Knowledge connector is visible to all Microsoft 365 users in your tenant, accessible through Microsoft Search or Copilot.

## Prerequisites
- You must be a search admin for your organization's Microsoft 365 tenant.
- To create a new connection, use your organization’s Salesforce Knowledge Instance URL. This URL is the specific web address used to access and interact with Salesforce Knowledge's API services for data retrieval, which usually looks like `https://[COMPANY_NAME].my.salesforce.com`. 
     
## Get Started

### 1. Display name 
A display name is used to identify each citation in Copilot, helping users easily recognize the associated file or item. Display name also signifies trusted content. Display name is also used as a content source filter. A default value is present for this field, but you can customize it to a name that users in your organization recognize.

### 2. Salesforce Knowledge URL
Use your organization’s Salesforce Knowledge Instance URL. This URL is the specific web address used to access and interact with Salesforce Knowledge's API services for data retrieval, which typically looks like `https://[COMPANY_NAME].my.salesforce.com`

### 3. Authentication Type
For Salesforce Knowledge graph connector, use OAuth 2.0 for authentication. 

To authenticate, enter the Client ID and Client Secret. The Client ID is a unique identifier assigned to your application for making requests to the Salesforce Knowledge API. The Client Secret is a confidential key used alongside the Client ID to securely authenticate your application with the Salesforce Knowledge API. 
 
### 4. Roll out to limited audience
Deploy this connection to a limited user base if you want to validate it in Copilot and other Search surfaces before expanding the rollout to a broader audience. To know more about limited rollout, see [staged rollout](staged-rollout-for-graph-connectors.md).

At this point, you're ready to create the connection for Salesforce Knowledge. You can click on the "Create" button to publish your connection and index posts from your Salesforce Knowledge account.

## Custom Setup

Custom setup is for admins who want to edit the default values for settings. Once you click on the 'Custom Setup' option, you see three other tabs: Users, Content, and Sync.

### Users
Currently, articles from your organization’s Salesforce Knowledge instance are indexed. All the data indexed using the Salesforce Knowledge connector is visible to all Microsoft 365 users in your tenant, accessible through Microsoft Search or Copilot. 
 
### Content

**Manage properties**

Here, you can add or remove available properties from your Salesforce Knowledge data source, assign a schema to the property (define whether a property is searchable, queryable, retrievable, or refinable), change the semantic label and add an alias to the property. Properties that are selected by default are listed below:

**Source Property** | **Semantic Label** |**Description**| **Schema**
--- | ---- | --- | ---
ArticleId | | | Query, Retrieve 
ArticleNumber | | The unique number automatically assigned to the article when it's created. | Query, Retrieve 
ArticleType | | The type or category of the knowledge article (for example, FAQ, Support Article, How-To). | Retrieve 
CondensedBody | | Includes the Full content or main body of the article | Retrieve, Search 
CreatedById | | | Query, Retrieve, Search 
CreatedByName | createdBy | The user who initially created the article. | Query, Retrieve, Search 
CreatedDate | createdDateTime | Timestamp of when the article was initially created. | Query, Retrieve 
IconUrl | iconUrl | | Retrieve 
Language | | The language in which the article is written. | Retrieve 
LastModifiedById | | | Query, Retrieve, Search 
LastModifiedByName | lastModifiedBy | The user who last updated the article. | Query, Retrieve, Search 
LastModifiedDate | lastModifiedDateTime | Timestamp of the most recent update to the article. | Query, Retrieve 
LastPublishedDate | | The date when the article was last published. | Query, Retrieve 
LastPublishedVersionId | | | Query, Retrieve 
Summary | | A brief overview or abstract of the article's content. | Search 
Title | title | The main headline or title of the article. | Query, Retrieve, Search 
Url | url | Link to the article in Salesforce Knowledge. | Retrieve 
UrlName | | A unique URL-friendly name generated for the article. | Query, Retrieve 

### Sync

The refresh interval determines how often your data is synced between the data source and the Graph connector index. There are two types of refresh intervals - full crawl and incremental crawl. For more information, see [refresh settings](configure-connector.md#step-8-refresh-settings).

## Troubleshooting
After publishing your connection, you can review the status under the **Data Sources** tab in the [admin center](https://admin.microsoft.com). To learn how to make updates and deletions, see [Manage your connector](manage-connector.md). 

If you have issues or want to provide feedback, contact [Microsoft Graph | Support](https://developer.microsoft.com/en-us/graph/support).

---
title: "Configure your Microsoft-built connector for Microsoft Search"
ms.author: monaray
author: monaray97
manager: jameslau
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Configure your Microsoft-built connector for Microsoft Search"
---
<!-- markdownlint-disable no-trailing-punctuation -->

# Set up your Microsoft-built connector for Microsoft Search

This article guides you through the steps of configuring a Microsoft-built connector. It outlines the flow of setting up a connection in the Microsoft 365 [admin center](https://admin.microsoft.com). For more information on how to set up specific Microsoft-built connectors, see these articles:

* [Azure Data Lake Storage Gen2](azure-data-lake-connector.md)
* [Azure DevOps](azure-devops-connector.md)
* [Azure SQL](MSSQL-connector.md)
* [Enterprise websites](enterprise-web-connector.md)
* [MediaWiki](mediawiki-connector.md)
* [Microsoft SQL server](MSSQL-connector.md)
* [ServiceNow](servicenow-connector.md)

## Set up

Complete the following steps to configure any of the Microsoft-built connectors.

1. Go to the [Connectors tab](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/Connectors) in the [Microsoft 365 admin center](https://admin.microsoft.com).
2. Sign in to your account with the credentials for your [Microsoft 365](https://www.microsoft.com/microsoft-365) tenant.
3. Select **Add a connector**.
4. From the list of available connectors, select the connector of your choice.

![Data sources available include: Azure DevOps Connector, ServiceNow, ADLS Gen2, Enterprise websites, MediaWiki, Microsoft SQL server, and Azure SQL.](media/add_connector.png)

### Name the connector

To create a connection, first specify these attributes:

1. Name of the connection
2. Connection ID
3. Description (optional)

The connection ID creates implicit properties for your connector. It must contain only alphanumeric characters and be a maximum of 32 characters.

### Connect to a data source

The data connection process varies based on the type of connector. To learn more about connecting to your on-premises data source, see [Install an on-premises data gateway](https://aka.ms/configuregateway).

### Select source properties

The data fields set by your third-party data source as source properties are indexed into Microsoft Search. To modify these properties, select **Edit properties** in the side bar on the right of the **Connectors** page. You can select **up to 64 source properties**.

### Manage the search schema

#### Content property

You can select which source property is the **content** property (full-text index of the item) by selecting any string property from the **content** property dropdown. Alternatively, you can keep the default selected property if one is present.

It is especially important that the correct property is selected since this property used for full-text indexing of content, search results page snippet generation, language detection, HTML/text support, ranking and relevance, and query formulation.

If you select a property for **content**, you will have the option of using the system-generated property **ResultSnippet** when you [create your result type](customize-results-layout.md). This property serves as a placeholder for the dynamic snippets that are generated from the **content** property at query time. If you use this property in your result type, snippets will be generated in your search results.

#### Search schema attributes

You can set the search schema attributes to control search functionality of each source property. A search schema helps determine what results display on the search results page and what information end users can view and access.

Search schema attributes include **searchable**, **queryable**, and **retrievable**. The following table lists each of the attributes that Microsoft Graph connectors support and explains their functions.

Search schema attribute | Function | Example
--- | --- | ---
SEARCHABLE | Makes the text content of a property searchable. Property contents are included in the full-text index. | If the property is **title**, a query for **Enterprise** returns answers that contain the word **Enterprise** in any text or title.
QUERYABLE | Searches by query for a match for a particular property. The property name can then be specified in the query either programmatically or verbatim. |  If the **Title** property is queryable, then the query **Title: Enterprise** is supported.
RETRIEVABLE | Only retrievable properties can be used in the result type and display in the search result. |

For all connectors, custom types must be set manually. To activate search capabilities for each field, you need a search schema mapped to a list of properties. The connection wizard automatically selects a search schema based on the set of source properties you choose. You can modify this schema by selecting the check boxes for each property and attribute in the search schema page.

![Schema for a connector can be customized by adding or removing Query, Search, and Retrieve functions.](media/manageschema.png)

#### Restrictions and recommendations for search schema settings

* The **content** property is searchable only. Once selected in the dropdown, this property cannot be marked **retrievable** or **queryable**. Significant performance issues occur when search results render with the **content** property. An example is the **Text** content field for a [ServiceNow](https://www.servicenow.com) knowledge-base article.

* Only properties marked as retrievable render in the search results and can be used to create modern result types (MRTs).

* Only string properties can be marked searchable.


> [!Note]
> After you create a connection, you **can't** modify the schema. To do that, you need to delete your connection and create a new one.

### Manage search permissions

Access Control Lists (ACLs) determine which users in your organization can access each item of data. All the connectors support search permissions that are visible to all users.

### Set the refresh schedule

The refresh schedule determines how often your data is synced with the index in Microsoft Graph and Microsoft Search. You can schedule the refresh in two ways: full crawl or incremental crawl.

With a **full crawl**, the search engine processes and indexes every item in the content source, regardless of previous crawls. Full crawl works best in these situations:

* Detecting deletions of data.
* The incremental crawl failed to crawl content for errors.
* ACLs were modified.
* Crawl rules were modified.
* A software update for Microsoft Search is required. Updates modify the search schema.

With an **incremental crawl**, the search engine can process and index only the items that were created or modified since the last successful crawl. Therefore, not all the data in the content source is re-indexed. Incremental crawls work best to detect content, metadata, permission, and other updates.

Incremental crawls are much faster than full crawls because unchanged items aren’t processed. To maintain an accurate data sync between the content source and the search index, you need to run both crawls periodically.

Each connector will have a different optimal set of refresh schedules based on how often data is modified and the type of modifications.

![Incremental crawl and full crawl interval settings showing Incremental at 15 minutes and Full crawl at 1 week.](media/refreshschedule.png)

### Review connector settings

After you configure your connector, the [admin center](https://admin.microsoft.com) takes you to a page where you can review your settings. You can go back through the configuration process to edit any setting before you confirm the connection. To learn more, see [Manage your connector](manage-connector.md).

## Next steps: Customize the search results page

With the Microsoft Search user interface (UI), your end users can search content from your [Microsoft 365](https://www.microsoft.com/microsoft-365) productivity apps and the broader Microsoft ecosystem. A search vertical refers to the tabs that are shown when a user views their search results in [SharePoint](https://sharepoint.com/), [Microsoft Office](https://Office.com), and Microsoft Search in [Bing](https://Bing.com). You can customize search verticals to narrow down results, so that only a certain type of search results is displayed. These verticals appear as a tab on the top of the search results page. A modern result type (MRT) is the UI that designates how results are presented.

Create your own verticals and result types, so end users can view search results from new connections. Without this step, data from your connection won’t show up on the search results page.

To learn more about how to create your verticals and MRTs, see [Search results page customization](customize-search-page.md).

## How do I know the connection setup worked?

Go to the list of your published connections under the **Connectors** tab in the [admin center](https://admin.microsoft.com). To learn how to make updates and deletions, see [Manage your connector](manage-connector.md).

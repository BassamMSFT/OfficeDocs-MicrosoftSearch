---
title: "Create a custom search results page in SharePoint Online"
ms.author: jeffkizn
author: jeffkizn
manager: jeffkizn
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
description: "Create your own search results page for a SharePoint Online site"
---
# Create a custom search results page in SharePoint Online

One way to customize the search experience in SharePoint is to create a custom search results page for a site. This allows you to use a page that you created, rather than the default in Microsoft Search results page. This gives you more flexibility on how the search results experience looks for your users.

>[!NOTE]
> To make changes to the default Microsoft Search results page that is
available by default, please see [Customize the search results page](customize-search-page.md).

With a custom results page you can create a new page that can be used to control the layout and design of search results to support your organization's needs. You can use any built-in web parts, open-source search web parts from SharePoint Patterns and Practices community, as well as any custom web parts that you may have developed using SharePoint Framework.

## Configure a results page

To configure a custom results page in SharePoint Online follow the steps below:

1. Browse to the site where you would like to configure a custom results page and go to **Site Settings > Site Collection Settings > Search Settings**.

2. In Search Settings, clear selection from **Use the same results page settings as my parent**, choose **Send queries to a custom results page**, and provide a value for **Results page URL:**. Then, save your changes. The URL you use here should be for the page that you created to use as your custom results page.

>[!NOTE]
> The custom results page needs to be on the same domain as your site, but it does not have to be in the same site collection.  

Alternatively, you can use the [Set-PnPSearchSettings SharePoint PnP PowerShell command](https://docs.microsoft.com/powershell/module/sharepoint-pnp/set-pnpsearchsettings?view=sharepoint-ps) to set the value instead of using the Site Settings page.

Once set, the custom search results page is displayed when you search using the Microsoft Search box that appears in the navigation bar on top of the page and is used when you enter search from site pages or the home page of the site. It is not used when you are searching within a list, library, or the site contents page. You may use the link to expand your search from search results in lists and libraries to get to the custom results page.

## Change the layout of your custom results page

A page layout named **HeaderlessSearchResults** can be used to make the search results page appear closer to our out of box search results experience. This new layout can only be active for the pages that are set to be the custom search results page.

To set the page layout, you can use the [Set-PnPClientSidePageSharePoint PnP PowerShell
command](https://docs.microsoft.com/powershell/module/sharepoint-pnp/set-pnpclientsidepage?view=sharepoint-ps) with -LayoutType HeaderlessSearchResults.

## Use SharePoint Framework Query extensions

Custom search results pages can also make use of the [SharePoint Framework Query Extension](https://docs.microsoft.com/sharepoint/dev/spfx/building-search-extensions) to modify the query before it gets sent to the search engine.

## Additional resources

To learn more about custom results page, check out our [Ignite 2019
Search Customization and Development
session](https://myignite.techcommunity.microsoft.com/sessions/85238?source=sessions).

For open source projects, getting started with our Microsoft Search
APIs, and more customization and extensibility samples, visit [Microsoft
Search on GitHub](https://github.com/microsoft-search).

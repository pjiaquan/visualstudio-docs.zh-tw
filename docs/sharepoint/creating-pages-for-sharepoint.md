---
title: "建立 SharePoint 的網頁"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "內容頁面 [Visual Studio 中的 SharePoint 程式開發], 設計"
  - "主版頁面 [Visual Studio 中的 SharePoint 程式開發], 設計"
  - "頁面配置 [Visual Studio 中的 SharePoint 程式開發], 設計"
  - "Visual Studio 中的 SharePoint 開發, 內容頁面"
  - "Visual Studio 中的 SharePoint 開發, 主版頁面"
  - "Visual Studio 中的 SharePoint 開發, 頁面配置"
ms.assetid: 57678ed1-841f-45de-a1d3-5f9e233bf3ce
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 建立 SharePoint 的網頁
  您可以為 SharePoint 網站建立應用程式頁面、網站頁面、主版頁面和頁面配置。  
  
 您可以在 Visual Studio 中使用範本來建立應用程式頁面。  藉由使用 SharePoint Designer 來建立網站頁面、主版頁面和頁面配置。  接著，您可以將這些頁面匯入至 Visual Studio 中，以便在 SharePoint 專案中使用。  
  
 您也可以使用階層式樣式表、ECMAScript 和佈景主題來修改頁面的外觀與行為。  
  
## SharePoint 頁面的類型  
 下表說明 SharePoint 網站所包含的四種主要頁面類型。  
  
|頁面類型|說明|  
|----------|--------|  
|應用程式頁面|如果您想要在頁面中納入自訂程式碼，或要讓多個網站共用頁面，請建立應用程式頁面。  若非如此，網站頁面可能是最佳選擇。|  
|網站頁面|如果您要執行下列任何一項工作，請建立網站頁面：<br /><br /> -   將頁面加入至 SharePoint 文件庫。<br />-   讓頁面能夠裝載動態 Web 組件和 Web 組件區域之類的功能。<br />-   讓使用者能夠使用 SharePoint Designer 自訂頁面。<br /><br /> 如果您想要在頁面中包含自訂程式碼，請不要建立網站頁面。  雖然您可以將自訂程式碼加入至網站頁面，但程式碼會在使用者使用 SharePoint Designer 自訂頁面時停止執行。|  
|主版頁面|如果您要為網站頁面和應用程式頁面定義通用結構，請建立主版頁面。|  
|頁面配置|頁面配置是 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 特有的功能，可讓您進一步為網站頁面和應用程式頁面定義通用結構。|  
  
 如需網頁的每種類型的概觀，請參閱 [建置組塊：頁面和使用者介面](http://go.microsoft.com/fwlink/?LinkID=182095) 以及 [頁面配置和主版頁面](http://go.microsoft.com/fwlink/?LinkID=182096)。  
  
## 建立應用程式頁面  
 在 Visual Studio 中，您可以將 \[**應用程式頁面**\] 項目加入至 SharePoint 專案，以建立應用程式頁面。  您可以將控制項加入至頁面，然後加入程式碼來處理控制項事件。  
  
 您可以在頁面的程式碼檔案中設定中斷點、啟動偵錯工具，然後在本機 SharePoint 網站上測試頁面，而不需執行任何其他設定步驟。  如需詳細資訊，請參閱[建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)。  
  
## 建立網站頁面、主版頁面和頁面配置  
 您可以使用 SharePoint Designer 建立網站頁面、主版頁面和頁面配置。  接著，您可以將這些頁面匯入至 Visual Studio 中。  如果您要利用 Visual Studio 中提供的部署或原始檔控制功能，請匯入您的頁面。  如需詳細資訊，請參閱[從現有的 SharePoint 網站匯入項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)。  
  
 這些頁面一旦匯入即難以修改，因此您應該在匯入這些頁面之前先做好設計。  
  
## 建立階層式樣式表、ECMAScript 和佈景主題  
 Visual Studio 並未提供範本來開發 SharePoint 網站的階層式樣式表 \(CSS\)、ECMAScript \(JavaScript、JScript\) 或佈景主題檔案。  您可以使用 SharePoint SDK 中提供的指引或 SharePoint Designer 之類的工具，來建立這些檔案。  
  
 您可以直接將這些檔案加入至方案，也可以匯入這些檔案。  無論採用何種方式，您都必須為每個加入的項目建立適當的對應資料夾。  如需如何建立對應資料夾的詳細資訊，請參閱 [如何：新增與移除對應的資料夾](../sharepoint/how-to-add-and-remove-mapped-folders.md)。  
  
 如需建立階層式樣式表的詳細資訊，請參閱 [SharePoint Foundation 中的階層式樣式表類別使用方式](http://go.microsoft.com/fwlink/?LinkID=182098)。  如需為 SharePoint 方案建立 JavaScript 和 JScript 檔案的詳細資訊，請參閱 [設定 ECMAScript 的基本 ASPX 頁面](http://go.microsoft.com/fwlink/?LinkID=182099)。  如需佈景主題的詳細資訊，請參閱 [建置組塊：頁面和使用者介面](http://go.microsoft.com/fwlink/?LinkID=182095)。  
  
## 相關主題  
  
|標題|說明|  
|--------|--------|  
|[建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)|說明如何加入應用程式頁面，即與 SharePoint 主版頁面合併的 .aspx 內容。|  
|[如何：建立應用程式頁面](../sharepoint/how-to-create-an-application-page.md)|示範如何建立在 SharePoint 網站上執行的 ASP.NET 頁面。|  
|[逐步解說：建立 SharePoint 應用程式頁面](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|示範如何設計和偵錯 SharePoint 網站的 ASP.NET 網頁。|  
|[使用 Visual Web Developer](http://msdn.microsoft.com/zh-tw/9c31f93b-c8fb-4599-9b14-6194ec8c7539)|說明如何使用開啟專案中的網頁時出現的設計工具。|  
  
  
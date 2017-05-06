---
title: "建立 SharePoint 的應用程式頁面"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "應用程式頁面 [Visual Studio 中的 SharePoint 程式開發], 建立"
  - "應用程式頁面 [Visual Studio 中的 SharePoint 程式開發], 開發"
  - "Visual Studio 中的 SharePoint 開發, 應用程式頁面"
  - "Visual Studio 中的 SharePoint 開發, 內容頁面"
  - "Visual Studio 中的 SharePoint 開發, Web 網頁"
ms.assetid: a6e97149-15dd-4bdb-8d75-3b53f886f76c
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# 建立 SharePoint 的應用程式頁面
  「*應用程式頁面*」\(Application Page\) 是專門供 SharePoint 網站使用的 ASP.NET Web 網頁。  應用程式頁面是專門的 ASP.NET 網頁類型，  它和標準 ASP.NET 網頁之間的主要差異，在於應用程式頁面包含與 SharePoint 主版頁面合併的內容。  主版頁面可讓應用程式頁面與某一網站上的其他頁面共用相同的外觀和行為。  
  
 Visual Studio 可讓您使用設計工具來設計應用程式頁面。  設計工具會顯示主版頁面中定義之各個內容預留位置的內容區域。  透過將控制項拖曳到這些內容區域的方式，您即可設計應用程式頁面。  
  
## 應用程式頁面  
 應用程式頁面會在伺服器上所有的網站中共用，而網站頁面則僅供單一網站使用。  如需詳細資訊，請參閱 [SharePoint 頁面類型](http://go.microsoft.com/fwlink/?LinkID=211584)。  
  
 當您建立 SharePoint 網站時，顯示的多數頁面預設都是網站頁面。  網站頁面可以加入至 SharePoint 網頁庫。  使用者可以使用工具 \(例如 SharePoint Designer\) 來自訂網站頁面。  網站頁面也可以裝載功能 \(例如動態網頁組件和網頁組件區域\)。  
  
 應用程式頁面就無法執行上述工作。  但是，如果您想要在頁面中納入自訂程式碼，應用程式頁面就是最適當的網頁類型。  雖然您可以將自訂程式碼加入至網站頁面，但程式碼會在使用者利用工具 \(例如 SharePoint Designer\) 自訂頁面時停止執行。  
  
> [!NOTE]  
>  Visual Studio 並不提供可協助您為 SharePoint 網站建立網站頁面的範本。  如需詳細資訊，請參閱 [SharePoint 頁面類型](http://go.microsoft.com/fwlink/?LinkID=211584)。  
  
## 建立應用程式頁面  
 若要建立應用程式頁面，請將 \[**應用程式頁面**\] 項目加入至 SharePoint 專案。  建立應用程式頁面時，Visual Studio 會在您的專案中加入下列資料夾：  
  
|資料夾|說明|  
|---------|--------|  
|Layouts|對應至 SharePoint 檔案系統的 \_layouts 虛擬目錄。|  
|Layouts 子資料夾|包含組成應用程式頁面的檔案。  根據預設，這個資料夾的名稱與專案名稱相同，  您可以隨時重新命名此資料夾。  在您執行專案時，Visual Studio 會將此資料夾部署至 SharePoint 檔案系統的 \_layouts 虛擬目錄。|  
  
 Visual Studio 會將下列檔案加入至您的專案：  
  
|檔案|說明|  
|--------|--------|  
|ASP.NET 網頁檔 \(.aspx\)|包含可定義頁面的 XML 標記。|  
|應用程式頁面程式碼檔|包含應用程式頁面的組成程式碼。  加入可處理此檔案之事件的程式碼。|  
|應用程式頁面設計工具程式碼檔|包含設計工具產生的程式碼。  請勿直接編輯這個檔案。|  
  
## 設計和偵錯應用程式頁面  
 您可以使用 Visual Studio 中的 Visual Web Developer 設計工具，設計應用程式頁面的內容。  這個設計工具會在您開啟專案中的應用程式頁面 \(透過按兩下該項目或是開啟其捷徑功能表中選擇 \[**開啟**\]\) 時顯示。  如需如何使用此設計工具的詳細資訊，請參閱 [Visual Studio Web Development Content Map](http://msdn.microsoft.com/zh-tw/9c31f93b-c8fb-4599-9b14-6194ec8c7539)。  
  
> [!NOTE]  
>  您只能在設計工具的 \[**原始碼**\] 檢視中設計頁面。  設計工具會停用應用程式頁面的 \[**設計**\] 檢視。  
  
 您可以偵錯應用程式頁面，其方式就和偵錯 Visual Studio 中其他 SharePoint 專案項目一樣。  當您啟動 Visual Studio 偵錯工具時，Visual Studio 就會開啟 SharePoint 網站。  
  
 若要檢視應用程式頁面，您必須以手動方式巡覽至應用程式頁面的所在位置 \(例如：http:\/\/*Server\_Name*\/\_layouts\/*Project\_Name*\/ApplicationPage1.aspx\)。  
  
 如需如何偵錯 SharePoint 專案的詳細資訊，請參閱[SharePoint 方案疑難排解](../sharepoint/troubleshooting-sharepoint-solutions.md)。  
  
## 選擇主版頁面  
 在預設情況下，\[**應用程式頁面**\] 項目會參考您用來偵錯專案之網站的主版頁面，  該頁面的名稱為 v4.master，您可以在 SharePoint 網站的 \[**主版頁面圖庫**\] 中找到。  
  
 您可以設定應用程式 `Page` 項目的 `MasterPageFile` 屬性，明確地變更應用程式頁面使用的主版頁面\(例如：`MasterPageFile="~/_layouts/applicationv4.master"`\)。  事實上，如果 SharePoint 伺服器上並未啟用動態主版頁面，您就必須設定這個屬性。  如需 SharePoint 的主版頁面的詳細資訊，請參閱 [主版頁面](http://go.microsoft.com/fwlink/?LinkID=169281)。  
  
## 請參閱  
 [SharePoint 詳細架構開發](http://go.microsoft.com/fwlink/?LinkID=182103)   
 [ASP.NET 網頁概觀](http://msdn.microsoft.com/library/52fa0455-41ea-4315-8208-2861d1527da2)   
 [ASP.NET Web 網頁語法概觀](http://msdn.microsoft.com/library/09074b20-ece9-46fa-bc8f-ab2595ed2c02)   
 [以程式設計 ASP.NET Web 網頁](http://msdn.microsoft.com/zh-tw/5626c661-8057-4de8-b658-c2e35ed4b4c9)  
  
  
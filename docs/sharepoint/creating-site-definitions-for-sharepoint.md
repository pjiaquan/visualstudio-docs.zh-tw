---
title: "建立 SharePoint 的站台定義 | Microsoft Docs"
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
  - "[Visual Studio 中的 SharePoint 開發]，網站定義 "
  - "網站定義 [Visual Studio 中的 SharePoint 開發]"
ms.assetid: 83db570d-6b9f-4dab-9e71-db41f17b987a
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# 建立 SharePoint 的站台定義
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的 SharePoint 網站定義專案可讓您建立「*網站定義*」\(Site Definition\)，這可做為新 SharePoint 網站的基礎。  這些定義不僅決定 SharePoint 網站的外觀和行為，也會定義其預設內容和功能。  在定義中，您可以放入預先設定的清單、內容類型、事件接收器、影像和其他項目。  例如， SharePoint 隨附一些網站定義 \(例如部落格\)。  當您根據部落格網站定義建立網站時，網站會包含部落格網站所需的清單、Web 組件和其他項目。  
  
 如需網站定義的詳細資訊，請參閱 [網站範本和定義](http://go.microsoft.com/fwlink/?LinkId=179134)。  
  
## 網站定義專案  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的網站定義專案只提供 SharePoint 網站所需的基本檔案，而不提供任何預設功能。  您必須加入檔案和內容來提供所要的功能。  您可以建立和加入所需的檔案，以手動建置網站。  
  
## 功能裝訂  
 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中建立網站定義的一個好處是網站定義會自動使用「*功能裝訂*」\(Feature Stapling\)。  功能裝訂會將功能附加至網站定義，而不是將其功能嵌入網站定義本身。  這麼做可讓您將功能加入至使用網站定義建立的任何網站，而不必修改原始網站定義。  如需詳細資訊，請參閱 [裝訂功能](http://go.microsoft.com/fwlink/?LinkID=119283)。  
  
## 網站定義專案元件  
 當您建立網站定義方案時，下列預設檔案會加入其 \[**SiteDefinition**\] 節點。  
  
|檔案名稱|說明|  
|----------|--------|  
|default.aspx|新 SharePoint 網站的預設 ASPX 首頁。|  
|onet.xml|指定新網站的組態、網站定義範本的元件以及預設行為。  這些設定可包含屬性，例如啟用的內容類型、預設清單檢視、文件範本檔案以及網站隨附的 Web 組件。  根據預設，`Modules` 區段會列出要加入至 SharePoint 網站的檔案以及設定它們的方式。|  
|webtemp\_*SiteDefinitionName*.xml|指定網站定義組態，該組態會出現在 \[**新增 SharePoint 網站**\] 頁面的 \[**範本選擇**\] 區段中。|  
  
 根據預設，所有網站定義都儲存在 *drive:*\\Program Files\\Common Files\\Microsoft Shared\\Web Server Extensions\\14\\TEMPLATE\\SiteTemplates 資料夾中。  每個網站定義都有專屬的子資料夾。  
  
## 相關主題  
  
|標題|說明|  
|--------|--------|  
|[逐步解說：建立基本網站定義專案](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|引導您在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中逐步建立基本網站定義專案。|  
|[如何：建立自訂網站定義和組態](http://go.microsoft.com/fwlink/?LinkId=183309)|描述如何藉由複製現有的網站定義及修改複本，在 SharePoint 中建立自訂網站定義。|  
|[WebTemp.xml](http://go.microsoft.com/fwlink/?LinkId=183310)|描述原始檔案，該檔案會在 \[**新增 SharePoint 網站**\] 頁面的 \[**範本選擇**\] 區段中指定可用的網站定義。|  
|[當地語系化 SharePoint 方案](../sharepoint/localizing-sharepoint-solutions.md)|描述如何準備 SharePoint 方案以供全域使用。|  
|[建立 SharePoint 的 Web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)|說明如何建立使用者可修改的 SharePoint 頁面組件。|  
|[為 Web 組件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|說明如何在應用程式頁面和 Web 組件中建立可重複使用的控制項。|  
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|說明如何使用開啟專案中的網頁時出現的設計工具。|  
|[ASP.NET Web 網頁概觀](http://go.microsoft.com/fwlink/?LinkId=178726)|提供 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 網頁結構、[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 如何處理網頁，以及 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 網頁如何顯示符合 XHTML 標準之標記的一般資訊。|  
|[ASP.NET Web 網頁語法](http://go.microsoft.com/fwlink/?LinkId=178727)|說明構成 ASP.NET 網頁的標記項目。|  
|[以程式設計 ASP.NET Web 網頁](http://go.microsoft.com/fwlink/?LinkId=178728)|提供如何在 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 網頁中建立事件處理常式，以及如何使用用戶端指令碼的相關資訊。|  
|[Windows SharePoint Services 的程式設計](http://go.microsoft.com/fwlink/?LinkId=178729)|說明如何使用 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 中提供的 Managed 物件模型。|  
  
## 請參閱  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  
---
title: "沙箱化方案考量 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.SandboxedSolutions"
  - "VS.SharePointTools.Security.SandboxedSolutions"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "陣列方案 [Visual Studio 中的 SharePoint 開發]"
  - "沙箱化方案 [Visual Studio 中的 SharePoint 開發]"
  - "Visual Studio 中的 SharePoint 開發, 陣列方案"
  - "Visual Studio 中的 SharePoint 開發, 沙箱化方案"
ms.assetid: 6c2d2dc6-4acb-4b68-ba94-a61087e8dff0
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# 沙箱化方案考量
  「*沙箱化方案*」\(Sandboxed Solution\) 是 Microsoft SharePoint 2010 中的功能，可讓網站集合使用者上載自己的自訂程式碼方案。  常見的沙箱化方案是使用者上載自己的 Web 組件。  
  
 沙箱 SharePoint 應用程式會在安全、受監控的處理序中執行，此處理序只能存取 Web 伺服陣列的有限部分。  Microsoft SharePoint 2010 使用功能、方案庫、方案監視和驗證架構的組合來啟用沙箱化方案。  
  
## 指定專案信任層級  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 透過名為 \[*Sandboxed Solution*\] 的布林專案屬性，支援沙箱化方案。  您可以隨時在專案中設定此屬性，或可以在 \[**SharePoint 自訂精靈**\] 中建立專案時指定它。  
  
> [!NOTE]  
>  若在建立專案後才變更其 \[*Sandboxed Solution*\] 屬性，可能會導致驗證錯誤。  
  
 如果 \[*Sandboxed Solution*\] 屬性設定為 \[**false**\]，或是您選取 \[**部署為陣列方案**\] 選項，則方案會被視為陣列範圍方案。  不過，如果 \[*Sandboxed Solution*\] 屬性設定為 \[**true**\]，或是您在精靈中選取 \[**部署為沙箱化方案**\] 選項，則會以不同於陣列方案的方式處理方案。  
  
## SharePoint 網站階層架構  
 若要了解沙箱化方案的運作方式，則知道 SharePoint 網站在範圍中是以階層方式呈現，將會很有幫助。  頂端項目稱為 Web 伺服陣列，其他項目則附屬在下面：  
  
 Web 伺服陣列  
  
 Web 應用程式 A  
  
 網站集合 A1  
  
 網站 A1a  
  
 Web 應用程式 B  
  
 網站集合 B1  
  
 網站 B1a  
  
 網站 B1b  
  
 網站集合 B2  
  
 網站 B2a  
  
 如上所示，Web 伺服陣列可以包含一個或多個 Web 應用程式，而 Web 應用程式又可以包含一個或多個網站集合，網站集合下面又可以有子網站，以此類推。  對一個網站集合所做的變更只會影響該網站集合，不會影響其他網站集合。  不過，在 Web 伺服陣列層級所做的變更則會影響陣列中的所有網站集合。  
  
 Windows SharePoint Services \(WSS\) 3.0 只能讓您將方案部署到陣列層級，但 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 則可讓您部署到陣列層級 \(陣列方案\) 或網站集合層級 \(沙箱化方案\)。  
  
## 為什麼要使用沙箱化方案？  
 在 WSS 3.0 中，方案只能部署到陣列層級。  這表示可能會部署潛在有害或不穩定的方案，而影響到整個 Web 伺服陣列以及在底下執行的所有其他網站集合和應用程式。  不過，藉由使用沙箱化方案，您可以將方案部署至陣列的子區域，即特定的網站集合。  為提供進一步的保護，方案的組件不會載入主 [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] 處理序 \(w3wp.exe\)，  而會載入至另外不同的處理序 \(SPUCWorkerProcess.exe\) 中。  此處理序受到監控，並實作配額和節流以免伺服陣列受到執行有害活動 \(例如執行會耗用 CPU 週期的緊密迴圈\) 的沙箱化方案影響。  
  
## 網站集合方案庫  
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 有稱為「網站集合方案庫」的功能。若要存取這項功能，您可以從 SharePoint 2010 管理中心頁面或透過開啟 \[**網站動作**\] 功能表，選擇 \[**網站設定**\]，然後選擇 SharePoint 網站中在 \[**繪製廊**\] 下的 \[**方案**\] 連結。  方案庫是方案的儲存機制，可讓網站集合管理員管理其網站集合中的方案。  
  
 方案庫是儲存在 SharePoint 網站 Web 根目錄中的文件庫。  方案庫會取代網站範本並支援方案封裝。  上載 SharePoint 方案封裝 \(.wsp\) 檔案時，會以沙箱化方案來處理它。  
  
## 沙箱化方案限制  
 部署沙箱化方案時，它可以使用的 SharePoint 功能陣列會受到限制，有助於減少可能出現的安全性弱點。  下列是部分限制：  
  
-   沙箱化方案只能使用有限的可部署方案項目子集。  易受攻擊的 SharePoint 專案範本 \(如網站定義和工作流程\) 則無法使用。  
  
-   SharePoint 會在與主 [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] 應用程式集區 \(w3wp.exe\) 處理序分開的處理序 \(SPUCWorkerProcess.exe\) 中執行沙箱化方案程式碼。  
  
-   對應的資料夾無法加入至專案。  
  
-   [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 組件 Microsoft.Office.Server 中的型別不能用於沙箱化方案。  此外，只有 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 組件 Microsoft.SharePoint 中的型別能用於沙箱化方案。  
  
 請注意，將 SharePoint 方案指定為沙箱化方案對於 SharePoint 伺服器並沒有任何影響；這只會決定 SharePoint 專案從 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 部署至 SharePoint 的方式，以及所繫結的組件。  這不會影響產生的 .wsp 檔案，而且 .wsp 檔案也沒有資料與 \[*Sandboxed Solution*\] 屬性直接相互關聯。  
  
## 沙箱化方案中的功能和項目  
 沙箱化方案支援下列功能和項目：  
  
-   內容類型\/欄位  
  
-   自訂動作  
  
-   宣告式工作流程  
  
-   事件接收器  
  
-   功能圖說文字  
  
-   清單定義  
  
-   清單執行個體  
  
-   模組\/檔案  
  
-   巡覽  
  
-   Onet.xml  
  
-   SPItemEventReceiver  
  
-   SPListEventReceiver  
  
-   SPWebEventReceiver  
  
-   支援衍生自 `System.Web.UI.WebControls.WebParts.WebPart` 的所有 Web 組件  
  
-   Web 組件  
  
-   WebTemplate 功能項目 \(而非 Webtemp.xml\)  
  
-   視覺 Web 組件  
  
 沙箱化方案不支援下列功能和項目：  
  
-   應用程式頁面  
  
-   自訂動作群組  
  
-   陣列範圍功能  
  
-   `HideCustomAction` 項目  
  
-   Web 應用程式範圍功能  
  
-   具有程式碼的工作流程  
  
## 請參閱  
 [沙箱化方案與伺服器陣列方案之間的差異](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  
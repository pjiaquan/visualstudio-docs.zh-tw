---
title: "建立商務資料連接模型"
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
  - "BDC [Visual Studio 中的 SharePoint 開發], 建立模型"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 建立模型"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 模型"
  - "Visual Studio 中的 SharePoint 開發, 商務資料連接服務"
ms.assetid: 19fd12d0-a51a-4da4-98ac-918542e84507
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# 建立商務資料連接模型
  您可以使用 Visual Studio 來建立商務資料連接 \(BDC\) 模型，或自訂現有的 BDC 模型。  每個 SharePoint 專案均只能包含一個模型。  如需詳細資訊，請參閱[將商業資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)。  
  
## 建立新的模型  
 若要建立新模型，請在\[**空的 SharePoint 專案**\] 中加入 \[**商務資料連接模型**\] 項目，或是建立 \[**商務資料連接模型**\] 專案。  
  
> [!NOTE]  
>  您的電腦中必須安裝 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]。  
  
 Visual Studio 隨即將資料夾加入至專案。  這個資料夾的名稱是您在 \[**加入新項目**\] 對話方塊中，為 \[**商務資料連接模型**\] 項目指定的名稱。  如果您建立了新的 \[**商務資料連接模型**\] 專案，Visual Studio 會將資料夾命名為 \[**BdcModel1**\]。  
  
 Visual Studio 會將下列檔案加入新資料夾中：  
  
|檔案|說明|  
|--------|--------|  
|模型定義檔|包含 XML，該 XML 可定義實體、方法、特定業務 \(LOB\) 系統物件以及其他說明此模型的中繼資料。<br /><br /> 透過使用 \[BDC 設計工具\]、\[**BDC 總管**\]、\[**BDC 方法詳細資料**\] 視窗以及 \[**屬性視窗**\] 的方式，修改這個檔案內的中繼資料。|  
|實體服務程式碼檔案|包含可擷取、更新以及刪除預設實體之執行個體的方法。|  
  
 若要定義實體的屬性，請編輯實體程式碼檔案。  如需詳細資訊，請參閱[如何：將實體加入至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)。  
  
 若要擷取、更新以及刪除實體的執行個體，請在實體服務程式碼檔案中加入程式碼。  如需詳細資訊，請參閱[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
 編譯專案時，Visual Studio 會建立一個組件，  請確認您並未將其他可將程式碼新增到專案組件的項目 \(例如 \[**循序工作流程**\] 項目或 \[**網頁組件**\] 項目\) 加入專案中。  由於方案套件並不會將組件複製到全域組件快取，因此在您部署方案時，該項目的程式碼將不會執行，方案套件只會將組件部署至 SharePoint 中的 BDC 資料庫。  
  
> [!NOTE]  
>  當您偵錯專案時，Visual Studio 會將組件複製到本機電腦上的兩個位置。  
  
## 新增現有模型  
 您可以匯入以其他工具 \(例如 SharePoint 設計工具\) 建立的模型。  在下列情況中，您可能會選擇將現有模型匯入您的專案：  
  
-   自訂已經部署至 SharePoint 伺服器陣列的模型。  
  
-   封裝現有模型並部署至多個 SharePoint 伺服器陣列。  
  
 不論是上述哪一種情況，在匯入的模型中定義之 LOB 系統均不會受到影響，並且會繼續正常運作。  若要將現有模型加入至 SharePoint 專案，請使用 Visual Studio \[**加入現有項目**\] 對話方塊。  如需詳細資訊，請參閱[如何：將現有的 BDC 模型檔案加入至 SharePoint 專案](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)。  
  
 在 \[**加入 .NET 組件 LobSystem**\] 中選取選項，即可將 .NET Framework 組件類型的 LOB 系統加入至您匯入的模型，  這樣一來，您就可以撰寫自訂程式碼，並使用設計工具來定義匯入之模型的中繼資料。  
  
## 相關主題  
  
|標題|說明|  
|--------|--------|  
|[如何：建立 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)|示範如何建立新的 BDC 模型。|  
|[如何：將現有的 BDC 模型檔案加入至 SharePoint 專案](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|示範如何將現有模型匯入至 SharePoint 專案。|  
|[如何：使用資源檔來指定當地語系化名稱、屬性和使用權限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|說明如何在網頁組件或網頁使用模型時，提供與模型中繼資料合併的字串。|  
|[如何：在 BDC 功能中包含自訂組件](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|示範如何將自訂組件納入功能中。|  
  
  
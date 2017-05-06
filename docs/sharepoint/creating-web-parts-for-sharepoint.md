---
title: "建立 SharePoint 的 Web 組件"
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
  - "Microsoft.SharePoint.WebControls.DateTimeControl"
  - "Microsoft.SharePoint.WebControls.CssLink"
  - "Microsoft.SharePoint.WebControls.RssLink"
  - "Microsoft.SharePoint.WebControls.Theme"
  - "Microsoft.SharePoint.WebControls.AspMenu"
  - "Microsoft.SharePoint.WebControls.ListProperty"
  - "Microsoft.SharePoint.WebControls.ProjectProperty"
  - "Microsoft.SharePoint.WebControls.FormsDigest"
  - "Microsoft.SharePoint.WebControls.ScriptLink"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 開發, Web 組件"
  - "Web 組件 [Visual Studio 中的 SharePoint 開發], 設計"
ms.assetid: a6349e85-45cf-4766-b856-e25c9f1ffd34
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# 建立 SharePoint 的 Web 組件
  您可以使用 Web 組件，透過瀏覽器修改 SharePoint 網站頁面的內容、外觀及行為。  Web 組件是在網頁組件頁面內部執行的伺服器端控制項：它們是 SharePoint 網站上顯示之網頁的建置組塊。  請參閱[建置組塊：Web 組件](http://go.microsoft.com/fwlink/?LinkID=182097)。  
  
 透過使用 Visual Studio 提供的範本，您可以在 SharePoint 網站上建立及偵錯 Web 組件。  
  
## 在 Visual Studio 中建立 Web 組件  
 您可以在任何 SharePoint 專案中新增 \[**網頁組件**\] 項目來建立 Web 組件，  您可以使用沙箱化方案或陣列方案中的 \[**網頁組件**\] 項目。  
  
 如果您想要利用設計工具以視覺化方式設計 Web 組件，請建立 \[**視覺 Web 組件**\] 專案，或將 \[**視覺 Web 組件**\] 項目加入至任何 SharePoint 專案。  在一個陣列方案中，您只能使用一個 \[**視覺 Web 組件**\] 項目。  
  
### Web 組件項目  
 \[**網頁組件**\] 項目提供可用來設計 SharePoint 網站之 Web 組件的檔案。  新增 \[**網頁組件**\] 項目時，Visual Studio 會在您的專案中建立一個資料夾，然後在其中加入數個檔案。  下表將針對各個檔案進行說明。  
  
|檔案|描述|  
|--------|--------|  
|Elements.xml|包含專案中功能定義檔案用來部署 Web 組件的資訊。|  
|.webpart 檔|提供 SharePoint 在網頁組件庫中顯示網頁組件時所需的資訊。|  
|程式碼檔|包含方法，這些方法可用來將控制項加入至 Web 組件，並在 Web 組件內部產生自訂內容。|  
  
 如需詳細資訊，請參閱[如何：建立 SharePoint Web 組件](../sharepoint/how-to-create-a-sharepoint-web-part.md)。  
  
### 視覺 Web 組件項目  
 視覺 Web 組件就是您使用 Visual Studio 中的 Visual Web Developer 設計工具所建立的 Web 組件。  請參閱 [Visual Studio Web Development Content Map](http://msdn.microsoft.com/zh-tw/9c31f93b-c8fb-4599-9b14-6194ec8c7539)。  
  
 視覺 Web 組件的運作方式和其他 Web 組件相同。  若要將控制項 \(例如按鈕和文字方塊\) 加入至 Web 組件，請將程式碼加入至 XML 檔案。  不過，您可以從 Visual Studio \[**工具箱**\] 拖曳或複製控制項到 Web 組件，將控制項加入至視覺 Web 組件。  設計工具接著會產生 XML 檔案所需的程式碼。  請參閱 [如何：使用設計工具建立 SharePoint Web 組件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)。  
  
## SharePoint 控制項  
 Visual Studio 會提供一些建立 SharePoint 頁面 \(例如應用程式頁面\) 的控制項。  這些控制項會在 \[**SharePoint 控制項**\] 底下的 \[**工具箱**\] 中出現。  這些控制項的功能衍生自 [Microsoft.SharePoint.WebControls](http://go.microsoft.com/fwlink/?LinkId=235315) 命名空間，此命名空間包含用於 SharePoint 網站及列出頁面的 ASP.NET 伺服器控制項。  
  
|控制項名稱|描述|  
|-----------|--------|  
|[AspMenu](http://go.microsoft.com/fwlink/?LinkId=235307)|插入 ASP 功能表。  如需詳細資訊，請參閱[功能表控制項概觀](http://go.microsoft.com/fwlink/?LinkId=235316)。|  
|[CssLink](http://go.microsoft.com/fwlink/?LinkId=235308)|將 **CssRegistration** 插入 .aspx 網頁，並套用一個或多個由 **LINK** 所定義的外部樣式表。|  
|[DateTimeControl](http://go.microsoft.com/fwlink/?LinkId=235306)|將 DateTime 控制項插入 .aspx 網頁中。|  
|[FormDigest](http://go.microsoft.com/fwlink/?LinkId=235309)|將安全性驗證插入 .aspx 網頁中。|  
|[ListProperty](http://go.microsoft.com/fwlink/?LinkId=235310)|傳回指定之清單的屬性。|  
|[ProjectProperty](http://go.microsoft.com/fwlink/?LinkId=235311)|傳回目前網站的全域屬性。|  
|[RssLink](http://go.microsoft.com/fwlink/?LinkId=235312)|將 RSS 摘要的連結插入 .aspx 網頁中。|  
|[ScriptLink](http://go.microsoft.com/fwlink/?LinkId=235313)|在頁面上提供用於註冊資源的屬性和方法 \(例如指令碼\)，以便在顯示網頁時要求這些資源。|  
|[佈景主題](http://go.microsoft.com/fwlink/?LinkId=235314)|將佈景主題套用至 .aspx 網頁。|  
  
## Web 組件偵錯  
 您可以偵錯包含 Web 組件的 SharePoint 專案，其方式和偵錯其他 Visual Studio 專案相同。  當您啟動 Visual Studio 偵錯工具時，Visual Studio 就會開啟 SharePoint 網站。  
  
 若要開始偵錯您的程式碼，請將 Web 組件加入至 SharePoint 中的 Web 組件頁面。  
  
 如需如何偵錯 SharePoint 專案的詳細資訊，請參閱[SharePoint 方案疑難排解](../sharepoint/troubleshooting-sharepoint-solutions.md)。  
  
## 視覺 Web 組件限制  
 從 Visual Studio 開始，您可以將視覺 Web 組件加入至沙箱化 SharePoint 方案與伺服器陣列方案。  不過，視覺 Web 組件有下列限制：  
  
-   視覺 Web 組件不支援可取代的參數。  如需詳細資訊，請參閱[可置換的參數](../sharepoint/replaceable-parameters.md)。  
  
-   您無法將使用者控制項或視覺 Web 組件拖放或複製到視覺 Web 組件上。  這個動作會導致建置錯誤。  
  
-   視覺 Web 組件不直接支援 SharePoint 伺服器語彙基元，例如 $SPUrl。  如需詳細資訊，請參閱主題[SharePoint 方案疑難排解](../sharepoint/troubleshooting-sharepoint-solutions.md)中的＜沙箱化視覺 Web 組件中的權杖限制＞。  
  
-   沙箱化方案中的視覺 Web 組件偶而會收到錯誤「沙箱化程式碼執行要求被拒絕，因為沙箱化程式碼主機服務太忙碌，無法處理要求」。如需此錯誤的詳細資訊，請參閱 [SharePoint 開發人員團隊部落格](http://go.microsoft.com/fwlink/?LinkId=225932)中的這篇文章。  
  
-   Visual Studio 不支援伺服器端 JavaScript 偵錯，但支援用戶端 JavaScript 偵錯。  
  
     雖然您可以將內嵌 JavaScript 加入到伺服器端標記檔案，但是偵錯不支援加入至標記的中斷點。  若要偵錯 JavaScript，請參考標記檔案中的外部 JavaScript 檔案，然後在 JavaScript 檔案中設定中斷點。  
  
-   內嵌 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 程式碼偵錯必須在產生的程式碼檔案中完成，而不是在標記檔案。  
  
-   視覺 Web 組件不支援使用 `<@ Assembly Src=` 指示詞。  
  
-   SharePoint 沙箱環境不支援 SharePoint Web 控制項和部分 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 控制項。  如果不支援的控制項用於沙箱化方案中的視覺 Web 組件，會出現錯誤：「命名空間 'Microsoft.SharePoint.WebControls' 中沒有類型或命名空間名稱 'Theme'」。  
  
 如需沙箱化方案的詳細資訊，請參閱[沙箱化方案與伺服器陣列方案之間的差異](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)。  
  
## 建立舊樣式 SharePoint 架構的 Web 組件  
 您可以使用 Visual Studio 中的範本，建立適用於 SharePoint 的自訂 [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] Web 組件。  [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] Web 組件建置在 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 組件基礎結構上，新專案建議使用這種類型。  
  
 在極少數情況下，您可能必須使用舊樣式 SharePoint 架構 Web 組件來建立 Web 組件。  您可以使用 Visual Studio 建立這些類型的 Web 組件，但 Visual Studio 並不提供任何為這個用途特別設計的範本來協助您建立這些組件。  
  
 如需建立舊樣式 SharePoint 架構之 Web 組件的時機詳細資訊，請參閱 [Windows SharePoint Services 中的 Web 組件基礎結構](http://go.microsoft.com/fwlink/?LinkId=169290) \(英文\)。  如需如何使用舊樣式 SharePoint 架構的 Web 組件來建立 Web 組件的詳細資訊，請參閱[逐步解說：建立基本的 SharePoint Web 組件](http://go.microsoft.com/fwlink/?LinkId=169288) \(英文\)。  
  
## 相關主題  
  
|標題|描述|  
|--------|--------|  
|[如何：建立 SharePoint Web 組件](../sharepoint/how-to-create-a-sharepoint-web-part.md)|示範如何建立 SharePoint 頁面的 Web 組件。|  
|[如何：使用設計工具建立 SharePoint Web 組件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|示範如何使用視覺化設計介面來建立 SharePoint 的 Web 組件。|  
|[如何：為 SharePoint 應用程式頁面或 Web 組件建立使用者控制項](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|示範如何為在 SharePoint 中執行的應用程式頁面和 Web 組件，建立可供其利用之自訂、可重複使用的控制項。|  
|[逐步解說：建立 SharePoint 的 Web 組件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|說明如何設計 SharePoint 的 Web 組件。|  
|[逐步解說：使用設計工具建立 SharePoint 的 Web 組件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|說明如何將控制項拖曳至視覺化設計介面，以設計 SharePoint 的 Web 組件。|  
|[逐步解說：建立可顯示 SharePoint 之 OData 的 Silverlight Web 組件](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|說明如何設計裝載 Silverlight 應用程式並顯示 SharePoint 清單資料的 SharePoint Web 組件。|  
|[使用 Visual Web Developer](http://msdn.microsoft.com/zh-tw/9c31f93b-c8fb-4599-9b14-6194ec8c7539)|說明如何使用開啟專案中的網頁時出現的設計工具。|  
  
  
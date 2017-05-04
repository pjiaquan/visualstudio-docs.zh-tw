---
title: "SharePoint 專案與專案項目範本 | Microsoft Docs"
ms.custom: ""
ms.date: "02/22/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.SPE.FirstWizardPage"
  - "VS.SharePointTools.SPE.ListInstance"
  - "VS.SharePointTools.SPE.ListDefinition"
  - "VS.SharePointTools.SPE.ListDefFromContentType"
  - "VS.SharePointTools.SPE.ContentType"
  - "SPE.Wizard"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 開發, 專案與專案項目範本"
  - "Visual Studio 中的 SharePoint 開發, 範本"
ms.assetid: 54a7576f-d3f9-475d-8ed7-b675ad21cb53
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# SharePoint 專案與專案項目範本
  下列各節說明可用的 SharePoint 專案和專案項目範本和它們的使用方式。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
##  <a name="project_items_templates_overview"></a> 專案和專案項目範本概觀  
 當您建立新的 SharePoint 專案在 Visual Studio 中時，SharePoint 專案會加入至方案以及所有由該專案類型所需的專案項目。  例如，如果您建立 Silverlight 網頁組件專案時，Visual Studio 會建立的方案，其中包含視覺化網頁組件的專案項目和 Silverlight 應用程式專案項目以及這些專案項目所需的所有檔案。  專案項目範本用來將專案項目加入至現有的 SharePoint 專案，例如新增事件接收器、 站台\] 欄中或清單。  
  
 SharePoint 基礎概念的相關資訊，請參閱 [SharePoint 基礎建置組塊](http://go.microsoft.com/fwlink/?LinkId=179404)。  進階的使用者可以建立自訂的專案和專案項目範本。  如需詳細資訊，請參閱 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
##  <a name="project_templates"></a> 專案範本  
 下列是 SharePoint 專案範本的清單。  若要檢視 SharePoint 專案範本，在 Visual Studio 中**新的專案** 對話方塊方塊中，展開 \[  **SharePoint** 下任一個節點**視覺化 C\#** 或 **Visual Basic**，然後選擇 \[  **2010年**。  
  
### SharePoint 2010 專案  
 內容的 *SharePoint 2010 專案*包含在每個 SharePoint 專案範本。  SharePoint 2010 專案包含：  
  
-   專案檔。  
  
-   專案屬性\] 頁面中。  
  
-   A **參考**資料夾列出所有專案中的組件參考。  
  
-   A **功能** .feature 組態檔，用來部署功能到 SharePoint 伺服器所在的資料夾。  
  
-   A **套件**包含用來將方案部署到 SharePoint 的 Package.package 檔案的資料夾。  
  
-   Key.snk \(強式名稱金鑰\) 檔案，用來簽署強式名稱組件的增強安全性。  
  
### SharePoint 2010 Silverlight 網頁組件  
 *SharePoint 2010 Silverlight 網頁組件*專案可讓您建立顯示 Silverlight 應用程式的 SharePoint 網頁組件。  當您建立這個專案時，您可以指定是否要新增新的 Silverlight 應用程式，或參考現有的平台。  如需詳細資訊，請參閱[建立 SharePoint 的 Web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)和  [逐步解說：建立可顯示 SharePoint 之 OData 的 Silverlight Web 組件](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### SharePoint 2010 Visual Web 組件  
 A  *SharePoint 2010 Visual Web 組件* 專案包含一個 Elements.xml 定義檔案中， **網頁組件** 項目，以及 **使用者控制項**項目。  您可以拖曳或從 Visual Studio 工具箱將控制項複製到使用者控制項的介面，以設計 visual web 組件的外觀。  如需詳細資訊，請參閱[如何：使用設計工具建立 SharePoint Web 組件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)和 [建置組塊： Web 組件](http://go.microsoft.com/fwlink/?LinkId=179438)。  
  
### 匯入 SharePoint 2010 方案套件  
 *匯入 SharePoint 2010 方案套件*專案可讓您匯入現有的 SharePoint 2010 網站，匯出到 SharePoint 解決方案 \(.wsp\) 檔案，為 Visual Studio 的全部或部分。  一旦匯入 Visual Studio，您可以自訂它的項目，並重新部署它們。  如需詳細資訊，請參閱 [從現有的 SharePoint 網站匯入項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
### 匯入可重複使用 SharePoint 2010 工作流程  
 *匯入可重複使用 SharePoint 2010 工作流程*專案可讓您匯入至 Visual Studio 在 SharePoint 設計工具 2010年建立可重複使用、 宣告式工作流程。  工作流程是從 SharePoint 網站匯出成.wsp 檔案。  一旦匯入 Visual Studio，您可以自訂它，加入程式碼，並再將它部署到 SharePoint 網站。  如需詳細資訊，請參閱 [逐步解說：將 SharePoint Designer 可重複使用的工作流程匯入 Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
##  <a name="project_item_templates"></a> 專案項目範本  
 下列是 SharePoint 專案項目範本的清單。  專案項目範本會將檔案加入至 SharePoint 解決方案支援 SharePoint 功能，例如網站欄、 清單和內容類型。  例如，將站台資料行加入至您的方案網站欄將專案加入包含 Elements.xml 定義檔。  加入視覺化網頁組件加入 visual web 組件專案至方案包含一個 Elements.xml 檔案、 使用者控制項項目和一個視覺化的 web 組件項目。  
  
 若要檢視 SharePoint 專案項目範本，在**方案總管\] 中**、 開啟 SharePoint 專案的快顯功能表，然後選擇 **新增**， **新的項目**。  展開 **SharePoint** 下的節點**視覺 C\#** 或 **Visual Basic**，然後選擇 \[  **2010年**。  
  
### 應用程式頁 \(伺服陣列解決方案\)  
 **應用程式只在一頁 \(伺服陣列解決方案\)** 項目可讓您設計 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]SharePoint 網站的 web 網頁。  應用程式網頁只能用於伺服陣列解決方案。  您只能伺服陣列解決方案中加入此專案項目。  如需詳細資訊，請參閱[如何：建立應用程式頁面](../sharepoint/how-to-create-an-application-page.md)和 [應用程式 \_layouts 頁面類型](http://go.microsoft.com/fwlink/?LinkId=179434)。  
  
### 商務資料連接模型 \(伺服陣列解決方案\)  
 A **商務資料連接模型 \(伺服陣列解決方案僅\)** 項目可讓您將商務資料整合到 SharePoint。  商務資料可以來自後端伺服器應用程式，例如，  [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)]，Siebel 和服務通告通訊協定 \(SAP\)。  商務資料的連線模型只能用於伺服陣列解決方案。  您只能伺服陣列解決方案中加入此專案項目。  如需詳細資訊，請參閱 [如何：建立 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)，   [如何：使用資源檔來指定當地語系化名稱、屬性和使用權限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)，和 [新： Business Connectivity Services](http://go.microsoft.com/fwlink/?LinkId=179411)。  
  
### 內容類型  
 *內容型別*項目可讓您建立自訂的內容類型，如文件、 通知或工作現有的 \(基本\) 內容類型為基礎。  自訂的內容型別提供相同的屬性和欄位做為基礎的內容類型，以及您定義任何站台欄 \(欄位\)。  例如，您可以建立自訂的連絡人內容類型為基礎的基底的連絡人內容類型隨附在 SharePoint 中。  您可以藉由變更現有的網站欄或多個網站欄新增到已經包含在基底的內容類型的自訂內容類型。  
  
> [!NOTE]  
>  因為 SharePoint 本身的限制，您無法建立沙箱化的解決方案內容型別陣列的方案內容類型。  
  
 如需詳細資訊，請參閱[逐步解說：建立 SharePoint 的網站資料行、內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)和 [建置組塊： 內容型別](http://go.microsoft.com/fwlink/?LinkId=179413)。  
  
### 空白項目  
 *空白項目*通常用來定義專案或專案項目範本，在 Visual Studio 中的缺少的 SharePoint 專案項目。  當您將空項目新增至您的專案時，節點名為 EmptyElement x\(其中 x 唯一的數字\) 建立。  EmptyElement \[x\] 包含一個名為 Elements.xml 的單一檔案。  使用[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]陳述式以定義在 Elements.xml 中所要的項目。  
  
### 事件接收器  
 *事件接收者*處理的項目在 SharePoint 網站中，例如當某個項目新增至清單、 刪除一個 web 項目時，或工作流程的啟動時的事件。  事件接收器專案項目範本可讓您處理  
  
-   清單事件  
  
-   清單項目事件  
  
-   清單的電子郵件事件  
  
-   Web 事件  
  
-   清單工作流程事件  
  
 事件接收器專案項目會建立**事件接收者** ，其中包含的所有事件的事件處理常式您指定當您建立專案中的單一類別檔案的資料夾  **SharePoint 自訂精靈**。   event receiver類別可以處理發生在 SharePoint 網站，當項目，例如檔案、 欄位、 項目、 清單、 附件、 web 組件和工作流程會加入、 更新、 刪除或移除的事件。  如需詳細資訊，請參閱[如何：建立事件接收器](../sharepoint/how-to-create-an-event-receiver.md)和 [建置組塊： 事件處理](http://go.microsoft.com/fwlink/?LinkId=179416)。  
  
### 清單  
 清單是可重複使用基底 SharePoint 清單定義的例如行事曆\] 或 \[工作清單執行個體。  將清單新增至您的方案後, 清單設計工具可讓您新增到清單的網站欄並建立自訂清單資料行。  這包括網站的內容類型的資料行。  您可以指定*檢視* ，如清單決定將會出現在清單中的資料行。  如需詳細資訊，請參閱[逐步解說：建立 SharePoint 的網站資料行、內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)和 [建置組塊： 清單和文件庫](http://go.microsoft.com/fwlink/?LinkId=179421)。  
  
### 模組  
 *模組* \(不必與搞混 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]模組\) 包含您想要部署到 SharePoint 伺服器，例如影像或備忘稿的任何檔案。  模組的專案項目包含**模組**節點。  在模組節點包含兩個專案項目範本： XML 定義檔案，做為此模組的資訊清單和 sample.txt 檔案，預留位置檔案。  如需詳細資訊，請參閱[使用模組來包含方案中的檔案](../sharepoint/using-modules-to-include-files-in-the-solution.md)和 [模組](http://go.microsoft.com/fwlink/?LinkId=179425)。  
  
### 循序工作流程 \(伺服陣列解決方案\)  
 A *的循序工作流程*是一系列的商務邏輯，執行步驟的順序，直到完成最後一個步驟。  循序工作流程用來管理牽涉到 SharePoint 的項目，例如清單和文件的處理程序。  您可以建立站台層級 \(全域\) 工作流程或清單層級 \(本機\) 的工作流程，而且您可以選擇是否要在工作流程啟動自動或手動。  此專案項目只能用於伺服陣列解決方案。  您只能伺服陣列解決方案中加入此專案項目。  如需詳細資訊，請參閱 [建立 SharePoint 工作流程方案](../sharepoint/creating-sharepoint-workflow-solutions.md)，  [工作流程在 SharePoint 伺服器 2010年](http://go.microsoft.com/fwlink/?LinkId=260555)，和 [新： 工作流程改良](http://go.microsoft.com/fwlink/?LinkId=179418)。  
  
### Silverlight 網頁組件  
 *Silverlight 網頁組件*專案項目可讓您建立顯示 Silverlight 應用程式的 SharePoint 網頁組件。  當您將此專案項目新增至您的方案時，您可以選擇是否要新增新的 Silverlight 應用程式，或於稍後參考現有的平台。  如需詳細資訊，請參閱[建立 SharePoint 的 Web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)和  [逐步解說：建立可顯示 SharePoint 之 OData 的 Silverlight Web 組件](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### 網站資料行  
 A *的網站欄*，也就是 *欄位*，是其中一個您可以新增到 SharePoint 專案最基本的項目。  網站欄代表一種資料，例如電話號碼、 文字註解或連絡人清單中連絡人的縣市名稱。  如需詳細資訊，請參閱[建立 SharePoint 的網站資料行、內容類型和清單](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)和 [資料行](http://go.microsoft.com/fwlink/?LinkId=226840)。  
  
### 網站定義 \(伺服陣列解決方案\)  
 *網站定義*專案項目包含站台定義資料夾包含下列檔案：  
  
-   預設.aspx 頁面中，為預設的 web 網頁使用站台。  
  
-   定義元件的站台的 onet.xml 檔案。  
  
-   指定出現在站台定義設定的 webtemp xml 檔**範本選擇** 一節的 **新的 SharePoint 網站**頁面。  
  
 新增網站定義之後，您可以加入程式碼，並介紹功能的檔案。  此專案項目只能用於伺服陣列解決方案。  您只能伺服陣列解決方案中加入此專案項目。  如需詳細資訊，請參閱[建立 SharePoint 的站台定義](../sharepoint/creating-site-definitions-for-sharepoint.md)和 [網站定義和組態](http://go.microsoft.com/fwlink/?LinkId=260554)。  
  
### 狀態機器工作流程 \(伺服陣列解決方案\)  
 A *狀態機器工作流程*是一組的商務邏輯狀態、 轉換和動作。  狀態機器工作流程中的步驟並不會執行的順序 ； 相反地，它們便會觸發動作的狀態。  如同循序工作流程，狀態機器工作流程是 SharePoint 清單和文件等的項目相關聯的。  同樣地，您可以建立站台層級 \(全域\) 工作流程或清單層級 \(本機\) 的工作流程。  您也可以選取是否在工作流程啟動自動或手動。  此專案項目只能用於伺服陣列解決方案。  您只能伺服陣列解決方案中加入此專案項目。  如需詳細資訊，請參閱 [建立 SharePoint 工作流程方案](../sharepoint/creating-sharepoint-workflow-solutions.md)，  [工作流程在 SharePoint 伺服器 2010年](http://go.microsoft.com/fwlink/?LinkId=260555)，和 [新： 工作流程改良](http://go.microsoft.com/fwlink/?LinkId=179418)。  
  
### 使用者控制項 \(伺服陣列解決方案\)  
 A *使用者控制項*是自訂、 可重複使用的控制項，您可以新增其他 ASP.NET 控制項和 SharePoint 控制項。  使用者控制項可以加入應用程式頁面及在 SharePoint 中執行的 web 組件。  此專案項目只能用於伺服陣列解決方案。  您只能伺服陣列解決方案中加入此專案項目。  如需詳細資訊，請參閱[建立 Web 組件或應用程式頁面的可重複使用控制項](http://go.microsoft.com/fwlink/?LinkId=226841)。  
  
### 視覺化網頁組件  
 A *視覺化網頁組件* 專案項目包含 Elements.xml 定義檔案， **網頁組件** 項目，以及 **使用者控制項**項目。  您可以拖曳或從 Visual Studio 工具箱將控制項複製到使用者控制項的介面，以設計 visual web 組件的外觀。  如需詳細資訊，請參閱[如何：使用設計工具建立 SharePoint Web 組件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)和 [建置組塊： Web 組件](http://go.microsoft.com/fwlink/?LinkId=179438)。  
  
### 網頁組件  
 A *網頁組件*是特殊類型的網頁呼叫網頁組件內所執行的伺服器端控制項。  它們是出現在 SharePoint 網站的頁面的建置組塊。  Web 組件項目提供讓您設計的 SharePoint 網站的網頁組件的檔案。  如需詳細資訊，請參閱[如何：建立 SharePoint Web 組件](../sharepoint/how-to-create-a-sharepoint-web-part.md)和 [建置組塊： Web 組件](http://go.microsoft.com/fwlink/?LinkId=179438)。  
  
## 請參閱  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [SharePoint 產品和技術](http://go.microsoft.com/fwlink/?LinkId=178818)  
  
  
---
title: "封裝和部署 SharePoint 方案 | Microsoft Docs"
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
  - "部署 [Visual Studio 中的 SharePoint 開發]"
  - "封裝 [Visual Studio 中的 SharePoint 開發]"
  - "Visual Studio 中的 SharePoint 開發, 封裝和部署"
ms.assetid: 39072fa7-9f94-49c0-9a67-cbcce0147e61
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# 封裝和部署 SharePoint 方案
  一般而言，SharePoint 方案會使用方案套件 \(.wsp\) 檔部署至 SharePoint 伺服器。  您可以使用 Visual Studio 將 SharePoint 專案項目組織成功能，以及建立套件來部署您的 SharePoint 功能。  
  
 本主題提供下列資訊：  
  
-   [建立功能和套件](#Creating)  
  
-   [功能和封裝工具支援](#Tools)  
  
-   [部署 SharePoint 方案](#Deploying)  
  
-   [部署 SharePoint 方案中的檔案](#DeployingFiles)  
  
##  <a name="Creating"></a> 建立功能和套件  
 您可以使用 Visual Studio 將相關 SharePoint 項目群組成「*功能*」\(Feature\)。  例如，連絡人清單定義的功能可能包含清單執行個體和清單定義。  您可以將這兩個項目合併成單一功能，以便進行部署。  如需功能的詳細資訊，請參閱 [建置組塊：功能](http://go.microsoft.com/fwlink/?LinkID=169183)。  
  
 您接著可以建立 SharePoint 方案套件 \(.wsp\)，將多個功能、網站定義、組件和其他檔案搭配組合成單一套件，這個套件會以 SharePoint 部署檔案至伺服器所需的格式存放檔案。  如需詳細資訊，請參閱 [建置組塊：方案](http://go.microsoft.com/fwlink/?LinkID=169186)。  
  
##  <a name="Tools"></a> 功能和封裝工具支援  
 您可以使用 Visual Studio 中的 SharePoint 開發工具，快速將 SharePoint 檔案組織成功能和方案套件，讓部署更為容易。  您可以使用下列工具來設定功能和方案套件。  
  
-   功能設計工具和封裝設計工具。  
  
-   封裝總管 \(工具視窗\)。  
  
-   方案總管。  
  
### 功能設計工具和封裝設計工具  
 您可以使用「功能設計工具」建立功能、設定範圍，以及將其他功能標示為相依性。  設計工具也會顯示可描述每個功能的最終 XML 檔。  如需詳細資訊，請參閱[建立 SharePoint 功能](../sharepoint/creating-sharepoint-features.md)。  
  
 在功能設計工具中設定功能的「*範圍*」\(Scope\)，可將功能套用到某個特定網站或一組網站。  如果針對個別網站啟動功能，該功能僅適用於該特定網站。  如果針對網站集合啟動功能，功能中的項目則適用於整個網站集合。  如需詳細資訊，請參閱 [項目範圍](http://go.microsoft.com/fwlink/?LinkID=169189)。  
  
 如果您的功能依賴其他功能，您可以設定「*功能啟動相依性*」\(Feature Activation Dependency\) 先標記相依功能，使其成為可用的功能。  功能啟動相依性會檢查相依功能是否已在該範圍內啟動。  如需詳細資訊，請參閱 [啟動相依性和範圍](http://go.microsoft.com/fwlink/?LinkID=169190)。  
  
 在封裝設計工具中，您可以將 SharePoint 項目群組成單一方案套件，並設定是否要在部署期間重設 Web 伺服器。  若要設定部署伺服器類型，請使用 \[**屬性**\] 視窗。  設計工具也會產生描述套件內容的 XML 檔。  如需詳細資訊，請參閱[建立 SharePoint 方案套件](../sharepoint/creating-sharepoint-solution-packages.md)。  
  
 在部署期間，Internet Information Services \(IIS\) 服務會停止，以便將方案檔複製到 SharePoint 伺服器。  藉由使用 Visual Studio 中的封裝設計工具，您可以選擇是否應重新啟動 Web 伺服器。  若要設定將方案部署至前端 Web 伺服器還是應用程式伺服器，請使用 \[**屬性**\] 視窗。  如需詳細資訊，請參閱 [方案項目 \(方案\)](http://go.microsoft.com/fwlink/?LinkID=169191)。  
  
### 封裝總管  
 為搭配使用功能設計工具和封裝設計工具，您可以使用「封裝總管」將 SharePoint 檔案群組成功能和套件。  此外，您還可以透過階層式檢視查看套件、功能、SharePoint 專案項目和檔案。  封裝總管是工具視窗，可用來完成下列工作：  
  
-   開啟 SharePoint 專案項目和檔案。  
  
-   將 SharePoint 專案項目從一個功能拖放至另一個功能。  
  
-   將 SharePoint 專案項目和功能從一個套件拖放至另一個套件。  
  
-   將新功能加入至套件。  
  
-   開啟功能設計工具或封裝設計工具。  
  
-   驗證功能和套件。  
  
 Visual Studio 中的 SharePoint 開發工具擁有驗證規則，可確保方案套件的格式正確無誤。  此外，規則還會驗證 .wsp 方案檔是否可在 SharePoint 伺服器上成功部署並啟動。  如需功能之 XML 結構描述的詳細資訊，請參閱 [功能結構描述](http://go.microsoft.com/fwlink/?LinkID=169192)。  
  
 您可以將自訂功能和封裝驗證規則加入至 SharePoint 專案系統。  如需詳細資訊，請參閱[How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)。  
  
 如需封裝總管的詳細資訊，請參閱 [如何：使用封裝總管在套件中新增與移除功能和項目](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)。  
  
### 方案總管  
 您可以使用「方案總管」來巡覽和開啟 SharePoint 專案的檔案。  使用方案總管中的內容功能表可加入功能、功能事件接收器和功能資源。  此外，您還可以開啟功能設計工具和封裝設計工具，以設定功能和套件進行部署。  
  
##  <a name="Deploying"></a> 部署 SharePoint 方案  
 在 Visual Studio 中自訂功能和套件之後，您可以建立 .wsp 檔案以部署至 SharePoint 伺服器。  您只能在開發電腦上的 SharePoint 伺服器使用 Visual Studio 偵錯和測試 .wsp。  如需如何將 SharePoint 方案部署至遠端 SharePoint 伺服器的詳細資訊，請參閱 [部署方案](http://go.microsoft.com/fwlink/?LinkID=169194)。  
  
 您也可以自訂開發電腦上的部署步驟。  如需詳細資訊，請參閱[部署、發行和升級 SharePoint 方案套件](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)。  
  
##  <a name="DeployingFiles"></a> 部署 SharePoint 方案中的檔案  
 一般來說，當您將 SharePoint 專案項目加入至 SharePoint 方案時，所有必要的檔案都會包含在其中。  可以編譯的檔案 \(程式碼檔\) 會建置在方案的輸出組件中。  但是，您可能也必須將不相容的檔案 \(例如 .xml、.txt 或資源檔\) 加入至 SharePoint 專案。  這些檔案不會自動封裝在方案中。  為了確保這些檔案會封裝，請將檔案加入至對應資料夾或 SharePoint 專案項目。  
  
 當部署方案時，加入至對應資料夾的檔案會自動複製到 SharePoint 登錄區。  加入至 SharePoint 專案項目的檔案會部署到 \[**部署位置**\] 屬性中針對每一個檔案所指定的位置，這個位置的一部分是根據 \[**部署類型**\] 屬性來設定。  根據預設，\[**部署類型**\] 屬性值為 \[**NoDeployment**\]，這表示此檔案並未與方案一起部署。  您必須為此屬性設定另一個值，以便將檔案包含在封裝內。  
  
 例如，若要將 .xml 檔案加入至 SharePoint 專案，請執行下列其中一個動作：  
  
-   將 SharePoint "Layouts" 對應資料夾加入至您的專案。  這樣會在 \[**方案總管**\] 中建立名為 \[**Layouts**\] 的資料夾，該資料夾擁有專案的子資料夾。  將 .xml 檔案加入至新的子資料夾。  根據預設，此檔案會部署到在 ..\\TEMPLATE\\LAYOUTS\\*Folder Name*\\ 之下的 SharePoint 檔案系統。  如需如何加入對應資料夾的詳細資訊，請參閱 [如何：新增與移除對應的資料夾](../sharepoint/how-to-add-and-remove-mapped-folders.md)。  
  
-   將 .xml 檔案加入至 SharePoint 專案項目的資料夾，然後將 .xml 檔案的 \[**部署類型**\] 屬性從 \[**NoDeployment**\] 變更為另一項設定 \(例如 \[**RootFile**\] 或 \[**ElementFile**\]\)。  適當的 \[**部署類型**\] 設定取決於檔案和專案。  如需 \[**部署類型**\] 屬性設定的詳細資訊，請參閱[Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)。  
  
 如果加入的檔案不適用於方案中的任何特定專案，您可以將空的 SharePoint 專案加入至方案，然後在其中加入其他檔案。  將檔案部署到 SharePoint 有另一個替代方法 \(特別是針對內容資料庫\)，也就是將模組加入至專案，然後將檔案加入至模組。  如需詳細資訊，請參閱[使用模組來包含方案中的檔案](../sharepoint/using-modules-to-include-files-in-the-solution.md)。  
  
## 請參閱  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [建置和偵錯 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  
---
title: "逐步解說：從現有的 SharePoint 網站匯入項目"
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
  - "匯入項目 [Visual Studio 中的 SharePoint 開發]"
  - "Visual Studio 中的 SharePoint 開發, 匯入項目"
ms.assetid: faac3309-88d7-4fb2-8392-feda07fc00e5
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# 逐步解說：從現有的 SharePoint 網站匯入項目
  本逐步解說示範如何從現有的 SharePoint 網站匯入項目至 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 專案中。  
  
 本逐步解說將示範下列工作：  
  
-   加入自訂網站欄 \(也稱為「*欄位*」\(Field\)\) 來自訂 SharePoint 網站。  
  
-   將 SharePoint 網站匯出至 .wsp 檔案。  
  
-   使用 .wsp 匯入專案將 .wsp 檔案匯入 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] 和 SharePoint 版本。  如需詳細資訊，請參閱[開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
## 自訂 SharePoint 網站  
 在此範例中，您將建立和自訂 SharePoint 子網站，方式是在其中加入新網站欄並建立另一個子網站供稍後使用。  之後，您將匯出第一個子網站至 .wsp 檔案，然後使用 .wsp 匯入專案將自訂網站欄匯入第二個子網站。  
  
#### 若要建立和自訂 SharePoint 網站  
  
1.  使用 Web 瀏覽器開啟 SharePoint 網站，例如 http:\/\/*system name*\/SitePages\/Home.aspx。  
  
2.  開啟 \[**網站動作**\] 功能表，然後選擇 \[**新增網站**\]，在主要 SharePoint 網站以外建立子網站。  
  
3.  在網站的 \[**建立**\] 對話方塊中，選取 \[**空白的網站**\] 類型。  
  
4.  在 \[**標題**\] 方塊中輸入「Site Column Test 1」，在 \[**URL 名稱**\] 方塊中輸入 columntest1，保留其他設定的預設值，然後按一下 \[**建立**\] 按鈕。  
  
5.  建立網站之後，在瀏覽器中巡覽回主網站 http:\/\/*system name*\/SitePages\/Home.aspx。  
  
6.  再次開啟 \[**網站動作**\] 功能表，然後選取 \[**新增網站**\]，在主要 SharePoint 網站以外建立空白子網站，然後選取 \[**空白網站**\] 類型。  
  
7.  在 \[**標題**\] 方塊中輸入「Site Column Test 2」，在 \[**URL 名稱**\] 方塊中輸入 columntest2，保留其他設定的預設值，然後按一下 \[**建立**\] 按鈕。  
  
8.  巡覽回到第一個子網站， http:\/\/*SystemName*\/columntest1\/default.aspx。  
  
9. 在 \[**網站動作**\] 功能表上，選擇 \[**網站設定**\]，顯示 \[網站設定\] 頁面。  
  
10. 在 \[**組件庫**\] 區段中，選擇 \[**網站欄**\] 連結。  
  
11. 在 \[**網站欄組件庫**\] 頁面頂端，選擇 \[**建立**\] 按鈕。  
  
12. 在 \[**資料行名稱。**\] 方塊中，輸入 Test Column，保留其他預設值，然後選擇 \[**確定**\] 按鈕。  
  
13. \[**Test Column**\] 一欄會出現在 \[網站欄組件庫\] 中的 \[自訂欄\] 標題底下。  
  
## 匯出 SharePoint 網站  
 接下來，取得 SharePoint 安裝 \(.wsp\) 檔，其中包含您要匯入至 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 專案的 SharePoint 項目 \(Item\) 和項目 \(Element\)。  如果您還沒有 .wsp 檔案，則必須從現有的 SharePoint 網站建立檔案。  在此範例中，您會將預設 SharePoint 網站匯出至 .wsp 檔案。  
  
> [!IMPORTANT]  
>  如果您在執行下列程序時收到執行階段錯誤，表示必須在可存取 SharePoint 網站的系統上執行程序。  
  
#### 若要匯出現有的 SharePoint 網站  
  
1.  在 SharePoint 網站中，按一下 \[**網站動作**\] 索引標籤上的 \[**網站設定**\]，顯示 \[網站設定\] 頁面。  
  
2.  在 \[網站設定\] 頁面的 \[**網站動作**\] 區段中，按一下 \[**將網站儲存為範本**\] 連結。  
  
3.  在 \[**檔案名稱**\] 方塊中輸入 ExampleSite，然後在 \[**範本名稱**\] 方塊中輸入「範例網站」。  
  
4.  在此範例中，將 \[**包括內容**\] 核取方塊保留在清除的狀態。  
  
     如果您選取此方塊，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將所有清單和文件庫以及其內容儲存至 .wsp 檔案。  雖然這在某些情況下很有用，但此範例並不需要這樣做。  
  
5.  作業順利完成時，按下 \[**使用者方案庫**\] 連結來檢視 .wsp 檔案。  
  
     若要稍後檢視方案庫頁面，請開啟 \[**網站動作**\] 功能表，選擇 \[**網站設定**\]、\[**網站集合管理**\] 區段中的 \[**移至最上層網站設定**\]，然後再按一下 \[**組件庫**\] 區段中的 \[**方案**\] 連結。  
  
6.  在方案庫中，選擇 \[**ExampleSite**\] 連結。  
  
7.  在 \[**檔案下載**\] 對話方塊中，選取 \[**儲存**\] 按鈕將檔案儲存在您的本機系統，根據預設，在您的下載資料夾。  
  
## 匯入 .wsp 檔案  
 現在您已具有包含想要重複使用之項目 \(自訂網站資料行 \[測試資料行\]\) 的 .wsp 檔案，請匯入 .wsp 檔案來存取它。  
  
#### 若要匯入 .wsp 檔案  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的功能表列上，選擇 \[**檔案**\]、\[**新增**\]、\[**專案**\]，顯示 \[**新增專案**\] 對話方塊。  如果您的 IDE 設定為使用 Visual Basic 開發設定，請在功能表上選擇 \[**檔案**\]、\[**新增專案**\]。  
  
2.  展開 \[**Visual C\#**\] 或 \[**Visual Basic**\] 底下的 \[**SharePoint**\] 節點，然後選擇 \[**2010**\] 節點。  
  
3.  選擇 \[**範本**\] 窗格中的 \[**匯入 SharePoint 2010 方案套件**\]，將專案名稱保留為 WspImportProject1，然後按一下 \[**確定**\] 按鈕。  
  
     \[**SharePoint 自訂精靈**\] 隨即出現。  
  
4.  在 \[**指定網站和安全性層級進行偵錯**\] 頁面上，為您先前建立之第二個 SharePoint 子網站輸入 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]。  您會將新的自訂欄位項目 \(http:\/\/*system name*\/columntest2\) 加入至該子網站。  
  
5.  在 \[**此 SharePoint 方案的信任層級為何?**\] 區段中，保留 \[**部署為沙箱化方案**\] 的選擇。  
  
6.  在 \[**指定新專案來源**\] 頁面中，瀏覽至您先前在系統上儲存 .wsp 檔案的位置，然後選擇 \[**下一步**\] 按鈕。  
  
    > [!NOTE]  
    >  如果您選取此頁面上的 \[**結束**\] 按鈕，將會匯入 .wsp 檔案中的所有可用項目。  
  
7.  在 \[**選取要匯入的項目**\] 方塊中，清除清單中 \[**測試資料行**\] 以外的所有項目，然後按一下 \[**完成**\] 按鈕。  
  
     由於清單包含許多項目，您可以按 Ctrl \+ A 鍵選取清單中的所有項目，選取空格鍵清除所有核取方塊，然後指選取 \[**測試資料行**\] 項目旁邊的核取方塊。  
  
     完成匯入作業後，系統會建立名為 \[**WspImportProject1**\] 的新專案，其中包含名為 \[**Fields**\] 的資料夾。  此資料夾包含自訂網站欄 \[**測試資料行**\] 及其定義檔 Elements.xml。  
  
## 部署專案  
 最後，將 \[**WspImportProject1**\] 部署至您先前建立的第二個 SharePoint 子網站，以檢視自訂網站欄。  
  
#### 若要部署專案  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中，按 F5 鍵部署和執行 .wsp 匯入專案。  
  
2.  在 SharePoint 網站，開啟 \[**網站動作**\] 功能表，然後選擇 \[**站台設定**\] 以顯示網站設定頁面。  
  
3.  在 \[**組件庫**\] 區段中，選擇 \[**網站欄**\] 連結。  
  
4.  向下捲動至 \[**自訂欄**\] 區段。  
  
     請注意，您從第一個 SharePoint 網站匯入的自訂網站欄會出現在清單中。  
  
## 請參閱  
 [從現有的 SharePoint 網站匯入項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [為 Web 組件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  
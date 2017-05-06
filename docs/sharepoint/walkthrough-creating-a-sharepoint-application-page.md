---
title: "逐步解說：建立 SharePoint 應用程式頁面"
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
  - "應用程式頁面 [Visual Studio 中的 SharePoint 程式開發]，開發"
  - "應用程式頁面 [Visual Studio 中的 SharePoint 程式開發]，建立"
ms.assetid: 5b6dd941-5c59-4a89-89d0-8e973a00ae9e
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# 逐步解說：建立 SharePoint 應用程式頁面
  「應用程式頁面」\(Application Page\) 是 ASP.NET 網頁的一種特殊形式，  應用程式頁面包含與 SharePoint 主版頁面合併的內容。  如需詳細資訊，請參閱[建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)。  
  
 本逐步解說將示範如何建立應用程式頁面，然後使用本機 SharePoint 網站來偵錯該頁面。  這個頁面會顯示每個使用者已在伺服器陣列所有網站中建立或修改的所有項目。  
  
 這個逐步解說將說明下列工作：  
  
-   建立 SharePoint 專案。  
  
-   將應用程式頁面加入至 SharePoint 專案。  
  
-   將 ASP.NET 控制項加入至應用程式頁面。  
  
-   加入 ASP.NET 控制項的程式碼。  
  
-   測試應用程式頁面。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置：  您所擁有的 Visual Studio 版本和使用的設定決定了這些項目。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的 Windows 和 SharePoint 版本。  如需詳細資訊，請參閱[開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]，或者 Visual Studio Ultimate 或 Visual Studio Premium 的版本。  
  
## 建立 SharePoint 專案  
 首先，請建立 \[**空的 SharePoint 專案**\]。  稍後，您會將 \[**應用程式頁面**\] 項目加入至這個專案。  
  
#### 若要建立 SharePoint 專案  
  
1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  開啟 \[**新增專案**\] 對話方塊、在您要使用之語言下展開 \[**Office\/SharePoint**\] 節點，然後選擇 \[**SharePoint 方案**\] 節點。  
  
3.  在 \[**Visual Studio 安裝的範本**\] 窗格中，選擇 \[**SharePoint 2010 – 空專案**\]。  將專案命名為 MySharePointProject，然後選擇 \[**確定**\] 按鈕。  
  
     \[**SharePoint 自訂精靈**\] 隨即出現。  這個精靈可讓您選取用來偵錯專案的網站以及方案的信任層級。  
  
4.  選擇 \[**部署為陣列方案**\] 選項按鈕，然後選擇 \[**完成**\] 按鈕以接受預設的本機 SharePoint 網站。  
  
## 建立應用程式頁面  
 若要建立應用程式頁面，請將 \[**應用程式頁面**\] 項目加入至專案。  
  
#### 若要建立應用程式頁面  
  
1.  在 \[**方案總管**\] 中，選擇 \[**MySharePointProject**\] 專案。  
  
2.  在功能表列中，選擇 \[**專案**\]、\[**加入新項目**\]。  
  
3.  在 \[**加入新項目**\] 對話方塊中，選擇 \[**應用程式頁面 \(僅限陣列方案\)**\] 範本。  
  
4.  將頁面命名為 SearchItems，然後選擇 \[**加入**\] 按鈕。  
  
     Visual Web Developer 設計工具會在 \[**來源**\] 檢視內顯示應用程式頁面，您可以在該檢視中查看頁面的 HTML 項目。  設計工具會顯示多個 <xref:System.Web.UI.WebControls.Content> 控制項的標記。  每一個控制項都會對應至預設應用程式主版頁面中定義的 <xref:System.Web.UI.WebControls.ContentPlaceHolder> 控制項。  
  
## 設計應用程式頁面的配置  
 \[應用程式頁面\] 項目可讓您使用設計工具，將 ASP.NET 控制項加入至應用程式頁面。  此設計工具與您在 Visual Web Developer 中使用的設計工具相同。  請將標籤、選項按鈕清單和資料表加入至設計工具的 \[**原始碼**\] 檢視，然後設定屬性，其步驟和您設計任何標準 ASP.NET 網頁的方式相同。  
  
 如需如何在 Visual Web Developer 中使用設計工具的詳細資訊，請參閱[Visual Studio Web Development Content Map](http://msdn.microsoft.com/zh-tw/9c31f93b-c8fb-4599-9b14-6194ec8c7539)。  
  
#### 若要設計應用程式頁面的配置  
  
1.  在功能表列上選擇 \[**檢視**\]、\[**工具箱**\]。  
  
2.  在 \[**工具箱**\] 的 \[標準\] 節點中，執行下列其中一個步驟：  
  
    -   開啟 \[**標籤**\] 項目的捷徑功能表，選擇 \[**複製**\]，開啟設計工具中 \[**PlaceHolderMain**\] 內容控制項底下那一行的捷徑功能表，然後選擇 \[**貼上**\]。  
  
    -   從 \[**工具箱**\] 將 **Label** 項目拖曳至 **PlaceHolderMain** 內容控制項的主體上。  
  
3.  重複以上步驟，將 \[**DropDownList**\] 項目和 \[**Table**\] 項目加入至 \[**PlaceHolderMain**\] 內容控制項。  
  
4.  在設計工具上，將 \[Label\] 控制項的 `Text` 屬性值變更為 \[顯示所有項目\]。  
  
5.  在設計工具上，以下列 XML 取代 `<asp:DropDownList>` 項目。  
  
    ```  
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"  
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">  
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>  
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>  
    </asp:DropDownList>  
    ```  
  
## 處理頁面上的控制項事件  
 處理應用程式頁面中控制項的方式，就像處理任何 ASP.NET 頁面的控制項一樣。  在本程序中，您將處理下拉式清單的 `SelectedIndexChanged` 事件。  
  
#### 若要處理頁面上的控制項事件  
  
1.  在 \[**檢視**\] 功能表上選擇 \[**程式碼**\]。  
  
     應用程式頁面程式碼檔案隨即在 \[程式碼編輯器\] 中開啟。  
  
2.  將下列方法加入至 `SearchItems` 類別。  這個程式碼會呼叫您稍後將在本逐步解說中建立的方法，以處理 <xref:System.Web.UI.WebControls.DropDownList> 的 <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> 事件。  
  
     [!code-csharp[SP_ApplicationPage#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]
     [!code-vb[SP_ApplicationPage#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]  
  
3.  在應用程式頁面程式碼檔案上方加入下列陳述式。  
  
     [!code-csharp[SP_ApplicationPage#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]
     [!code-vb[SP_ApplicationPage#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]  
  
4.  將下列方法加入至 `SearchItems` 類別。  這個方法會逐一查看伺服器陣列上的所有網站，並搜尋目前使用者所建立或修改的項目。  
  
     [!code-csharp[SP_ApplicationPage#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]
     [!code-vb[SP_ApplicationPage#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]  
  
5.  將下列方法加入至 `SearchItems` 類別。  這個方法會在資料表中顯示目前使用者所建立或修改的項目。  
  
     [!code-csharp[SP_ApplicationPage#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]
     [!code-vb[SP_ApplicationPage#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]  
  
## 測試應用程式頁面  
 執行專案時，SharePoint 網站會開啟，然後顯示應用程式頁面。  
  
#### 若要測試應用程式頁面  
  
1.  在 \[**方案總管**\] 中，開啟應用程式頁面的捷徑功能表，然後選擇 \[**設定為啟動項目**\]。  
  
2.  選擇 F5 鍵。  
  
     SharePoint 網站隨即開啟。  
  
3.  在應用程式頁面上，選擇 \[**我修改的**\] 選項。  
  
     應用程式頁面隨即重新整理，並顯示您在伺服器陣列上全部的網站中修改過的所有項目。  
  
4.  在應用程式頁面上，選擇清單中的 \[**我建立的**\]。  
  
     應用程式頁面隨即重新整理，並顯示您在伺服器陣列上全部的網站中建立的所有項目。  
  
## 後續步驟  
 如需 SharePoint 應用程式頁面的詳細資訊，請參閱[建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)。  
  
 您可以透過下列主題，進一步了解如何使用 Visual Web 設計工具來設計 SharePoint 頁面內容：  
  
-   [建立 SharePoint 的 Web 組件](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
-   [為 Web 組件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
## 請參閱  
 [如何：建立應用程式頁面](../sharepoint/how-to-create-an-application-page.md)   
 [應用程式 \_layouts 頁面類型](http://go.microsoft.com/fwlink/?LinkID=169274)  
  
  
---
title: "逐步解說：建立基本網站定義專案"
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
ms.assetid: b0df5b0e-5fa0-43d8-a339-6d92f1276764
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# 逐步解說：建立基本網站定義專案
  本逐步解說示範如何建立基本網站定義，其中包含上面有一些控制項的視覺 Web 組件。  為能清楚說明，您所建立的視覺 Web 組件只有幾個控制項。  不過，您可以建立包含更多功能、更複雜的 SharePoint 網站定義。  
  
 本逐步解說將示範下列工作：  
  
-   使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 專案範本建立網站定義。  
  
-   使用 SharePoint 中的網站定義建立 SharePoint 網站。  
  
-   將視覺 Web 組件加入至方案。  
  
-   將新的視覺 Web 組件加入網站的 default.aspx 頁面來自訂它。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的 Microsoft Windows 和 SharePoint 版本。  如需詳細資訊，請參閱＜開發 SharePoint 方案的要求＞。  
  
-   Visual Studio。  
  
## 建立網站定義方案  
 首先，在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中建立網站定義專案。  
  
#### 若要建立網站定義專案  
  
1.  在功能表列上，選擇 \[**檔案**\]、\[**新增**\]、\[**專案**\]。  如果您的 IDE 設定為使用 Visual Basic 開發設定，請在功能表上選擇 \[**檔案**\]、\[**新增專案**\]。  
  
     \[**新增專案**\] 對話方塊隨即出現。  
  
2.  展開 \[**Visual C\#**\] 節點或 \[**Visual Basic**\] 節點，展開 \[**SharePoint**\] 節點，然後選取 \[**2010**\] 節點。  
  
3.  在 \[**範本**\] 清單中，選取 \[**SharePoint 2010 專案**\] 範本。  
  
4.  在 \[**名稱**\] 方塊中，輸入 TestSiteDef，然後選擇 \[**確定**\] 按鈕。  
  
     \[**SharePoint 自訂精靈**\] 隨即出現。  
  
5.  在 \[**指定網站和安全性層級進行偵錯**\] 頁面上，輸入您想要偵錯網站定義之 SharePoint 伺服器網站的 URL，或使用預設位置 \(http:\/\/*System Name*\/\)。  
  
6.  在 \[**此 SharePoint 方案的信任層級為何?**\] 區段中，選擇 \[**部署為陣列方案**\] 選項按鈕。  
  
     所有網站定義專案都必須部署為陣列方案。  如需沙箱化方案與陣列方案的比較的詳細資訊，請參閱[沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)。  
  
7.  選擇 \[**完成**\] 按鈕。  
  
     專案隨即出現在 \[**方案總管**\] 中。  
  
8.  在 \[**方案總管**\] 中，選擇專案節點，然後在功能表列上選擇 \[**專案**\]、\[**加入新項目**\]。  
  
9. 在 \[**Visual C\#**\] 或 \[**Visual Basic**\] 底下，展開 \[**SharePoint**\] 節點，然後選擇 \[**2010**\] 節點。  
  
10. 在 \[**範本**\] 窗格中，選取 \[**網站定義**\] 範本，將 \[**名稱**\] 保留為 \[**SiteDefinition1**\]，然後選擇 \[**加入**\] 按鈕。  
  
## 建立視覺 Web 組件  
 接下來，建立視覺 Web 組件，以顯示在網站定義主頁面。  
  
#### 若要建立視覺 Web 組件  
  
1.  在 \[**方案總管**\] 中按一下 \[**顯示所有檔案**\] 按鈕。  
  
2.  選取 \[**SiteDefinition1**\] 專案節點，然後在功能表列上，選擇 \[**專案**\]、\[**加入新項目**\]。  
  
     \[**加入新項目**\] 對話方塊隨即出現。  
  
3.  展開 \[**Visual C\#**\] 節點或 \[**Visual Basic**\] 節點，展開 \[**SharePoint**\] 節點，然後選取 \[**2010**\] 節點。  
  
4.  在範本清單中，選取 \[**視覺 Web 組件**\] 範本，並保留預設名稱 VisualWebPart1，然後選擇 \[**加入**\] 按鈕。  
  
     VisualWebPart1.ascx 檔案隨即開啟。  
  
5.  在 VisualWebPart1.ascx 最下方，加入下列標記，將三個控制項加入至表單：文字方塊、按鈕和標籤：  
  
    ```  
    <table>  
      <tr>  
        <td>  
          <asp:TextBox runat="server" ID="tbName"></asp:TextBox>  
        </td>  
        <td>  
          <asp:Button runat="server" ID="btnSubmit" Text = "Change Label Text" OnClick="btnSubmit_Click"></asp:Button>  
        </td>  
        <td>  
          <asp:Label runat="server" ID="lblName"></asp:Label>  
        </td>  
      </tr>  
    </table>  
    ```  
  
6.  開啟位於 VisualWebPart1.ascx 底下的 VisualWebPart1.ascx.cs \(適用於 [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]\) 或 VisualWebPart1.ascx.vb \(適用於 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\) 檔案，然後加入下列程式碼：  
  
     [!code-csharp[SP_SimpleSiteDef#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_simplesitedef/cs/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]
     [!code-vb[SP_SimpleSiteDef#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_simplesitedef/vb/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]  
  
     這段程式碼會加入 Web 組件的按一下按鈕動作的功能。  
  
## 將視覺 Web 組件加入至預設 ASPX 網頁  
 接下來，將視覺 Web 組件加入至網站定義的預設 ASPX 網頁。  
  
#### 若要將視覺 Web 組件加入至預設 ASPX 網頁  
  
1.  開啟 default.aspx 頁面，然後在 `WebPartPages` 標籤底下加入下列程式碼：  
  
    ```  
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>  
    ```  
  
     這一行會將名稱 MyWebPartControls 與 Web 組件及其程式碼相關聯。  *Namespace* 參數符合 VisualWebPart1.ascx 程式碼檔案中的命名空間。  
  
2.  在 `</asp:Content>` 項目之後，使用下列程式碼取代整個 `ContentPlaceHolderId="PlaceHolderMain"` 區段及其內容：  
  
    ```  
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">  
        <MyWebPartControls:VisualWebPart1 runat="server" />      
    </asp:Content>  
    ```  
  
     這段程式碼會建立您先前所建立之視覺 Web 組件的參考。  
  
3.  在 \[**方案總管**\] 中，開啟 \[**SiteDefinition1**\] 節點的捷徑功能表，然後選擇 \[**設為啟動項目**\]。  
  
## 部署和執行網站定義方案  
 接下來，將專案部署至 SharePoint，然後執行專案。  
  
#### 若要部署和執行網站定義  
  
-   在功能表列上，選擇 \[**建置**\]、\[**部署測試網站定義**\]。  
  
-   選擇 F5 鍵。  
  
     Visual Studio 會編譯程式碼、加入其功能、將所有檔案封裝至 SharePoint solution \(WSP\) 檔案，然後將 WSP 檔案部署至 SharePoint 伺服器。  SharePoint 接著會安裝檔案並啟動功能。  
  
## 根據網站定義建立網站  
 接下來，使用新網站定義建立網站。  
  
#### 若要使用網站定義建立網站  
  
1.  SharePoint 網站上隨即出現 \[新增 SharePoint 網站\] 頁面。  
  
2.  在 \[**標題和說明**\] 區段中，輸入「我的新網站」做為標題，並輸入網站的描述。  
  
3.  在 \[**網站位址**\] 區段的 \[**URL 名稱**\] 方塊中，輸入 mynewsite。  
  
4.  在 \[**範本**\] 區段中，選取 \[**SharePoint 自訂**\] 索引標籤。  
  
5.  在 \[**選取範本**\] 清單中，選取 \[**SiteDefinition1**\]。  
  
6.  保留其他設定的預設值，然後按一下 \[**建立**\] 按鈕。  
  
     新網站隨即出現。  
  
## 測試新網站  
 接下來，測試新網站是否正常運作。  
  
#### 若要測試新網站  
  
-   在預設 ASPX 網頁的文字方塊中輸入一些文字，然後按一下文字方塊旁的 \[**改變標籤文字**\]。  
  
     文字會出現在按鈕右邊的標籤中。  
  
## 請參閱  
 [如何：建立事件接收器](../sharepoint/how-to-create-an-event-receiver.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  
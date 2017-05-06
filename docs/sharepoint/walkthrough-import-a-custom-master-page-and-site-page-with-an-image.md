---
title: "逐步解說：匯入自訂主版頁面及包含影像的網站頁面"
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
helpviewer_keywords: 
  - "匯入項目 [Visual Studio 中的 SharePoint 開發]"
  - "Visual Studio 中的 SharePoint 開發, 匯入項目"
ms.assetid: d1703957-81e2-47e1-b4ca-6a8d550d8da2
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# 逐步解說：匯入自訂主版頁面及包含影像的網站頁面
  本逐步解說示範如何將 SharePoint 自訂主版頁面及擁有影像的網站頁面匯入 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 專案中。  
  
 此逐步解說示範如何完成下列工作：  
  
-   在 SharePoint Designer 中使用影像來建立自訂主版頁面和網站頁面。  
  
-   將自訂主版頁面、影像和網站頁面匯入 SharePoint 方案 \(.wsp\) 檔。  
  
-   使用 \[匯入 SharePoint 方案套件\] 專案，將 .wsp 檔匯入及部署到 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 專案。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 若要完成這個逐步解說，您必須擁有以下元件：  
  
-   支援的 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] 和 SharePoint 版本。  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio。  
  
-   SharePoint Designer 2010。  
  
## 在 SharePoint Designer 中建立項目  
 此範例示範如何在 SharePoint Designer 中建立三個匯出的項目：自訂主版頁面、參考自訂主版頁面的網站頁面，以及出現在網站頁面上的影像檔。  此影像會加入至 SharePoint 中的 \/images\/ 資料夾。  
  
#### 若要在 SharePoint Designer 中建立自訂主版頁面  
  
1.  在 SharePoint Designer 的巡覽窗格中，選擇 \[**主版頁面**\] 網站物件。  
  
2.  在 \[**主版頁面**\] 功能區，請選取 \[**空白主版頁面**\]。  
  
3.  選取新的主版頁面，然後在 \[**主版頁面**\] 功能區，請選取 \[**編輯檔案**\]。  
  
4.  在 SharePoint Designer 的底部，選擇 \[**程式碼**\] 索引標籤。  
  
5.  以下列標記取代現有的標記。  
  
    ```  
    <%@ Master Language="C#" %>  
    <%@ Register tagprefix="SharePoint" namespace="Microsoft.SharePoint.WebControls" assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <html dir="ltr">  
    <head runat="server">  
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">  
    <SharePoint:RobotsMetaTag runat="server" __designer:Preview="" __designer:Values="<P N='InDesign' T='False' /><P N='ID' T='ctl00' /><P N='Page' ID='1' /><P N='TemplateControl' ID='2' /><P N='AppRelativeTemplateSourceDirectory' R='-1' />"></SharePoint:RobotsMetaTag>  
    <title>Web Page</title>  
    </head>  
    <body>  
    <form id="form1" runat="server">  
    <asp:ContentPlaceHolder id="ContentPlaceHolderMain"   
            runat="server">  
          </asp:ContentPlaceHolder>  
    </form>  
    </body>  
    </html>  
    ```  
  
6.  儲存頁面上，選取 \[**主版頁面**\] 索引標籤，並將主版頁面命名為 **mybasic1.master**。  
  
## 在 SharePoint Designer 中將影像加入至內容資料庫  
 現在您可以加入影像，使其顯示在網站頁面上。  此影像會部署到 SharePoint 內容資料庫。  
  
#### 若要在 SharePoint Designer 中將影像加入至內容資料庫  
  
1.  在巡覽窗格中，選取 \[**所有檔案**\] 網站物件，然後在樹狀檢視中選取 \[**影像**\] 資料夾。  
  
2.  在 \[**所有檔案**\] 功能區，請選取 \[**匯入檔案**\]，選取檔案，然後選擇 \[**確定**\] 按鈕。  在此範例中，檔案名為 **myimg1.png**。  
  
     您也可以選擇建立子資料夾來組織影像。  
  
3.  關閉 \[**匯入**\] 對話方塊。  
  
## 建立網站頁面  
 這個基本網站頁面會使用自訂主版頁面，並顯示您在上一個步驟所加入的影像。  
  
#### 若要建立網站頁面  
  
1.  在巡覽窗格中，選取 \[**網站頁面**\] 物件。  
  
2.  在 \[**頁面**\] 功能區，選擇 \[**頁面**\] 按鈕，並選取 \[**ASPX**\] 頁面類型，然後將新檔案命名為 **mycontentpage1.aspx**。  
  
     您也可以選擇建立子資料夾來組織網站頁面。  
  
3.  在網站頁面清單中，選擇 \[**MyContentPage1.aspx**\] 開啟其屬性頁，然後在頁面底部按下 \[**編輯**\] 連結。  
  
     如果出現訊息顯示這個頁面不包含任何在安全模式下可編輯的區域，並詢問您是否要在高階模式開啟這個頁面，請選擇 \[**是**\] 按鈕。  
  
4.  在頁面底部按下 \[**程式碼**\] 按鈕。  
  
5.  以下列標記取代現有的標記。  
  
    ```  
    <%@ Import Namespace="Microsoft.SharePoint.ApplicationPages" %>  
    <%@ Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Register Tagprefix="Utilities" Namespace="Microsoft.SharePoint.Utilities" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Register Tagprefix="asp" Namespace="System.Web.UI" Assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" %>  
    <%@ Import Namespace="Microsoft.SharePoint" %>  
    <%@ Assembly Name="Microsoft.Web.CommandUI, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Page Language="C#" Inherits="Microsoft.SharePoint.WebControls.LayoutsPageBase" MasterPageFile="../_catalogs/masterpage/mybasic1.master" meta:progid="SharePoint.WebPartPage.Document" %>  
  
    <asp:Content ID="Main" ContentPlaceHolderID="ContentPlaceHolderMain" runat="server">  
    <img alt="My Image" longdesc="My image from images folder" src="../images/myimg1.png" />  
    </asp:Content>  
    ```  
  
6.  儲存更新的網站頁面。  
  
## 從 SharePoint 匯出項目  
 將 SharePoint 中的項目匯出到 SharePoint 方案 \(.wsp\) 檔。  
  
#### 若要從 SharePoint Designer 匯出項目  
  
1.  在 SharePoint Designer 的巡覽窗格中，選取 \[**小組網站**\] 物件，然後，在 \[**網站**\] 功能區，請選取 \[**儲存為範本**\]。  
  
2.  在 \[**另存範本**\] 對話方塊中，輸入檔案名稱和範本名稱，再選取 \[**包括內容**\] 核取方塊，然後按下 \[**確定**\] 按鈕。  
  
     這樣會將網站的內容儲存在 .wsp 檔中。  
  
3.  在方案匯出之後，請按下 \[**方案庫**\] 連結，顯示可用方案檔的清單。  
  
4.  開啟新 .wsp 檔案的捷徑功能表，然後選擇 \[**另存目標**\] 將它加入至系統。  
  
## 將項目匯入 Visual Studio  
 匯入 .wsp 檔案至 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  在匯入內容之後，您可以自訂、加入其他項目，然後部署它。  
  
#### 若要將 .wsp 檔中的項目匯入 Visual Studio  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中，建立 \[**匯入 SharePoint 2010 方案套件**\] 專案。  
  
2.  在 \[**選取要匯入的項目**\] 頁面上、\[**類型**\] 欄中的\[**模組**\] 底下的，選取下表中要匯入的檔案的核取方塊。  
  
    |檔案名稱|說明|  
    |----------|--------|  
    |\_catalogsmasterpage\_|自訂主版頁面。|  
    |images\_|SharePoint 檔案系統中的影像檔。|  
    |SitePages\_|網站頁面。|  
  
3.  選擇 \[**結束**\] 按鈕匯入選取的項目。  
  
4.  在 \[**方案總管**\] 中按下 \_catalogsmasterpage\_ 節點，並將它的 \[**部署衝突解決**\] 屬性值設定為 \[**自動**\]。  
  
     如此可確保任何部署衝突都可自動解決。  
  
5.  如果新的主版頁面與現有的頁面同名，請確定現有的頁面並未在 SharePoint Designer 中標示為「預設主版頁面」或「自訂主版頁面」。  
  
     如果現有主版頁面標示為「預設主版頁面」或「自訂主版頁面」，您將會收到部署錯誤，表示無法刪除主版頁面。  若要避免這個問題，請執行下列作業：  
  
    -   如果現有的主版頁面設定為「預設主版頁面」，請暫時將另一個主版頁面設定為「預設主版頁面」。  在您將檔案部署到 SharePoint 之後，請將新的主版頁面設定為「預設主版頁面」。  
  
    -   如果現有的主版頁面設定為「自訂主版頁面」，請暫時將另一個主版頁面設定為「自訂主版頁面」。  在您將檔案部署到 SharePoint 之後，請將新的主版頁面設定為「自訂主版頁面」。  
  
6.  在功能表列上，選擇 \[**建置**\]、\[**部署方案**\]。  
  
7.  開啟 SharePoint 網站，檢視部署的項目。  
  
 將檔案匯入 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 並部署到 SharePoint 的替代方法就是在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中將檔案加入至模組內。  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][如何：匯入主版頁面或佈景主題](../sharepoint/how-to-import-a-master-page-or-theme.md)和[使用模組來包含方案中的檔案](../sharepoint/using-modules-to-include-files-in-the-solution.md)。  
  
## 請參閱  
 [從現有的 SharePoint 網站匯入項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [為 Web 組件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  
---
title: "逐步解說：建立 SharePoint 的 Web 組件"
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
  - "Web 組件 [Visual Studio 中的 SharePoint 開發], 建立"
  - "Web 組件 [Visual Studio 中的 SharePoint 開發], 設計"
  - "Web 組件 [Visual Studio 中的 SharePoint 開發], 開發"
ms.assetid: 51fb5bdd-b99c-4716-83bc-e66a5da15169
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# 逐步解說：建立 SharePoint 的 Web 組件
  Web 組件可讓使用者直接透過瀏覽器，修改 SharePoint 網站頁面的內容、外觀及行為。  本逐步解說將示範如何使用 Visual Studio 2010 中的 \[**網頁組件**\] 項目範本，建立網頁組件。  
  
 網頁組件會在資料格中顯示員工。  使用者可指定包含員工資料之檔案的位置，  也可以篩選資料格，讓清單只顯示經理級的員工。  
  
 這個逐步解說將說明下列工作：  
  
-   使用 Visual Studio \[**網頁組件**\] 項目範本建立網頁組件。  
  
-   建立可由網頁組件的使用者設定之屬性，  這個屬性會指定員工資料檔案的位置。  
  
-   將控制項加入至網頁組件控制項集合，以呈現網頁組件中的內容。  
  
-   建立稱為「*動詞命令*」\(Verb\) 的新功能表項目，該項目會出現在呈現之網頁組件的動詞命令功能表中。  動詞命令可讓使用者修改出現在網頁組件中的資料。  
  
-   在 SharePoint 中測試網頁組件。  
  
    > [!NOTE]  
    >  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置：  您所擁有的 Visual Studio 版本和使用的設定決定了這些項目。  如需詳細資訊，請參閱[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的 Microsoft Windows 和 SharePoint 版本。  如需詳細資訊，請參閱[開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vs_pro_current_short](../sharepoint/includes/vs-pro-current-short-md.md)] 或某個 Visual Studio Application Lifecycle Management \(ALM\) 版本。  
  
## 建立空的 SharePoint 專案  
 首先，請建立 \[空的 SharePoint 專案\]，  稍後您將使用 \[**網頁組件**\] 項目範本，將網頁組件加入至專案。  
  
#### 若要建立空的 SharePoint 專案  
  
1.  使用 \[**以系統管理員身分執行**\] 選項來啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在功能表上依序選擇**\[檔案\]**、**\[開新檔案\]**和**\[專案\]**。  
  
3.  在 \[**新增專案**\] 對話方塊中，展開您要使用之語言下的 \[**SharePoint**\] 節點，然後選取 \[**2010**\] 。  
  
4.  在 \[**範本**\] 窗格中，選擇 \[**SharePoint 2010 \- 空專案**\] 項目，然後選擇 \[**確定**\] 按鈕。  
  
     \[**SharePoint 自訂精靈**\] 隨即出現。  這個精靈可讓您選取用來偵錯專案的網站以及方案的信任層級。  
  
5.  選擇 \[**部署為陣列方案**\] 選項按鈕，然後選擇 \[**完成**\] 按鈕以接受預設的本機 SharePoint 網站。  
  
## 在專案中加入網頁組件。  
 在專案中加入 \[**網頁組件**\] 項目，  \[**網頁組件**\] 項目隨即加入網頁組件程式碼檔案。  稍後，您會在網頁組件程式碼檔案中加入程式碼，以呈現網頁組件的內容。  
  
#### 若要在專案中加入網頁組件  
  
1.  在功能表列中，選擇 \[**專案**\]、\[**加入新項目**\]。  
  
2.  在 \[**加入新項目**\] 對話方塊中，在 \[**已安裝的範本**\] 窗格中展開 \[**SharePoint**\] 節點，然後按一下 \[**2010**\]。  
  
3.  在範本清單中，選擇 \[**SharePoint 2013 \- 視覺 Web 組件**\] 範本，然後選擇 \[**確定**\] 按鈕。  
  
     \[**網頁組件**\] 項目就會出現在 \[**方案總管**\] 中。  
  
## 呈現網頁組件的內容  
 您可以指定要在網頁組件中顯示的控制項，只要將這些控制項加入至網頁組件類別的控制項集合即可。  
  
#### 若要呈現網頁組件的內容  
  
1.  在 \[**方案總管**\] 中，開啟 WebPart1.vb （使用 Visual Basic 時）或 WebPart1.cs （使用 C\# 時）。  
  
     網頁組件程式碼檔案隨即在 \[程式碼編輯器\] 中開啟。  
  
2.  在網頁組件程式碼檔案頂端加入下列陳述式。  
  
     [!code-csharp[SP_WebPart#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#1)]  
  
3.  將下列程式碼加入至 `WebPart1` 類別。  這個程式碼會宣告下列欄位：  
  
    -   用來在網頁組件中顯示員工的資料格。  
  
    -   顯示在用來篩選資料格之控制項上的文字。  
  
    -   在資料格無法顯示資料時，用來顯示錯誤訊息的標籤。  
  
    -   包含員工資料檔案之路徑的字串。  
  
     [!code-csharp[SP_WebPart#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#2)]  
  
4.  將下列程式碼加入至 `WebPart1` 類別。  這個程式碼會在網頁組件中加入名為 `DataFilePath` 的自訂屬性。  自訂屬性就是使用者可以在 SharePoint 中設定的屬性，  這個屬性會取得及設定用來填入資料格之 XML 資料檔案的位置。  
  
     [!code-csharp[SP_WebPart#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#3)]  
  
5.  以下列程式碼取代 `CreateChildControls` 方法。  這個程式碼會執行下列工作：  
  
    -   加入您在上一個步驟中宣告的資料格和標籤。  
  
    -   將資料格繫結至包含員工資料的 XML 檔案。  
  
     [!code-csharp[SP_WebPart#4](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#4)]  
  
6.  將下列方法加入至 `WebPart1` 類別。  這個程式碼會執行下列工作：  
  
    -   建立一個動詞命令，該動詞命令會出現在呈現之網頁組件的網頁組件動詞命令功能表中。  
  
    -   處理使用者選擇動詞命令功能表中的動詞命令時所引發的事件。  這個程式碼會篩選出現在資料格中的員工清單。  
  
     [!code-csharp[SP_WebPart#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#5)]  
  
## 測試網頁組件  
 執行專案時，SharePoint 網站會開啟。  網頁組件會自動新增至 SharePoint 中的 \[Web 組件庫\]。  您可以將網頁組件加入至任何網路組件頁面中。  
  
#### 若要測試網頁組件  
  
1.  將下列 XML 貼到 \[記事本\] 檔案上。  這個 XML 檔案包含會出現在網頁組件中的範例資料。  
  
    ```  
  
    <employees xmlns="http://schemas.microsoft.com/vsto/samples">  
       <employee>  
           <name>David Hamilton</name>  
           <hireDate>2001-05-11</hireDate>  
           <title>Sales Associate</title>  
       </employee>  
       <employee>  
           <name>Karina Leal</name>  
           <hireDate>1999-04-01</hireDate>  
           <title>Manager</title>  
       </employee>  
       <employee>  
           <name>Nancy Davolio</name>  
           <hireDate>1992-05-01</hireDate>  
           <title>Sales Associate</title>  
       </employee>  
       <employee>  
           <name>Steven Buchanan</name>  
           <hireDate>1955-03-04</hireDate>  
           <title>Manager</title>  
       </employee>  
       <employee>  
           <name>Suyama Michael</name>  
           <hireDate>1963-07-02</hireDate>  
           <title>Sales Associate</title>  
       </employee>  
    </employees>  
    ```  
  
2.  在記事本的功能表列上選擇 \[**檔案**\]、\[**儲存**\]。  
  
3.  在 \[**另存新檔**\] 對話方塊的 \[**存檔類型**\] 下拉式選單中，選取 \[**所有檔案**\]。  
  
4.  在 \[**檔案名稱**\] 方塊中，輸入 data.xml。  
  
5.  使用 \[**瀏覽資料夾**\] 按鈕來選取任何資料夾，然後按一下 \[**儲存**\]。  
  
6.  在 Visual Studio 中，按下**F5** 鍵。  
  
     SharePoint 網站隨即開啟。  
  
7.  在 \[**網站動作**\] 功能表上，按一下 \[**更多選項**\]。  
  
8.  在 \[**建立**\] 頁面上，選取 \[**Web 組件頁面**\] 類型，然後選擇 \[**建立**\] 按鈕。  
  
9. 在 \[**新增網頁組件頁面**\] 頁面中，將頁面命名為 **SampleWebPartPage.aspx**，然後選擇 \[**建立**\] 按鈕。  
  
     該網頁組件頁面隨即出現。  
  
10. 選取該網頁組件頁面上的任何區域。  
  
11. 在頁面頂端按一下 \[**插入**\] 索引標籤，然後按一下 \[**網頁組件**\]。  
  
12. 在 \[**分類**\] 窗格中按一下 \[**自訂**\] 資料夾，選擇 \[**WebPart1**\] 網頁組件，然後按一下 \[**加入**\]。  
  
     該網頁組件隨即出現在頁面上。  
  
## 測試自訂屬性  
 若要填入出現在網頁組件中的資料格，請指定包含每位員工相關資料之 XML 檔案的路徑。  
  
#### 若要測試自訂屬性  
  
1.  選取 Web 組件右邊的箭號，然後從展開的功能表中選擇 \[**編輯 Web 組件**\] 。  
  
     包含網頁組件之屬性的窗格隨即顯示在頁面右邊。  
  
2.  在窗格中展開 \[**其他**\] 節點，輸入先前建立之 XML 檔案的路徑，按一下 \[**套用**\]，然後選擇 \[**確定**\]。  
  
     確認員工清單出現在網頁組件中。  
  
## 測試網路組件動詞命令  
 按一下出現在網頁組件動詞命令功能表中的項目，以顯示和隱藏非經理級的員工。  
  
#### 若要測試網頁組件動詞命令  
  
1.  選取 Web 組件右邊的箭號，然後從展開的功能表中選擇 \[**編輯 Web 組件**\] 。  
  
     只有經理級的員工會出現在網頁組件中。  
  
2.  請選取箭號，然後從展開的功能表中選擇 \[**顯示所有員工**\] 。  
  
     所有的員工都會出現在網頁組件中。  
  
## 請參閱  
 [建立 SharePoint 的 Web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [如何：建立 SharePoint Web 組件](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [如何：使用設計工具建立 SharePoint Web 組件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [逐步解說：使用設計工具建立 SharePoint 的 Web 組件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  
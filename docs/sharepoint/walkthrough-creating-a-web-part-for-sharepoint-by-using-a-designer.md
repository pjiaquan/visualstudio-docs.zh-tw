---
title: "逐步解說：使用設計工具建立 SharePoint 的 Web 組件"
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
  - "Web 組件 [Visual Studio 中的 SharePoint 開發], 設計工具"
  - "Web 組件 [Visual Studio 中的 SharePoint 開發], 設計"
ms.assetid: 3dd62654-ada2-468f-b7da-eb5704a2ff7a
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# 逐步解說：使用設計工具建立 SharePoint 的 Web 組件
  如果您建立 SharePoint 網站的 Web 組件，使用者可以使用瀏覽器，直接修改該網站頁面的內容、外觀及行為。  本逐步解說將示範如何使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的 SharePoint \[**視覺 Web 組件**\] 專案範本，以視覺化方式建立網頁組件。  
  
 您將建立的網頁組件會在網站上顯示月份行事曆檢視，而且每個行事曆清單都有一個核取方塊。  使用者可以選取核取方塊，指定要納入月份行事曆檢視中的行事曆清單。  
  
 這個逐步解說將說明下列工作：  
  
-   使用 \[**視覺 Web 組件**\] 專案範本建立 Web 組件。  
  
-   使用 Visual Studio 中的 Visual Web Developer 設計工具來設計 Web 組件。  
  
-   加入程式碼來處理 Web 組件上控制項的事件。  
  
-   在 SharePoint 中測試 Web 組件。  
  
    > [!NOTE]  
    >  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。  您所擁有的 Visual Studio 版本和使用的設定決定了這些項目。  請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的 Windows 和 SharePoint 版本。  請參閱 [開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)] \(含\) 以上版本。  
  
## 建立 Web 組件專案  
 首先，使用 \[**視覺 Web 組件**\] 專案範本建立網頁組件專案。  
  
#### 若要建立視覺 Web 組件專案  
  
1.  使用 \[**以系統管理員身分執行**\] 選項來啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在功能表列上，選擇 \[**檔案**\]、\[**新增**\]、\[**專案**\]。  
  
     \[新增專案\] 對話方塊隨即出現。  
  
3.  在 \[**新增專案**\] 對話方塊中的 \[**Visual C\#**\] 或 \[**Visual Basic**\] 底下，展開 \[**Office\/SharePoint**\]，然後選擇 \[**SharePoint 方案**\] 分類。  
  
4.  在範本清單中，選擇 \[**SharePoint 2013 \- 視覺 Web 組件**\] 範本，然後選擇 \[**確定**\] 按鈕。  
  
     \[**SharePoint 自訂精靈**\] 隨即出現。  您可以這個精靈，指定用來偵錯專案的網站以及方案的信任層級。  
  
5.  在 \[**此 SharePoint 方案的信任層級為何?**\] 區段中，選擇 \[**部署為陣列方案**\] 選項按鈕。  
  
6.  選擇 \[**完成**\] 按鈕以接受預設的本機 SharePoint 網站。  
  
## 設計 Web 組件  
 您可以將控制項由 \[**工具箱**\] 加入至 Visual Web Developer 設計工具的介面，以設計 Web 組件。  
  
#### 若要設計網頁組件的配置  
  
1.  在 Visual Web Developer 設計工具上，選擇 \[**設計**\] 索引標籤，切換至 \[設計\] 檢視。  
  
2.  在功能表列上選擇 \[**檢視**\]、\[**工具箱**\]。  
  
3.  在 \[**工具箱**\] 的 \[**標準**\] 節點中，選擇 \[**CheckBoxList**\] 控制項，然後執行下列其中一個步驟：  
  
    -   開啟 \[**CheckBoxList**\] 控制項的捷徑功能表，選擇 \[**複製**\]，開啟設計工具中第一行的捷徑功能表，然後選擇 \[**貼上**\]。  
  
    -   從 \[**工具箱**\] 拖曳 **CheckBoxList** 控制項，並將控制項連接至設計工具中的第一行。  
  
4.  重複上述步驟，但是要將 Button 移至設計工具的下一行。  
  
5.  在設計工具中，選擇 \[**Button1**\] 按鈕。  
  
6.  在功能表上選擇 \[**檢視**\]、\[**屬性視窗**\]。  
  
     \[**屬性**\] 視窗隨即開啟。  
  
7.  在按鈕的 \[**文字**\] 屬性中輸入「更新」。  
  
## 處理 Web 組件上控制項的事件  
 加入可讓使用者將行事曆新增到主要行事曆檢視的程式碼。  
  
#### 若要處理網頁組件上控制項的事件  
  
1.  請執行下列其中一組步驟：  
  
    -   在設計工具中，按兩下 \[**更新**\] 按鈕。  
  
    -   在 \[**更新**\] 按鈕的 \[**屬性**\] 視窗中，選擇 \[**事件**\] 按鈕。  在 \[**按一下**\] 屬性中，輸入 **Button1\_Click**，然後選擇 Enter 鍵。  
  
     使用者控制項程式碼檔案隨即在 \[程式碼編輯器\] 中開啟，並且出現 `Button1_Click` 事件處理常式。  稍後，您會在這個事件處理常式中加入程式碼。  
  
2.  在使用者控制項程式碼檔案上方加入下列陳述式。  
  
     [!code-csharp[SP_VisualWebPart#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]
     [!code-vb[SP_VisualWebPart#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]  
  
3.  在 `VisualWebPart1` 類別中加入下列程式碼，  此程式碼會宣告月份行事曆檢視控制項。  
  
     [!code-csharp[SP_VisualWebPart#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]
     [!code-vb[SP_VisualWebPart#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]  
  
4.  以下列程式碼取代 `VisualWebPart1` 類別的 `Page_Load` 方法。  這個程式碼會執行下列工作：  
  
    -   將月份行事曆檢視加入至使用者控制項。  
  
    -   在網站上為每個行事曆清單加入核取方塊。  
  
    -   為行事曆檢視中出現的各個項目類型指定範本。  
  
     [!code-csharp[SP_VisualWebPart#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]
     [!code-vb[SP_VisualWebPart#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]  
  
5.  以下列程式碼取代 `VisualWebPart1` 類別的 `Button1_Click` 方法。  此程式碼會將各個選定行事曆的項目加入至主要行事曆檢視。  
  
     [!code-csharp[SP_VisualWebPart#4](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]
     [!code-vb[SP_VisualWebPart#4](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]  
  
## 測試 Web 組件  
 執行專案時，SharePoint 網站會開啟。  網頁組件會自動新增至 SharePoint 中的網頁組件庫。  若要測試這個專案，請執行下列工作：  
  
-   在兩個不同的行事曆清單中分別加入一項事件。  
  
-   將 Web 組件加入至網頁組件頁面。  
  
-   指定要包含在月份行事曆檢視中的清單。  
  
#### 若要將事件新增至網站上的行事曆清單  
  
1.  在 Visual Studio 中，選擇 F5 鍵。  
  
     SharePoint 網站隨即開啟，[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] \[快速啟動\] 列也會出現在頁面上。  
  
2.  在 \[快速啟動\] 列的 \[**清單**\] 下，選擇 \[**行事曆**\] 連結。  
  
     \[**行事曆**\] 頁面隨即出現。  
  
     如果沒有行事曆連結出現在快速啟動列，請選擇 \[**網站內容**\] 連結。  如果網站內容頁面未顯示 \[**行事曆**\] 項目，請建立一個。  
  
3.  在行事曆頁面上，選擇一天，然後選擇所選日期中的 \[**加入**\] 連結以加入事件。  
  
4.  在 \[**標題**\] 方塊中，輸入「預設行事曆中的事件」，然後選擇 \[**儲存**\] 按鈕。  
  
5.  選擇 \[**網站內容**\] 連結，然後選擇 \[**加入應用程式**\] 磚。  
  
6.  在 \[**建立**\] 頁面上，選擇 \[**行事曆**\] 類型，命名行事曆，然後選擇 \[**建立**\] 按鈕。  
  
7.  將事件加入至新的行事曆，在自訂行事曆中將事件命名為 Event，然後選擇 \[**儲存**\] 按鈕。  
  
#### 若要將網頁組件加入至網頁組件頁面  
  
1.  在 \[**網站內容**\] 頁面中，開啟 \[**網站頁面**\] 資料夾。  
  
2.  在功能區上，選擇 \[**檔案**\] 索引標籤，開啟 \[**新增文件**\] 功能表，然後選擇 \[**網頁組件頁面**\] 命令。  
  
3.  在 \[**新增網頁組件頁面**\] 頁面中，將頁面命名為 **SampleWebPartPage.aspx**，然後選擇 \[**建立**\] 按鈕。  
  
     該網頁組件頁面隨即出現。  
  
4.  在 Web 組件頁面的上方區域中，選擇 \[**插入**\] 索引標籤，然後選擇 \[**Web 組件**\] 按鈕。  
  
5.  選擇 \[**自訂**\] 資料夾，選擇 \[**VisualWebPart1**\] 網頁組件，然後選擇 \[**加入**\] 按鈕。  
  
     該網頁組件隨即出現在頁面上。  下列控制項會出現在網頁組件上：  
  
    -   月份行事曆檢視。  
  
    -   \[**更新**\] 按鈕。  
  
    -   \[**行事曆**\] 核取方塊。  
  
    -   \[**自訂行事曆**\] 核取方塊。  
  
#### 若要指定要包含在月份行事曆檢視中的清單  
  
1.  在 Web 組件中，指定您要納入月份行事曆檢視中的行事曆，然後選擇 \[**更新**\]。  
  
     您所指定之所有行事曆中的事件都會顯示在月份行事曆檢視中。  
  
## 請參閱  
 [建立 SharePoint 的 Web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [如何：建立 SharePoint Web 組件](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [如何：使用設計工具建立 SharePoint Web 組件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [逐步解說：建立 SharePoint 的 Web 組件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)  
  
  
---
title: "逐步解說：文件層級專案中的簡單資料繫結 | Microsoft Docs"
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
  - "資料 [Visual Studio 中的 Office 程式開發], 資料繫結"
  - "資料繫結 [Visual Studio 中的 Office 程式開發], 工作表儲存格至資料庫欄位"
  - "資料庫欄位 [Visual Studio 中的 Office 程式開發]"
  - "簡單資料繫結 [Visual Studio 中的 Office 程式開發]"
  - "工作表 [Visual Studio 中的 Office 程式開發], 將工作表儲存格繫結至資料庫欄位"
ms.assetid: 6b8fd638-af13-4ea1-b1c0-2763e2d8ae23
caps.latest.revision: 58
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 57
---
# 逐步解說：文件層級專案中的簡單資料繫結
  本逐步解說示範使用文件層級專案進行資料繫結的基本概念。  SQL Server 資料庫中的單一資料欄位會繫結至 Microsoft Office Excel 中的已命名範圍。  此逐步解說也將示範如何加入可讓您捲動資料表中所有記錄的控制項。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   建立 Excel 專案的資料來源。  
  
-   將控制項加入至工作表。  
  
-   捲動資料庫記錄。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   與具有 Northwind SQL Server 範例資料庫之伺服器的連線。  
  
-   從 SQL Server 資料庫讀取及寫入該資料庫的使用權限。  
  
## 建立新專案  
 在這個步驟中，您將會建立一個 Excel 活頁簿專案。  
  
#### 若要建立新的專案  
  
1.  使用 Visual Basic 或 C\#，建立名為 **My Simple Data Binding** 的 Excel 活頁簿專案。  請確定已選取 \[**建立新文件**\]。  如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
 Visual Studio 會在設計工具中開啟新的 Excel 活頁簿，並將 My Simple Data Binding 專案加入至 \[**方案總管**\]。  
  
## 建立資料來源  
 請使用 \[**資料來源**\] 視窗，將具型別資料集加入您的專案。  
  
#### 建立資料來源  
  
1.  如果 \[**資料來源**\] 視窗中不可見，請顯示它，請在功能表列上，選擇 \[**檢視**\]\]，則 \[**其他視窗**\]， \[**資料來源**\]。  
  
2.  選取 \[**加入新資料來源**\] 啟動 \[**資料來源組態精靈**\]。  
  
3.  選取 \[**資料庫**\]，再按一下 \[**下一步**\]。  
  
4.  選取與 Northwind 範例 SQL Server 資料庫的資料連接，或使用 \[**新增連接**\] 按鈕加入新的連接。  
  
5.  在選取或建立連接後，請按 \[**下一步**\]。  
  
6.  如果已經選取，請清除儲存連接的選項，然後按一下 \[**下一步**\]。  
  
7.  在 \[**資料庫物件**\] 視窗中，展開 \[**資料表**\] 節點。  
  
8.  選取 \[**Customers**\] 資料表旁的核取方塊。  
  
9. 按一下 \[完成\]。  
  
 精靈會將 \[**Customers**\] 資料表加入至 \[**資料來源**\] 視窗。  也會將具型別資料集加入至 \[**方案總管**\] 中可以看得到的專案。  
  
## 將控制項加入至工作表  
 對於本逐步解說，在第一個工作表上，您需要兩個已命名的範圍和四個按鈕。  首先，請從 \[**資料來源**\] 視窗加入兩個已命名的範圍，使它們自動繫結至資料來源。  接著，再從 \[**工具箱**\] 加入按鈕。  
  
#### 若要加入兩個已命名的範圍  
  
1.  驗證 \[**我的簡單資料 Binding.xlsx**\] 活頁簿在 Visual Studio 中開啟設計工具，並顯示 \[**Sheet1**\] 。  
  
2.  開啟 \[**資料來源**\] 視窗，然後展開 \[**Customers**\] 節點。  
  
3.  選取 \[**CompanyName**\] 資料行，然後按一下顯示的下拉箭號。  
  
4.  在下拉式清單中，選取 \[**NamedRange**\]，然後將 \[**CompanyName**\] 資料行拖曳至 \[**A1**\] 儲存格。  
  
     \[**A1**\] 儲存格中會建立一個名為 <xref:Microsoft.Office.Tools.Excel.NamedRange> 的 `companyNameNamedRange` 控制項。  同時，會將名為 `customersBindingSource` 的 <xref:System.Windows.Forms.BindingSource>、資料表配接器，以及 <xref:System.Data.DataSet> 執行個體加入至專案。  控制項繫結至 <xref:System.Windows.Forms.BindingSource>，繼而又繫結至 <xref:System.Data.DataSet> 執行個體。  
  
5.  在 \[**資料來源**\] 視窗中選取 \[**CustomerID**\] 資料行，然後按一下顯示的下拉箭號。  
  
6.  在下拉式清單中，按一下 \[**NamedRange**\]，然後將 \[**CustomerID**\] 資料行拖曳至 \[**B1**\] 儲存格。  
  
7.  另一個名為 `customerIDNamedRange` 的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項會建立在 \[**B1**\] 儲存格中，並繫結至 <xref:System.Windows.Forms.BindingSource>。  
  
#### 若要加入四個按鈕  
  
1.  從 \[**工具箱**\] 的 \[**通用控制項**\] 索引標籤，將 <xref:System.Windows.Forms.Button> 控制項加入至工作表的 \[**A3**\] 儲存格。  
  
     這個按鈕的名稱為 `Button1`。  
  
2.  依照此順序將另外三個按鈕加入至下列儲存格，使名稱如下所示：  
  
    |儲存格|\(名稱\)|  
    |---------|------------|  
    |B3|Button2|  
    |C3|Button3|  
    |D3|Button4|  
  
 下一步驟是在按鈕上加入文字，並在 C\# 中加入事件處理常式。  
  
## 初始化控制項  
 設定按鈕文字，並在 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 事件期間加入事件處理常式。  
  
#### 若要初始化控制項  
  
1.  在 \[**方案總管**\] 中，在 \[**Sheet1.vb**\] 或 \[**Sheet1.cs**\] 上按一下滑鼠右鍵，再按捷徑功能表上的 \[**檢視程式碼**\]。  
  
2.  將下列程式碼加入至 `Sheet1_Startup` 方法，以設定每個按鈕的文字。  
  
     [!code-csharp[Trin_VstcoreDataExcel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreDataExcel#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#2)]  
  
3.  如果是 C\#，請將按鈕 Click 事件的事件處理常式加入至 `Sheet1_Startup` 方法中。  
  
     [!code-csharp[Trin_VstcoreDataExcel#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#3)]  
  
 現在，請加入程式碼以處理按鈕的 <xref:System.Windows.Forms.Control.Click> 事件，以便使用者可以瀏覽目錄。  
  
## 加入程式碼以啟用捲動資料錄的功能  
 將程式碼加入至每個按鈕的 <xref:System.Windows.Forms.Control.Click> 事件處理常式，以便在資料錄中移動。  
  
#### 若要移至第一個記錄  
  
1.  為 `Button1` 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件加入事件處理常式，然後加入下列程式碼，以移至第一個記錄：  
  
     [!code-csharp[Trin_VstcoreDataExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#4)]  
  
#### 若要移至上一個記錄  
  
1.  為 `Button2` 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件加入事件處理常式，然後加入下列程式碼，以後退一個記錄位置：  
  
     [!code-csharp[Trin_VstcoreDataExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#5)]  
  
#### 若要移至下一個記錄  
  
1.  為 `Button3` 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件加入事件處理常式，然後加入下列程式碼，以前進一個記錄的位置：  
  
     [!code-csharp[Trin_VstcoreDataExcel#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#6)]  
  
#### 若要移至最後一個記錄  
  
1.  為 `Button4` 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件加入事件處理常式，然後加入下列程式碼，以移至最後一個記錄：  
  
     [!code-csharp[Trin_VstcoreDataExcel#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#7)]  
  
## 測試應用程式  
 現在，請您測試活頁簿以確定您可以瀏覽資料庫中的記錄。  
  
#### 若要測試您的活頁簿  
  
1.  請按 F5 執行您的專案。  
  
2.  請確認第一個記錄出現在 \[**A1**\] 和 \[**B1**\] 儲存格中。  
  
3.  按一下 \[**\>**\] \(`Button3`\) 按鈕，並確認下一個記錄出現在 \[**A1**\] 和 \[**B1**\] 儲存格中。  
  
4.  按一下其他捲動按鈕，以確認記錄如預期變更。  
  
## 後續步驟  
 這個逐步解說顯示將已命名的範圍繫結至資料庫中資料欄位的基本概念。  以下則是接下來的一些工作：  
  
-   快取資料，使您能夠離線使用資料。  如需詳細資訊，請參閱[如何：快取資料供離線使用或於伺服器上使用](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)。  
  
-   將儲存格繫結至資料表中多個資料行，而不是一個資料欄位。  如需詳細資訊，請參閱[逐步解說：文件層級專案中的複雜資料繫結](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)。  
  
-   使用 <xref:System.Windows.Forms.BindingNavigator> 控制項，以捲動記錄。  如需詳細資訊，請參閱[如何：使用 Windows Form BindingNavigator 控制項巡覽資料](../Topic/How%20to:%20Navigate%20Data%20with%20the%20Windows%20Forms%20BindingNavigator%20Control.md)。  
  
## 請參閱  
 [將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Office 方案的資料](../vsto/data-in-office-solutions.md)   
 [逐步解說：文件層級專案中的複雜資料繫結](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)  
  
  
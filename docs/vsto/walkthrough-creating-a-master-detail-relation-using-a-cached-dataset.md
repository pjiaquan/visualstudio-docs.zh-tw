---
title: "逐步解說：使用快取資料集來建立主從式關聯 | Microsoft Docs"
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
  - "資料快取 [Visual Studio 中的 Office 程式開發], 主從式關係"
  - "主從式資料表 [Visual Studio 中的 Office 程式開發], 逐步解說"
ms.assetid: 419f4e07-c67f-4fc9-973a-bc794f349ac3
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# 逐步解說：使用快取資料集來建立主從式關聯
  這個逐步解說示範如何在工作表上建立主從式 \(Master\/Detail\) 關聯，以及如何快取資料，使得此方案可以離線使用。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 在瀏覽這份逐步解說期間，您將了解如何：  
  
-   將控制項加入至工作表  
  
-   在工作表中設定要快取的資料集  
  
-   加入程式碼，以啟用捲動資料錄的功能  
  
-   測試您的專案  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置：  您所擁有的 Visual Studio 版本和使用的設定決定了這些項目。  如需詳細資訊，請參閱[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   Northwind SQL Server 範例資料庫的存取權。  資料庫可以位於開發電腦或是伺服器上。  
  
-   從 SQL Server 資料庫讀取及寫入該資料庫的使用權限。  
  
## 建立新專案  
 在這個步驟中，您將會建立一個 Excel 活頁簿專案。  
  
#### 若要建立新的專案  
  
1.  使用 Visual Basic 或 C\#，建立名為 **My Master\-Detail** 的 Excel 活頁簿專案。  請確定已選取 \[**建立新文件**\]。  如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
 Visual Studio 會在設計工具中開啟新的 Excel 活頁簿，並將 My Master\-Detail 專案加入至 \[**方案總管**\]。  
  
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
  
8.  選取 \[**訂單**\] 資料表和 \[**訂貨明細**\] 資料表。  
  
9. 按一下 \[完成\]。  
  
 精靈會將這兩個資料表加入至 \[**資料來源**\] 視窗，  也會將具型別資料集加入至 \[**方案總管**\] 中可以看得到的專案。  
  
## 將控制項加入至工作表  
 在這個步驟中，您會將已命名的範圍、清單物件和兩個按鈕加入至第一個工作表。  首先，請從 \[**資料來源**\] 視窗加入已命名的範圍和清單物件，使它們自動繫結至資料來源。  接著，再從 \[**工具箱**\] 加入按鈕。  
  
#### 若要加入已命名的範圍和清單物件  
  
1.  驗證 \[**我的主要 Detail.xlsx**\] 活頁簿在 Visual Studio 中開啟設計工具，並顯示 \[**Sheet1**\] 。  
  
2.  開啟 \[**資料來源**\] 視窗，然後展開 \[**訂單**\] 節點。  
  
3.  選取 \[**OrderID**\] 資料行，然後按一下顯示的下拉箭號。  
  
4.  在下拉式清單中，按一下 \[**NamedRange**\]，然後將 \[**OrderID**\] 資料行拖曳到 \[**A2**\] 儲存格。  
  
     **A2** 儲存格中會建立一個名為 `OrderIDNamedRange` 的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項。  同時，會將名為 `OrdersBindingSource` 的 <xref:System.Windows.Forms.BindingSource>、資料表配接器，以及 <xref:System.Data.DataSet> 執行個體加入至專案。  控制項繫結至 <xref:System.Windows.Forms.BindingSource>，繼而又繫結至 <xref:System.Data.DataSet> 執行個體。  
  
5.  捲動超過 \[**訂單**\] 資料表下的資料行。  位在清單底部的是 \[**訂貨明細**\] 資料表。由於它是 \[**訂單**\] 資料表的子系，因而位在該處。  請選取這個 \[**訂貨明細**\] 資料表，不要選取與 \[**訂單**\] 資料表位於相同層級的資料表，然後按一下顯示的下拉箭號。  
  
6.  在下拉式清單中按一下 \[**ListObject**\]，然後將 \[**Order Details**\] 資料表拖曳到 \[**A6**\] 儲存格。  
  
7.  \[**A6**\] 儲存格中會建立一個名為 **Order\_DetailsListObject** 的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項，且該控制項會繫結至 <xref:System.Windows.Forms.BindingSource>。  
  
#### 若要加入兩個按鈕  
  
1.  從 \[**工具箱**\] 的 \[**通用控制項**\] 索引標籤，將 <xref:System.Windows.Forms.Button> 控制項加入至工作表的 \[**A3**\] 儲存格。  
  
     這個按鈕的名稱為 `Button1`。  
  
2.  將另一個 <xref:System.Windows.Forms.Button> 控制項加入至工作表的 \[**B3**\] 儲存格。  
  
     這個按鈕名為 `Button2`。  
  
 接下來，在文件中標記要快取的資料集。  
  
## 快取資料集  
 公開資料集並設定 **CacheInDocument** 屬性，在文件中標記要快取的資料集。  
  
#### 若要快取資料集  
  
1.  在元件匣中選取 \[**NorthwindDataSet**\]。  
  
2.  在 \[**屬性**\] 視窗中，將 \[**Modifiers**\] 屬性變更為 \[**Public**\]。  
  
     您必須先公開資料集，才能啟用快取。  
  
3.  將 \[**CacheInDocument**\] 屬性變更為 **True**。  
  
 下一個步驟是在按鈕上加入文字，並在 C\# 中加入程式碼以連結事件處理常式。  
  
## 初始化控制項  
 設定按鈕文字，並在 <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> 事件期間加入事件處理常式。  
  
#### 若要初始化資料和控制項  
  
1.  在 \[**方案總管**\] 中，在 \[**Sheet1.vb**\] 或 \[**Sheet1.cs**\] 上按一下滑鼠右鍵，再按捷徑功能表上的 \[**檢視程式碼**\]。  
  
2.  將下列程式碼加入至 `Sheet1_Startup` 方法，以設定按鈕的文字。  
  
     [!code-csharp[Trin_VstcoreDataExcel#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#15)]
     [!code-vb[Trin_VstcoreDataExcel#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet2.vb#15)]  
  
3.  如果是 C\#，請將按鈕 Click 事件的事件處理常式加入至 `Sheet1_Startup` 方法中。  
  
     [!code-csharp[Trin_VstcoreDataExcel#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#16)]  
  
## 加入程式碼以啟用捲動資料錄的功能  
 將程式碼加入至每個按鈕的 <xref:System.Windows.Forms.Control.Click> 事件處理常式，以便在資料錄中移動。  
  
#### 若要捲動資料錄  
  
1.  為 `Button1` 的 <xref:System.Windows.Forms.Control.Click> 事件加入事件處理常式，然後加入下列程式碼，以向後瀏覽資料錄：  
  
     [!code-csharp[Trin_VstcoreDataExcel#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#17)]
     [!code-vb[Trin_VstcoreDataExcel#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet2.vb#17)]  
  
2.  為 `Button2` 的 <xref:System.Windows.Forms.Control.Click> 事件加入事件處理常式，然後加入下列程式碼，以向前瀏覽資料錄：  
  
     [!code-csharp[Trin_VstcoreDataExcel#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#18)]
     [!code-vb[Trin_VstcoreDataExcel#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet2.vb#18)]  
  
## 測試應用程式  
 現在您可以測試活頁簿，確認資料將如預期般顯示，而且可以離線使用該方案。  
  
#### 若要測試資料快取  
  
1.  請按 **F5**。  
  
2.  確認已命名的範圍和清單物件中會填入資料來源中的資料。  
  
3.  按一下按鈕以捲動部分資料錄。  
  
4.  儲存活頁簿，然後關閉活頁簿和 Visual Studio。  
  
5.  停用資料庫的連接。  如果資料庫位於伺服器上，請拔下電腦上的網路線。如果資料庫位於開發電腦上，請停止 SQL Server 服務。  
  
6.  開啟 Excel 然後開啟 \[**我的主要 Detail.xlsx**\] 從\\ bin 目錄 \(\\ My 主從式\\ bin 在 Visual Basic 或\\ My 主從式\\ bin \\ debug 在 C\# 偵錯\)。  
  
7.  捲動部分資料錄，確定工作表在中斷連接時是否能正常運作。  
  
8.  重新連接至資料庫。  如果資料庫位於伺服器上，請將電腦重新連接至網路。如果資料庫位於開發電腦上，請啟動 SQL Server 服務。  
  
## 後續步驟  
 這個逐步解說示範在工作表上建立主從式關聯，以及快取資料集的基本步驟。  以下則是接下來的一些工作：  
  
-   部署方案。  如需詳細資訊，請參閱[部署 Office 方案](../vsto/deploying-an-office-solution.md)。  
  
## 請參閱  
 [將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Office 方案的資料](../vsto/data-in-office-solutions.md)   
 [快取資料](../vsto/caching-data.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)  
  
  
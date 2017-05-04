---
title: "逐步解說：在伺服器的活頁簿中插入資料 | Microsoft Docs"
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
  - "資料 [Visual Studio 中的 Office 程式開發], 在伺服器上存取"
  - "資料集 [Visual Studio 中的 Office 程式開發], 在伺服器上存取"
  - "文件 [Visual Studio 中的 Office 程式開發], 伺服器端資料存取"
  - "伺服器端資料存取 [Visual Studio 中的 Office 程式開發]"
  - "活頁簿 [Visual Studio 中的 Office 程式開發], 插入資料"
ms.assetid: e6481902-781c-4666-bc18-4d69368c9bb3
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# 逐步解說：在伺服器的活頁簿中插入資料
  本逐步解說將示範如何在不啟動 Excel 的情況下，使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別將資料插入至 Microsoft Office Excel 活頁簿中快取的資料集。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   定義資料集，其中包含 AdventureWorksLT 資料庫中的資料。  
  
-   在 Excel 活頁簿專案和主控台應用程式專案中建立資料集的執行個體。  
  
-   建立繫結至活頁簿之資料集的 <xref:Microsoft.Office.Tools.Excel.ListObject>。  
  
-   將活頁簿中的資料集加入至資料快取。  
  
-   在未啟動 Excel 的情況下，藉由在主控台應用程式中執行程式碼，將資料插入至快取的資料集。  
  
 雖然這個逐步解說假設您正在開發電腦上執行程式碼，但是它所示範的程式碼可以在沒有安裝 Excel 的伺服器上使用。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置：  您所擁有的 Visual Studio 版本和使用的設定決定了這些項目。  如需詳細資訊，請參閱[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   存取附加了 AdventureWorksLT 範例資料庫之執行中的 Microsoft SQL Server 或 Microsoft SQL Server Express 執行個體。  您可以從 [CodePlex 網站](http://go.microsoft.com/fwlink/?linkid=87843) \(英文\) 下載 AdventureWorksLT 資料庫。  如需附加資料庫的詳細資訊，請參閱下列主題：  
  
    -   若要使用 SQL Server Management Studio 或 SQL Server Management Studio Express 來附加資料庫，請參閱 [HOW TO：附加資料庫 \(SQL Server Management Studio\)](http://msdn.microsoft.com/zh-tw/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa)。  
  
    -   若要使用命令列來附加資料庫，請參閱 [HOW TO：將資料庫檔案附加至 SQL Server Express](http://msdn.microsoft.com/zh-tw/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68)。  
  
## 建立定義資料集的類別庫專案  
 若要在 Excel 活頁簿專案和主控台應用程式專案中使用相同的資料集，您必須在這兩個專案同時參考的另一個組件中定義資料集。  在本逐步解說中，請於類別庫專案中定義資料集。  
  
#### 若要建立類別庫專案  
  
1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在 \[**檔案**\] 功能表上，指向 \[**新增**\]，然後按一下 \[**專案**\]。  
  
3.  在 \[範本\] 窗格中，展開 \[**Visual C\#**\] 或 \[**Visual Basic**\]，然後按一下 \[**Windows**\]。  
  
4.  在專案範本清單中，選取 \[**類別庫**\]。  
  
5.  在 \[**名稱**\] 方塊中輸入 **AdventureWorksDataSet**。  
  
6.  按一下 \[**瀏覽**\]，巡覽至您的 %UserProfile%\\My Documents \(適用於 Windows XP \(含\) 以前版本\) 或 %UserProfile%\\Documents \(適用於 Windows Vista\) 資料夾，然後按一下 \[**選取資料夾**\]。  
  
7.  在 \[**新增專案**\] 對話方塊中，確認未選取 \[**為方案建立目錄**\] 核取方塊。  
  
8.  按一下 \[**確定**\]。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將 **AdventureWorksDataSet** 專案加入至 \[**方案總管**\]，並開啟 **Class1.cs** 或 **Class1.vb** 程式碼檔案。  
  
9. 在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**Class1.cs**\] 或 \[**Class1.vb**\]，再按一下 \[**刪除**\]。  在這個逐步解說中，您不需要這個檔案。  
  
## 在類別庫專案中定義資料集  
 定義具型別資料集，其中包含 SQL Server 2005 之 AdventureWorksLT 資料庫中的資料。  在此逐步解說稍後的內容中，您會從 Excel 活頁簿專案和主控台應用程式專案參考這個資料集。  
  
 此資料集是「*具型別資料集*」\(Typed Dataset\)，表示 AdventureWorksLT 資料庫之 Product 資料表中的資料。  如需具型別資料集的詳細資訊，請參閱 [使用 Visual Studio 中的資料集](../data-tools/dataset-tools-in-visual-studio.md)。  
  
#### 若要在類別庫專案中定義具型別資料集  
  
1.  在 \[**方案總管**\] 中，按一下 \[**AdventureWorksDataSet**\] 專案。  
  
2.  如果 \[**資料來源**\] 視窗中不可見，請顯示它，請在功能表列上，選擇 \[**檢視**\]\]，則 \[**其他視窗**\]， \[**資料來源**\]。  
  
3.  選取 \[**加入新資料來源**\] 啟動 \[**資料來源組態精靈**\]。  
  
4.  按一下 \[**資料庫**\]，然後按 \[**下一步**\]。  
  
5.  如果您有現有的 AdventureWorksLT 資料庫連接，請選擇此連接，再按 \[**下一步**\]。  
  
     否則，請按一下 \[**新增連接**\]，並使用 \[**加入連接**\] 對話方塊建立新連接。  如需詳細資訊，請參閱[How to: Connect to Data in a Database](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)。  
  
6.  在 \[**Save the Connection String to the Application Configuration File**\] 頁面中，按 \[**Next**\]。  
  
7.  在 \[**選擇您的資料庫物件**\] 頁面中，展開 \[**資料表**\]，並選取 \[**Product \(SalesLT\)**\]。  
  
8.  按一下 \[完成\]。  
  
     AdventureWorksLTDataSet.xsd 檔案隨即加入至 **AdventureWorksDataSet** 專案。  這個檔案定義下列項目：  
  
    -   名稱為 `AdventureWorksLTDataSet` 的具型別資料集。  這個資料集表示 AdventureWorksLT 資料庫中 Product 資料表的內容。  
  
    -   名為 `ProductTableAdapter` 的 TableAdapter。  這個 TableAdapter 可以用來讀取和寫入 `AdventureWorksLTDataSet` 中的資料。  如需詳細資訊，請參閱[TableAdapter 概觀](/visual-studio/data-tools/tableadapter-overview)。  
  
     在這個逐步解說後面的步驟中，您會用到這兩個物件。  
  
9. 在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**AdventureWorksDataSet**\]，再按一下 \[**建置**\]。  
  
     接著驗證專案建置無誤。  
  
## 建立 Excel 活頁簿專案  
 建立資料介面的 Excel 活頁簿專案。  在此逐步解說稍後的內容中，您會建立顯示資料的 <xref:Microsoft.Office.Tools.Excel.ListObject>，也會將資料集的執行個體加入至活頁簿的資料快取。  
  
#### 若要建立 Excel 活頁簿專案  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**AdventureWorksDataSet**\] 方案，指向 \[**加入**\]，再按一下 \[**新增專案**\]。  
  
2.  在範本窗格中，展開 \[**Visual C\#**\] 或 \[ **Visual Basic**\]，然後展開 \[**Office SharePoint\/**\]。  
  
3.  在展開的 \[**Office SharePoint\/**\] 節點下，選取 \[**Office 增益集**\] 節點。  
  
4.  在專案範本清單中，選取 \[**Excel 2010 活頁簿**\] 或 \[**Excel 2013 活頁簿**\] 專案。  
  
5.  在 \[**名稱**\] 方塊中輸入 **AdventureWorksReport**。  請勿修改位置。  
  
6.  按一下 \[**確定**\]。  
  
     \[**Visual Studio Tools for Office 專案精靈**\] 便會開啟。  
  
7.  確認已選取 \[**建立新文件**\]，然後按一下 \[**確定**\]。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會在設計工具中開啟 **AdventureWorksReport** 活頁簿，並將 **AdventureWorksReport** 專案加入至 \[**方案總管**\]。  
  
## 將資料集加入至 Excel 活頁簿專案中的資料來源  
 您必須先將資料集加入至 Excel 活頁簿專案中的資料來源，才能在 Excel 活頁簿中顯示資料集。  
  
#### 若要將資料集加入至 Excel 活頁簿專案中的資料來源  
  
1.  在 \[**方案總管**\] 中，按兩下 \[**AdventureWorksReport**\] 專案底下的 \[**Sheet1.cs**\] 或 \[**Sheet1.vb**\]。  
  
     活頁簿就會在設計工具中開啟。  
  
2.  在 \[**資料**\] 功能表上，請按一下 \[**加入新資料來源**\]。  
  
     \[**資料來源組態精靈**\] 隨即開啟。  
  
3.  按一下 \[**物件**\]，然後按 \[**下一步**\]。  
  
4.  在 \[**選取您要繫結的目標物件**\] 頁面中，按一下 \[**加入參考**\]。  
  
5.  在 \[**專案**\] 索引標籤上，按一下 \[**AdventureWorksDataSet**\]，然後按 \[**確定**\]。  
  
6.  在 \[**AdventureWorksDataSet**\] 組件的 \[**AdventureWorksDataSet**\] 命名空間底下，按一下 \[**AdventureWorksLTDataSet**\]，然後按一下 \[**完成**\]。  
  
     \[**資料來源**\] 視窗隨即開啟，而且 \[**AdventureWorksLTDataSet**\] 也會加入至資料來源清單中。  
  
## 建立繫結至資料集執行個體的 ListObject  
 若要將資料集顯示在活頁簿中，請建立繫結至資料集執行個體的 <xref:Microsoft.Office.Tools.Excel.ListObject>。  如需將控制項繫結至資料的詳細資訊，請參閱[將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)。  
  
#### 若要建立繫結至資料集執行個體的 ListObject  
  
1.  在 \[**資料來源**\] 視窗中，展開 \[**AdventureWorksDataSet**\] 底下的 \[**AdventureWorksLTDataSet**\] 節點。  
  
2.  選取 \[**產品**\] 節點，按一下出現的下拉箭號，然後在下拉式清單中選取 \[**ListObject**\]。  
  
     如果下拉箭號沒有出現，請確認活頁簿已在設計工具中開啟。  
  
3.  將 \[**產品**\] 資料表拖曳至儲存格 A1。  
  
     工作表中會建立一個名為 `productListObject` 的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項 \(從儲存格 A1 開始\)。  同時，也會將名為 `adventureWorksLTDataSet` 的資料集物件和名為 `productBindingSource` 的 <xref:System.Windows.Forms.BindingSource> 加入至專案。  <xref:Microsoft.Office.Tools.Excel.ListObject> 會繫結至 <xref:System.Windows.Forms.BindingSource>，而後者則繫結至資料集物件。  
  
## 將資料集加入至資料快取  
 若要讓 Excel 活頁簿專案外部的程式碼能夠存取活頁簿中的資料集，您必須將資料集加入至資料快取。  如需資料快取的詳細資訊，請參閱[文件層級自訂中的快取資料](../vsto/cached-data-in-document-level-customizations.md)和[快取資料](../vsto/caching-data.md)。  
  
#### 若要將資料集加入至資料快取  
  
1.  在設計工具中，按一下 \[**adventureWorksLTDataSet**\]。  
  
2.  在 \[**屬性**\] 視窗中，將 \[**Modifiers**\] 屬性設定為 \[**Public**\]。  
  
3.  將 \[**CacheInDocument**\] 屬性設定為 \[**True**\]。  
  
## 檢查點  
 建置並執行 Excel 活頁簿專案，以確保此專案能正確編譯及執行。  
  
#### 若要建置及執行專案  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**AdventureWorksReport**\] 專案，選擇 \[**偵錯**\]，然後按一下 \[**開始新執行個體**\]。  
  
     專案已建置，而且活頁簿會在 Excel 中開啟。  Sheet1 中的 <xref:Microsoft.Office.Tools.Excel.ListObject> 是空白，因為資料快取中的 `adventureWorksLTDataSet` 物件目前沒有資料。  在下節，您將使用主控台應用程式，將資料填入 `adventureWorksLTDataSet` 物件。  
  
2.  關閉 Excel。  請勿儲存任何變更。  
  
## 建立主控台應用程式專案  
 您可以建立主控台應用程式專案，用來將資料插入至活頁簿中快取的資料集。  
  
#### 若要建立主控台應用程式專案  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**AdventureWorksDataSet**\] 方案，指向 \[**加入**\]，再按一下 \[**新增專案**\]。  
  
2.  在 \[**專案類型**\] 窗格中，展開 \[**Visual C\#**\] 或 \[**Visual Basic**\]，然後按一下 \[**Windows**\]。  
  
3.  在 \[**範本**\] 窗格中選取 \[**主控台應用程式**\]。  
  
4.  在 \[**名稱**\] 方塊中，輸入 **DataWriter**。  請勿修改位置。  
  
5.  按一下 \[**確定**\]。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將 **DataWriter** 專案加入至 \[**方案總管**\]，並開啟 **Program.cs** 或 **Module1.vb** 程式碼檔。  
  
## 使用主控台應用程式，將資料加入至快取的資料集  
 您可以在主控台應用程式中使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別，將資料填入活頁簿中快取的資料集。  
  
#### 若要將資料加入至快取的資料集  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**DataWriter**\] 專案，再按一下 \[**加入參考**\]。  
  
2.  在 \[**.NET**\] 索引標籤上，選取 \[**Microsoft.VisualStudio.Tools.Applications.ServerDocument**\]。  
  
3.  按一下 \[**確定**\]。  
  
4.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**DataWriter**\] 專案，再按一下 \[**加入參考**\]。  
  
5.  在 \[**專案**\] 索引標籤上，選取 \[**AdventureWorksDataSet**\]，然後按一下 \[**確定**\]。  
  
6.  在程式碼編輯器中開啟 Program.cs 或 Module1.vb 檔案。  
  
7.  將下列 **using** \(適用於 C\#\) 或 **Imports** \(適用於 Visual Basic\) 陳述式加入至程式碼檔案的最上方。  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/CS/DataWriter/Program.cs#1)]
     [!code-vb[Trin_CachedDataWalkthroughs#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/VB/DataWriter/Module1.vb#1)]  
  
8.  將以下程式碼加入至 `Main` 方法中。  這個程式碼會宣告下列物件：  
  
    -   `AdventureWorksLTDataSet` 和 `ProductTableAdapter` 型別的執行個體，這些執行個體是在 **AdventureWorksDataSet** 專案中定義。  
  
    -   **AdventureWorksReport** 專案之組建資料夾中 AdventureWorksReport 活頁簿的路徑。  
  
    -   要用來在活頁簿中存取資料快取的 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 物件。  
  
        > [!NOTE]  
        >  下列程式碼假設您使用的是副檔名為 .xlsx 的活頁簿。  如果專案中的活頁簿是使用不同的副檔名，請視需要修改路徑。  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/CS/DataWriter/Program.cs#3)]
     [!code-vb[Trin_CachedDataWalkthroughs#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/VB/DataWriter/Module1.vb#3)]  
  
9. 將下列程式碼加入至 `Main` 方法中，加入的位置是您在前一個步驟中加入的程式碼後面。  這個程式碼會執行下列工作：  
  
    -   它會使用資料表配接器 \(Adapter\)，填滿具型別資料集物件。  
  
    -   它會使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別的 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> 屬性來存取活頁簿中的快取資料集。  
  
    -   它會使用 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> 方法，將本機具型別資料集的資料填入快取的資料集。  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/CS/DataWriter/Program.cs#4)]
     [!code-vb[Trin_CachedDataWalkthroughs#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/VB/DataWriter/Module1.vb#4)]  
  
10. 在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**DataWriter**\] 專案，指向 \[**偵錯**\]，然後按一下 \[**開始新執行個體**\]。  
  
     隨即建置專案，而且當本機資料集填滿時，以及在應用程式將資料儲存至活頁簿中快取的資料集時，主控台應用程式會顯示數個狀態訊息。  按 ENTER 鍵關閉應用程式。  
  
## 測試活頁簿  
 當您開啟活頁簿時，<xref:Microsoft.Office.Tools.Excel.ListObject> 現在會顯示已透過主控台應用程式加入至快取資料集的資料。  
  
#### 若要測試活頁簿  
  
1.  如果 Visual Studio 設計工具中的 AdventureWorksReport 活頁簿仍然開啟，請將它關閉。  
  
2.  在檔案總管中，開啟 **AdventureWorksReport** 專案的建置資料夾中的 AdventureWorksReport 活頁簿。  根據預設，建置資料夾位於下列其中一個位置：  
  
    -   %UserProfile%\\My Documents\\AdventureWorksReport\\bin\\Debug \(適用於 Windows XP \(含\) 以前版本\)  
  
    -   %UserProfile%\\Documents\\AdventureWorksReport\\bin\\Debug \(適用於 Windows Vista\)  
  
3.  確認活頁簿開啟之後，<xref:Microsoft.Office.Tools.Excel.ListObject> 已填入資料。  
  
## 後續步驟  
 您可以透過下列主題，進一步了解如何使用快取資料：  
  
-   在未啟動 Excel 的情況下，變更快取資料集中的資料。  如需詳細資訊，請參閱[逐步解說：變更伺服器上的活頁簿快取資料](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)。  
  
## 請參閱  
 [逐步解說：變更伺服器上的活頁簿快取資料](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)   
 [連接至 Windows Form 應用程式中的資料](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)  
  
  
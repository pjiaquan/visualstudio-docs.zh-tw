---
title: "逐步解說：將 WPF 控制項繫結到資料集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "WPF 資料繫結 [Visual Studio], 逐步解說"
  - "WPF Designer, 資料繫結"
  - "WPF, Visual Studio 中的資料繫結"
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
caps.latest.revision: 32
caps.handback.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逐步解說：將 WPF 控制項繫結到資料集
您將在此逐步解說中，建立包含資料繫結控制項的 WPF 應用程式。  這些控制項會繫結至封裝於資料集中的產品記錄。  您也要加入按鈕，以瀏覽產品，並將變更儲存至產品記錄。  
  
 這個逐步解說將說明下列工作：  
  
-   建立 WPF 應用程式，以及建立從 AdventureWorksLT 範例資料庫中的資料產生的資料集。  
  
-   從 \[資料來源\] 視窗將資料表拖曳至 WPF 設計工具的視窗，以建立一組資料繫結控制項。  
  
-   建立可向前及向後巡覽產品記錄的按鈕。  
  
-   建立可將使用者對產品記錄所做的變更儲存至資料表和基礎資料來源的按鈕。  
  
     [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
-   對執行中的 SQL Server 或 SQL Server Express \(其中連結了 AdventureWorksLT 範例資料庫\) 執行個體的存取權。  您可以從 [CodePlex 網站](http://go.microsoft.com/fwlink/?linkid=87843) 下載 AdventureWorksLT 資料庫。  
  
 預先了解下列概念也有助於完成此逐步解說 \(但非必要\)：  
  
-   資料集和 TableAdapter。  如需詳細資訊，請參閱[使用 Visual Studio 中的資料集](../data-tools/dataset-tools-in-visual-studio.md)與[TableAdapter 概觀](../data-tools/tableadapter-overview.md)。  
  
-   使用 WPF 設計工具。  如需詳細資訊，請參閱[WPF 和 Silverlight 設計工具概觀](http://msdn.microsoft.com/zh-tw/570b7a5c-0c86-4326-a371-c9b63378fc62)。  
  
-   WPF 資料繫結。  如需詳細資訊，請參閱[資料繫結概觀](../Topic/Data%20Binding%20Overview.md)。  
  
## 建立專案  
 建立新的 WPF 專案。  此專案將顯示產品記錄。  
  
#### 若要建立專案  
  
1.  啟動 Visual Studio。  
  
2.  在 \[檔案\] 功能表中，指向 \[新增\]，然後按一下 \[專案\]。  
  
3.  展開 \[Visual Basic\] 或 \[Visual C\#\]，然後選取 \[Windows\]。  
  
4.  選取 \[WPF 應用程式\] 專案範本。  
  
5.  在 \[名稱\] 方塊中，輸入 `AdventureWorksProductsEditor`，然後按一下 \[確定\]。  
  
     Visual Studio 隨即建立 `AdventureWorksProductsEditor` 專案。  
  
## 建立應用程式的資料集  
 建立資料繫結控制項之前，您必須先定義應用程式的資料模型，並將其加入至 \[資料來源\] 視窗。  在此逐步解說中，您會建立資料集做為資料模型。  
  
#### 建立資料集  
  
1.  按一下 \[**資料**\] 功能表上的 \[**顯示資料來源**\]。  
  
     \[資料來源\] 視窗隨即開啟。  
  
2.  在 \[**資料來源**\] 視窗中，按一下 \[**加入新資料來源**\]。  
  
     \[**資料來源組態精靈**\] 隨即開啟。  
  
3.  在 \[**選擇資料來源類型**\] 頁面上，選取 \[**資料庫**\]，再按 \[**下一步**\]。  
  
4.  在 \[**選擇資料庫模型**\] 頁面上，選取 \[**資料集**\]，再按 \[**下一步**\]。  
  
5.  在 \[選擇資料連接\] 頁面中，選取下列其中一個選項：  
  
    -   若下拉式清單中有提供 AdventureWorksLT 範例資料庫的資料連接，請選取此資料連接，然後按 \[下一步\]。  
  
         \-或\-  
  
    -   按一下 \[新增連接\]，建立與 AdventureWorksLT 資料庫的連接。  
  
6.  在 \[將連接字串儲存到應用程式組態檔\] 頁面中，選取 \[是，將連接儲存為\] 核取方塊，然後按 \[下一步\]。  
  
7.  在 \[選擇您的資料庫物件\] 頁面中，展開 \[資料表\]，然後選取 **Product \(SalesLT\)** 資料表。  
  
8.  按一下 \[**完成**\]。  
  
     Visual Studio 隨即將新的 AdventureWorksLTDataSet.xsd 檔案加入至專案，並將對應的 \[AdventureWorksLTDataSet\] 項目加入至 \[資料來源\] 視窗。  AdventureWorksLTDataSet.xsd 檔案會定義名稱為 `AdventureWorksLTDataSet` 的類型資料集，以及名稱為 `ProductTableAdapter` 的 TableAdapter。  在此逐步解說稍後的內容中，您會使用 `ProductTableAdapter` 將資料填入資料集，並將變更儲存回資料庫。  
  
9. 建置專案。  
  
## 編輯 TableAdapter 的預設 Fill 方法  
 若要將資料填入資料集，請使用 `ProductTableAdapter` 的 `Fill` 方法。  根據預設，`Fill` 方法會使用 Product 資料表的所有資料列，填入 `AdventureWorksLTDataSet` 中的 `ProductDataTable`。  您可以修改此方法，使其只傳回資料列的子集。  在此逐步解說中，會修改 `Fill` 方法，使其只針對具有相片的產品傳回資料列。  
  
#### 載入具有相片的產品資料列  
  
1.  在**方案總管**中，按兩下 AdventureWorksLTDataSet.xsd 檔案。  
  
     DataSet 設計工具隨即開啟。  
  
2.  在設計工具中，在 \[Fill,GetData\(\)\] 查詢上按一下滑鼠右鍵，然後選取 \[設定\]。  
  
     \[TableAdapter 組態精靈\] 隨即開啟。  
  
3.  在 \[輸入 SQL 陳述式\] 頁面中，將下列 WHERE 子句加在文字方塊中 `SELECT` 陳述式的後面。  
  
    ```  
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'  
    ```  
  
4.  按一下 \[**完成**\]。  
  
## 定義使用者介面  
 透過在 WPF 設計工具中修改 XAML，將數個按鈕加入至視窗。  在此逐步解說稍後的內容中，您會加入程式碼，讓使用者使用這些按鈕捲動及儲存產品記錄的變更。  
  
#### 定義視窗的使用者介面  
  
1.  在**方案總管**中，按兩下 MainWindow.xaml。  
  
     隨即在 WPF 設計工具中開啟視窗。  
  
2.  在設計工具的 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 檢視中，在 `<Grid>` 標記之間加入下列程式碼：  
  
    ```  
    <Grid.RowDefinitions>  
        <RowDefinition Height="75" />  
        <RowDefinition Height="625" />  
    </Grid.RowDefinitions>  
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>  
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>  
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>  
    ```  
  
3.  建置專案。  
  
## 建立資料繫結控制項  
 從 \[資料來源\] 視窗將 `Product` 資料表拖曳至 WPF 設計工具，以建立顯示客戶記錄的控制項。  
  
#### 建立資料繫結控制項  
  
1.  在 \[資料來源\] 視窗中，按一下 \[Product\] 節點的下拉式功能表，然後選取 \[詳細資料\]。  
  
2.  展開 \[Product\] 節點。  
  
3.  在此範例中，不會顯示某些欄位，因此請按下列節點旁邊的下拉式功能表，然後選取 \[無\]：  
  
    -   ProductCategoryID  
  
    -   ProductModelID  
  
    -   ThumbnailPhotoFileName  
  
    -   rowguid  
  
    -   ModifiedDate  
  
4.  按一下 \[ThumbNailPhoto\] 節點旁邊的下拉式功能表，並選取 \[影像\]。  
  
    > [!NOTE]
    >  根據預設，\[資料來源\] 視窗中表示圖片的項目，會將其預設控制項設定為 \[無\]。  這是因為圖片是以位元組陣列儲存在資料庫中，且位元組陣列可以包含任何項目，從簡單位元組陣列到大型應用程式的可執行檔。  
  
5.  從 \[資料來源\] 視窗將 \[Product\] 節點拖曳至包含按鈕的資料列底下的資料格列。  
  
     Visual Studio 會產生 XAML，其定義了一組繫結至 **Products** 資料表之資料的控制項。  此外還會產生載入資料的程式碼。  如需產生之 XAML 和程式碼的詳細資訊，請參閱 [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
6.  在設計工具中，按一下 \[Product ID\] 標籤旁邊的文字方塊。  
  
7.  在 \[屬性\] 視窗中，選取 **IsReadOnly** 屬性旁邊的核取方塊。  
  
## 巡覽產品記錄  
 加入可讓使用者使用 **\<** 及 **\>** 按鈕捲動產品記錄的程式碼。  
  
#### 讓使用者巡覽產品記錄  
  
1.  在設計工具中，按兩下視窗介面上的 **\<** 按鈕。  
  
     Visual Studio 會開啟程式碼後置檔案，並建立 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件的新 `backButton_Click` 事件處理常式。  
  
2.  修改 `Window_Loaded` 事件處理常式，使 `ProductViewSource`、`AdventureWorksLTDataSet` 和 `AdventureWorksLTDataSetProductTableAdapter` 位於方法之外，且整個表單都可以存取它們。  只將這些項目從全域宣告為表單，並以類似下列的方式在 `Window_Loaded` 事件處理常式中指派它們：  
  
     [!CODE [Data_WPFDATASET#1](../CodeSnippet/VS_Snippets_ProTools/data_wpfdataset#1)]  
  
3.  將下列程式碼加入至 `backButton_Click` 事件處理常式：  
  
     [!CODE [Data_WPFDATASET#2](../CodeSnippet/VS_Snippets_ProTools/data_wpfdataset#2)]  
  
4.  回到設計工具，然後按兩下 **\>** 按紐。  
  
5.  將下列程式碼加入至 `nextButton_Click` 事件處理常式：  
  
     [!CODE [Data_WPFDATASET#3](../CodeSnippet/VS_Snippets_ProTools/data_wpfdataset#3)]  
  
## 儲存產品記錄的變更  
 加入程式碼，讓使用者可以使用 \[儲存變更\] 按鈕儲存產品記錄的變更。  
  
#### 加入可儲存產品記錄變更的功能  
  
1.  在設計工具中，按兩下 \[儲存變更\] 按鈕。  
  
     Visual Studio 會開啟程式碼後置檔案，並建立 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件的新 `saveButton_Click` 事件處理常式。  
  
2.  將下列程式碼加入至 `saveButton_Click` 事件處理常式：  
  
     [!CODE [Data_WPFDATASET#4](../CodeSnippet/VS_Snippets_ProTools/data_wpfdataset#4)]  
  
    > [!NOTE]
    >  此範例使用 `TableAdapter` 的 `Save` 方法來儲存變更。  在此逐步解說中，這是適當的方法，因為只會變更一個資料表。  若您必須將變更儲存至多個資料表，可以改用 Visual Studio 以您的資料集所產生之 `TableAdapterManager` 的 `UpdateAll` 方法。  如需詳細資訊，請參閱[TableAdapterManager 概觀](../Topic/TableAdapterManager%20Overview.md)。  
  
## 測試應用程式  
 建置並執行應用程式。  驗證您是否可以檢視及更新產品記錄。  
  
#### 若要測試應用程式  
  
1.  請按 **F5**。  
  
     隨即建置應用程式並執行。  驗證下列各項：  
  
    -   文字方塊會從具有相片的第一個產品記錄顯示資料。  此產品具有產品 ID 713，以及名稱 **Long\-Sleeve Logo Jersey, S**。  
  
    -   您可以按一下 **\>** 或 **\<** 按鈕，巡覽其他產品記錄。  
  
2.  在其中一個產品記錄中，變更 **Size** 值，然後按一下 \[儲存變更\]。  
  
3.  關閉應用程式，然後在 Visual Studio 中按 **F5** 鍵，以重新啟動應用程式。  
  
4.  巡覽至您剛變更的產品記錄，確認變更已保存。  
  
5.  關閉應用程式。  
  
## 後續步驟  
 完成此逐步解說後，您可以執行下列相關的工作：  
  
-   學習如何使用 Visual Studio 中的 \[資料來源\] 視窗，將 WPF 控制項繫結至其他資料來源類型。  如需詳細資訊，請參閱[逐步解說：將 WPF 控制項繫結至 WCF 資料服務](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)。  
  
-   學習如何使用 Visual Studio 中的 \[資料來源\] 視窗，顯示 WPF 控制項中的相關資料 \(也就是具有父子關聯性中的資料\)。  如需詳細資訊，請參閱[逐步解說：顯示 WPF 應用程式中的相關資料](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)。  
  
## 請參閱  
 [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [如何：將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [使用 Visual Studio 中的資料集](../data-tools/dataset-tools-in-visual-studio.md)   
 [WPF 和 Silverlight 設計工具概觀](http://msdn.microsoft.com/zh-tw/570b7a5c-0c86-4326-a371-c9b63378fc62)   
 [資料繫結概觀](../Topic/Data%20Binding%20Overview.md)
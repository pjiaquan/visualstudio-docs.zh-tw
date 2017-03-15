---
title: "逐步解說：將 WPF 控制項繫結至 WCF 資料服務 | Microsoft Docs"
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
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
caps.latest.revision: 40
caps.handback.revision: 38
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逐步解說：將 WPF 控制項繫結至 WCF 資料服務
您將在此逐步解說中，建立包含資料繫結控制項的 WPF 應用程式。  這些控制項會繫結至封裝於 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]中的客戶記錄。  您也會加入按鈕，讓客戶可使用這些按鈕檢視及更新記錄。  
  
 這個逐步解說將說明下列工作：  
  
-   建立從 AdventureWorksLT 範例資料庫中的資料產生的實體資料模型。  
  
-   建立 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]，以將實體資料模型中的資料公開給 WPF 應用程式。  
  
-   從 \[資料來源\] 視窗將項目拖曳至 WPF 設計工具，以建立一組資料繫結控制項。  
  
-   建立可向前及向後巡覽客戶記錄的按鈕。  
  
-   建立按鈕，以將控制項中的資料變更儲存至 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]及基礎資料來源。  
  
     [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
-   對執行中的 SQL Server 或 SQL Server Express \(其中連結了 AdventureWorksLT 範例資料庫\) 執行個體的存取權。  您可以從 [CodePlex 網站](http://go.microsoft.com/fwlink/?linkid=87843) 下載 AdventureWorksLT 資料庫。  
  
 預先了解下列概念也有助於完成此逐步解說 \(但非必要\)：  
  
-   WCF 資料服務。  如需詳細資訊，請參閱[概觀](../Topic/WCF%20Data%20Services%20Overview.md)。  
  
-   [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]中的資料模型。  
  
-   實體資料模型及 ADO.NET Entity Framework。  如需詳細資訊，請參閱[Entity Framework 概觀](../Topic/Entity%20Framework%20Overview.md)。  
  
-   使用 WPF 設計工具。  如需詳細資訊，請參閱[WPF 和 Silverlight 設計工具概觀](http://msdn.microsoft.com/zh-tw/570b7a5c-0c86-4326-a371-c9b63378fc62)。  
  
-   WPF 資料繫結。  如需詳細資訊，請參閱[資料繫結概觀](../Topic/Data%20Binding%20Overview.md)。  
  
## 建立服務專案  
 建立 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]的專案以開始此逐步解說。  
  
#### 建立服務專案  
  
1.  啟動 Visual Studio。  
  
2.  在 \[檔案\] 功能表中，指向 \[新增\]，然後按一下 \[專案\]。  
  
3.  展開 \[Visual C\#\] 或 \[Visual Basic\]，然後選取 \[Web\]。  
  
4.  選取 \[ASP.NET Web 應用程式\] 專案範本。  
  
5.  在 \[名稱\] 方塊中，輸入 `AdventureWorksService`，然後按一下 \[確定\]。  
  
     Visual Studio 隨即建立 `AdventureWorksService` 專案。  
  
6.  在**方案總管**中的 **Default.aspx** 上按一下滑鼠右鍵，並選取 \[刪除\]。  在此逐步解說中不需要此檔案。  
  
## 建立服務的實體資料模型  
 若要使用 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]將資料公開給應用程式，您必須定義服務的資料模型。  [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]支援兩種類型的資料模型：實體資料模型及自訂資料模型，後者使用實作 <xref:System.Linq.IQueryable%601> 介面的 Common Language Runtime \(CLR\) 所定義。  在此逐步解說中，您要建立資料模型的實體資料模型。  
  
#### 建立實體資料模型  
  
1.  在 \[專案\] 功能表中，按一下 \[加入新項目\]。  
  
2.  在 \[已安裝的範本\] 清單中，按一下 \[資料\]，然後選取 \[ADO.NET 實體資料模型\] 專案項目。  
  
3.  將名稱變更為 `AdventureWorksModel.edmx`，然後按一下 \[加入\]。  
  
     \[實體資料模型精靈\] 隨即開啟。  
  
4.  在 \[選擇模型內容\] 頁面中，按一下 \[從資料庫產生\]，然後按 \[下一步\]。  
  
5.  在 \[選擇資料連接\] 頁面中，選取下列其中一個選項：  
  
    -   若下拉式清單中有提供 AdventureWorksLT 範例資料庫的資料連接，請選取此資料連接。  
  
         \-或\-  
  
    -   按一下 \[新增連接\]，建立與 AdventureWorksLT 資料庫的連接。  
  
6.  在 \[選擇資料連接\] 頁面中，確定已選取 \[將 App.Config 中的實體連接設定儲存為\] 選項，然後按 \[下一步\]。  
  
7.  在 \[選擇您的資料庫物件\] 頁面中，展開 \[資料表\]，然後選取 **SalesOrderHeader** 資料表。  
  
8.  按一下 \[**完成**\]。  
  
## 建立服務  
 建立 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]，以將實體資料模型中的資料公開給 WPF 應用程式。  
  
#### 建立服務  
  
1.  在 \[專案\] 功能表中，選取 \[加入新項目\]。  
  
2.  在 \[已安裝的範本\] 清單中，按一下 \[Web\]，然後選取 \[WCF 資料服務\] 專案項目。  
  
3.  在 \[名稱\] 方塊中，輸入 `AdventureWorksService.svc`，然後按一下 \[加入\]。  
  
     Visual Studio 隨即會將 `AdventureWorksService.svc` 加入至專案。  
  
## 設定服務  
 您必須設定服務，以處理您建立的實體資料模型。  
  
#### 設定服務  
  
1.  在 `AdventureWorks.svc` 程式碼檔案中，將 `AdventureWorksService` 類別宣告替換為下列程式碼。  
  
     [!code-cs[Data_WPFWCF#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_1.cs)]
     [!code-vb[Data_WPFWCF#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_1.vb)]  
  
     此程式碼會更新 `AdventureWorksService` 類別，使其衍生自處理您實體資料模型中 `AdventureWorksLTEntities` 物件內容類別的 <xref:System.Data.Services.DataService%601>。  該程式碼也會更新 `InitializeService` 方法，允許服務的用戶端對 `SalesOrderHeader` 實體具有完整的讀取\/寫入存取權。  
  
2.  建置專案，並確認專案建置無誤。  
  
## 建立 WPF 用戶端應用程式  
 若要從 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]顯示資料，請使用以服務為基礎的資料來源，建立新的 WPF 應用程式。  稍後您將在此逐步解說中，將資料繫結控制項加入至應用程式。  
  
#### 建立 WPF 用戶端應用程式  
  
1.  在**方案總管**中，在方案上按一下滑鼠右鍵，再按一下 \[加入\]，然後選取 \[新增專案\]。  
  
2.  在 \[新增專案\] 對話方塊中，展開 \[Visual C\#\] 或 \[Visual Basic\]，然後選取 \[視窗\]。  
  
3.  選取 \[WPF 應用程式\] 專案範本。  
  
4.  在 \[名稱\] 方塊中，輸入 `AdventureWorksSalesEditor`，然後按一下 \[確定\]。  
  
     Visual Studio 隨即將 `AdventureWorksSalesEditor` 專案加入至方案。  
  
5.  按一下 \[**資料**\] 功能表上的 \[**顯示資料來源**\]。  
  
     \[資料來源\] 視窗隨即開啟。  
  
6.  在 \[**資料來源**\] 視窗中，按一下 \[**加入新資料來源**\]。  
  
     \[**資料來源組態精靈**\] 隨即開啟。  
  
7.  在精靈的 \[選擇資料來源類型\] 頁面中，選取 \[服務\]，然後按 \[下一步\]。  
  
8.  在 \[加入服務參考\] 對話方塊中，按一下 \[探索\]。  
  
     Visual Studio 會搜尋可用服務的目前方案，並將 `AdventureWorksService.svc` 加入至 \[服務\] 方塊的可用服務清單中。  
  
9. 在 \[命名空間\] 方塊中，輸入 `AdventureWorksService`。  
  
10. 在 \[服務\] 方塊中，按一下 **AdventureWorksService.svc**，然後按一下 \[確定\]。  
  
     Visual Studio 會下載服務資訊，然後傳回 \[資料來源組態精靈\]。  
  
11. 選擇 \[加入服務參考\] 頁面中，按一下 \[完成\]。  
  
     Visual Studio 會將代表服務所傳回之資料的節點，加入至 \[資料來源\] 視窗。  
  
## 定義視窗的使用者介面  
 透過在 WPF 設計工具中修改 XAML，將數個按鈕加入至視窗。  在此逐步解說的稍後內容中，您會加入程式碼，讓使用者使用這些按鈕檢視及更新銷售記錄。  
  
#### 建立視窗配置  
  
1.  在**方案總管**中，按兩下 MainWindow.xaml。  
  
     隨即會在 WPF 設計工具中開啟視窗。  
  
2.  在設計工具的 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 檢視中，在 `<Grid>` 標記之間加入下列程式碼：  
  
    ```  
    <Grid.RowDefinitions>  
        <RowDefinition Height="75" />  
        <RowDefinition Height="525" />  
    </Grid.RowDefinitions>  
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>  
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>  
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>  
    ```  
  
3.  建置專案。  
  
## 建立資料繫結控制項  
 從 \[資料來源\] 視窗將 \[SalesOrderHeaders\] 節點拖曳至設計工具，以建立顯示客戶記錄的控制項。  
  
#### 建立資料繫結控制項  
  
1.  在 \[資料來源\] 視窗中，按一下 \[SalesOrderHeaders\] 節點的下拉式功能表，然後選取 \[詳細資料\]。  
  
2.  展開 \[SalesOrderHeaders\] 節點。  
  
3.  在此範例中，不會顯示某些欄位，因此請按下列節點旁邊的下拉式功能表，然後選取 \[無\]：  
  
    -   **CreditCardApprovalCode**  
  
    -   **ModifiedDate**  
  
    -   **OnlineOrderFlag**  
  
    -   **RevisionNumber**  
  
    -   **rowguid**  
  
     此動作可避免 Visual Studio 在下一個步驟中建立這些節點的資料繫結控制項。  在此逐步解說中，會假設使用者不需要看到此資料。  
  
4.  從 \[資料來源\] 視窗將 \[SalesOrderHeaders\] 節點拖曳至包含按鈕的資料列底下的資料格列。  
  
     Visual Studio 會產生 XAML 和程式碼，其可建立一組繫結至 **Products** 資料表之資料的控制項。  如需產生之 XAML 和程式碼的詳細資訊，請參閱 [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
5.  在設計工具中，按一下 \[Customer ID\] 標籤旁邊的文字方塊。  
  
6.  在 \[屬性\] 視窗中，選取 **IsReadOnly** 屬性旁邊的核取方塊。  
  
7.  為下列每個文字方塊設定 **IsReadOnly** 屬性：  
  
    -   **Purchase Order Number**  
  
    -   **Sales Order ID**  
  
    -   **Sales Order Number**  
  
## 從服務載入資料  
 使用服務 Proxy 物件從服務載入銷售資料，然後將傳回的資料指派給 WPF 視窗中 <xref:System.Windows.Data.CollectionViewSource> 的資料來源。  
  
#### 從服務載入資料  
  
1.  在設計工具中，按兩下文字 **MainWindow**，以建立 `Window_Loaded` 事件處理常式。  
  
2.  以下列程式碼取代事件處理常式。  確認您是使用開發電腦的本機主機位址，取代此程式碼中的 *localhost* 位址。  
  
     [!code-cs[Data_WPFWCF#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_2.cs)]
     [!code-vb[Data_WPFWCF#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_2.vb)]  
  
## 巡覽銷售記錄  
 加入可讓使用者使用 **\<** 及 **\>** 按鈕捲動銷售記錄的程式碼。  
  
#### 讓使用者巡覽銷售記錄  
  
1.  在設計工具中，按兩下視窗介面上的 **\<** 按鈕。  
  
     Visual Studio 會開啟程式碼後置檔案，並建立 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件的新 `backButton_Click` 事件處理常式。  
  
2.  將下列程式碼加入至產生的 `backButton_Click` 事件處理常式：  
  
     [!code-cs[Data_WPFWCF#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_3.cs)]
     [!code-vb[Data_WPFWCF#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_3.vb)]  
  
3.  回到設計工具，然後按兩下 **\>** 按紐。  
  
     Visual Studio 會開啟程式碼後置檔案，並建立 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件的新 `nextButton_Click` 事件處理常式。  
  
4.  將下列程式碼加入至產生的 `nextButton_Click` 事件處理常式：  
  
     [!code-cs[Data_WPFWCF#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_4.cs)]
     [!code-vb[Data_WPFWCF#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_4.vb)]  
  
## 儲存銷售記錄的變更  
 加入程式碼，讓使用者可以使用 \[儲存變更\] 按鈕檢視及儲存銷售記錄的變更。  
  
#### 加入可儲存銷售記錄變更的功能  
  
1.  在設計工具中，按兩下 \[儲存變更\] 按鈕。  
  
     Visual Studio 會開啟程式碼後置檔案，並建立 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件的新 `saveButton_Click` 事件處理常式。  
  
2.  將下列程式碼加入至 `saveButton_Click` 事件處理常式。  
  
     [!code-cs[Data_WPFWCF#5](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_5.cs)]
     [!code-vb[Data_WPFWCF#5](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_5.vb)]  
  
## 測試應用程式  
 建置並執行應用程式，以確認您可以檢視及更新客戶記錄。  
  
#### 若要測試應用程式  
  
1.  在 \[建置\] 功能表中，按一下 \[建置方案\]。  確認方案建置無誤。  
  
2.  按 **CTRL\+F5** 鍵。  
  
     Visual Studio 會啟動 **AdventureWorksService** 專案且不進行偵錯。  
  
3.  在**方案總管**中，在 **AdventureWorksSalesEditor** 上按一下滑鼠右鍵。  
  
4.  在內容功能表的 \[偵錯\] 下，按一下 \[開始新執行個體\]。  
  
     應用程式隨即執行。  驗證下列各項：  
  
    -   這些文字方塊是從第一筆銷售記錄 \(具有銷售訂單 ID **71774**\) 的資料顯示不同的欄位。  
  
    -   您可以按一下 **\>** 或 **\<** 按鈕，巡覽其他銷售記錄。  
  
5.  在其中一個銷售記錄中，在 \[註解\] 方塊中輸入部分文字，然後按一下 \[儲存變更\]。  
  
6.  關閉應用程式，然後從 Visual Studio 再次啟動應用程式。  
  
7.  巡覽至您變更過的銷售記錄，並確認變更在您關閉及重新開啟應用程式之後仍然存在。  
  
8.  關閉應用程式。  
  
## 後續步驟  
 完成此逐步解說後，您可以執行下列相關的工作：  
  
-   學習如何使用 Visual Studio 中的 \[資料來源\] 視窗，將 WPF 控制項繫結至其他資料來源類型。  如需詳細資訊，請參閱[逐步解說：將 WPF 控制項繫結到資料集](../data-tools/bind-wpf-controls-to-a-dataset.md)。  
  
-   學習如何使用 Visual Studio 中的 \[資料來源\] 視窗，顯示 WPF 控制項中的相關資料 \(也就是具有父子關聯性中的資料\)。  如需詳細資訊，請參閱[逐步解說：顯示 WPF 應用程式中的相關資料](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)。  
  
## 請參閱  
 [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [如何：將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [逐步解說：將 WPF 控制項繫結到資料集](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [概觀](../Topic/WCF%20Data%20Services%20Overview.md)   
 [Entity Framework 概觀](../Topic/Entity%20Framework%20Overview.md)   
 [WPF 和 Silverlight 設計工具概觀](http://msdn.microsoft.com/zh-tw/570b7a5c-0c86-4326-a371-c9b63378fc62)   
 [資料繫結概觀](../Topic/Data%20Binding%20Overview.md)
---
title: "逐步解說：在執行階段更新功能區中的控制項 | Microsoft Docs"
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
  - "控制項 [Visual Studio 中的 Office 程式開發], 功能區"
  - "動態功能表 [Visual Studio 中的 Office 程式開發]"
  - "功能區 [Visual Studio 中的 Office 程式開發], 控制項"
  - "功能區 [Visual Studio 中的 Office 程式開發], 動態功能表"
  - "功能區 [Visual Studio 中的 Office 程式開發], 更新"
  - "更新控制項控制項"
ms.assetid: ed80790f-3f95-47e4-8a41-872588a8ca07
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# 逐步解說：在執行階段更新功能區中的控制項
  這個逐步解說示範如何使用功能區物件模型，在功能區載入至 Office 應用程式之後，更新功能區上的控制項。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 此範例會提取 Northwind 範例資料庫的資料，填入 Microsoft Office Outlook 中的下拉式方塊和功能表。  您在這些控制項中選取的項目，會自動填入電子郵件的 \[收件人\] 和 \[主旨\] 等欄位。  
  
 這個逐步解說將說明下列工作：  
  
-   建立新的 Outlook VSTO 增益集專案。  
  
-   設計自訂的功能區群組。  
  
-   將自訂群組加入內建索引標籤。  
  
-   在執行階段更新功能區上的控制項。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置：  您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Outlook  
  
## 建立新的 Outlook VSTO 增益集專案  
 首先，建立 Outlook VSTO 增益集專案。  
  
#### 建立新的 Outlook VSTO 增益集專案  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中建立名為 Ribbon\_Update\_At\_Runtime 的 Outlook VSTO 增益集專案。  
  
2.  在 \[新增專案\] 對話方塊中，選取 \[為方案建立目錄\]。  
  
3.  將專案儲存至預設的專案目錄。  
  
     如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
## 設計自訂的功能區群組  
 此範例中的功能區，會在使用者撰寫新郵件時出現。  若要建立功能區自訂群組，請先在專案中加入功能區項目，然後在功能區設計工具中設計群組。  這個自訂群組會從資料庫提取姓名和訂單記錄，協助您產生給客戶的追蹤電子郵件。  
  
#### 設計自訂群組  
  
1.  在 \[專案\] 功能表中，按一下 \[加入新項目\]。  
  
2.  選取 \[**加入新項目**\] 對話方塊中的 \[**功能區 \(視覺化設計工具\)**\]。  
  
3.  將新功能區的名稱變更為 **CustomerRibbon**，然後按一下 \[加入\]。  
  
     **CustomerRibbon.cs** 或 **CustomerRibbon.vb** 檔案會在功能區設計工具中開啟，並顯示預設的索引標籤和群組。  
  
4.  按一下選取功能區設計工具。  
  
5.  在 \[屬性\] 視窗中，按一下 \[RibbonType\] 屬性旁的下拉箭號，然後再按一下 \[Microsoft.Outlook.Mail.Compose\]。  
  
     這可讓功能區於使用者在 Outlook 中撰寫新郵件時出現。  
  
6.  在功能區設計工具中，按一下選取 \[Group1\]。  
  
7.  在 \[屬性\] 視窗中，將 \[Label\] 設為 Customer Purchases。  
  
8.  從 \[工具箱\] 的 \[Office 功能區控制項\] 索引標籤，將 \[ComboBox\] 拖曳到 \[Customer Purchases\] 群組。  
  
9. 按一下選取 \[CheckBox1\]。  
  
10. 在 \[屬性\] 視窗中，將 \[Label\] 設為 Customers。  
  
11. 從 \[工具箱\] 的 \[Office 功能區控制項\] 索引標籤，將 \[功能表\] 拖曳到 \[Customer Purchases\] 群組。  
  
12. 在 \[屬性\] 視窗中，將 \[Label\] 設為 Product Purchased。  
  
13. 將 \[動態\] 設為 **true**。  
  
     在功能區載入至 Office 應用程式之後，這可讓您在執行階段加入和移除功能表上的控制項。  
  
## 將自訂群組加入內建索引標籤  
 內建索引標籤是已經在 Outlook 總管或偵測器之功能區的索引標籤。  在這個程序中，您要將自訂群組加入內建索引標籤，然後指定自訂群組在索引標籤上的位置。  
  
#### 將自訂群組加入內建索引標籤  
  
1.  按一下選取 \[TabAddins \(內建\)\] 索引標籤。  
  
2.  在 \[屬性\] 視窗中展開 \[ControlId\] 屬性，然後將 \[OfficeId\] 設為 \[TabNewMailMessage\]。  
  
     這會將 \[客戶購買\] 群組加入新郵件功能區的 \[郵件\] 索引標籤。  
  
3.  按一下選取 \[客戶購買\]群組。  
  
4.  在 \[屬性\] 視窗中，展開 \[位置\] 屬性，按一下 \[PositionType\] 屬性旁的下拉箭號，然後再按一下 \[BeforeOfficeId\]。  
  
5.  將 \[OfficeId\] 屬性設為 GroupClipboard。  
  
     這會將 \[客戶購買\] 群組放在 \[郵件\] 索引標籤的 \[剪貼簿\] 群組前面。  
  
## 建立資料來源  
 使用 \[資料來源\] 視窗將型別資料集加入專案。  
  
#### 若要建立資料來源  
  
1.  在 \[**資料**\] 功能表上，請按一下 \[**加入新資料來源**\]。  
  
     這會啟動 \[資料來源組態精靈\]。  
  
2.  選取 \[資料庫\]，然後按一下 \[下一步\]。  
  
3.  選取 \[資料集\]，然後按一下 \[下一步\]。  
  
4.  選取 Northwind 範例 Microsoft SQL Server Compact 4.0 資料庫的資料連線，或使用 \[新增連接\] 按鈕加入新連線。  
  
5.  選取或建立連接之後，請按一下 \[下一步\]。  
  
6.  按一下 \[下一步\] 儲存連接字串。  
  
7.  展開 \[選擇您的資料庫物件\] 頁面上的 \[資料表\]。  
  
8.  選取下列每個資料表旁的核取方塊：  
  
    1.  **Customers**  
  
    2.  **訂單詳細資料**  
  
    3.  **訂單**  
  
    4.  **產品**  
  
9. 按一下 \[**完成**\]。  
  
## 在執行階段更新自訂群組中的控制項  
 使用功能區物件模型執行下列工作：  
  
-   將客戶名稱加入 \[客戶\] 下拉式方塊。  
  
-   在代表銷售訂單和賣出產品的 \[購買的產品\] 功能表中，加入功能表和按鈕控制項。  
  
-   使用 \[客戶\] 下拉式方塊和 \[購買的產品\] 功能表中的資料，填入新郵件的 To、Subject 和 Body 欄位。  
  
#### 使用功能區物件模型更新自訂群組中的控制項  
  
1.  在 \[專案\] 功能表上，按一下 \[加入參考\]。  
  
2.  按一下 \[加入參考\] 對話方塊中的 \[.NET\] 索引標籤，接著選取 \[System.Data.Linq\] 組件，再按一下 \[確定\]。  
  
     這個組件包含使用 Language\-Integrated Queries \(LINQ\) 的類別。  您會使用 LINQ，以 Northwind 資料庫的資料填入自訂群組中的控制項。  
  
3.  在 \[方案總管\] 中，按一下選取 \[CustomerRibbon.cs\] 或 \[CustomerRibbon.vb\]。  
  
4.  在 \[檢視\] 功能表上，按一下 \[程式碼\]。  
  
     功能區程式碼檔案隨即在程式碼編輯器中開啟。  
  
5.  在功能區程式碼檔的頂端加入下列陳述式。  這些陳述式可讓您輕鬆存取 LINQ 命名空間和 Outlook 主要 interop 組件 \(PIA\) 的命名空間。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#1)]  
  
6.  在 CustomerRibbon 類別內加入下列程式碼。  這個程式碼會宣告資料表和資料表配接器，您會用它們儲存來自 Northwind 資料庫之客戶、訂單、訂單詳細資料和產品資料表的資訊。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#2)]  
  
7.  在 `CustomerRibbon` 類別中加入下列程式碼區塊。  這個程式碼會在執行階段，加入建立功能區控制項的三種 helper 方法。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#3)]  
  
8.  以下列程式碼取代 `CustomerRibbon_Load` 事件處理常式方法。  這個程式碼使用 LINQ 查詢執行下列工作：  
  
    -   使用 Northwind 資料庫中 20 名客戶的識別碼和名稱填入 \[客戶\] 下拉式方塊。  
  
    -   呼叫 `PopulateSalesOrderInfo` helper 方法。  這個方法會以與目前選取客戶有關的銷售訂單號碼，更新 \[購買的產品\] 功能表。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#4)]  
  
9. 將下列程式碼加入 `CustomerRibbon` 類別。  這個程式碼使用 LINQ 查詢執行下列工作：  
  
    -   在與所選客戶相關的每筆銷售訂單的 \[購買的產品\] 功能表加入子功能表。  
  
    -   在與銷售訂單相關之產品的每個子功能表加入按鈕。  
  
    -   在每個按鈕加入事件處理常式。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#6)]  
  
10. 在 \[方案總管\] 中，按兩下功能區程式碼檔案。  
  
     螢幕設計工具隨即開啟。  
  
11. 在功能區設計工具中，按兩下 \[客戶\] 下拉式方塊。  
  
     功能區程式碼檔案會在程式碼編輯器中開啟，且 `ComboBox1_TextChanged` 事件處理常式隨即出現。  
  
12. 以下列程式碼取代 `ComboBox1_TextChanged` 事件處理常式。  這個程式碼會執行下列工作：  
  
    -   呼叫 `PopulateSalesOrderInfo` helper 方法。  這個方法會以與選取客戶有關的銷售訂單，更新 \[購買的產品\] 功能表。  
  
    -   呼叫 `PopulateMailItem` helper 方法，並在目前的文字，也就是選取的客戶名稱中傳遞。  這個方法會填入新郵件的 To、Subject 和 Body 欄位。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#5)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#5)]  
  
13. 將下列 Click 事件處理常式加入 `CustomerRibbon` 類別。  這個程式碼會將選取的產品名稱加入新郵件的 Body 欄位。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#8)]  
  
14. 將下列程式碼加入 `CustomerRibbon` 類別。  這個程式碼會執行下列工作：  
  
    -   使用目前選取客戶的電子郵件地址填入新郵件的 To 行。  
  
    -   在新郵件的 Subject 和 Body 欄位加入文字。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#7)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#7)]  
  
## 測試自訂群組中的控制項  
 當您在 Outlook 中開啟新的郵件表單時，名為 \[客戶購買\] 的自訂群組即會出現在功能區的 \[郵件\] 索引標籤上。  
  
 若要建立客戶追蹤電子郵件，請選取一位客戶，然後選取該客戶購買的產品。  \[客戶購買\] 群組中的控制項會在執行階段以 Northwind 資料庫中的資料更新。  
  
#### 測試自訂群組中的控制項  
  
1.  請按 F5 執行您的專案。  
  
     Outlook 啟動。  
  
2.  開啟 Outlook 的 \[檔案\] 功能表，指向 \[新增\]，然後按一下 \[郵件\]。  
  
     即會發生下列動作：  
  
    -   新的郵件偵測器視窗出現。  
  
    -   在功能區的 \[郵件\] 索引標籤上，\[客戶購買\] 群組出現在 \[剪貼簿\] 群組的前面。  
  
    -   群組的 \[客戶\] 下拉式方塊會以 Northwind 資料庫中的客戶名稱更新。  
  
3.  在功能區的 \[郵件\] 索引標籤上，在 \[客戶購買\] 群組中，從 \[客戶\] 下拉式方塊選取一位客戶。  
  
     即會發生下列動作：  
  
    -   \[購買的產品\] 功能表會更新以顯示所選客戶的每筆銷售訂單。  
  
    -   每個銷售訂單的子功能表都會更新以顯示該訂單中購買的產品。  
  
    -   選取的客戶電子郵件地址會加入郵件的 \[收件人\] 行，並在郵件的主旨及本文中填入文字。  
  
4.  按一下 \[購買的產品\]\] 功能表，指向任一銷售訂單，然後按一下 銷售訂單中的產品。  
  
     產品名稱會加入郵件的本文。  
  
## 後續步驟  
 您可以透過下列主題，進一步了解自訂 Office UI 的方式：  
  
-   將內容為主的 UI 加入至任何文件層級的自訂。  如需詳細資訊，請參閱[執行窗格概觀](../vsto/actions-pane-overview.md)。  
  
-   展開標準或自訂的 Microsoft Office Outlook 表單。  如需詳細資訊，請參閱[逐步解說：設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)。  
  
-   將自訂工作窗格加入 Outlook。  如需詳細資訊，請參閱[自訂工作窗格](../vsto/custom-task-panes.md)。  
  
## 請參閱  
 [在執行階段存取功能區](../vsto/accessing-the-ribbon-at-run-time.md)   
 [功能區概觀](../vsto/ribbon-overview.md)   
 [Language\-integrated Query \(LINQ\)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)   
 [如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [功能區設計工具](../vsto/ribbon-designer.md)   
 [逐步解說：使用功能區設計工具建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [功能區物件模型概觀](../vsto/ribbon-object-model-overview.md)   
 [自訂 Outlook 的功能區](../vsto/customizing-a-ribbon-for-outlook.md)   
 [如何：變更功能區索引標籤的位置](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [如何：自訂內建索引標籤](../vsto/how-to-customize-a-built-in-tab.md)   
 [如何：將控制項加入至 Backstage 檢視](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [如何：將功能區設計工具的功能區匯出到功能區 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [如何：顯示增益集使用者介面錯誤](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  
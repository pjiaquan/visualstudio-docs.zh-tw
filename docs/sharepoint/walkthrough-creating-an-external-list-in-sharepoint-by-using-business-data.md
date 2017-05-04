---
title: "逐步解說：使用商務資料在 SharePoint 中建立外部清單 | Microsoft Docs"
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
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 程式開發]，網頁組件中的商務資料"
  - "BDC [Visual Studio 中的 SharePoint 程式開發]，外部清單"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 程式開發]，SharePoint 清單中的商務資料"
  - "BDC [Visual Studio 中的 SharePoint 程式開發]，SharePoint 清單中的商務資料"
  - "BDC [Visual Studio 中的 SharePoint 程式開發]，網頁組件中的商務資料"
  - "BDC [Visual Studio 中的 SharePoint 程式開發]，實體後援清單"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 程式開發]，實體後援清單"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 程式開發]，外部清單"
ms.assetid: 046cf234-705a-4a6f-91f8-c5c569ae0dd0
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# 逐步解說：使用商務資料在 SharePoint 中建立外部清單
  商務資料連接 \(BDC\) 服務可讓 SharePoint 顯示後端伺服器應用程式、Web 服務和資料庫中的商務資料。  
  
 本逐步解說將示範如何為傳回範例資料庫中聯絡人相關資料的 BDC 服務建立模型，  然後您將使用此模型在 SharePoint 中建立外部清單。  
  
 這個逐步解說將說明下列工作：  
  
-   建立專案。  
  
-   在模型中新增實體。  
  
-   加入搜尋方法。  
  
-   加入特定搜尋方法。  
  
-   測試專案。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的 Windows 和 SharePoint 版本。  如需詳細資訊，請參閱[開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]、[!INCLUDE[vsUltLong](../sharepoint/includes/vsultlong-md.md)] 或 [!INCLUDE[vsPreLong](../sharepoint/includes/vsprelong-md.md)]。  
  
-   AdventureWorks 範例資料庫的存取權限。  如需如何安裝 AdventureWorks 資料庫的詳細資訊，請參閱 [SQL Server 範例資料庫](http://go.microsoft.com/fwlink/?LinkID=117483)。  
  
## 建立包含 BDC 模型的專案  
  
#### 若要建立包含 BDC 模型的專案  
  
1.  在 Visual Studio的功能表列，選擇 \[ **檔案**\]， **新增**， **專案**。  
  
     \[**新增專案**\] 對話方塊隨即開啟。  
  
2.  在 \[**Visual C\#**\] 或 \[**Visual Basic**\] 底下，展開的 \[**SharePoint**\] 節點，然後按一下 \[**2010**\] 項目。  
  
3.  在 \[**範本**\] 窗格中，選擇 \[**SharePoint 2010 \-**\] 項目，命名為 AdventureWorksTest 然後選擇 \[**確定**\] 按鈕。  
  
     \[**SharePoint 自訂精靈**\] 隨即出現。  在這個精靈，指定用來偵錯專案的網站以及設定方案的信任層級。  
  
4.  選取 \[**部署為陣列方案**\] 選項按鈕設定信任層級。  
  
5.  選擇 \[**完成**\] 按鈕以接受預設的本機 SharePoint 網站。  
  
6.  在 \[**方案總管**\] 中選擇 SharePoint 專案節點。  
  
7.  在功能表列中，選擇 \[**專案**\]、\[**加入新項目**\]。  
  
     \[**加入新項目**\] 對話方塊隨即開啟。  
  
8.  在 \[**範本**\] 窗格中，選取 \[**商務資料連接模型 \(僅限陣列方案\)**\]，將專案命名為 AdventureWorksContacts，然後選擇 \[**加入**\] 按鈕。  
  
## 在專案中加入資料存取類別  
  
#### 若要在專案中加入資料存取類別  
  
1.  在選單條上選擇 \[**工具**\] ，按一下 \[**連接至資料庫**\]。  
  
     \[**加入連接**\] 對話方塊隨即開啟。  
  
2.  加入 SQL Server AdventureWorks 範例資料庫的連接。  
  
     如需詳細資訊，請參閱[Add\/Modify Connection \(Microsoft SQL Server\)](http://msdn.microsoft.com/zh-tw/fa400910-26c3-4df7-b9d1-115e688b4ea3)。  
  
3.  在 \[**方案總管**\] 中選擇專案節點。  
  
4.  在功能表列中，選擇 \[**專案**\]、\[**加入新項目**\]。  
  
5.  在 \[**已安裝的範本**\] 窗格中選取 \[**資料**\] 節點。  
  
6.  在 \[**範本**\] 窗格中選取 \[**LINQ to SQL 類別**\]。  
  
7.  在 \[**名稱**\] 文字方塊中指定 specify AdventureWorks 輸入 TestGames.cpp，然後選擇 \[**新增**\] 按鈕。  
  
     專案中隨即加入一個 .dbml 檔，並開啟物件關聯式設計工具 \(O\/R 設計工具\)。  
  
8.  在功能表上，選擇 \[**檢視**\]，\[**伺服器總管**\]。  
  
9. 在 \[**伺服器總管**\] 中展開表示 AdventureWorks 範例資料庫的節點，然後再展開 \[**資料表**\] 節點。  
  
10. 將 \[**Contact \(Person\)**\] 資料表加入至 O\/R 設計工具上。  
  
     實體類別隨即建立並出現在設計介面上。  這個實體類別的屬性會對應至 \[Contact \(Person\)\] 資料表中的資料行。  
  
## 從 BDC 模型中移除預設實體  
 \[**商務資料連線模型**\] 專案會將名為 Entity1 的預設實體新增至模型，  請移除這個實體。  稍後，您將加入新的實體。  在一開始就使用空模型，可減少完成逐步解說所需的步驟數目。  
  
#### 若要從模型中移除預設實體  
  
1.  在 \[**方案總管**\] 中展開 \[**BdcModel1**\] 節點，然後打開 \[BdcModel1.bdcm\] 檔案。  
  
2.  商務資料連接模型檔案隨即在 \[BDC 設計工具\] 中開啟。  
  
3.  在設計工具中，開啟 \[**Entity1**\] 節點的捷徑功能表，然後選擇 \[**刪除**\]。  
  
4.  在 \[**方案總管**\] 中，開啟 Entity1.vb \(Visual Basic\) 或 Entity1.cs 的捷徑功能表 \(在 C\# 中\)，然後選取 \[**刪除**\]。  
  
5.  開啟 Entity1Service.vb \(Visual Basic\) 或 Entity1Service.cs 的捷徑功能表 \(在 C\# 中\)，然後選取 \[**刪除**\]。  
  
## 在模型中新增實體  
 將模型新增至實體。  您可以將實體從 Visual Studio \[**工具箱**\] 加入至 BDC 設計工具上。  
  
#### 若要在模型中新增實體  
  
1.  在功能表列上選擇 \[**檢視**\]、\[**工具箱**\]。  
  
2.  從 \[**工具箱**\] 的 \[**BusinessDataConnectivity**\] 索引標籤中，把一個**實體**加入至 BDC 設計工具。  
  
     新實體隨即出現在設計工具中。  Visual Studio 會將檔案加入至名為 EntityService.vb \(使用 Visual Basic 時\) 或 EntityService.cs \(使用 C\# 時\) 的專案。  
  
3.  在功能表上選擇 \[**檢視**\]、\[**屬性**\] 、\[**視窗**\]。  
  
4.  在 \[**屬性**\] 視窗中，將 \[**Name**\] 屬性設定為 Contact。  
  
5.  在設計工具中，開啟實體的捷徑功能表，選擇 \[**新增**\]，然後選擇 \[**識別項**\]。  
  
     新識別項隨即出現在實體上。  
  
6.  在 \[**屬性視窗**\] 中，將識別項的名稱變更為 ContactID。  
  
7.  在 \[**輸入名稱**\] 清單中，選取 \[**System.Int32**\]。  
  
## 加入特定搜尋方法  
 若要讓 BDC 服務顯示特定的連絡人，您必須加入「特定搜尋」方法。  當使用者在清單中選取項目，然後選擇 \[功能區\] 中的 \[**檢視項目**\] 按鈕時，BDC 服務便會呼叫特定搜尋方法。  
  
 請使用 \[**BDC 方法詳細資料**\] 視窗，在 Contact 實體中加入特定搜尋方法。  若要傳回特定實體，請在方法中加入程式碼。  
  
#### 若要加入特定搜尋方法  
  
1.  在 BDC 設計工具上選取 \[**Contact**\] 實體。  
  
2.  在功能表列上，選擇 \[**檢視**\]，\[**其他視窗**\]， \[**BDC 方法詳細資料**\]。  
  
     \[BDC 方法詳細資料\] 視窗隨即開啟。  
  
3.  在 \[**加入方法**\] 清單中，選取 \[**建立特定搜尋方法**\]。  
  
     Visual Studio 會將下列項目加入至模型。  這些項目會顯示在 \[**BDC 方法詳細資料**\] 視窗中。  
  
    -   名為 ReadItem 的方法。  
  
    -   此方法的輸入參數。  
  
    -   方法的傳回參數。  
  
    -   各個參數的型別描述元。  
  
    -   此方法的方法執行個體。  
  
4.  在 \[**BDC 方法詳細資料**\] 視窗中，開啟針對 \[**聯絡人**\]型別描述元而顯示的下拉式清單，然後選擇 \[ **編輯**\]。  
  
     \[**BDC 總管**\] 可讓您以階層方式檢視和打開模型。  
  
5.  在 \[**屬性**\] 視窗中，按一下 \[**TypeName**\] 屬性旁邊的開啟清單中，選取 \[**本專案**\] 索引標籤，然後選取 \[**連絡人**\] 屬性。  
  
6.  在 \[**BDC 總管**\] 中，開啟\[**連絡人**\]型別描述元的捷徑功能表，然後選擇 \[**加入型別描述元**\]。  
  
     名為 \[**TypeDescriptor1**\] 的新型別描述元隨即在 \[**BDC 總管**\] 中顯示。  
  
7.  在 \[**屬性視窗**\] 中，將 \[**名稱**\] 屬性設定為 **ContactID**。  
  
8.  在 \[**TypeName**\] 屬性旁邊的開啟清單，然後選取 \[**Int32**\]。  
  
9. 在 \[**識別項**\] 屬性旁邊的開啟清單，然後選取 **ContactID**。  
  
10. 重複步驟 6，為下列各個欄位建立型別描述元。  
  
    |名稱|類型名稱|  
    |--------|----------|  
    |FirstName|System.String|  
    |LastName|System.String|  
    |Phone|System.String|  
    |EmailAddress|System.String|  
    |EmailPromotion|System.Int32|  
    |NameStyle|System.Boolean|  
    |PasswordHash|System.String|  
    |PasswordSalt|System.String|  
  
11. 在 BDC 設計工具的 \[**Contact**\] 實體上，打開 \[**ReadItem**\] 方法。  
  
     Contact 服務程式碼檔案隨即在 \[程式碼編輯器\] 中開啟。  
  
12. 在 `ContactService` 類別中，使用下列程式碼取代 `ReadItem` 方法。  這個程式碼會執行下列工作：  
  
    -   從 AdventureWorks 資料庫的 \[連絡人\] 資料表擷取記錄。  
  
    -   將 Contact 實體傳回至 BDC 服務。  
  
    > [!NOTE]  
    >  將 `ServerName` 欄位的值替換成您的伺服器名稱。  
  
     [!code-csharp[SP_BDC#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#3)]  
  
## 加入搜尋方法  
 若要讓 BDC 服務顯示清單中的連絡人，您必須加入搜尋方法。  請使用 \[**BDC 方法詳細資料**\] 視窗，在 Contact 實體中加入搜尋方法。  若要將實體集合傳回至 BDC 服務，請在方法中加入程式碼。  
  
#### 若要加入搜尋方法  
  
1.  在 BDC 設計工具中選取 \[**Contact**\] 實體。  
  
2.  在 \[**BDC 方法詳細資料**\] 視窗中，摺疊 \[**ReadItem**\] 節點。  
  
3.  在 \[**ReadList**\] 方法下方的 \[**將方法**\] 清單中，選取 \[**建立搜尋方法**\]。  
  
     Visual Studio 會加入方法、傳回參數以及型別描述元。  
  
4.  在 BDC 設計工具中按一下 \[**Contact**\] 實體，然後打開 \[**ReadList**\] 方法。  
  
     Contact 服務程式碼檔案隨即在 \[程式碼編輯器\] 中開啟。  
  
5.  在 `ContactService` 類別中，使用下列程式碼取代 `ReadList` 方法。  這個程式碼會執行下列工作：  
  
    -   從 AdventureWorks 資料庫的 \[連絡人\] 資料表擷取資料。  
  
    -   將 Contact 實體清單傳回至 BDC 服務。  
  
    > [!NOTE]  
    >  將 `ServerName` 欄位的值替換成您的伺服器名稱。  
  
     [!code-csharp[SP_BDC#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#2)]  
  
## 測試專案  
 在您執行專案時，SharePoint 網站隨即開啟，而 Visual Studio 則會將您的模型加入至「商務資料連接」服務。  請在 SharePoint 中建立會參考 Contact 實體的外部清單。  AdventureWorks 資料庫中的連絡人資料會顯示在清單中。  
  
> [!NOTE]  
>  在可以對方案進行偵錯之前，您可能需要修改 SharePoint 中的安全性設定。如需詳細資訊，請參閱[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
#### 若要測試專案  
  
1.  選擇 **F5** 鍵。  
  
     SharePoint 網站隨即開啟。  
  
2.  在 \[**網站動作**\] 功能表上，選擇 \[**取得更多選項**\] 命令。  
  
3.  在 \[**建立**\] 頁面上，選取 \[**外部清單**\] 範本，然後選擇 \[**建立**\] 按鈕。  
  
4.  將自訂清單命名為 Contacts。  
  
5.  選取 \[**外部內容類型**\] 欄位旁的瀏覽按鈕。  
  
6.  在 \[**外部內容類型選擇器**\] 對話方塊中，選取 \[**AdventureWorksContacts.BdcModel1.Contact**\] 項目，然後按一下 \[**建立**\] 按鈕。  
  
     SharePoint 會建立一個外部清單從 AdventureWorks 範例資料庫中的連絡人。  
  
7.  若要測試特定搜尋方法，請選擇清單中的連絡人。  
  
8.  在功能區，請選取 \[**項目**\] 索引標籤，然後選取 \[**檢視項目**\] 命令。  
  
     您選取之聯絡人的詳細資料會顯示在表單上。  
  
## 後續步驟  
 您可以透過下列主題，進一步了解如何在 SharePoint 中設計 BDC 服務的模型：  
  
-   [如何：加入建立者方法](../sharepoint/how-to-add-a-creator-method.md).  
  
-   [如何：加入更新者方法](../sharepoint/how-to-add-an-updater-method.md).  
  
-   [如何：加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md).  
  
## 請參閱  
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)   
 [將商業資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  
---
title: "Walkthrough: Extending a SharePoint Project Item Type | Microsoft Docs"
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
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: 1cea4e0f-ce33-4cd7-a664-800184865456
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Walkthrough: Extending a SharePoint Project Item Type
  您可以使用 \[**商務資料連接模型**\] 專案項目在 SharePoint 中建立商務資料連接 \(BDC\) 服務的模型。  根據預設，當您使用此專案項目建立模型時，模型中的資料不會對使用者顯示。  您也必須在 SharePoint 中建立外部清單，才能讓使用者檢視資料。  
  
 在此逐步解說中，您將建立 \[**商務資料連接模型**\] 專案項目的擴充功能。  開發人員可以使用擴充功能在顯示 BDC 模型資料的專案中建立外部清單。  本逐步解說將示範下列工作：  
  
-   建立執行兩項主要工作的 Visual Studio 擴充功能：  
  
    -   它會產生顯示 BDC 模型資料的外部清單。  擴充功能會使用 SharePoint 專案系統的物件模型產生定義清單的 Elements.xml 檔。  此外還會將檔案加入至專案，以便隨 BDC 模型一併部署。  
  
    -   它會將捷徑功能表項目加入至 \[**方案總管**\] 中的 \[**商務資料連接模型**\] 專案項目。  開發人員按一下此功能表項目，就可以產生 BDC 模型的外部清單。  
  
-   建置 Visual Studio Extension \(VSIX\) Package 以部署擴充組件。  
  
-   測試擴充功能。  
  
## 必要條件  
 開發電腦上需要下列元件才能完成此逐步解說：  
  
-   支援的 Microsoft Windows、SharePoint 和 Visual Studio 版本。  如需詳細資訊，請參閱[開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。  這個逐步解說使用 SDK 中的 **VSIX 專案**範本建立 VSIX 套件，以部署專案項目。  如需詳細資訊，請參閱[Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 了解下列概念有助於完成此逐步解說 \(但非必要\)：  
  
-   [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 中的 BDC 服務。  如需項目的詳細資訊，請參閱 [BDC Architecture](http://go.microsoft.com/fwlink/?LinkId=177798)。  
  
-   BDC 模型的 XML 結構描述。  如需詳細資訊，請參閱[BDC Model Infrastructure](http://go.microsoft.com/fwlink/?LinkId=177799) 。  
  
## 建立專案  
 若要完成這個逐步解說，您必須建立兩個專案：  
  
-   VSIX 專案，用於建立 VSIX 套件以部署專案項目擴充功能。  
  
-   類別庫專案，用於實作專案項目擴充功能。  
  
 從建立這些專案開始進行此逐步解說。  
  
#### 若要建立 VSIX 專案  
  
1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在功能表列上，選擇 \[**檔案**\]、\[**新增**\]、\[**專案**\]。  
  
3.  在 **新增專案** 對話方塊中，展開 **Visual C\#** 或 **Visual Basic**節點，然後選擇 **擴充性** 節點。  
  
    > [!NOTE]  
    >  **擴充性** 節點只有在安裝 Visual Studio SDK 時才可使用。  如需詳細資訊，請參閱本主題稍早討論的＜必要條件＞一節。  
  
4.  在 清單頂端**新增專案** 對話方塊，選取**.NET Framework 4.5**。  
  
     SharePoint 工具擴充功能需要這版的 .NET Framework 功能。  
  
5.  選擇 **VSIX 專案** 範本  
  
6.  在**名稱**文字方塊中，輸入**GenerateExternalDataLists**，然後選擇**確定**按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將 \[**GenerateExternalDataLists**\] 專案加入至 \[**方案總管**\]。  
  
7.  如果 source.extension.vsixmanifest 檔案不會自動開啟，請開啟它在 GenerateExternalDataLists 專案的捷徑功能表，然後選擇 **開啟**  
  
8.  確認 source.extension.vsixmanifest 檔案具有非空白項目 \(輸入 Contoso\) 的欄位，請儲存檔案並關閉它。  
  
#### 若要建立擴充功能專案  
  
1.  在 **方案總管**，開啟**GenerateExternalDataLists**解決方案節點，選取**加入**，然後選取**新增專案**。  
  
    > [!NOTE]  
    >  在 Visual Basic 專案中，方案節點只有在已選取[NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/zh-tw/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)中的 \[**永遠顯示方案**\] 核取方塊時，才會出現在 \[**方案總管**\] 中。  
  
2.  在 **加入新的專案** 對話方塊中展開 **Visual C\#**或**Visual Basic**節點，然後選擇**視窗**節點。  
  
3.  在對話方塊上方的清單中，選取 **.NET Framework 4.5**。  
  
4.  在專案範本清單中，選取 **類別庫**。  
  
5.  在 **名稱**文字方塊中，輸入 **BdcProjectItemExtension**，然後選擇 **確定**按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將 \[**BdcProjectItemExtension**\] 專案加入至方案，然後開啟預設的 Class1 程式碼檔。  
  
6.  從專案刪除 Class1 程式碼檔。  
  
## 設定擴充功能專案  
 在您撰寫程式碼建立專案項目擴充功能之前，請先將程式碼檔案和組件參考加入至擴充功能專案。  
  
#### 若要設定專案  
  
1.  在 \[BdcProjectItemExtension\] 專案中，加入名稱如下的兩個程式碼檔：  
  
    -   ProjectItemExtension  
  
    -   GenerateExternalDataLists  
  
2.  選取 BdcProjectItemExtension 專案，然後，在功能表列上，選擇 **專案**，則 **加入參考**。  
  
3.  在 **組件**節點下，選取 **Framework**節點並選取下列組件中的每一個核取方塊:  
  
    -   System.ComponentModel.Composition  
  
    -   WindowsBase  
  
4.  在 **組件**節點下，選取 **擴充功能**節點，為下列組件然後選取核取方塊:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  選擇 \[**確定**\] 按鈕。  
  
## 定義專案項目擴充功能  
 建立類別，該類別會定義 \[**商務資料連接模型**\] 專案項目的擴充功能。  為定義擴充功能，此類別會實作 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 介面。  在您要擴充現有專案項目的類型時實作此介面。  
  
#### 若要定義專案項目擴充功能  
  
1.  下列程式碼貼入 ProjectItemExtension 程式碼檔案。  
  
    > [!NOTE]  
    >  加入這段程式碼後，專案會出現一些編譯錯誤。  在後續步驟中加入程式碼時，這些錯誤將不存在。  
  
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.bdcgenerateexternaldatalists/cs/bdcprojectitemextension/projectitemextension.cs#1)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.bdcgenerateexternaldatalists/vb/bdcprojectitemextension/projectitemextension.vb#1)]  
  
## 建立外部資料清單  
 加入 `GenerateExternalDataListsExtension` 類別的部分定義，該類別會為 BDC 模型中的每一個實體建立外部資料清單。  若要建立外部資料清單，此程式碼會先透過剖析 BDC 模型檔中 XML 資料的方式，讀取 BDC 模型中的實體資料。  然後會根據 BDC 模型建立清單執行個體，並且將此清單執行個體加入至專案。  
  
#### 若要建立外部資料清單  
  
1.  下列程式碼貼入 GenerateExternalDataLists 程式碼檔案。  
  
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.bdcgenerateexternaldatalists/cs/bdcprojectitemextension/generateexternaldatalists.cs#2)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.bdcgenerateexternaldatalists/vb/bdcprojectitemextension/generateexternaldatalists.vb#2)]  
  
## 檢查點  
 在逐步解說中進行至此處時，專案項目擴充功能的所有程式碼都會位於專案中。  建置方案，以確定專案在編譯時未發生任何錯誤。  
  
#### 若要建置方案  
  
1.  在功能表列上，選擇 \[**建置**\]、\[**建置方案**\]。  
  
## 建立 VSIX 套件以部署專案項目擴充功能  
 若要部署擴充功能，請在您的方案中使用 VSIX 專案，以建立 VSIX 套件。  首先，修改 VSIX 專案包含的 source.extension.vsixmanifest 檔案，來設定 VSIX 套件。  接著，建置方案來建立 VSIX 套件。  
  
#### 若要設定和建立 VSIX 套件  
  
1.  在 **方案總管** 中開啟 GenerateExternalDataLists專案中的source.extension.vsixmanifest檔案捷徑功能表，然後選擇 **開啟**。  
  
     Visual Studio 會在資訊清單編輯器中開啟檔案。  source.extension.vsixmanifest 檔案是所有 VSIX 套件所需要 extension.vsixmanifest 檔案的基準。  如需這個檔案的詳細資訊，請參閱[VSIX 擴充結構描述參考](http://msdn.microsoft.com/zh-tw/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在 **產品名稱** 方塊中，輸入**外部資料清單產生器**。  
  
3.  在 **作者** 方塊中，輸入 **Contoso**。  
  
4.  在 **描述** 方塊中，輸入**可用來產生外部資料清單之商務資料連接模型專案項目的擴充功能**。  
  
5.  在編輯器中的**資產**索引標籤上，選擇 **新增**按鈕。  
  
     **加入新資產**對話方塊隨即出現。  
  
6.  在**類型** 清單中，選取 **Microsoft.VisualStudio.MefComponent**。  
  
    > [!NOTE]  
    >  這個值對應於 extension.vsixmanifest 檔案中的 `MefComponent` 項目。  這個項目指定 VSIX 套件中的擴充組件名稱。  如需詳細資訊，請參閱[NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/zh-tw/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
7.  在**來源**清單中，選取 **在目前方案中的專案**。  
  
8.  在 **專案** 清單中，選擇 **BdcProjectItemExtension**，然後選擇 **確定** 按鈕。  
  
9. 在功能表列上，選擇 \[**建置**\]、\[**建置方案**\]。  
  
10. 建置專案，以確定在編譯時未發生任何錯誤。  
  
11. 確定 GenerateExternalDataLists 專案的建置輸出資料夾現已包含 GenerateExternalDataLists.vsix 檔。  
  
     根據預設，建置輸出資料夾是 ...\\bin\\Debug 資料夾，包含在您的專案檔下。  
  
## 測試專案項目擴充功能  
 您現在可以測試專案項目擴充功能。  首先，在 Visual Studio 的實驗執行個體中開始偵錯擴充功能專案。  然後，使用 Visual Studio 實驗執行個體中的擴充功能來產生 BDC 模型的外部清單。  最後，在 SharePoint 網站上開啟外部清單，確認其功能正常。  
  
#### 若要啟動對擴充功能的偵錯  
  
1.  如果需要，以管理認證重新啟動 Visual Studio，然後開啟 GenerateExternalDataLists 方案。  
  
2.  在 BdcProjectItemExtension 專案中，開啟 ProjectItemExtension 程式碼檔，然後將中斷點加入至 `Initialize` 方法內的程式碼中。  
  
3.  開啟 GenerateExternalDataLists 程式碼檔，然後將中斷點加入至 `GenerateExternalDataLists_Execute` 方法內的第一行程式碼中。  
  
4.  您可以選擇 F5鍵，或在功能表列上，選擇 **偵錯**、 **啟動偵錯**來開始偵錯。  
  
     Visual Studio 會將擴充功能安裝至 %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\10.0Exp\\Extensions\\Contoso\\External Data List Generator\\1.0，並啟動 Visual Studio 的實驗執行個體。  您將會在 Visual Studio 的這個執行個體中測試專案項目。  
  
#### 若要測試擴充功能  
  
1.  在 Visual Studio 的實驗執行個體中，在 **檔案** 功能表列上的 **新增** 中，選擇 **專案**。  
  
2.  在 **新增專案** 對話方塊的左窗格中，依序展開 **範本** 節點、**Visual C\#** 節點、 **SharePoint**節點，然後選取**2010**。  
  
3.  在對話方塊上方的清單中，確定已選取 **.NET Framework 3.5**。  [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 的專案需要此版本的 .NET Framework。  
  
4.  在專案範本清單中，選擇 **SharePoint 2010 專案**。  
  
5.  在**名稱** 方塊中，輸入 Vision Clinic，然後選擇 **SharePointProjectTestBDC**按鈕並選擇**確定**按鈕。  
  
6.  在 SharePoint 自訂精靈中，輸入要用於偵錯的網站 URL，然後選擇 **部署為陣列方案**，然後選擇 **結束**按鈕。  
  
7.  開啟SharePointProjectTestBDC專案節點的捷徑功能表，選擇 **加入**，然後選擇 **新項目**。  
  
8.  在**加入 NewItem – SharePointProjectTestBDC**對話方塊中，展開安裝的語言節點，展開 **SharePoint**節點。  
  
9. 選取 **2010**節點，然後選取**商務資料連接模型 \(僅限陣列方案\)** 範本。  
  
10. 在**名稱** 文字方塊中輸入**TestBDCModel**，然後選擇**新增**按鈕。  
  
11. 確認另一個 Visual Studio 執行個體中的程式碼在您在ProjectItemExtension程式檔的 `Initialize` 方法中設定的中斷點停止。  
  
12. 在 Visual Studio 停止的執行個體，請選擇 **F5** 鍵，或在功能表列上，選擇 **偵錯**、 **繼續**，繼續偵錯專案。  
  
13. 在 Visual Studio 的實驗執行個體，請選擇 **F5**鍵，或在功能表列上，選擇**偵錯**，**啟動偵錯**，建置、部署和執行 **TestBDCModel**項目。  
  
     Web 瀏覽器會開啟用於偵錯的 SharePoint 網站預設頁面。  
  
14. 確認快速啟動區中的 **清單**區段尚未包含依據專案中預設 BDC 模型的清單。  您必須先使用 SharePoint 使用者介面或使用專案項目擴充功能建立外部資料清單。  
  
15. 關閉 Web 瀏覽器。  
  
16. 在開啟 TestBDCMode專案的 Visual Studio 執行個體中，以滑鼠右鍵按一下**方案總管**中的 **TestBDCModel**節點，然後選擇**產生外部資料清單**。  
  
17. 確認另一個 Visual Studio 執行個體中的程式碼在您於 `GenerateExternalDataLists_Execute` 方法中設定的中斷點停止。  選擇 **F5** 鍵，或在功能表列上，選擇**偵錯**、**繼續**，繼續偵錯專案。  
  
18. Visual Studio 的實驗執行個體會將名為 **Entity1DataList** 的清單執行個體加入至 TestBDCModel 專案，同時會針對清單執行個體產生名為 **Feature2** 的功能。  
  
19. 選擇**F5**鍵，或在功能表列上選擇 **偵錯**，則**啟動偵錯**建置、部署和執行 TestBDCModel 專案。  
  
     Web 瀏覽器會開啟用於偵錯的 SharePoint 網站預設頁面。  
  
20. 在 **清單**的快速啟動區中，按一下**Entity1DataList** 清單。  
  
21. 確認清單包含名為 Identifier1 和 Message 的資料行，且其中一個項目的 Identifier1 值為 0，Message 值為 Hello World。  
  
     **Business Data Connectivity Model**專案樣板產生預設BDC模板以提供資料。  
  
22. 關閉 Web 瀏覽器。  
  
## 清理開發電腦  
 在您完成測試專案項目擴充功能之後，從 SharePoint 網站移除外部清單和 BDC 模型，並且從 Visual Studio 移除專案項目擴充功能。  
  
#### 若要從 SharePoint 網站移除外部資料清單  
  
1.  在 SharePoint 網站的快速啟動區中，選取 **Entity1DataList**清單。  
  
2.  在 SharePoint 網站的功能區中，選取 **清單**索引標籤。  
  
3.  在**清單**索引標籤的**設定**群組中，選取 **清單設定**。  
  
4.  在 **使用權限和管理** 底下，選取 **刪除這個清單**，然後選取 **好**確認您要傳送清單到資源回收筒。  
  
5.  關閉 Web 瀏覽器。  
  
#### 若要從 SharePoint 網站移除 BDC 模型  
  
1.  在 Visual Studio 的實驗執行個體中，選取**建置**功能列表上的 **撤銷**  
  
     Visual Studio 會從 SharePoint 網站移除 BDC 模型。  
  
#### 若要從 Visual Studio 移除專案項目擴充功能  
  
1.  在 Visual Studio 的實驗執行個體中，選擇 **工具**功能表列上的 **擴充和更新**。  
  
     \[**擴充功能和更新**\] 對話方塊隨即開啟。  
  
2.  在擴充功能清單中，按一下 **外部資料清單產生器**，然後按一下 **解除安裝**。  
  
3.  在所顯示的對話方塊中，選擇 **是**，確認您要解除安裝擴充功能。  
  
4.  選擇**立即重新啟動**完成解除安裝。  
  
5.  關閉 Visual Studio 的兩個執行個體 \(Visual Studio 的實驗執行個體，以及其中有開啟 GenerateExternalDataLists 專案的執行個體\)。  
  
## 請參閱  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  
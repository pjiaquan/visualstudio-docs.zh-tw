---
title: "Walkthrough: Creating a SharePoint Project Extension | Microsoft Docs"
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
  - "projects [SharePoint development in Visual Studio], extending"
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint projects, extending"
ms.assetid: 5547e2ed-47a3-48f1-9619-42149c03df76
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Walkthrough: Creating a SharePoint Project Extension
  本逐步解說將說明如何建立 SharePoint 專案的擴充功能。  在專案中，加入、刪除或重新命名時，您可以使用專案擴充功能回應專案層級事件。  您還可以加入自訂屬性或在屬性值變更時回應。  與專案項目擴充功能不同，專案擴充功能無法與特定 SharePoint 專案類型產生關聯。  當您建立專案擴充功能時，擴充功能會在任何類型的 SharePoint 專案於 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中開啟時載入。  
  
 在這個逐步解說中，您將建立可加入至在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中所建立任何 SharePoint 專案的自訂布林屬性。  當設定為 **True** 時，新屬性會將 \[影像\] 資源資料夾加入或對應至專案。  當設定為 **False** 時，會移除 \[影像\] 資料夾 \(若存在的話\)。  如需詳細資訊，請參閱[如何：新增與移除對應的資料夾](../sharepoint/how-to-add-and-remove-mapped-folders.md)。  
  
 本逐步解說將示範下列工作：  
  
-   建立 SharePoint 專案的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 擴充功能可執行下列內容：  
  
    -   將自訂專案屬性加入至 \[屬性\] 視窗。  該屬性套用至任何 SharePoint 專案。  
  
    -   使用 SharePoint 專案物件模型將對應的資料夾加入至專案。  
  
    -   使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Automation 物件模型 \(Automation Object Model，DTE\)，將對應的資料夾從專案刪除。  
  
-   建置 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 擴充功能 \(VSIX\) 套件以部署專案屬性的擴充功能組件。  
  
-   偵錯和測試專案屬性。  
  
## 必要條件  
 開發電腦上需要下列元件才能完成此逐步解說：  
  
-   支援的 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]、SharePoint 和 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 版本。  如需詳細資訊，請參閱[開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。  本逐步解說使用 [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] 中的 \[**VSIX 專案**\] 範本建立 VSIX 套件，以部署專案屬性擴充功能。  如需詳細資訊，請參閱[Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
## 建立專案  
 若要完成這個逐步解說，您必須建立兩個專案：  
  
-   VSIX 專案，用於建立 VSIX 套件以部署專案擴充功能。  
  
-   類別庫專案，可實作專案擴充功能。  
  
 從建立這些專案開始進行此逐步解說。  
  
#### 若要建立 VSIX 專案  
  
1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在功能表列上，選擇 \[**檔案**\]， \[**新增**\]， \[**Project**\]。  
  
3.  在 \[**新增專案**\] 對話方塊中，展開 \[**Visual C\#**\] 或 \[**Visual Basic**\] 節點，然後選取 \[**擴充性**\] 節點。  
  
    > [!NOTE]  
    >  為，當您安裝 Visual Studio SDK，節點為止。  如需詳細資訊，請參閱本主題稍早討論的＜必要條件＞一節。  
  
4.  在對話方塊的頂端，選取 .NET Framework 版本的清單 \[**.NET Framework 4.5**\] ，然後選取 \[**VSIX 專案**\] 範本。  
  
5.  在 \[**Name**\]方塊中，輸入 **ProjectExtensionPackage**，然後選取 \[**確定**\] 按鈕。  
  
     \[**ProjectExtensionPackage**\]專案會出現在 \[**方案總管**\]。  
  
#### 若要建立擴充功能專案  
  
1.  在 \[**方案總管**\]，開啟方案節點的捷徑功能表，選擇\[**新增**\]，然後選取 \[**新增專案**\]。  
  
    > [!NOTE]  
    >  在 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 專案，，才 \[**永遠顯示方案**\] 核取方塊在 [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/zh-tw/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)，選取方案節點出現在 \[**方案總管**\] 。  
  
2.  在 \[**新增專案**\] 對話方塊中，展開 \[**Visual C\#**\] 或 \[**Visual Basic**\] 節點，然後選取 \[**視窗**\]。  
  
3.  在對話方塊的頂端，選取 .NET Framework 版本的清單 **.NET Framework 4.5** ，然後選取 \[**類別庫**\] 專案範本。  
  
4.  在 \[**Name**\]方塊中，輸入 **ProjectExtension**，然後選取 \[**確定**\] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將 \[**ProjectExtension**\] 專案加入至方案，然後開啟預設的 Class1 程式碼檔。  
  
5.  從專案刪除 Class1 程式碼檔。  
  
## 設定專案  
 在您撰寫程式碼建立專案擴充功能之前，請先將程式碼檔案和組件參考加入至擴充功能專案。  
  
#### 若要設定專案  
  
1.  加入名為至 ProjectExtension 專案的 **CustomProperty** 程式碼檔案。  
  
2.  開啟 \[**ProjectExtension**\]專案的捷徑功能表，然後選取 \[**新增參考**\]。  
  
3.  在 \[**參考管理員– CustomProperty**\] 對話方塊中，選取 \[**Framework**\] 節點，在 System.ComponentModel.Composition 和 System.Windows.Forms 組件旁邊的然後選取核取方塊。  
  
4.  選取 \[**延伸**\] 節點，在 EnvDTE 和 Microsoft.VisualStudio.SharePoint 組件旁邊的核取方塊，然後選取 \[**確定**\] 按鈕。  
  
5.  在 \[**方案總管**\]，在 \[**ProjectExtension**\]專案的 \[**參考**\] 資料夾底下，選取 \[**EnvDTE**\]。  
  
6.  在 \[**屬性**\] 視窗中，將 \[**內嵌 Interop 型別**\] 屬性變更為 \[**False**\]。  
  
## 定義新的 SharePoint 專案屬性  
 建立定義專案擴充功能和新專案屬性行為的類別。  為了定義新專案擴充功能，類別會實作 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 介面。  在您要定義 SharePoint 專案的擴充功能時實作此介面。  另外，請將 <xref:System.ComponentModel.Composition.ExportAttribute> 加入至類別。  此屬性可讓 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 探索並載入 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 實作。  將 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 型別傳遞至屬性的建構函式。  
  
#### 若要定義新的 SharePoint 專案屬性  
  
1.  下列程式碼貼入 CustomProperty 程式碼檔案。  
  
     [!code-csharp[SPExt_ProjectExtension#1](../snippets/csharp/VS_Snippets_OfficeSP/spext_projectextension/cs/projectextension/customproperty.cs#1)]
     [!code-vb[SPExt_ProjectExtension#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_projectextension/vb/projectextension/customproperty.vb#1)]  
  
## 建置方案  
 接下來，建置方案，以確定專案在編譯時未發生任何錯誤。  
  
#### 若要建置方案  
  
1.  在功能表列上，選擇， \[**組建**\]\[**建置方案**\]。  
  
## 建立 VSIX 套件以部署專案屬性擴充功能  
 若要部署專案擴充功能，請在您的方案中使用 VSIX 專案，以建立 VSIX 套件。  首先，修改 VSIX 專案包含的 source.extension.vsixmanifest 檔案，來設定 VSIX 套件。  接著，建置方案來建立 VSIX 套件。  
  
#### 若要設定和建立 VSIX 套件  
  
1.  在 \[**方案總管**\]，開啟 source.extension.vsixmanifest 檔案的捷徑功能表，然後選取 \[**開啟**\] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 開啟在資訊清單設計工具中開啟該檔案。  也會顯示在 \[**中繼資料**\] 選項的相關資訊隨即出現在 \[**副檔名和更新**\]。所有 VSIX 套件都需要 extension.vsixmanifest 檔案。  如需這個檔案的詳細資訊，請參閱[VSIX 擴充結構描述參考](http://msdn.microsoft.com/zh-tw/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在 \[**產品名稱**\]方塊中，輸入 **自訂專案屬性**。  
  
3.  在 \[**作者**\]方塊中，輸入 **Contoso**。  
  
4.  在 \[**Description**\]方塊中，輸入 **切換 \[影像\] 資源資料夾對應至專案的自訂 SharePoint 專案屬性**。  
  
5.  選取 \[**資產**\] 索引標籤，然後選取 \[**新增**\] 按鈕。  
  
     \[**將新的屬性**\] 對話方塊隨即出現。  
  
6.  在 \[**型別**\] 清單中，選取 \[**Microsoft.VisualStudio.MefComponent**\]。  
  
    > [!NOTE]  
    >  這個值對應於 extension.vsixmanifest 檔案中的 `MEFComponent` 項目。  這個項目指定 VSIX 套件中的擴充組件名稱。  如需詳細資訊，請參閱[NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/zh-tw/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
7.  在 \[**Source**\] 清單中，選取 \[**在目前方案中的專案**\] 選項按鈕。  
  
8.  在 \[**Project**\] 清單中，選取 **ProjectExtension**。  
  
     這個值會識別組件的名稱在專案建置。  
  
9. 選取 \[**確定**\] 關閉 \[**將新的屬性**\] 對話方塊。  
  
10. 在功能表列上，選擇 \[**檔案**\]， \[**全部儲存**\] ，當您完成時，然後關閉資訊清單設計工具。  
  
11. 在功能表列上，選擇， \[**組建**\]\[**建置方案**\]，然後確定專案在編譯時未發生任何錯誤。  
  
12. 在 \[**方案總管**\]，開啟 \[**ProjectExtensionPackage**\]專案的捷徑功能表，然後選擇\[**在檔案總管中開啟資料夾**\] 按鈕。  
  
13. 在 \[**檔案總管**\]，開啟 ProjectExtensionPackage 專案的建置輸出資料夾，然後確認這個資料夾包含名為 ProjectExtensionPackage.vsix 的檔案。  
  
     根據預設，建置輸出資料夾為 ..  \\bin\\Debug 資料夾，其位於專案檔案包含的資料夾下。  
  
## 測試專案屬性  
 您現在可以測試自訂專案屬性。  偵錯和測試 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]在的實驗執行個體中新專案屬性擴充功能是最容易的。  當您執行 VSIX 或其他擴充性項目時， [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 建立這個執行個體。  在偵錯專案之後，您可以安裝在系統中的副檔名並繼續進行偵錯和測試它在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]的一般執行個體。  
  
#### 若要在 Visual Studio 的實驗執行個體中對擴充功能進行偵錯和測試  
  
1.  重新啟動以管理認證的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，然後開啟 ProjectExtensionPackage 方案。  
  
2.  藉由選取 \[**F5**\]索引鍵啟動專案的偵錯組建或，在功能表列上，選擇， \[**偵錯**\]\[**啟動偵錯**\]。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將擴充功能安裝至 %UserProfile% \\ AppData \\ Local \\ Microsoft \\ VisualStudio \\ 11.0Exp \\ Extensions \\ Contoso \\ Custom Project Property \\模糊並啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]的實驗執行個體。  
  
3.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]實驗執行個體中，建立陣列方案的 SharePoint 專案，並且為其他值使用預設值在精靈。  
  
    1.  在功能表列上，選擇 \[**檔案**\]， \[**新增**\]， \[**Project**\]。  
  
    2.  在 \[**新增專案**\] 對話方塊的頂端，選取 .NET Framework 版本的清單 \[**.NET Framework 3.5**\] 。  
  
         SharePoint 工具擴充功能需要 [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]的這個版本的功能。  
  
    3.  在 \[**範本**\] 節點下，展開 \[**Visual C\#**\] 或 \[**Visual Basic**\] 節點，然後選取 \[**SharePoint**\] 節點，然後選取 \[**2010**\] 節點。  
  
    4.  選取 \[**SharePoint 2010 專案**\] 範本，然後輸入 **ModuleTest** 是專案的名稱。  
  
4.  在 \[**方案總管**\]，選取 \[**ModuleTest**\]專案節點。  
  
     新的自訂屬性 \[**對應影像資料夾**\] 出現在 \[**屬性**\] 視窗中，並且預設值為 **False**。  
  
5.  變更該屬性的值變更為 **True**。  
  
     \[影像\] 資源資料夾隨即加入至 SharePoint 專案。  
  
6.  變更該屬性的值 **False**回。  
  
     如果您在 \[**刪除 Images 資料夾?**\]對話方塊的 \[**是**\] 按鈕， \[影像\] 資源資料夾從 SharePoint 專案刪除。  
  
7.  關閉 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的實驗執行個體。  
  
## 請參閱  
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  
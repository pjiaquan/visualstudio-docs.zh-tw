---
title: "逐步解說：使用專案範本建立網站資料行專案項目 (第 2 部分)"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "專案項目 [Visual Studio 中的 SharePoint 程式開發]、建立範本精靈"
  - "SharePoint 專案項目、建立範本精靈"
  - "Visual Studio 中的 SharePoint 程式開發、定義新的專案項目類型"
ms.assetid: da14207d-ac09-41ba-b387-c7f881b2a366
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# 逐步解說：使用專案範本建立網站資料行專案項目 (第 2 部分)
  當您在 Visual Studio 中定義自訂類型的 SharePoint 專案項目，並為其建立與專案範本之間的關聯後，您也可以提供該範本專用的精靈。  您可以使用精靈，在使用者利用您的範本建立包含該專案項目的新專案時，向使用者收集資訊。  您收集到的資訊可用來初始化專案項目。  
  
 在本逐步解說中，您將會在[逐步解說：使用專案範本建立網站欄專案項目 &#40;第 1 部分&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)示範的網站欄專案範本中加入精靈。  當使用者建立網站欄專案時，精靈會收集網站欄的相關資訊 \(例如其基底型別和群組\)，並將此資訊加入至新專案中的 Elements.xml 檔案。  
  
 本逐步解說將示範下列工作：  
  
-   建立與專案範本有關聯之自訂 SharePoint 專案項目類型的精靈。  
  
-   為Visual Studio中的 SharePoint 專案來定義類似內建精靈的自訂精靈 UI。  
  
-   建立兩個「*SharePoint 命令*」\(SharePoint Command\)，用來在精靈執行時呼叫本機 SharePoint 網站。  SharePoint 命令是 Visual Studio 擴充功能可用來在 SharePoint 伺服器物件模型中呼叫 API 的方法。  如需詳細資訊，請參閱[Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
-   使用可取代的參數，以您在精靈中收集到的資料初始化 SharePoint 專案檔。  
  
-   在每個新的網站欄專案執行個體中建立新的 .snk 檔案。  這個檔案是用來簽署專案輸出，讓 SharePoint 方案組件可以部署到全域組件快取。  
  
-   對精靈進行偵錯和測試。  
  
> [!NOTE]  
>  您可以從下列位置取得內含完成的專案、程式碼和其他檔案的範例：[http:\/\/go.microsoft.com\/fwlink\/?LinkId\=191369](http://go.microsoft.com/fwlink/?LinkId=191369)。  
  
## 必要條件  
 若要執行本逐步解說，您必須先完成[逐步解說：使用專案範本建立網站欄專案項目 &#40;第 1 部分&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)，以建立 SiteColumnProjectItem 方案。  
  
 此外，您的開發電腦上必須要有下列元件，才能完成此逐步解說：  
  
-   所支援的 Windows版本、SharePoint版本以及Visual Studio版本。  如需詳細資訊，請參閱[開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio SDK.  這個逐步解說使用 SDK 中的 **VSIX 專案**範本建立 VSIX 套件，以部署專案項目。  如需詳細資訊，請參閱[Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 了解下列概念有助於完成此逐步解說 \(但非必要\)：  
  
-   Visual Studio 中的專案和項目範本專用的精靈。  如需詳細資訊，請參閱 [如何：搭配專案範本使用精靈](~/extensibility/how-to-use-wizards-with-project-templates.md)和 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 介面。  
  
-   SharePoint 中的網站欄。  如需詳細資訊，請參閱 [Columns](http://go.microsoft.com/fwlink/?LinkId=183547)。  
  
##  <a name="wizardcomponents"></a> 了解精靈元件  
 本逐步解說中示範的精靈包含數個元件。  下表說明這些元件。  
  
|元件|描述|  
|--------|--------|  
|精靈實作|這是名為 `SiteColumnProjectWizard` 的類別，其實作 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 介面。  這個介面會定義 Visual Studio 在精靈啟動和完成時呼叫的方法，以及在精靈執行時的某些時候呼叫的方法。|  
|精靈 UI|這是名為 `WizardWindow` 的 WPF 視窗。  這個視窗包含兩個使用者控制項，分別名為 `Page1` 和 `Page2`。  這兩個使用者控制項代表精靈的兩個頁面。<br /><br /> 在本逐步解說中，精靈實作的 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> 方法會顯示精靈 UI。|  
|精靈資料模型|這是名為 `SiteColumnWizardModel` 的中繼類別，其提供精靈 UI 與精靈實作之間的階層。  此範例會使用這個類別來協助互相擷取精靈實作與精靈 UI；這個類別不是所有精靈的必要元件。<br /><br /> 在本逐步解說中，精靈實作顯示精靈 UI 時會將 `SiteColumnWizardModel` 物件傳遞到精靈視窗。  精靈 UI 會使用這個物件的方法，儲存 UI 中的控制項值以及執行像是驗證輸入網站 URL 是否有效的工作。  在使用者完成精靈之後，精靈實作會使用 `SiteColumnWizardModel` 物件判斷 UI 的最終狀態。|  
|專案簽署管理員|這是名為 `ProjectSigningManager` 的 Helper 類別，其由精靈實作用來在每個新的專案執行個體中建立新的 key.snk 檔案。|  
|SharePoint 命令|這些是精靈資料模型用來在精靈執行時呼叫本機 SharePoint 網站的方法。  因為 SharePoint 命令必須以 .NET Framework 3.5 為目標，這些命令都是在與其餘的精靈程式碼不同的組件中實作。|  
  
## 建立專案  
 為了完成本逐步解說，您必須在[逐步解說：使用專案範本建立網站欄專案項目 &#40;第 1 部分&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md) 建立的 SiteColumnProjectItem 方案中加入數個專案：  
  
-   WPF 專案。  您將會在這個專案中實作 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 介面並定義精靈 UI。  
  
-   定義 SharePoint 命令的類別庫專案。  這個專案必須以 .NET Framework 3.5 為目標。  
  
 從建立這些專案開始進行此逐步解說。  
  
#### 若要建立 WPF 專案  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中，請開啟 SiteColumnProjectItem 方案。  
  
2.  在 \[**方案總管**\]，開啟 **SiteColumnProjectItem**方案節點的捷徑功能表中，選取 \[**加入**\]，然後選取 \[**新增專案**\]。  
  
    > [!NOTE]  
    >  在 Visual Basic 專案中，只有在已選取[NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/zh-tw/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)中的 \[**永遠顯示方案**\] 核取方塊時，才會出現方案節點。  
  
3.  在 \[**加入新的專案**\] 對話方塊的頂端，請確認在 .NET Framework 的版本清單中已經選取 \[**.NET Framework 4.5**\] 。  
  
4.  展開 \[**Visual C\#**\] 節點或 \[**Visual Basic**\] 節點，然後選取 \[**視窗**\] 節點。  
  
5.  在專案範本清單中，選取 \[**WPF 使用者控制項程式庫**\]\]，將專案命名為 **ProjectTemplateWizard**，然後選擇 \[**好**\] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將 \[**ProjectTemplateWizard**\] 專案加入至方案，並開啟預設 UserControl1.xaml 檔案。  
  
6.  從專案中刪除 UserControl1.xaml 檔案。  
  
#### 若要建立 SharePoint 命令專案  
  
1.  在 \[**方案總管**\]，開啟 SiteColumnProjectItem 方案節點的捷徑功能表中，選取 \[**加入**\]，然後選取 \[**新增專案**\]。  
  
2.  在 \[**加入新的專案**\] 對話方塊的頂端，選取 .NET Framework 版本清單中的 \[**.NET Framework 3.5**\] 。  
  
3.  展開 \[**Visual C\#**\] 節點或 \[**Visual Basic**\] 節點，接著選取 \[**視窗**\] 節點。  
  
4.  選取 \[**類別庫**\] 專案範本，將專案命名為 **SharePointCommands**，然後選擇 \[**好**\] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將 \[**SharePointCommands**\] 專案加入至方案，然後開啟預設的 Class1 程式碼檔。  
  
5.  從專案刪除 Class1 程式碼檔。  
  
## 設定專案  
 在建立精靈之前，您必須先將一些程式碼檔案和組件參考加入至專案。  
  
#### 若要設定精靈專案  
  
1.  在 \[**方案總管**\] 中開啟 \[**ProjectTemplateWizard**\] 專案節點的捷徑功能表，然後選擇 \[**屬性**\]。  
  
2.  在 \[**專案設計工具**\] 中，選取 Visual C\# 專案的 \[**應用程式**\] 索引標籤，或選取 Visual Basic 專案中的 \[**編譯**\] 索引標籤。  
  
3.  確定目標 Framework 設定為 .NET Framework 4.5，而不是 .NET Framework 4.5 Client Profile。  
  
     如需詳細資訊，請參閱[如何：以 .NET Framework 版本為目標](~/ide/how-to-target-a-version-of-the-dotnet-framework.md)。  
  
4.  開啟\[**ProjectTemplateWizard**專案節點的捷徑功能表，選擇 \[**加入**\]，然後選擇 \[**新增項目**\]。  
  
5.  選取 \[**Windows \(WPF\)**\] 項目，將項目命名為 **WizardWindow**，然後選擇 \[**加入**\] 按鈕。  
  
6.  將兩個 \[**使用者控制項 \(WPF\)**\] 項目加入至專案，並將它們命名為 **Page1** 和 **Page2**。  
  
7.  在專案中加入四個程式碼檔，並命名為下列的名稱：  
  
    -   SiteColumnProjectWizard  
  
    -   SiteColumnWizardModel  
  
    -   ProjectSigningManager  
  
    -   CommandIds  
  
8.  開啟\[**ProjectTemplateWizard**\] 專案節點的捷徑功能表，然後選擇\[**加入參考**\] 。  
  
9. 展開\[**組件**\] 節點，選取 \[**擴充功能**\] 節點，然後請在下列組件旁邊的核取方塊勾選：  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.10.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
10. 選擇 \[**好**\] 按鈕，將組件加入至專案。  
  
11. 在 \[**方案總管**\] 中，**ProjectTemplateWizard**專案的 \[**參考**\] 資料夾底下選取 \[**EnvDTE**\]。  
  
    > [!NOTE]  
    >  在 Visual Basic 專案中，只有在已選取[NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/zh-tw/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)中的 \[**永遠顯示方案**\] 核取方塊時，才會出現 \[**參考**\] 資料夾。  
  
12. 在 \[**屬性**\] 視窗中，將 \[**內嵌 Interop 型別**\] 屬性值變更為 \[**False**\]。  
  
13. 如果開發 Visual Basic 專案，請使用 \[**專案設計工具**\] 將 ProjectTemplateWizard 命名空間匯入專案中。  
  
     如需詳細資訊，請參閱[如何：加入或移除匯入的命名空間 &#40;Visual Basic&#41;](~/ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)。  
  
#### 若要設定 SharePointCommands 專案  
  
1.  在 \[**方案總管**\] 中，選取 \[**SharePointCommands**\] 專案節點。  
  
2.  在功能表列中，選擇 \[**專案**\]、\[**加入現有項目**\]。  
  
3.  在 \[**加入現有項目**\] 對話方塊中，瀏覽至包含 ProjectTemplateWizard 專案程式碼檔案的資料夾，然後選取**CommandIds**程式碼檔案。  
  
4.  選取在 \[**加入**\] 按鈕旁邊的箭號，然後選取顯示功能表的 \[**加入為連結。**\] 選項。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將程式碼檔案加入至 **SharePointCommands** 專案做為連結。  程式碼檔案位於 **ProjectTemplateWizard** 專案中，但是檔案中的程式碼也會在 **SharePointCommands** 專案中編譯。  
  
5.  在 \[**SharePointCommands**\] 專案中，加入另一個名為 Commands 的程式碼檔。  
  
6.  選取 SharePointCommands 專案，然後在功能表列上，選擇 \[**專案**\]、 \[**加入參考**\]。  
  
7.  展開\[**組件**\] 節點，選取 \[**擴充功能**\] 節點，然後請在下列組件旁邊的核取方塊勾選：  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
8.  選擇 \[**好**\] 按鈕，將組件加入至專案。  
  
## 建立精靈模型、簽署管理員和 SharePoint 命令 ID  
 將程式碼加入至 ProjectTemplateWizard 專案，以便在範例中實作下列元件：  
  
-   SharePoint 命令 ID。  這些字串識別精靈所用的 SharePoint 命令。  稍後在本逐步解說中，您將在 SharePointCommands 專案中加入程式碼來實作命令。  
  
-   精靈資料模型。  
  
-   專案簽署管理員。  
  
 如需這些元件的詳細資訊，請參閱[了解精靈元件](#wizardcomponents)。  
  
#### 若要定義 SharePoint 命令 ID  
  
1.  在 ProjectTemplateWizard 專案中，開啟 CommandIds 程式碼檔案，然後以下列程式碼取代這個檔案的整個內容。  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/commandids.vb#5)]  
  
#### 若要建立精靈模型  
  
1.  開啟 SiteColumnWizardModel 程式碼檔，然後以下列程式碼取代這個檔案的整個內容。  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]  
  
#### 若要建立專案簽署管理員  
  
1.  開啟 ProjectSigningManager 程式碼檔，然後以下列程式碼取代這個檔案的整個內容。  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/projectsigningmanager.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/projectsigningmanager.vb#8)]  
  
## 建立精靈 UI  
 加入 XAML 以定義精靈視窗的 UI 和兩個為精靈頁面提供 UI 的使用者控制項，並加入程式碼以定義視窗和使用者控制項的行為。  所建立的精靈類似於 Visual Studio 中 SharePoint 專案的內建精靈。  
  
> [!NOTE]  
>  在下列步驟中，於專案中加入 XAML 或程式碼之後，將會出現一些編譯錯誤。  在後續步驟中加入程式碼時，這些錯誤將不存在。  
  
#### 若要建立精靈視窗 UI  
  
1.  在 ProjectTemplateWizard 專案中，開啟 WizardWindow.xaml 檔案的捷徑功能表，然後選擇 \[**開啟**\] 以設計工具開啟的視窗。  
  
2.  在設計工具的 XAML 檢視中，以下列 XAML 取代目前的 XAML。  這個 XAML 定義的 UI 包含標題、內含精靈頁面的 <xref:System.Windows.Controls.Grid> 和位於視窗底部的導覽按鈕。  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/wizardwindow.xaml#10)]  
  
    > [!NOTE]  
    >  在這個 XAML 中所建立的視窗衍生自 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> 基底類別。  在 Visual Studio 中加入自訂 WPF 對話方塊時，建議您從這個類別衍生對話方塊，使其樣式與其他 Visual Studio 對話方塊一致，以避免可能發生的強制回應對話方塊的問題。  如需詳細資訊，請參閱[建立和管理強制回應對話方塊](../extensibility/creating-and-managing-modal-dialog-boxes.md)。  
  
3.  如果您正在開發 Visual Basic 專案，請在 `Window` 項目的 `x:Class` 屬性中，將 `ProjectTemplateWizard` 命名空間從 `WizardWindow` 類別名稱移除。  這個項目位於 XAML 的第一行。  當您完成之後，第一行應如以下範例所示。  
  
    ```  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  開啟 WizardWindow.xaml 檔案的程式碼後置檔案。  
  
5.  以下列程式碼取代此檔案的內容，除了在檔案頂端的`using` 宣告。  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/wizardwindow.xaml.cs#4)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/wizardwindow.xaml.vb#4)]  
  
#### 若要建立第一個精靈頁面 UI  
  
1.  在 ProjectTemplateWizard 專案中，開啟 Page1.xaml 檔案的捷徑功能表，然後選擇 \[**開啟**\] 以設計工具開啟的使用者控制項。  
  
2.  在設計工具的 XAML 檢視中，以下列 XAML 取代目前的 XAML。  XAML 定義內含使用者可以輸入他們想要偵錯的本機網站 URL的文字方塊之UI。  此UI 也包括使用者可以指定專案是否沙箱化的選項按鈕。  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/page1.xaml#11)]  
  
3.  如果您正在開發 Visual Basic 專案，請在 `UserControl` 項目的 `x:Class` 屬性中，將 `ProjectTemplateWizard` 命名空間從 `Page1` 類別名稱移除。  這位於 XAML 的第一行。  當您完成之後，第一行應如下所示。  
  
    ```  
    <UserControl x:Class="Page1"  
    ```  
  
4.  以下列程式碼取代Page1.xaml檔案的內容，除了在檔案頂端的`using` 宣告以外。  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/page1.xaml.cs#2)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/page1.xaml.vb#2)]  
  
#### 若要建立第二個精靈頁面 UI  
  
1.  在 ProjectTemplateWizard 專案中，開啟 Page2.xaml 檔案的捷徑功能表，然後選擇 \[**開啟**\]。  
  
     使用者控制項隨即在設計工具中開啟。  
  
2.  在此 \[XAML\] 檢視中，將目前的XAML替換成下列 XAML。  這個 XAML 定義的 UI 包含用於選擇網站欄之基底型別的下拉式清單、用於指定要在組件庫中顯示網站欄所依據之自訂或內建群組的下拉式方塊，以及用於指定網站欄名稱的文字方塊。  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/page2.xaml#12)]  
  
3.  如果您正在開發 Visual Basic 專案，請在 `UserControl` 項目的 `x:Class` 屬性中，將 `ProjectTemplateWizard` 命名空間從 `Page2` 類別名稱移除。  這位於 XAML 的第一行。  當您完成之後，第一行應如下所示。  
  
    ```  
    <UserControl x:Class="Page2"  
    ```  
  
4.  以下列程式碼來取代Page2.xaml 檔案程式碼後置檔案中，除了在檔案頂端的 `using` 宣告以外的部分內容。  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/page2.xaml.cs#3)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/page2.xaml.vb#3)]  
  
## 實作精靈  
 精靈的主要功能是藉由實作 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 介面來定義。  這個介面會定義 Visual Studio 在精靈啟動和完成時呼叫的方法，以及在精靈執行時的某些時候呼叫的方法。  
  
#### 若要實作精靈  
  
1.  在 ProjectTemplateWizard 專案中，開啟 SiteColumnProjectWizard 程式碼檔案。  
  
2.  以下列程式碼取代這個檔案的整個內容。  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]  
  
## 建立 SharePoint 命令  
 建立兩個呼叫 SharePoint 伺服器物件模型的自訂命令。  一個命令判斷使用者在精靈中輸入的網站 URL 是否有效。  另一個命令會從指定的 SharePoint 網站取得所有欄位型別，讓使用者可以選擇要用哪一個型別做為新網站欄的基礎。  
  
#### 若要定義 SharePoint 命令  
  
1.  在 \[**SharePointCommands**\] 專案中，開啟 Commands 程式碼檔案。  
  
2.  以下列程式碼取代這個檔案的整個內容。  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/sharepointcommands/commands.cs#9)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/sharepointcommands/commands.vb#9)]  
  
## 檢查點  
 在逐步解說中進行至此處時，精靈的所有程式碼都會位於專案中。  建置專案，以確定在編譯時未發生任何錯誤。  
  
#### 若要建置您的專案  
  
1.  在功能表列上，選擇 \[**建置**\]、\[**建置方案**\]。  
  
## 從專案範本移除 key.snk 檔案  
 在[逐步解說：使用專案範本建立網站欄專案項目 &#40;第 1 部分&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)中，您所建立的專案範本包含用來簽署每個網站欄專案執行個體的 key.snk 檔案。  不再需要這個 key.snk 檔案，因為精靈現在會為每個專案產生新的 key.snk 檔案。  請從專案範本移除這個 key.snk 檔案，並移除這個檔案參考。  
  
#### 若要從專案範本移除 key.snk 檔案  
  
1.  在 \[**方案總管**\] 中的 \[**SiteColumnProjectTemplate**\] 節點下，開啟 \[**key.snk**\] 檔案的捷徑功能表，然後選擇 \[**刪除**\]。  
  
2.  在出現的確認對話方塊中，選擇 \[**好**\] 按鈕。  
  
3.  在 \[**SiteColumnProjectTemplate**\] 節點底下，開啟 SiteColumnProjectTemplate.vstemplate 檔案，然後移除下列項目。  
  
    ```  
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
    ```  
  
4.  儲存並關閉檔案。  
  
5.  在 \[**SiteColumnProjectTemplate**\] 節點底下，開啟 ProjectTemplate.csproj 或 ProjectTemplate.vbproj 檔案，然後從移除下列 `PropertyGroup` 項目。  
  
    ```  
    <PropertyGroup>  
      <SignAssembly>true</SignAssembly>  
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
    </PropertyGroup>  
    ```  
  
6.  移除 `None` 項目。  
  
    ```  
    <None Include="key.snk" />  
    ```  
  
7.  儲存並關閉檔案。  
  
## 建立精靈與專案範本的關聯  
 現在您已實作精靈，接著必須建立精靈與 \[**網站欄**\] 專案範本的關聯。  若要執行此作業，必須完成三個程序：  
  
1.  使用強式名稱簽署精靈組件。  
  
2.  取得精靈組件的公開金鑰語彙基元。  
  
3.  在 \[**網站欄**\] 專案範本的 .vstemplate 檔案中加入精靈組件的參考。  
  
#### 若要使用強式名稱簽署精靈組件  
  
1.  在 \[**方案總管**\] 中開啟**ProjectTemplateWizard**專案的捷徑功能表，然後選擇 \[**屬性**\]。  
  
2.  選取 \[**簽署**\] 索引標籤上的 \[**簽署組件**\] 核取方塊。  
  
3.  在 \[**選擇強式名稱金鑰檔**\] 清單中，選取 \[**\<新增...\>**\]。  
  
4.  在 \[**建立強式名稱金鑰**\] 對話方塊中，為新的金鑰檔輸入名稱，並清除 \[**以密碼保護我的金鑰檔**\] 核取方塊，然後選取**好** 按鈕。  
  
5.  開啟 \[**ProjectTemplateWizard**\] 專案的捷徑功能表，然後選取 \[**組建**\] 建立 ProjectTemplateWizard.dll 檔案。  
  
#### 若要取得精靈組件的公開金鑰語彙基元  
  
1.  在\[**\[開始\]功能表**\] 上，選取 \[**所有程式**\]，再選取\[**Microsoft Visual Studio**\] ，選取 \[**Visual Studio Tools**\]，然後選擇 \[**開發人員命令提示字元**\]。  
  
     開啟 \[Visual Studio 命令提示字元\] 視窗。  
  
2.  執行下列命令，將 *PathToWizardAssembly* 取代為 ProjectTemplateWizard 專案的內建 ProjectTemplateWizard.dll 組件位於您開發電腦上的完整路徑：  
  
    ```  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     ProjectTemplateWizard.dll 組件的公開金鑰語彙基元會寫入至 \[Visual Studio 命令提示字元\] 視窗。  
  
3.  讓 \[Visual Studio 命令提示字元\] 視窗保持開啟。  在下一個程序中，您將會需要這個公開金鑰語彙基元。  
  
#### 若要在 .vstemplate 檔案中加入精靈組件的參考  
  
1.  在 \[**方案總管**\] 中，展開 \[**SiteColumnProjectTemplate**\] 專案節點並開啟 SiteColumnProjectTemplate.vstemplate 檔案。  
  
2.  在檔案結尾附近，於 `</TemplateContent>` 與 `</VSTemplate>` 標記之間加入 `WizardExtension` 項目。  將`PublicKeyToken`屬性的*your token*值取代為您在上一個程序取得的公開金鑰語彙基元。  
  
    ```  
    <WizardExtension>  
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>  
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     如需 `WizardExtension` 項目的詳細資訊，請參閱 [WizardExtension 項目 &#40;Visual Studio 範本&#41;](../extensibility/wizardextension-element-visual-studio-templates.md)。  
  
3.  儲存並關閉檔案。  
  
## 將可取代的參數加入至專案範本中的 Elements.xml 檔案  
 將數個可取代的參數加入至 SiteColumnProjectTemplate 專案中的 Elements.xml 檔案。  這些參數會以您先前定義之 `SiteColumnProjectWizard` 類別中的 `RunStarted` 方法初始化。  當使用者建立網站欄專案時，Visual Studio 會自動在新專案中，將 Elements.xml 檔案中的這些參數取代為使用者在精靈中所指定的值。  
  
 可取代的參數是以貨幣符號 \($\) 字元開頭及結尾的語彙基元。  除了定義您自己的可取代參數以外，您也可以使用 SharePoint 專案系統所定義和初始化的內建參數。  如需詳細資訊，請參閱[可置換的參數](../sharepoint/replaceable-parameters.md)。  
  
#### 若要將可取代的參數加入至 Elements.xml 檔案  
  
1.  在SiteColumnProjectTemplate專案中，以下列 XML 取代 Elements.xml 檔案的內容。  
  
    ```  
  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
             Name="$fieldname$"   
             DisplayName="$fieldname$"   
             Type="$selectedfieldtype$"   
             Group="$selectedgrouptype$">  
      </Field>  
    </Elements>  
    ```  
  
     新的 XML 會將 `Name`、`DisplayName`、`Type` 和 `Group` 屬性的值變更為可取代的參數。  
  
2.  儲存並關閉檔案。  
  
## 將精靈加入至 VSIX 套件  
 若要使用包含網站欄專案範本的 VSIX 套件來部署精靈，請在 VSIX 專案的 source.extension.vsixmanifest 檔案中加入精靈專案和 SharePoint 命令專案的參考。  
  
#### 若要將精靈加入至 VSIX 套件  
  
1.  在 \[**方案總管**\] 的 \[**SiteColumnProjectItem**\] 專案中，開啟 \[**source.extension.vsixmanifest**\] 檔案的捷徑功能表，然後選擇 \[**開啟**\]。  
  
     Visual Studio 會在資訊清單編輯器中開啟檔案。  
  
2.  在編輯器中的 \[**資產**\] 索引標籤上，選擇 \[**新增**\] 按鈕。  
  
     \[**加入新資產**\] 對話方塊隨即開啟。  
  
3.  在 \[**輸入**\] 清單中，選取 \[**Microsoft.VisualStudio.Assembly**\]。  
  
4.  在 \[**來源**\] 清單中，選取 \[**在目前方案中的專案**\]。  
  
5.  在 \[**Project**\] 清單中，選擇 \[**ProjectTemplateWizard**\]，然後選擇 \[**確定**\] 按鈕。  
  
6.  在編輯器中的 \[**資產**\] 索引標籤上，再一次選擇 \[**新增**\] 按鈕。  
  
     \[**加入新資產**\] 對話方塊隨即開啟。  
  
7.  在 \[**輸入**\] 清單中，輸入 \[**SharePoint.Commands.v4**\]。  
  
8.  在 \[**來源**\] 清單中，選取 \[**在目前方案中的專案**\]。  
  
9. 在 \[**專案**\] 清單中，選取 \[**SharePointCommands**\] 專案，然後選擇 \[**好**\] 按鈕。  
  
10. 在功能表列上，選擇 \[**組建**\]， \[**建置方案**\]，然後確定方案在建立時未發生錯誤。  
  
## 測試精靈  
 您現在可以測試精靈。  首先，在 Visual Studio 的實驗執行個體中開始偵錯 SiteColumnProjectItem 方案。  接著，在 Visual Studio 的實驗執行個體中測試網站欄專案的精靈。  最後，建置並執行專案，確認網站欄功能正常。  
  
#### 若要開始偵錯方案  
  
1.  以系統管理員憑證重新啟動 Visual Studio，然後開啟 SiteColumnProjectItem 方案。  
  
2.  在 ProjectTemplateWizard 專案中開啟 SiteColumnProjectWizard 程式碼檔案，然後將中斷點加入至 `RunStarted` 方法內的第一行程式碼中。  
  
3.  在功能表列選擇 \[**偵錯**\]、\[**例外狀況**\]。  
  
4.  在 \[**例外狀況**\] 對話方塊中，請確定 \[**Common Language Runtime 例外狀況**\] 的 \[**擲回**\] 和 \[**使用者未處理**\] 核取方塊均已清除，然後選取**確定** 按鈕。  
  
5.  您可以選擇 \[**F5**\] 鍵，或在功能表列上，選擇 \[**偵錯**\]、 \[**啟動偵錯**\]來開始偵錯。  
  
     Visual Studio 會將擴充功能安裝至 %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0Exp\\Extensions\\Contoso\\Site Column\\1.0，並啟動 Visual Studio 的實驗執行個體。  您將會在 Visual Studio 的這個執行個體中測試專案項目。  
  
#### 若要在 Visual Studio 中測試精靈  
  
1.  在 Visual Studio 的實驗執行個體中，在 \[**檔案**\] 功能表列上的 \[**新增**\] 中，選擇 \[**專案**\]。  
  
2.  展開 \[**Visual C\#**\] 節點或 \[**Visual Basic**\] 節點 \(視專案範本支援的語言\)，展開 \[**SharePoint**\] 節點，然後選取 \[**2010**\] 節點。  
  
3.  在專案範本清單中，選擇 \[**Site Column**\] ，將命專案名為**SiteColumnWizardTest**，然後選擇 \[**確定**\] 按鈕。  
  
4.  確認另一個 Visual Studio 執行個體中的程式碼在您之前於 `RunStarted` 方法中設定的中斷點停止。  
  
5.  選擇 \[**F5**\] 鍵，或在功能表列上選擇 \[**偵錯**\]、 \[**繼續**\]，來繼續偵錯專案。  
  
6.  在 \[**SharePoint 自訂精靈**\] 中，輸入要用於偵錯的網站 URL，然後選擇 \[**下一步**\] 按鈕。  
  
7.  在 \[**SharePoint 自訂精靈**\] 的第二個頁面中進行以下選擇：  
  
    -   選擇 \[**類型**\] 清單中的 \[**Boolean**\]。  
  
    -   在 \[**群組**\] 清單中，選取 \[**自訂My Yes\/No Column**\]。  
  
    -   在 \[**名稱**\] 方塊中，輸入My Yes\/No Column，然後選擇 \[**結束**\] 按鈕。  
  
     在 \[**方案總管**\] 中，新專案會出現並包含名為 \[**Field1**\] 之專案項目，而且 Visual Studio 會在編輯器中開啟此專案的 Elements.xml 檔案。  
  
8.  確認 Elements.xml 包含您在精靈中指定的值。  
  
#### 若要在 SharePoint 中測試網站欄  
  
1.  在 Visual Studio 的實驗執行個體中選取 F5鍵。  
  
     網站欄會封裝並部署至專案的 \[**網站 URL**\] 屬性所指定的 SharePoint 網站。  Web 瀏覽器會開啟此網站的預設頁面。  
  
    > [!NOTE]  
    >  如果出現 \[**已停用指令碼偵錯**\] 對話方塊，請選擇 \[**是**\] 繼續偵錯專案。  
  
2.  請選取 \[**網站動作**\] 功能表上的 \[**網站設定**\]。  
  
3.  在網站設定頁面中，在 \[**組件庫**\] 下，選擇 \[**網站欄**\] 連結。  
  
4.  在網站欄清單中，請確認有一個 \[**Custom Yes\/No Columns**\] 群組，其中包含名為 \[**My Yes\/No Column**\] 的欄，然後關閉網頁瀏覽器。  
  
## 清理開發電腦  
 在您完成測試專案項目之後，請從 Visual Studio 的實驗執行個體中移除專案範本。  
  
#### 若要清理開發電腦  
  
1.  在 Visual Studio 的實驗執行個體中，選擇 \[**工具**\] 功能表列上的 \[**擴充和更新**\]。  
  
     \[**擴充功能和更新**\] 對話方塊隨即開啟。  
  
2.  在擴充功能清單中，請選取 \[**設置行**\]，然後選擇 \[**解除安裝**\] 按鈕。  
  
3.  在出現的對話方塊，請選擇 \[**是**\] 按鈕，確認您要解除安裝擴充功能，然後選擇 \[**現在再開始**\] 按鈕完成解除安裝。  
  
4.  關閉執行個體 \(Visual Studio 的實驗執行個體，以及其中有開啟 CustomActionProjectItem 專案的執行個體\)。  
  
     如需如何部署[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能的詳細資訊，請參閱[傳送 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)。  
  
## 請參閱  
 [逐步解說：使用專案範本建立網站欄專案項目 &#40;第 1 部分&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [如何：搭配專案範本使用精靈](~/extensibility/how-to-use-wizards-with-project-templates.md)  
  
  
---
title: "Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1 | Microsoft Docs"
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
  - "SharePoint project items, creating custom templates"
  - "SharePoint project items, defining your own types"
  - "project items [SharePoint development in Visual Studio], defining your own types"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: 41ed9c1c-4239-4d80-934b-975fde744288
caps.latest.revision: 152
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 151
---
# Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1
  您可以建立自己的專案項目類型，藉此擴充 Visual Studio 中的 SharePoint 專案系統。  在本逐步解說中，您將建立可加入至 SharePoint 專案的專案項目，以便在 SharePoint 網站上建立自訂動作。  自訂動作會將功能表項目加入至 SharePoint 網站的 \[**網站動作**\] 功能表。  
  
 本逐步解說將示範下列工作：  
  
-   建立為自訂動作定義新的 SharePoint 專案項目類型的 Visual Studio 擴充功能。  新專案項目類型會實作幾個自訂功能：  
  
    -   捷徑功能表可做為專案項目其他相關工作的起點，例如在 Visual Studio 中顯示自訂動作的設計工具。  
  
    -   開發人員變更專案項目以及包含該專案項目之專案的特定屬性時執行的程式碼。  
  
    -   出現在 \[**方案總管**\] 中專案項目旁邊的自訂圖示。  
  
-   建立專案項目的 Visual Studio 項目範本。  
  
-   建置 Visual Studio Extension \(VSIX\) 套件以部署專案項目範本和擴充組件。  
  
-   偵錯和測試專案項目。  
  
 這是獨立的逐步解說。  完成本逐步解說之後，您可以將精靈加入至項目範本來增強專案項目。  如需詳細資訊，請參閱[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)。  
  
> [!NOTE]  
>  您可以從下列位置取得本逐步解說所含之完成的專案、程式碼和其他檔案：[http:\/\/go.microsoft.com\/fwlink\/?LinkId\=191369](http://go.microsoft.com/fwlink/?LinkId=191369)。  
  
## 必要條件  
 開發電腦上需要下列元件才能完成此逐步解說：  
  
-   支援的 Microsoft Windows、SharePoint 和 Visual Studio 版本。  如需詳細資訊，請參閱[開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。  這個逐步解說使用 SDK 中的 **VSIX 專案**範本建立 VSIX 套件，以部署專案項目。  如需詳細資訊，請參閱[Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 了解下列概念有助於完成此逐步解說 \(但非必要\)：  
  
-   SharePoint 中的自訂動作。  如需自訂動作的詳細資訊，請參閱[自訂動作](http://go.microsoft.com/fwlink/?LinkId=177800)。  
  
-   Visual Studio 中的項目範本。  如需詳細資訊，請參閱[在 Visual Studio 中建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)。  
  
## 建立專案  
 若要完成這個逐步解說，您必須建立三個專案：  
  
-   VSIX 專案。  這個專案會建立 VSIX 套件，以部署 SharePoint 專案項目。  
  
-   項目範本專案。  這個專案會建立可用以將 SharePoint 專案項目加入至 SharePoint 專案的項目範本。  
  
-   類別庫專案。  這個專案會實作 Visual Studio 擴充功能，以定義 SharePoint 專案項目的行為。  
  
 從建立這些專案開始進行此逐步解說。  
  
#### 若要建立 VSIX 專案  
  
1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在功能表列上，選擇 \[**檔案**\]、\[**新增**\]、\[**專案**\]。  
  
3.  在 \[**新增專案**\] 對話方塊頂端的清單中，確定已選取 \[**.NET Framework 4.5**\]。  
  
4.  在 \[**新增專案**\] 對話方塊中，展開 \[**Visual C\#**\] 或 \[**Visual Basic**\] 節點，然後選擇 \[**擴充性**\] 節點。  
  
    > [!NOTE]  
    >  \[**擴充性**\] 節點只有在安裝 Visual Studio SDK 時才可使用。  如需詳細資訊，請參閱本主題稍早討論的＜必要條件＞一節。  
  
5.  選擇 **VSIX 專案** 範本  
  
6.  在 \[**名稱**\] 文字方塊中，輸入 **CustomActionProjectItem**，然後選擇 \[**確定**\] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將 **CustomActionProjectItem** 專案加入至 \[**方案總管**\]。  
  
#### 若要建立項目範本專案  
  
1.  在 \[**方案總管**\] 中，開啟 \[**方案**\] 節點的捷徑功能表，選擇 \[**加入**\]，然後選擇 \[新增專案\]。  
  
    > [!NOTE]  
    >  在 Visual Basic 專案中，方案節點只有在已選取[NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/zh-tw/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)中的 \[**永遠顯示方案**\] 核取方塊時，才會出現在 \[**方案總管**\] 中。  
  
2.  在 \[**新增專案**\] 對話方塊頂端的清單中，確定已選取 \[**.NET Framework 4.5**\]。  
  
3.  在 \[**新增專案**\] 對話方塊中，展開 \[**Visual C\#**\] 或 \[**Visual Basic**\] 節點，然後選擇 \[**擴充性**\] 節點。  
  
4.  在專案範本清單中，選擇 \[**C\# 項目範本**\] 或 \[**Visual Basic 項目範本**\]。  
  
5.  在 \[**名稱**\] 文字方塊中，輸入 **ItemTemplate**，然後選擇 \[**確定**\] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將 **ItemTemplate** 專案加入至方案。  
  
#### 若要建立擴充功能專案  
  
1.  在 \[**方案總管**\] 中，開啟 \[**方案**\] 節點的捷徑功能表，選擇 \[**加入**\]，然後選擇 \[新增專案\]。  
  
2.  在 \[**新增專案**\] 對話方塊頂端的清單中，確定已選取 \[**.NET Framework 4.5**\]。  
  
3.  在 \[**新增專案**\] 對話方塊中，展開 \[**Visual C\#**\] 或 \[**Visual Basic**\] 節點，選擇 \[**Windows**\] 節點，然後選擇 \[**類別庫**\] 專案範本。  
  
4.  在 \[**名稱**\] 文字方塊中，輸入 **ProjectItemDefinition**，然後選擇 \[**確定**\] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 隨即將 \[**ProjectItemDefinition**\] 專案加入至方案，然後開啟預設的 Class1 程式碼檔。  
  
5.  從專案刪除 Class1 程式碼檔。  
  
## 設定擴充功能專案  
 在您撰寫程式碼定義 SharePoint 專案項目類型之前，必須先將程式碼檔案和組件參考加入至擴充功能專案。  
  
#### 若要設定專案  
  
1.  在 \[**方案總管**\]，開啟 **ProjectItemDefinition** 專案的捷徑功能表，選取 \[**加入**\]，然後選取 \[**新增項目**\]。  
  
2.  在專案項目清單中，選擇 \[**程式碼檔**\]。  
  
3.  在 \[**名稱**\] 方塊中，輸入適當副檔名的名稱 **CustomAction** ，然後選擇 \[**加入**\] 按鈕。  
  
4.  在 \[**方案總管**\] 中，開啟 **ProjectItemDefinition** 專案的捷徑功能表，選取 \[**加入參考**\]。  
  
5.  在 \[**參考管理員– ProjectItemDefinition**\] 對話方塊中，選取 \[**組件**\] 節點，然後選取 \[**Framework**\] 節點。  
  
6.  選取下列每個組件旁邊的核取方塊：  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
7.  選取 \[**擴充功能**\] 節點，以 Microsoft.VisualStudio.Sharepoint 組件旁邊的核取方塊，然後選擇 \[**確認**\] 按鈕。  
  
## 定義新的 SharePoint 專案項目類型  
 建立實作 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 介面的類別，以定義新專案項目類型的行為。  在您要定義新的專案項目類型時實作此介面。  
  
#### 若要定義新的 SharePoint 專案項目類型  
  
1.  在 ProjectItemDefinition 專案中，開啟 CustomAction 程式碼檔案。  
  
2.  使用下列程式碼取代此檔案中的程式碼。  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/projectitemdefinition/customaction.vb#1)]  
  
## 在方案總管中建立專案項目的圖示  
 當您建立自訂 SharePoint 專案項目時，可以將影像 \(圖示或點陣圖\) 與專案項目產生關聯。  這個影像會出現在 \[**方案總管**\] 中該專案項目的旁邊。  
  
 在下列程序中，您會建立專案項目的圖示，並且將圖示嵌入擴充組件。  您之前建立之 `CustomActionProjectItemTypeProvider` 類別的 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> 會參考此圖示。  
  
#### 若要建立專案項目的自訂圖示  
  
1.  在 \[**方案總管**\] 中，開啟 **ProjectItemDefinition** 專案的捷徑功能表，選取 \[**加入**\]，然後選取 \[**新增項目**\]。  
  
2.  在專案項目清單中，選取 \[**圖示檔**\] 項目。  
  
    > [!NOTE]  
    >  在 Visual Basic 專案中，您必須選擇 \[**一般**\] 節點以顯示 \[**圖示檔**\] 項目。  
  
3.  在 \[**名稱**\] 文字方塊中輸入 **CustomAction\_SolutionExplorer.ico**，然後選擇 \[**新增**\] 按鈕。  
  
     新圖示隨即開啟於 \[**影像編輯器**\] 中。  
  
4.  編輯 16x16 版的圖示檔，以便能夠辨識其設計，然後儲存圖示檔。  
  
5.  在 \[**方案總管**\] 中，選擇 \[**CustomAction\_SolutionExplorer.ico**\]。  
  
6.  在 \[**屬性**\] 視窗中，選取 \[**建置動作**\] 屬性旁邊的箭號。  
  
7.  在出現的清單中，選取 \[**內嵌資源**\]。  
  
## 檢查點  
 在逐步解說中進行至此處時，專案項目的所有程式碼都會位於專案中。  建置專案，以驗證在編譯時未發生任何錯誤。  
  
#### 若要建置您的專案  
  
1.  開啟 **ProjectItemDefinition** 專案的捷徑功能表，然後選擇 \[**建置**\]。  
  
## 建立 Visual Studio 項目範本  
 若要讓其他開發人員使用您的專案項目，您必須建立專案範本或項目範本。  開發人員會在 Visual Studio 中透過建立新專案或在現有專案中加入項目的方式，使用這些範本建立專案項目的執行個體。  在本逐步解說中，請使用 ItemTemplate 專案來設定您的專案項目。  
  
#### 若要建立項目範本  
  
1.  從 ItemTemplate 專案刪除 Class1 程式碼檔案。  
  
2.  在 ItemTemplate 專案中，開啟 ItemTemplate.vstemplate 檔案。  
  
3.  以下列 XML 取代檔案的內容，然後儲存並關閉檔案。  
  
    > [!NOTE]  
    >  下列 XML 適用於 Visual C\# 項目範本。  如果您要建立 Visual Basic 項目範本，請將 `ProjectType` 項目的值取代為 `VisualBasic`。  
  
    ```  
  
    <VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
      <TemplateData>  
        <DefaultName>CustomAction</DefaultName>  
        <Name>Custom Action</Name>  
        <Description>SharePoint Custom Action by Contoso</Description>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>1000</SortOrder>  
        <Icon>ItemTemplate.ico</Icon>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
      <TemplateContent>  
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\Elements.xml">Elements.xml</ProjectItem>  
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\SharePointProjectItem.spdata">CustomAction.spdata</ProjectItem>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
     此檔案會定義項目範本的內容和行為。  如需此檔案內容的詳細資訊，請參閱 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)。  
  
4.  在 \[**方案總管**\] 中，開啟 **ItemTemplate** 專案的捷徑功能表，選取 \[**加入**\]，然後選取 \[**新增項目**\]。  
  
5.  在 \[**加入新項目。**\] 對話方塊中，選取 \[**文字檔**\] 範本。  
  
6.  在 \[**名稱**\] 文字方塊中輸入 **CustomAction.spdata**，然後選擇 \[**新增**\] 按鈕。  
  
7.  將下列 XML 加入至 CustomAction.spdata 檔案，然後儲存並關閉檔案。  
  
    ```  
  
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"   
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />  
      </Files>  
    </ProjectItem>  
    ```  
  
     此檔案包含專案項目所包含檔案的相關資訊。  `ProjectItem` 項目的 `Type` 屬性必須設為與傳遞至專案項目定義 \(您之前在本逐步解說中建立的 `CustomActionProjectItemTypeProvider` 類別\) 上的 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> 相同的字串。  如需 .spdata 檔案內容的詳細資訊，請參閱 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)。  
  
8.  在 \[**方案總管**\] 中，開啟 **ItemTemplate** 專案的捷徑功能表，選取 \[**加入**\]，然後選取 \[**新增項目**\]。  
  
9. 在 \[**加入新項目**\] 對話方塊中，選擇 \[**XML 檔**\] 範本。  
  
10. 在 \[**名稱**\] 文字方塊中輸入 **Elements.xml**，然後選擇 \[**新增**\] 按鈕。  
  
11. 以下列 XML 取代 Elements.xml 檔案的內容，然後儲存並關閉檔案。  
  
    ```  
  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="Replace this with a GUID or some other unique string"  
                    GroupId="SiteActions"  
                    Location="Microsoft.SharePoint.StandardMenu"  
                    Sequence="1000"  
                    Title="Replace this with your title"  
                    Description="Replace this with your description" >  
        <UrlAction Url="~site/Lists/Tasks/AllItems.aspx"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     此檔案會定義在 SharePoint 網站的 \[**網站動作**\] 功能表上建立功能表項目的預設自訂動作。  當使用者選擇功能表項目時，`UrlAction` 中指定的 URL 就會在 Web 瀏覽器中開啟。  如需可用於定義自訂動作之 XML 項目的詳細資訊，請參閱[自訂動作定義](http://go.microsoft.com/fwlink/?LinkId=177801)。  
  
12. \(選擇性\) 開啟 ItemTemplate.ico 檔案並加以修改，使其具有您可辨識的設計。  此圖示將在 \[**加入新項目**\] 對話方塊中該專案項目旁顯示。  
  
13. 在 \[**方案總管**\] 中，開啟 **ItemTemplate** 專案的捷徑功能表，然後選擇 \[**卸載專案**\]。  
  
14. 重新開啟 \[**ItemTemplate**\] 專案的捷徑功能表，然後選取 \[**編輯 ItemTemplate.csproj**\] 或 \[**編輯 ItemTemplate.vbproj**\]。  
  
15. 在專案檔中尋找下列 `VSTemplate` 項目。  
  
    ```  
    <VSTemplate Include="ItemTemplate.vstemplate">  
    ```  
  
16. 以下列 XML 取代 `VSTemplate` 的內容，然後儲存並關閉檔案。  
  
    ```  
    <VSTemplate Include="ItemTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     `OutputSubPath` 項目會在您建置專案時用以建立項目範本的路徑中，指定其他資料夾。  此處指定的資料夾是用來確定項目範本只有在使用者開啟 **加入新項目** 的對話方塊、展開 **SharePoint** 節點然後選擇 **2010** 節點時，才可存取。  
  
17. 在 \[**方案總管**\] 中，開啟 **ItemTemplate** 專案的捷徑功能表，然後選擇 \[**重新載入專案**\]。  
  
## 建立 VSIX 套件以部署專案項目  
 若要部署擴充功能，請在您的方案中使用 VSIX 專案，以建立 VSIX 套件。  首先，修改 VSIX 專案包含的 source.extension.vsixmanifest 檔案，來設定 VSIX 套件。  接著，建置方案來建立 VSIX 套件。  
  
#### 若要設定和建立 VSIX 套件  
  
1.  在 \[**方案總管**\] 中，開啟 CustomActionProjectItem 專案裡 **source.extension.vsixmanifest** 檔案的捷徑功能表，然後選擇 \[**開啟**\]。  
  
     Visual Studio 會在資訊清單編輯器中開啟檔案。  source.extension.vsixmanifest 檔案是所有 VSIX 套件需要之 extension.vsixmanifest 檔案的基準。  如需這個檔案的詳細資訊，請參閱[VSIX 擴充結構描述參考](http://msdn.microsoft.com/zh-tw/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在 \[**專案名稱**\] 方塊中，輸入 **Custom Action Project Item**。  
  
3.  在 \[**作者**\] 方塊中，輸入 **Contoso**。  
  
4.  在 \[**說明**\] 方塊中，輸入**代表自訂動作的 SharePoint 專案項目**。  
  
5.  在 \[**資產**\] 索引標籤上，選擇 \[**新增**\] 按鈕。  
  
     \[**加入新資產**\] 對話方塊隨即出現。  
  
6.  在 \[**輸入**\] 清單中，選取 \[**Microsoft.VisualStudio.ItemTemplate**\]。  
  
    > [!NOTE]  
    >  這個值對應於 extension.vsixmanifest 檔案中的 `ItemTemplate` 項目。  此項目會識別 VSIX 套件中包含專案項目範本的子資料夾。  如需詳細資訊，請參閱[NIB: ItemTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/zh-tw/1d489e54-c1c5-4f96-a510-6c2640867ff0)。  
  
7.  在 \[**來源**\] 清單中，選取 \[**在目前方案中的專案**\]。  
  
8.  在 \[**專案**\] 清單中，選擇 \[**ItemTemplate**\]，然後選擇 \[**確定**\] 按鈕。  
  
9. 在 \[**資產**\] 索引標籤中，再選取 \[**新增**\] 按鈕。  
  
     \[**加入新資產**\] 對話方塊隨即出現。  
  
10. 在 \[**輸入**\] 清單中，選取 \[**Microsoft.VisualStudio.MefComponent**\]。  
  
    > [!NOTE]  
    >  這個值對應於 extension.vsixmanifest 檔案中的 `MefComponent` 項目。  這個項目指定 VSIX 套件中的擴充組件名稱。  如需詳細資訊，請參閱[NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/zh-tw/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
11. 在 \[**來源**\] 清單中，選取 \[**在目前方案中的專案**\]。  
  
12. 在**專案**清單中，選擇 \[**ProjectItemDefinition**\]。  
  
13. 選擇 \[**確定**\] 按鈕。  
  
14. 在功能表列上，選擇 \[**組建**\]， \[**建置方案**\]，然後確定專案在編譯時未發生錯誤。  
  
15. 確定 CustomActionProjectItem 專案的建置輸出資料夾包含 CustomActionProjectItem.vsix 檔。  
  
     根據預設，建置輸出資料夾是 ...\\bin\\Debug 資料夾，在包含 CustomActionProjectItem 專案的資料夾底下。  
  
## 測試專案項目  
 您現在可以測試專案項目。  首先，在 Visual Studio 的實驗執行個體中開始偵錯 CustomActionProjectItem 方案。  接著，在 Visual Studio 的實驗執行個體中，測試 SharePoint 專案中的 **\[自訂動作\]** 專案項目。  最後，建置並執行 SharePoint 專案，確認自訂動作功能正常。  
  
#### 若要開始偵錯方案  
  
1.  以系統管理員權限重新啟動 Visual Studio 並且開啟 \[CustomActionProjectItem\] 專案。  
  
2.  開啟 CustomAction 程式碼檔，然後將中斷點加入至 `InitializeType` 方法中的第一行程式碼。  
  
3.  選擇 **F5** 鍵開始偵錯。  
  
     Visual Studio 會將擴充功能安裝至 %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\10.0Exp\\Extensions\\Contoso\\Custom Action Project Item\\1.0，並啟動 Visual Studio 的實驗執行個體。  您將會在 Visual Studio 的這個執行個體中測試專案項目。  
  
#### 若要在 Visual Studio 中測試專案項目  
  
1.  在 Visual Studio 的實驗執行個體中，在 \[**檔案**\] 功能表列上的 \[**新增**\] 中，選擇 \[**專案**\]。  
  
2.  展開 \[**Visual C\#**\] 或 \[**Visual Basic**\] \(視項目範本所支援的語言而定\)，然後展開 \[**SharePoint**\] 節點，再選擇 \[**2010**\] 節點。  
  
3.  在專案範本清單中，選擇 \[**SharePoint 2010 專案**\]。  
  
4.  在 \[**名稱**\] 方塊中，輸入 **CustomActionTest**，然後選擇 \[**確定**\] 按鈕。  
  
5.  在 \[**SharePoint 自訂精靈**\] 中，輸入要用於偵錯的網站 URL，然後選擇 \[**完成**\] 按鈕。  
  
6.  在 \[**方案總管**\] 中，開啟專案節點的捷徑功能表，選取 \[**加入**\]，然後選擇 \[**新增項目**\]。  
  
7.  在 \[**加入新項目**\] 對話方塊中，選擇 \[**SharePoint**\] 節點底下的 \[**2010**\] 節點。  
  
     確認 \[**自訂動作**\] 項目出現在專案項目的清單中。  
  
8.  選取 \[**自訂動作**\] 項目，然後選擇 \[**加入**\] 按鈕。  
  
     Visual Studio 會將名為 \[**CustomAction1**\] 的項目加入至專案，並在編輯器中開啟 Elements.xml 檔。  
  
9. 確認另一個 Visual Studio 執行個體中的程式碼在您之前於 `InitializeType` 方法中設定的中斷點停止。  
  
10. 選擇 \[**F5**\] 鍵繼續偵錯專案。  
  
11. 在 Visual Studio 的實驗執行個體中， \[**方案總管**\] 下，開啟 \[**CustomAction1**\] 節點的捷徑功能表，然後選擇 \[**檢視自訂動作設計工具**\]。  
  
12. 確認訊息方塊出現，然後選擇 \[**確定**\] 按鈕。  
  
     您可以使用此捷徑功能表為開發人員提供額外的選項或命令，例如顯示自訂動作的設計工具。  
  
13. 在功能表列上選擇 \[**檢視**\]、\[**輸出**\]。  
  
     \[**輸出**\] 視窗隨即開啟。  
  
14. 在 \[**方案總管**\] 中，開啟 \[**CustomAction1**\] 項目的捷徑功能表，然後將其名稱變更為 **MyCustomAction**。  
  
     在 \[**輸出**\] 視窗中，會顯示確認訊息：  這個訊息是由 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> 事件處理常式撰寫並在 `CustomActionProjectItemTypeProvider` 類別中定義。  當開發人員修改專案項目時，您可以處理此事件和其他專案項目事件以實作自訂行為。  
  
#### 若要測試 SharePoint 中的自訂動作  
  
1.  在 Visual Studio 的實驗執行個體中，開啟 Elements.xml 檔，這個檔案是 \[**MyCustomAction**\] 專案項目的子系。  
  
2.  在 Elements.xml 檔案中，進行下列變更，然後儲存檔案：  
  
    -   在 `CustomAction` 項目中，將 `Id` 屬性設定為 GUID 或其他特殊字串，如下列範例所示：  
  
        ```  
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"  
        ```  
  
    -   在 `CustomAction` 元素中，設定 `Title` 屬性，如以下範例所示：  
  
        ```  
        Title="SharePoint Developer Center"  
        ```  
  
    -   在 `CustomAction` 元素中，設定 `Description` 屬性，如以下範例所示：  
  
        ```  
        Description="Opens the SharePoint Developer Center Web site."  
        ```  
  
    -   在 `UrlAction` 元素中，設定 `Url` 屬性，如以下範例所示：  
  
        ```  
        Url="http://msdn.microsoft.com/sharepoint/default.aspx"  
        ```  
  
3.  選擇 F5 鍵。  
  
     自訂動作將會封裝並部署至專案中， \[**網站 URL**\] 屬性指定的 SharePoint 網站。  Web 瀏覽器會開啟此網站的預設頁面。  
  
    > [!NOTE]  
    >  如果出現 \[**已停用指令碼偵錯**\] 對話方塊，請選擇 \[**是**\] 繼續偵錯專案。  
  
4.  在 \[**設置動作**\] 功能表上，選擇 \[**SharePoint 開發人員中心**\]\]，確認瀏覽器開啟網站 http:\/\/msdn.microsoft.com\/sharepoint\/default.aspx，然後關閉瀏覽器。  
  
## 清理開發電腦  
 在您完成測試專案項目之後，請從 Visual Studio 的實驗執行個體中移除專案項目範本。  
  
#### 若要清理開發電腦  
  
1.  在 Visual Studio 的實驗執行個體中，選擇 \[**工具**\] 功能表列上的 \[**擴充和更新**\]。  
  
     \[**擴充功能和更新**\] 對話方塊隨即開啟。  
  
2.  在擴充功能清單中，選擇 \[**自訂動作專案項目**\]，然後選取 \[**解除安裝**\] 按鈕。  
  
3.  在所顯示的對話方塊中，選擇 \[**是**\]，確認您要解除安裝擴充功能。  
  
4.  選擇 \[**重新開始**\] 按鈕以完成解除安裝。  
  
5.  關閉執行個體 \(Visual Studio 的實驗執行個體，以及其中有開啟 CustomActionProjectItem 專案的執行個體\)。  
  
## 後續步驟  
 當您完成本逐步解說之後，您可以將精靈加入至項目範本。  當使用者將 \[自訂動作\] 專案項目加入至 SharePoint 專案時，精靈會收集動作的相關資訊 \(例如其位置，以及選取動作時要巡覽的目標 URL\)，並將此資訊加入至新專案項目中的 Elements.xml 檔案。  如需詳細資訊，請參閱[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)。  
  
## 請參閱  
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [Image Editor for Icons](/visual-cpp/windows/image-editor-for-icons)   
 [Creating an Icon or Other Image &#40;Image Editor for Icons&#41;](/visual-cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  
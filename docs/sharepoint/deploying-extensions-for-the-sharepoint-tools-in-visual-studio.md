---
title: "Deploying Extensions for the SharePoint Tools in Visual Studio"
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
  - "SharePoint development in Visual Studio, deploying extensions"
ms.assetid: 69927d95-acdf-4fd8-ac43-28e9a7fa8a38
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Deploying Extensions for the SharePoint Tools in Visual Studio
  若要部署 SharePoint 工具擴充功能，請建立 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 擴充功能 \(VSIX\) 套件，其中包含擴充功能組件和要與擴充功能一起散發的任何其他檔案。  VSIX 套件為符合「開放式封裝慣例」\(OPC\) 標準的壓縮檔。  VSIX 套件有 .vsix 副檔名。  
  
 建立 VSIX 套件之後，其他使用者就可以執行 .vsix 檔案來安裝您的擴充功能。  當使用者安裝您的擴充功能時，所有檔案都會安裝到 %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0\\Extensions 資料夾。  若要部署擴充功能，您可以將 VSIX 套件上載至 [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) 網站，或使用其他方式將套件散發至客戶，例如在網路共用或其他網站上裝載套件。  
  
 如需建立 VSIX 套件並將其部署到 [Visual Studio 組件庫](http://go.microsoft.com/fwlink/?LinkID=123847) \(英文\) 的詳細資訊，請參閱[傳送 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)。  
  
 您可以使用 Visual Studio 中的 \[**VSIX 專案**\] 範本，建立 VSIX 套件，或可以手動建立 VSIX 套件。  
  
## 使用 VSIX 專案建立 VSIX 套件  
 您可以使用 Visual Studio SDK 提供的 \[**VSIX 專案**\] 範本建立 SharePoint 工具擴充功能的 VSIX 套件。  使用 VSIX 專案與手動建立 VSIX 套件相比，可提供數個優點：  
  
-   當您建立專案時，Visual Studio 會自動產生 VSIX 套件。  系統會為您執行將部署檔案加入至套件和建立套件之 \[Content\_Types\].xml 檔案等這一類工作。  
  
-   您可以將 VSIX 專案設定為包含擴充功能專案的組建輸出和 VSIX 套件中的其他檔案，例如專案範本和項目範本。  
  
 如需使用 VSIX 專案的詳細資訊，請參閱[VSIX 專案範本](../extensibility/vsix-project-template.md)。  
  
### 組織專案  
 根據預設，VSIX 專案只會產生 VSIX 套件，而不是組件。  因此，通常不需要在 VSIX 專案中實作 SharePoint 工具擴充功能。  一般至少會用到兩個專案：  
  
-   VSIX 專案。  
  
-   實作擴充功能的類別庫專案。  
  
 也可能會用到某些擴充功能類型的其他專案：  
  
-   實作任何由擴充功能所用之 SharePoint 命令的類別庫專案。  如需示範此案例的逐步解說，請參閱[Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。  
  
-   建立項目範本或專案範本的項目範本或專案範本專案 \(如果擴充功能定義新的 SharePoint 專案項目類型\)。  如需示範此案例的逐步解說，請參閱[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)。  
  
-   為項目範本或專案範本實作自訂精靈的類別庫專案 \(如果擴充功能包含範本\)。  如需示範此案例的逐步解說，請參閱[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)。  
  
 如果在相同的 Visual Studio 方案中包含所有專案，則您可以修改 VSIX 專案中的 source.extension.vsixmanifest 檔案，以包含類別庫專案的組建輸出。  
  
### 編輯 VSIX 資訊清單  
 您必須編輯 VSIX 專案中的 source.extension.vsixmanifest 檔案，以便包含所有要包含在擴充功能中之項目 \(Item\) 的項目 \(Entry\)。  當您從開啟其捷徑功能表中的 source.extension.vsixmanifest 檔案，檔案會出現在為編輯檔案中的 XML 提供 UI 的設計工具。  如需詳細資訊，請參閱[VSIX 資訊清單設計工具](../extensibility/media/vsix-manifest-designer.png)。  
  
 您必須在 source.extension.vsixmanifest 檔案加入下列項目 \(Item\) 的項目 \(Entry\)：  
  
-   擴充功能組件。  
  
-   實作任何由擴充功能所用之 SharePoint 命令的組件。  
  
-   任何與擴充功能關聯的專案範本或項目範本。  
  
-   與擴充功能關聯之範本的自訂精靈。  
  
 下列程序說明如何在 .vsixmanifest 檔案加入每個這些項目 \(Item\) 的項目 \(Entry\)：  
  
##### 若要包含擴充功能組件  
  
1.  在 VSIX 專案中，開啟 source.extension.vsixmanifest 檔案的捷徑功能表，然後選取 \[**開啟**\]。  
  
     檔案隨即在設計工具中開啟。  
  
2.  在編輯器中 \[**資產**\] 索引標籤上，選取 \[**新增**\] 按鈕。  
  
     \[**將新的屬性**\] 對話方塊隨即開啟。  
  
3.  在 \[**型別**\] 清單中，選取 \[**Microsoft.VisualStudio.MefComponent**\]。  
  
4.  在 \[**Source**\] 清單中，執行下列其中一個步驟:  
  
    -   如果擴充功能組件是從與方案相同的 VSIX 專案，選取 \[**在目前方案中的專案**\] 的專案建置。  在 \[**Project**\] 清單中，選取專案名稱。  
  
    -   如果擴充功能組件，包含在您專案中的檔案，選取 \[**檔案在檔案系統**\]。  在 \[**路徑**\] 清單，請輸入完整路徑的擴充功能組件檔或使用 \[**瀏覽**\] 按鈕尋找和選取組件檔。  
  
5.  選擇 \[**確定**\] 按鈕。  
  
##### 若要包含 SharePoint 命令組件  
  
1.  在 VSIX 專案中，開啟 source.extension.vsixmanifest 檔案的捷徑功能表，然後選取 \[**開啟**\] 按鈕。  
  
     檔案隨即在設計工具中開啟。  
  
2.  在編輯器中 \[**資產**\] 區段中，選取 \[**新增**\] 按鈕。  
  
     \[**將新的屬性**\] 對話方塊隨即開啟。  
  
3.  在 \[**型別**\]方塊中，輸入 \[**SharePoint.Commands.v4**\]。  
  
4.  在 \[**Source**\] 清單中，執行下列其中一個步驟:  
  
    -   如果命令組件是從與方案相同的 VSIX 專案，選取 \[**在目前方案中的專案**\] 的專案建置。  在 \[**Project**\] 清單中，選取專案名稱。  
  
    -   如果命令組件中，在您專案中的檔案，選取 \[**在檔案系統中的檔案**\]。  在 \[**路徑**\] 清單，請輸入完整路徑的擴充功能組件檔或使用 \[**瀏覽**\] 按鈕尋找和選取組件檔。  
  
5.  選擇 \[**確定**\] 按鈕。  
  
##### 包括您剛才建立的範本  
  
1.  在 VSIX 專案中，開啟 source.extension.vsixmanifest 檔案的捷徑功能表，然後選取 \[**開啟**\] 按鈕。  
  
     檔案隨即在設計工具中開啟。  
  
2.  在編輯器中 \[**資產**\] 區段中，選取 \[**新增**\] 按鈕。  
  
     \[**將新的屬性**\] 對話方塊隨即開啟。  
  
3.  在 \[**型別**\] 清單中，選取 \[**Microsoft.VisualStudio.ProjectTemplate**\]或 \[**Microsoft.VisualStudio.ItemTemplate**\]。  
  
4.  在 \[**Source**\] 清單中，選取 \[**在目前方案中的專案**\]。  
  
5.  在 \[**Project**\] 清單中，選取專案名稱，然後選取 \[**確定**\] 按鈕。  
  
6.  在 \[**方案總管**\]，開啟您的專案範本或項目範本專案的捷徑功能表，然後選取 \[**卸載專案**\]。  
  
7.  重新開啟專案節點的捷徑功能表，然後選取 \[**編輯**\]*YourTemplateProjectName*\[**.csproj**\] 或 \[**編輯**\]*YourTemplateProjectName*\[**.vbproj**\]。  
  
8.  在專案檔中尋找下列 `VSTemplate` 項目。  
  
    ```  
    <VSTemplate Include="YourTemplateName.vstemplate">  
    ```  
  
9. 以下列 XML 取代項目。  
  
    ```  
    <VSTemplate Include="YourTemplateName.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     `OutputSubPath` 項目會在您建置專案時用以建立專案範本的路徑中，指定其他資料夾。  這裡指定的資料夾可確保項目範本可供使用，只有在用戶 \[**新增專案**\] 開啟對話方塊時， \[**SharePoint**\] 展開節點，然後選取 \[**2010**\] 節點。  
  
10. 儲存並關閉檔案。  
  
11. 在 \[**方案總管**\]，請開啟專案範本或項目範本專案的捷徑功能表，然後選取 \[**重新載入專案**\]。  
  
##### 若要包含手動建立的範本  
  
1.  在 VSIX 專案中，將新資料夾加入至專案中以包含範本。  
  
2.  在這個新資料夾下，建立下列子資料夾，然後將範本 \(.zip\) 檔案加入至 *Locale ID* 資料夾。  
  
     *YourTemplateFolder*  
  
     **SharePoint**  
  
     **SharePoint14**  
  
     *Locale ID*  
  
     *YourTemplateName*.zip  
  
     例如，如果具有名為 ContosoCustomAction.zip 且支援英文 \(美國\) 地區設定的項目範本，則完整路徑可能為 ItemTemplates\\SharePoint\\SharePoint14\\1033\\ContosoCustomAction.zip。  
  
3.  在 \[**方案總管**\]，選取範本檔 \(.zip\)*YourTemplateName*。  
  
4.  在 \[**屬性**\] 視窗中，將 \[**建置動作**\] 屬性設定為 \[**內容**\]。  
  
5.  開啟 source.extension.vsixmanifest 檔案的捷徑功能表，然後選取 \[**開啟**\]。  
  
     檔案隨即在設計工具中開啟。  
  
6.  在編輯器中 \[**資產**\] 區段中，選取 \[**新增**\] 按鈕。  
  
     \[**將新的屬性**\] 對話方塊隨即開啟。  
  
7.  在 \[**型別**\] 清單中，選取 \[**Microsoft.VisualStudio.ItemTemplate**\]或 \[**Microsoft.VisualStudio.ProjectTemplate**\]。  
  
8.  在 \[**Source**\] 清單中，選取 \[**在檔案系統中的檔案**\]。  
  
9. 在 \[**路徑**\] 欄位中，輸入完整路徑的組件 \(例如， \[**ItemTemplates\\SharePoint\\SharePoint14\\1033\\ContosoCustomAction.zip**\] 或使用 \[**瀏覽**\] 按鈕尋找和選取組件，然後選取 \[**確定**\] 按鈕。  
  
##### 若要包含專案範本或項目範本的精靈  
  
1.  在 VSIX 專案中，開啟 source.extension.vsixmanifest 檔案的捷徑功能表，然後選取 \[**開啟**\]。  
  
     檔案隨即在設計工具中開啟。  
  
2.  在編輯器中 \[**資產**\] 區段中，選取 \[**新增**\] 按鈕。  
  
     \[**將新的屬性**\] 對話方塊隨即開啟。  
  
3.  在 \[**型別**\] 清單中，選取 \[**Microsoft.VisualStudio.Assembly**\]。  
  
4.  在 \[**Source**\] 清單中，執行下列其中一個步驟:  
  
    -   如果精靈組件是從與方案相同的 VSIX 專案，選取 \[**在目前方案中的專案**\] 的專案建置。  在 \[**Project**\] 清單中，選取專案名稱。  
  
    -   如果精靈組件中，在您專案中的檔案，選取 \[**在檔案系統中的檔案**\]。  在 \[**路徑**\] 欄位中，輸入完整路徑的組件檔或使用 \[**瀏覽**\] 按鈕尋找和選取組件。  
  
5.  選擇 \[**確定**\] 按鈕。  
  
### 相關的逐步解說  
 下表所列的逐步解說將說明如何使用 VSIX 專案部署不同類型的 SharePoint 工具擴充功能。  
  
|擴充功能類型|相關的逐步解說|  
|------------|-------------|  
|只包含擴充功能組件的擴充功能|[Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|  
|任何包含 SharePoint 命令的擴充功能|[Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [逐步解說：使用專案範本建立網站資料行專案項目 &#40;第 2 部分&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
|任何包含 Visual Studio 範本的擴充功能|[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [逐步解說：使用專案範本建立網站欄專案項目 &#40;第 1 部分&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|  
|任何包含範本精靈的擴充功能|[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [逐步解說：使用專案範本建立網站資料行專案項目 &#40;第 2 部分&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
  
## 手動建立 VSIX 套件  
 如果您想要手動建立用於 SharePoint 工具擴充功能的 VSIX 套件，請執行下列步驟：  
  
1.  建立 extension.vsixmanifest 檔案、\[Content\_Types\].xml 和 VSIX 套件檔 \(.vsix file\)。  如需詳細資訊，請參閱[VSIX 套件的剖析](../extensibility/anatomy-of-a-vsix-package.md)與[如何：手動封裝擴充功能 &#40;VSIX 部署&#41;](~/misc/how-to-manually-package-an-extension-vsix-deployment.md)。  
  
2.  將擴充功能組件加入至 VSIX 套件。  如果擴充功能包含 SharePoint 命令，另請加入會對 VSIX 套件實作 SharePoint 命令的組件。  
  
3.  修改 extension.vsixmanifest 檔案：  
  
    -   將 `Microsoft.VisualStudio.MefComponent``Assets` 項目在項目之下，然後將新項目的值到實作自己的 VSIX 套件中擴充組件的相對路徑。  如需詳細資訊，請參閱[NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/zh-tw/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
    -   如果擴充功能包含會呼叫 SharePoint 伺服器物件模型中的 SharePoint 命令，請將 `Microsoft.VisualStudio.Assembly``Assets` 項目在項目之下。  將新項目的值到實作 VSIX 套件中 SharePoint 命令之組件的相對路徑。  如需詳細資訊，請參閱[資產的項目 \(VSX 結構描述\)](http://msdn.microsoft.com/zh-tw/9fcfc098-edc7-484b-9d4c-acd17829d737)。  
  
    -   如果擴充功能包含專案範本或項目範本，請將 `ProjectTemplate` 或 `ItemTemplate``Assets` 項目在項目之下。  將新項目的值加入至 VSIX 套件包含範本資料夾的相對路徑。  如需詳細資訊，請參閱[NIB: ProjectTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/zh-tw/87add64c-9dcd-495f-8815-209dab182cb1)與[NIB: ItemTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/zh-tw/1d489e54-c1c5-4f96-a510-6c2640867ff0)。  
  
    -   如果擴充功能包含專案範本或項目範本的自訂精靈，將 `Assembly``Assets` 項目在項目之下。  將新項目的值到組件的相對路徑 VSIX 套件中，然後將屬性設定為 `AssemblyName` 完整組件名稱 \(包括版本、文化特性和公開金鑰語彙基元\)。  如需詳細資訊，請參閱[相依性項目 \(VSX 結構描述\)](http://msdn.microsoft.com/zh-tw/1f63f60a-98ad-48ec-8e44-4eba383d3e37)。  
  
### 範例  
 下列範例顯示 SharePoint 工具擴充功能的 extension.vsixmanifest 檔案內容。  副檔名在名為 Contoso.ProjectExtension.dll 的組件中實作。  擴充功能包含名為 Contoso.ExtensionCommands.dll 和項目範本資料夾下 VSIX 套件中名為 \[**ItemTemplates**\]的 SharePoint 命令組件。  此範例假設兩個組件都位於 VSIX 套件中與 extension.vsixmanifest 檔案相同的資料夾中。  
  
```  
<PackageManifest Version=”2.0.0” xmlns=”http://schemas.microsoft.com/developer/vsx-schema/2011”>  
  <Metadata>  
    <Identity Id="CustomActionProjectItem.Microsoft.b99efe4d-cef3-4afd-b9af-034ca0c52743" Version="1.0" Language="en-US" Publisher="Microsoft" />  
    <DisplayName>CustomActionProjectItem</DisplayName>  
    <Description>Empty VSIX Project.</Description>  
  </Metadata>  
  <Installation>  
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="11.0" />  
  </Installation>  
  <Dependencies>  
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" Version="4.5" />  
  </Dependencies>  
  <Assets>  
    <Asset Type="Microsoft.VisualStudio.ItemTemplate" Path="ItemTemplates" />  
    <Asset Type="Microsoft.VisualStudio.MefComponent" Path="ProjectItemDefinition.dll" />  
  </Assets>  
</PackageManifest>  
  
```  
  
## 請參閱  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  
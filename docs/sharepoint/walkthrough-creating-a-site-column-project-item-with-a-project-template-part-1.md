---
title: "逐步解說：使用專案範本建立網站欄專案項目 (第 1 部分) | Microsoft Docs"
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
  - "SharePoint 專案項目、定義您自己的類型"
  - "專案項目 [Visual Studio 中的 SharePoint 程式開發]、定義您自己的類型"
  - "SharePoint 專案、建立自訂範本"
  - "Visual Studio 中的 SharePoint 程式開發、定義新的專案項目類型"
ms.assetid: b53d48d7-cbf2-45c2-9537-06a6819be397
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# 逐步解說：使用專案範本建立網站欄專案項目 (第 1 部分)
  SharePoint 專案是一個或多個 SharePoint 專案項目的容器。  您可以自行建立專案項目類型再使其與專案範本產生關聯，藉此擴充 Visual Studio 中的 SharePoint 專案系統。  在本逐步解說中，您將建立定義用於建立網站欄的專案項目類型，然後建立可用來建立包含網站欄專案項目之新專案的專案範本。  
  
 本逐步解說將示範下列工作：  
  
-   建立為網站欄定義新的 SharePoint 專案項目類型的 Visual Studio 擴充功能。  此專案項目類型包含會出現 \[**屬性**\] 視窗中的簡單自訂屬性。  
  
-   為專案項目建立 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 專案範本。  
  
-   建置 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 擴充功能 \(VSIX\) 套件以部署專案範本和擴充功能組件。  
  
-   偵錯和測試專案項目。  
  
 這是獨立的逐步解說。  完成本逐步解說之後，您可以將精靈加入至專案範本來增強專案項目。  如需詳細資訊，請參閱[逐步解說：使用專案範本建立網站資料行專案項目 &#40;第 2 部分&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。  
  
> [!NOTE]  
>  您可以從下列位置取得本逐步解說所含之完成的專案、程式碼和其他檔案：[http:\/\/go.microsoft.com\/fwlink\/?LinkId\=191369](http://go.microsoft.com/fwlink/?LinkId=191369)。  
  
## 必要條件  
 開發電腦上需要下列元件才能完成此逐步解說：  
  
-   支援的 Microsoft Windows、SharePoint 和 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 版本。  如需詳細資訊，請參閱[開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。  這個逐步解說使用 SDK 中的 **VSIX 專案**範本建立 VSIX 套件，以部署專案項目。  如需詳細資訊，請參閱[Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 了解下列概念有助於完成此逐步解說 \(但非必要\)：  
  
-   SharePoint 中的網站欄。  如需詳細資訊，請參閱 [Columns](http://go.microsoft.com/fwlink/?LinkId=183547)。  
  
-   Visual Studio 中的專案範本。  如需詳細資訊，請參閱[在 Visual Studio 中建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)。  
  
## 建立專案  
 若要完成這個逐步解說，您必須建立三個專案：  
  
-   VSIX 專案。  這個專案會建立 VSIX 套件，以部署網站欄專案項目和專案範本。  
  
-   專案範本專案。  這個專案會建立可用來建立包含網站欄專案項目之新 SharePoint 專案的專案範本。  
  
-   類別庫專案。  這個實作 Visual Studio 擴充功能的專案會定義網站欄專案項目的行為。  
  
 從建立這些專案開始進行此逐步解說。  
  
#### 若要建立 VSIX 專案  
  
1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在功能表列上，選擇 \[**檔案**\]、\[**新增**\]、\[**專案**\]。  
  
3.  在 \[**新的專案**\] 對話方塊的頂端，請確認在 .NET Framework 的版本清單中已經選取 \[**.NET Framework 4.5**\] 。  
  
4.  展開 \[**Visual Basic**\] 或 \[**Visual C\#**\] 節點，然後選取 \[**擴充性**\] 節點。  
  
    > [!NOTE]  
    >  \[**擴充性**\] 節點只有在安裝 Visual Studio SDK 時才可使用。  如需詳細資訊，請參閱本主題稍早討論的＜必要條件＞一節。  
  
5.  在專案清單中，選擇 \[**VSIX 專案**\]。  
  
6.  在 \[**名稱**\] 文字方塊中，輸入 **SiteColumnProjectItem**，然後選擇 \[**確定**\] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將 **SiteColumnProjectItem** 專案加入至 \[**方案總管**\]。  
  
#### 若要建立專案範本專案  
  
1.  在 \[**方案總管**\] 中，開啟方案節點的捷徑功能表，選擇 \[**加入**\]，然後選擇 \[**新增專案**\]。  
  
    > [!NOTE]  
    >  在 Visual Basic 專案中，方案節點只有在已選取[NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/zh-tw/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)中的 \[**永遠顯示方案**\] 核取方塊時，才會出現在 \[**方案總管**\] 中。  
  
2.  在 \[**新的專案**\] 對話方塊的頂端，請確認在 .NET Framework 的版本清單中已經選取 \[**.NET Framework 4.5**\] 。  
  
3.  展開 \[**Visual C\#**\] 或 \[**Visual Basic**\] 節點，然後選取 \[**擴充性**\] 節點。  
  
4.  在專案範本清單中，選取 \[**C\# 專案範本**\] 或 \[**Visual Basic 專案範本**\] 的範本。  
  
5.  在 \[**名稱**\] 文字方塊中，輸入 **SiteColumnProjectTemplate**，然後選擇 \[**確定**\] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 隨即將 \[**SiteColumnProjectTemplate**\] 專案加入至方案。  
  
6.  從專案刪除 Class1 程式碼檔。  
  
7.  如果您建立了 Visual Basic 專案，請一併從該專案刪除下列檔案：  
  
    -   MyApplication.Designer.vb  
  
    -   MyApplication.myapp  
  
    -   Resources.Designer.vb  
  
    -   Resources.resx  
  
    -   Settings.Designer.vb  
  
    -   Settings.settings  
  
#### 若要建立擴充功能專案  
  
1.  在 \[**方案總管**\] 中，開啟方案節點的捷徑功能表，選擇 \[**加入**\]，然後選擇 \[**新增專案**\]。  
  
2.  在 \[**新的專案**\] 對話方塊的頂端，請確認在 .NET Framework 的版本清單中已經選取 \[**.NET Framework 4.5**\] 。  
  
3.  展開 \[**Visual C\#**\] 或 \[**Visual Basic**\] 節點，選取 \[**視窗**\] 節點，然後選取 \[**類別庫**\] 範本。  
  
4.  在 \[**名稱**\] 方塊中，輸入 **ProjectItemTypeDefinition**，然後選擇 \[**確定**\] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 隨即將 \[**ProjectItemTypeDefinition**\] 專案加入至方案，然後開啟預設的 Class1 程式碼檔。  
  
5.  從專案刪除 Class1 程式碼檔。  
  
## 設定擴充功能專案  
 加入程式碼檔案和組件參考，以設定擴充功能專案。  
  
#### 若要設定專案  
  
1.  在 ProjectItemTypeDefinition 專案中，加入名為 **SiteColumnProjectItemTypeProvider** 的程式碼檔。  
  
2.  在功能表列上，選擇 \[**專案**\]、\[**加入參考**\]。  
  
3.  展開 \[**參考管理員 \- ProjectItemTypeDefinition**\] 對話方塊中的 \[**組件**\] 節點，選擇 \[**Framework**\] 節點，然後選取 \[System.ComponentModel.Composition\] 核取方塊。  
  
4.  選取 \[**擴充功能**\] 節點，以 Microsoft.VisualStudio.SharePoint 組件旁邊的核取方塊，然後選擇 \[**確認**\] 按鈕。  
  
## 定義新的 SharePoint 專案項目類型  
 建立實作 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 介面的類別，以定義新專案項目類型的行為。  在您要定義新的專案項目類型時實作此介面。  
  
#### 若要定義新的 SharePoint 專案項目類型  
  
1.  在 **SiteColumnProjectItemTypeProvider** 程式碼檔中，以下列程式碼取代預設的程式碼，然後儲存檔案。  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]  
  
## 建立 Visual Studio 專案範本  
 若要讓開發人員建立包含網站欄專案項目的新 SharePoint 專案，請建立專案範本。  SharePoint 專案範本包含 Visual Studio 中所有專案所需的檔案，例如 .csproj 或 .vbproj 和 .vstemplate 檔案及 SharePoint 專案特定的檔案。  如需詳細資訊，請參閱[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
 在此程序中，您會建立空的 SharePoint 專案產生專屬於 SharePoint 專案的檔案。  然後將這些檔案加入至 SiteColumnProjectTemplate 專案，以便在從這個專案產生的範本中。  您也一併設定 SiteColumnProjectTemplate 專案檔以指定專案範本出現在 \[**新的專案**\] 對話方塊中的位置。  
  
#### 若要為專案範本建立檔案  
  
1.  以系統管理員權限啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的第二個執行個體。  
  
2.  建立新的 SharePoint 2010 專案，並命名為 **BaseSharePointProject**。  
  
    > [!IMPORTANT]  
    >  在 \[**SharePoint 自訂精靈**\] 中，請勿選取 \[**部署為陣列方案**\] 選項按鈕。  
  
3.  將空元素項目加入至專案，然後將項目命名為 **Field1**。  
  
4.  儲存專案，然後關閉 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的第二個執行個體。  
  
5.  在開啟 SiteColumnProjectItem 專案的方案，請在 \[**方案總管**\] 的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 執行個體中，開啟 \[**SiteColumnProjectTemplate**\] 節點的捷徑功能表上，選擇 \[**加入**\]，然後選擇 \[**現有的項目。**\]。  
  
6.  在 \[**加入現有項目**\] 對話方塊中，開啟副檔名的清單，然後選取 \[**所有檔案 \(\*.\*\)**\]。  
  
7.  在包含 BaseSharePointProject 專案的目錄，請選取 key.snk 檔案，然後選擇 \[**加入**\] 按鈕。  
  
    > [!NOTE]  
    >  在本逐步解說中，您所建立的專案範本會以相同的 key.snk 檔案來簽署每一個使用範本建立的專案。  若要了解如何擴充這個範例來為每個專案執行個體建立的 key.snk 檔案，請參閱[逐步解說：使用專案範本建立網站資料行專案項目 &#40;第 2 部分&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。  
  
8.  重複步驟 5\-8，在 BaseSharePointProject 目錄中從指定的子資料夾加入下列檔案：  
  
    -   \\Field1\\Elements.xml  
  
    -   \\Field1\\SharePointProjectItem.spdata  
  
    -   \\Features\\Feature1\\Feature1.feature  
  
    -   \\Features\\Feature1\\Feature1.Template.xml  
  
    -   \\Package\\Package.package  
  
    -   \\Package\\Package.Template.xml  
  
     直接將這些檔案加入至 SiteColumnProjectTemplate 專案，請勿在專案中重新建立 Field1、Features 或 Package 子資料夾。  如需這些檔案的詳細資訊，請參閱[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
#### 若要設定開發人員在新的專案對話方塊中探索專案範本的方式  
  
1.  在 \[**方案總管**\]，開啟 \[**SiteColumnProjectTemplate**\] 方案節點的捷徑功能表，然後選取 \[**上傳專案**\]。  如果您接到儲存任何檔案變更的提示，選擇 \[**是**\] 按鈕。  
  
2.  打開 \[**SiteColumnProjectTemplate**\] 節點的捷徑功能表，然後選擇 \[**編輯 SiteColumnProjectTemplate.csproj**\] 或 \[**編輯 SiteColumnProjectTemplate.vbproj**\]。  
  
3.  在專案檔中，尋找下列 `VSTemplate` 項目。  
  
    ```  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
    ```  
  
4.  使用下列 XML 程式碼取代這個項目：  
  
    ```  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     `OutputSubPath` 項目會在您建置專案時用以建立專案範本的路徑中，指定其他資料夾。  可用專案範本之指定資料夾，當客戶開啟 \[**新的專案**\] 對話視窗，展開 \[**SharePoint**\] 節點，然後選擇 \[**2010**\] 節點  
  
5.  儲存並關閉檔案。  
  
6.  在 \[**方案總管**\] 中，開啟 \[**SiteColumnProjectTemplate**\] 專案的捷徑功能表，然後選擇 \[**重新載入專案**\]。  
  
## 編輯專案範本檔  
 在 SiteColumnProjectTemplate 專案中，編輯下列檔案，以定義專案範本的行為：  
  
-   AssemblyInfo.cs 或 AssemblyInfo.vb  
  
-   Elements.xml  
  
-   SharePointProjectItem.spdata  
  
-   Feature1.feature  
  
-   Package.package  
  
-   SiteColumnProjectTemplate.vstemplate  
  
-   ProjectTemplate.csproj 或 ProjectTemplate.vbproj  
  
 在下列程序中，您會將可取代的參數加入至若干的這些檔案。  可取代的參數是以貨幣符號 \($\) 字元開頭及結尾的語彙基元。  當使用者使用這個專案範本建立專案時，Visual Studio 會自動在新專案中將這些參數取代為特定值。  如需詳細資訊，請參閱[可置換的參數](../sharepoint/replaceable-parameters.md)。  
  
#### 若要編輯 AssemblyInfo.cs 或 AssemblyInfo.vb 檔案  
  
1.  在 SiteColumnProjectTemplate 專案中，開啟 AssemblyInfo.cs 或 AssemblyInfo.vb 檔案中，然後在頂端加入下列陳述式:  
  
    ```vb  
    Imports System.Security  
    ```  
  
    ```csharp  
    using System.Security;  
    ```  
  
     SharePoint 專案的 \[**沙箱化方案**\] 屬性設為 \[**True**\] 時，Visual Studio 會將 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 加入至 AssemblyInfo 程式碼檔案。  但是，專案範本中的 AssemblyInfo 程式碼檔案預設不會匯入 <xref:System.Security> 命名空間。  您必須加入這個 **using** 或 **Imports** 陳述式，以免發生編譯錯誤。  
  
2.  儲存並關閉檔案。  
  
#### 若要編輯 Elements.xml 檔案  
  
1.  在 SiteColumnProjectTemplate 專案中，以下列 XML 取代 Elements.xml 檔案的內容。  
  
    ```  
  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
          Name="$safeprojectname$"   
          DisplayName="$projectname$"   
          Type="Text"   
          Group="Custom Columns">  
      </Field>  
    </Elements>  
    ```  
  
     新的 XML 會加入一個 `Field` 項目，其定義網站欄的名稱、它的基底型別和要在組件庫中列出網站欄的群組。  如需這個檔案的詳細資訊，請參閱 [欄位定義結構描述](http://go.microsoft.com/fwlink/?LinkId=184290)。  
  
2.  儲存並關閉檔案。  
  
#### 若要編輯 SharePointProjectItem.spdata 檔案  
  
1.  在 SiteColumnProjectTemplate 專案中，以下列 XML 取代 SharePointProjectItem.spdata 檔案的內容。  
  
    ```  
  
    <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"   
                 xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />  
      </Files>   
    </ProjectItem>  
    ```  
  
     新的 XML 程會對檔案進行下列變更：  
  
    -   將 `ProjectItem` 項目的 `Type` 屬性變更為與傳遞至專案項目定義 \(您之前在本逐步解說中建立的 `SiteColumnProjectItemTypeProvider` 類別\) 上的 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> 的相同的字串。  
  
    -   從 `ProjectItem` 項目移除 `SupportedTrustLevels` 和 `SupportedDeploymentScopes` 屬性。  這些屬性值是不必要的，因為信任層級和部署範圍會在 ProjectItemTypeDefinition 專案的 `SiteColumnProjectItemTypeProvider` 類別中指定。  
  
     如需 .spdata 檔案內容的詳細資訊，請參閱 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)。  
  
2.  儲存並關閉檔案。  
  
#### 若要編輯 Feature1.feature 檔案  
  
1.  在 SiteColumnProjectTemplate 專案中，以下列 XML 取代 Feature1.feature 檔案的內容。  
  
    ```  
  
    <feature xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="$guid4$" featureId="$guid4$"   
             imageUrl="" solutionId="00000000-0000-0000-0000-000000000000" title="Site Column Feature1" version=""  
             deploymentPath="$SharePoint.Project.FileNameWithoutExtension$_$SharePoint.Feature.FileNameWithoutExtension$"  
             xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/FeatureModel">  
      <projectItems>  
        <projectItemReference itemId="$guid2$" />  
      </projectItems>  
    </feature>  
    ```  
  
     新的 XML 程會對檔案進行下列變更：  
  
    -   將 `feature` 項目的 `Id` 和 `featureId` 屬性值變更為 `$guid4$`。  
  
    -   將 `projectItemReference` 項目的 `itemId` 屬性值變更為 `$guid2$`。  
  
     如需 .feature 檔案的詳細資訊，請參閱[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
2.  儲存並關閉檔案。  
  
#### 若要編輯 Package.package 檔案  
  
1.  在 SiteColumnProjectTemplate 專案中，以下列 XML 取代 Package.package 檔案的內容。  
  
    ```  
  
    <package xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0"   
             Id="$guid3$" solutionId="$guid3$" resetWebServer="false" name="$safeprojectname$"   
             xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/PackageModel">  
      <features>  
        <featureReference itemId="$guid4$" />  
      </features>  
    </package>  
    ```  
  
     新的 XML 程會對檔案進行下列變更：  
  
    -   將 `package` 項目的 `Id` 和 `solutionId` 屬性值變更為 `$guid3$`。  
  
    -   將 `featureReference` 項目的 `itemId` 屬性值變更為 `$guid4$`。  
  
     如需 .package 檔案的詳細資訊，請參閱[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
2.  儲存並關閉檔案。  
  
#### 若要編輯 SiteColumnProjectTemplate.vstemplate 檔案  
  
1.  在 SiteColumnProjectTemplate 專案中，以 XML 的下列其中一個區段取代 SiteColumnProjectTemplate.vstemplate 檔案的內容。  
  
    -   如果建立 Visual C\# 專案範本，請使用下列 XML。  
  
    ```  
  
    <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
      <TemplateData>  
        <Name>Site Column</Name>  
        <Description>Creates a new site column in SharePoint</Description>  
        <FrameworkVersion>3.5</FrameworkVersion>  
        <ProjectType>CSharp</ProjectType>  
        <CreateNewFolder>true</CreateNewFolder>  
        <CreateInPlace>true</CreateInPlace>  
        <ProvideDefaultName>true</ProvideDefaultName>  
        <DefaultName>SiteColumn</DefaultName>  
        <LocationField>Enabled</LocationField>  
        <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
        <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <Icon>SiteColumnProjectTemplate.ico</Icon>  
        <SortOrder>1000</SortOrder>  
      </TemplateData>  
      <TemplateContent>  
        <Project TargetFileName="SharePointProject1.csproj" File="ProjectTemplate.csproj" ReplaceParameters="true">  
          <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
        </Project>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
    -   如果建立 Visual Basic 專案範本，請使用下列 XML。  
  
    ```  
  
    <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
      <TemplateData>  
        <Name>Site Column</Name>  
        <Description>Creates a new site column in SharePoint</Description>  
        <FrameworkVersion>3.5</FrameworkVersion>  
        <ProjectType>VisualBasic</ProjectType>  
        <CreateNewFolder>true</CreateNewFolder>  
        <CreateInPlace>true</CreateInPlace>  
        <ProvideDefaultName>true</ProvideDefaultName>  
        <DefaultName>SiteColumn</DefaultName>  
        <LocationField>Enabled</LocationField>  
        <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
        <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <Icon>SiteColumnProjectTemplate.ico</Icon>  
        <SortOrder>1000</SortOrder>  
      </TemplateData>  
      <TemplateContent>  
        <Project TargetFileName="SharePointProject1.vbproj" File="ProjectTemplate.vbproj" ReplaceParameters="true">  
          <ProjectItem ReplaceParameters="true" TargetFileName="My Project\AssemblyInfo.vb">AssemblyInfo.vb</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
        </Project>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
     新的 XML 程會對檔案進行下列變更：  
  
    -   設定 `Name` 項目到值 \[**設置行**\]。\(這個名稱會顯示在 \[**新的專案**\] 對話方塊\)。  
  
    -   為每個專案執行個體中包含的每個檔案加入 `ProjectItem` 項目。  
  
    -   使用命名空間「http:\/\/schemas.microsoft.com\/developer\/vstemplate\/2005」。  在這個方案的其他專案檔使用「http:\/\/schemas.microsoft.com\/developer\/msbuild\/2003」命名空間。  因此， XML 結構描述警告訊息將產生，不過您可以在這個逐步解說忽略它們。  
  
     如需 .vstemplate 檔案內容的詳細資訊，請參閱 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)。  
  
2.  儲存並關閉檔案。  
  
#### 若要編輯 ProjectTemplate.csproj 或 ProjectTemplate.vbproj 檔案  
  
1.  在 SiteColumnProjectTemplate 專案中，以 XML 的下列其中一個區段取代檔案 ProjectTemplate.csproj 或 ProjectTemplate.vbproj 檔案的內容。  
  
    -   如果建立 Visual C\# 專案範本，請使用下列 XML。  
  
    ```  
  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <SchemaVersion>2.0</SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <AppDesignerFolder>Properties</AppDesignerFolder>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{14822709-B5A1-4724-98CA-57A101D1B079};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineConstants>DEBUG;TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <DefineConstants>TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Web" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="Properties\AssemblyInfo.cs" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
    1.  如果建立 Visual Basic 專案範本，請使用下列 XML。  
  
    ```  
  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <ProductVersion>  
        </ProductVersion>  
        <SchemaVersion>  
        </SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{D59BE175-2ED0-4C54-BE3D-CDAA9F3214C8};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>  
        <OptionExplicit>On</OptionExplicit>  
        <OptionCompare>Binary</OptionCompare>  
        <OptionStrict>Off</OptionStrict>  
        <OptionInfer>On</OptionInfer>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <OutputPath>bin\Debug\</OutputPath>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <DefineDebug>false</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Import Include="Microsoft.VisualBasic" />  
        <Import Include="System" />  
        <Import Include="System.Collections" />  
        <Import Include="System.Collections.Generic" />  
        <Import Include="System.Data" />  
        <Import Include="System.Diagnostics" />  
        <Import Include="System.Linq" />  
        <Import Include="System.Xml.Linq" />  
        <Import Include="Microsoft.SharePoint" />  
        <Import Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="My Project\AssemblyInfo.vb" />  
      </ItemGroup>  
      <ItemGroup>  
        <AppDesigner Include="My Project\" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
     新的 XML 程會對檔案進行下列變更：  
  
    -   使用 `TargetFrameworkVersion` 項目以指定 .NET Framework 3.5 \(非 4.5\)。  
  
    -   加入 `SignAssembly` 和 `AssemblyOriginatorKeyFile` 項目以簽署專案輸出。  
  
    -   使用 SharePoint 專案所使用的組件參考加入 `Reference` 項目。  
  
    -   為專案中的每個預設檔案 \(例如 Elements.xml 和 SharePointProjectItem.spdata\) 加入新的項目。  
  
2.  儲存並關閉檔案。  
  
## 建立 VSIX 套件以部署專案範本  
 若要部署擴充功能，請在 **SiteColumnProjectItem** 方案中使用 VSIX 專案，以建立 VSIX 套件。  首先，修改 VSIX 專案包含的 source.extension.vsixmanifest 檔案，來設定 VSIX 套件。  接著，建置方案來建立 VSIX 套件。  
  
#### 若要設定和建立 VSIX 套件  
  
1.  在 \[**方案總管**\] 中，\[**SiteColumnProjectItem**\] 專案中，打開資訊清單編輯器的 source.extension.vsixmanifest 檔案。  
  
     source.extension.vsixmanifest 檔案是所有 VSIX 套件需要之 extension.vsixmanifest 檔案的基準。  如需這個檔案的詳細資訊，請參閱[VSIX 擴充結構描述參考](http://msdn.microsoft.com/zh-tw/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在 \[**產品名稱**\] 方塊中，輸入 **Site Column**。  
  
3.  在 \[**作者**\] 方塊中，輸入 **Contoso**。  
  
4.  在 \[**說明**\] 方塊中，輸入 **A SharePoint project for creating site columns**。  
  
5.  選取 \[**資產**\] 選項，然後選擇 \[**新增**\] 按鈕。  
  
     \[**加入新資產**\] 對話方塊隨即開啟。  
  
6.  在 \[**輸入**\] 清單中，選取 \[**Microsoft.VisualStudio.ProjectTemplate**\]。  
  
    > [!NOTE]  
    >  這個值對應於 extension.vsixmanifest 檔案中的 `ProjectTemplate` 項目。  此項目會識別 VSIX 套件中包含專案範本的子資料夾。  如需詳細資訊，請參閱[NIB: ProjectTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/zh-tw/87add64c-9dcd-495f-8815-209dab182cb1)。  
  
7.  在 \[**來源**\] 清單中，選取 \[**在目前方案中的專案**\]。  
  
8.  在 \[**專案**\] 清單中，選擇 \[**SiteColumnProjectTemplate**\]，然後選擇 \[**確定**\] 按鈕。  
  
9. 再次選擇 \[**新增**\] 按鈕。  
  
     \[**加入新資產**\] 對話方塊隨即開啟。  
  
10. 在 \[**輸入**\] 清單中，選取 \[**Microsoft.VisualStudio.MefComponent**\]。  
  
    > [!NOTE]  
    >  這個值對應於 extension.vsixmanifest 檔案中的 `MefComponent` 項目。  這個項目指定 VSIX 套件中的擴充組件名稱。  如需詳細資訊，請參閱[NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/zh-tw/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
11. 在 \[**來源**\] 清單中，選取 \[**在目前方案中的專案**\]。  
  
12. 在 \[**專案**\] 清單中，選擇 \[**ProjectItemTypeDefinition**\]，然後選擇 \[**確定**\] 按鈕。  
  
13. 在功能表列上，選擇 \[**組建**\]， \[**建置方案**\]，然後確定專案在編譯時未發生錯誤。  
  
## 測試專案範本  
 您現在可以測試專案範本。  首先，在 Visual Studio 的實驗執行個體中開始偵錯 SiteColumnProjectItem 方案。  接著，在 Visual Studio 的實驗執行個體中測試 \[**網站欄**\] 專案。  最後，建置並執行 SharePoint 專案，確認網站欄功能正常。  
  
#### 若要開始偵錯方案  
  
1.  以系統管理員憑證重新啟動 Visual Studio，然後開啟 SiteColumnProjectItem 方案。  
  
2.  在 SiteColumnProjectItemTypeProvider 程式碼檔案，請將中斷點加入至 `InitializeType` 方法的第一個程式碼，然後選擇 \[**F5**\] 鍵開始偵錯。  
  
     Visual Studio 會將擴充功能安裝至 %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\10.0Exp\\Extensions\\Contoso\\Site Column\\1.0，並啟動 Visual Studio 的實驗執行個體。  您將會在 Visual Studio 的這個執行個體中測試專案項目。  
  
#### 若要在 Visual Studio 中測試專案  
  
1.  在 Visual Studio 的實驗執行個體中，在 \[**檔案**\] 功能表列上的 \[**新增**\] 中，選擇 \[**專案**\]。  
  
2.  展開 \[**Visual C\#**\] 或 \[**Visual Basic**\] 節點 \(視專案範本支援的語言\)，展開 \[**SharePoint**\] 節點，然後選取 \[**2010**\] 節點。  
  
3.  在專案範本清單中，選取 \[**設置行**\] 範本。  
  
4.  在 \[**名稱**\] 方塊中，輸入 **SiteColumnTest**，然後選擇 \[**確定**\] 按鈕。  
  
     新的專案會出現在 \[**方案總管**\] 中，並具有名稱為 \[**Field1**\] 的專案項目。  
  
5.  確認另一個 Visual Studio 執行個體中的程式碼在您之前於 `InitializeType` 方法的中斷點停止，然後選擇 \[**F5**\] 鍵繼續偵錯專案。  
  
6.  在 \[**方案總管**\] 中，選取 \[**Field1**\] 節點，然後選擇 \[**F4**\] 鍵。  
  
     \[**屬性**\] 視窗隨即開啟。  
  
7.  在屬性清單中，確認 \[**Example Property**\] 屬性出現。  
  
#### 若要在 SharePoint 中測試網站欄  
  
1.  在 \[**方案總管**\] 中，選擇 \[**SiteColumnTest**\] 節點。  
  
2.  在 \[**屬性**\] 視窗中，\[**網站 URL**\] 屬性旁邊的文字方塊，輸入 **http:\/\/localhost**。  
  
     這個步驟會指定要用於偵錯的開發電腦上的本機 SharePoint 網站。  
  
    > [!NOTE]  
    >  \[**網站 URL**\] 屬性預設是空的，因為網站欄專案範本在建立時並未提供用來收集這個值的精靈。  若要了解如何加入要求開發人員提供這個值的精靈，然後在新專案中設定這個屬性，請參閱[逐步解說：使用專案範本建立網站資料行專案項目 &#40;第 2 部分&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。  
  
3.  選擇 **F5** 鍵。  
  
     網站欄會封裝並部署至專案的 \[**網站 URL**\] 屬性指定的 SharePoint 網站。  Web 瀏覽器會開啟此網站的預設頁面。  
  
    > [!NOTE]  
    >  如果出現 \[**已停用指令碼偵錯**\] 對話方塊，請選擇 \[**是**\] 繼續偵錯專案。  
  
4.  請選取 \[**網站動作**\] 功能表上的 \[**網站設定**\]。  
  
5.  在 \[**網站設定**\] 頁面的 \[**組件庫**\] 區段底下，選擇 \[**網站欄**\] 連結。  
  
6.  在網站欄清單中，確認有一個 \[**Custom Columns**\] 群組，其中包含名為 \[**SiteColumnTest**\] 的欄。  
  
7.  關閉 Web 瀏覽器。  
  
## 清理開發電腦  
 在您完成測試專案之後，請從 Visual Studio 的實驗執行個體中移除專案範本。  
  
#### 若要清理開發電腦  
  
1.  在 Visual Studio 的實驗執行個體中，選擇 \[**工具**\] 功能表列上的 \[**擴充和更新**\]。  
  
     \[**擴充功能和更新**\] 對話方塊隨即開啟。  
  
2.  在擴充功能清單中，請選取 \[**設置行**\] 擴充功能，然後選擇 \[**解除安裝**\] 按鈕。  
  
3.  在所顯示的對話方塊中，選擇 \[**是**\]，確認您要解除安裝的擴充功能。  
  
4.  選擇 \[**關閉**\] 按鈕以完成解除安裝。  
  
5.  關閉 Visual Studio 的兩個執行個體 \(Visual Studio 的實驗執行個體，以及其中有開啟 SiteColumnProjectItem 專案的執行個體\)。  
  
## 後續步驟  
 完成本逐步解說之後，您可以將精靈加入至專案範本。  當使用者建立網站欄專案時，精靈會詢問使用者要用於偵錯的網站 URL 以及是否將新方案沙箱化，精靈會藉此資訊設定新專案。  精靈也會收集欄的相關資訊 \(例如基底型別和要在網站欄組件庫中列出欄的群組\)，並將此資訊加入至新專案中的 Elements.xml 檔案。  如需詳細資訊，請參閱[逐步解說：使用專案範本建立網站資料行專案項目 &#40;第 2 部分&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。  
  
## 請參閱  
 [逐步解說：使用專案範本建立網站資料行專案項目 &#40;第 2 部分&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  
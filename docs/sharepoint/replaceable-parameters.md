---
title: "可置換的參數 | Microsoft Docs"
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
  - "可取代參數 [Visual Studio 中的 SharePoint 程式開發]"
  - "Visual Studio 中的 SharePoint 開發, 可置換的參數"
  - "Visual Studio 中的 SharePoint 開發, 語彙基元"
  - "語彙基元 [Visual Studio 中的 SharePoint 程式開發]"
ms.assetid: 3c46bbb1-0a98-495c-9fd1-dc57a6aedc11
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# 可置換的參數
  可置換的參數 \(或「*語彙基元*」\(Token\)\) 可用於專案檔內部，為設計階段尚不知道實際值的 SharePoint 方案項目提供值。  其功能類似於標準 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 範本語彙基元。  如需詳細資訊，請參閱[樣板參數](../ide/template-parameters.md)。  
  
## 語彙基元格式  
 語彙基元以貨幣符號 \($\) 字元當做開頭和結尾。  當專案在部署時間封裝至 SharePoint 方案套件 \(.wsp\) 檔案時，使用的任何語彙基元都會以實際值置換。  例如，語彙基元 **$SharePoint.Package.Name$** 可能會解析為字串 "Test SharePoint Package"。  
  
## 語彙基元規則  
 下列規則適用於語彙基元：  
  
-   可以在一行中的任何位置指定語彙基元。  
  
-   語彙基元不可跨多行。  
  
-   同一行和同一個檔案可指定相同的語彙基元多次。  
  
-   同一行可指定不同的語彙基元。  
  
 若語彙基元未遵守上述規則，系統將予以忽略而不會提供警告或錯誤。  
  
 資訊清單轉換後會立即以字串值置換語彙基元，因此可讓使用者編輯資訊清單範本以使用語彙基元。  
  
### 語彙基元名稱解析  
 在大部分的情況下，無論語彙基元位於何處，它都會解析為特定值。  但是，如果語彙基元與某個套件或功能相關，則語彙基元的值將視其所在位置而定。  例如，如果某個功能位於套件 A 中，則語彙基元 `$SharePoint.Package.Name$` 會解析為「套件 A」值。如果同一個功能位於套件 B 中，則 `$SharePoint.Package.Name$` 會解析為「套件 B」。  
  
## 語彙基元清單  
 下表列出可用的語彙基元。  
  
|名稱|說明|  
|--------|--------|  
|$SharePoint.Project.FileName$|包含專案檔的名稱，例如 "NewProj.csproj"。|  
|$SharePoint.Project.FileNameWithoutExtension$|包含專案檔的名稱，但是沒有副檔名。  例如 "NewProj"。|  
|$SharePoint.Project.AssemblyFullName$|包含專案之輸出組件的顯示名稱 \(強式名稱\)。|  
|$SharePoint.Project.AssemblyFileName$|包含專案之輸出組件的名稱。|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|包含專案之輸出組件的名稱，但是沒有副檔名。|  
|$SharePoint.Project.AssemblyPublicKeyToken$|包含專案之輸出組件的公開金鑰語彙基元，已轉換成字串 \(使用 "x2" 十六進位格式的 16 個字元\)。|  
|$SharePoint.Package.Name$|包含套件的名稱。|  
|$SharePoint.Package.FileName$|包含套件定義檔的名稱。|  
|$SharePoint.Package.FileNameWithoutExtension$|包含套件定義檔的名稱 \(沒有副檔名\)。|  
|$SharePoint.Package.Id$|包含套件的 SharePoint 識別碼。  如果某個功能使用在一個以上的套件中，則這個值會變更。|  
|$SharePoint.Feature.FileName$|包含功能定義檔的名稱，例如 Feature1.feature。|  
|$SharePoint.Feature.FileNameWithoutExtension$|功能定義檔的名稱，但是沒有副檔名。|  
|$SharePoint.Feature.DeploymentPath$|包含套件中功能的資料夾名稱。  此語彙基元相當於 \[功能設計工具\] 中的 \[部署路徑\] 屬性。  範例值為 "Project1\_Feature1"。|  
|$SharePoint.Feature.Id$|包含功能的 SharePoint 識別碼。  此語彙基元與所有功能層級的語彙基元一樣，套件中包含的檔案只能透過功能加以使用，但不能不使用功能而直接加入至套件中。|  
|$SharePoint.ProjectItem.Name$|專案項目的名稱 \(而非其檔名\)，與 **ISharePointProjectItem.Name** 取得者相同。|  
|$SharePoint.Type.\<GUID\>.AssemblyQualifiedName$|符合語彙基元的 [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] 型別的組件限定名稱。  [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] 的格式為小寫且對應於 Guid.ToString\("D"\) 格式 \(也就是 xxxxxxxx\-xxxx\-xxxx\-xxxx\-xxxxxxxxxxxx\)。|  
|$SharePoint.Type.\<GUID\>.FullName$|符合語彙基元中 GUID 之型別的完整名稱。  GUID 的格式為小寫且對應於 Guid.ToString\("D"\) 格式 \(也就是 xxxxxxxx\-xxxx\-xxxx\-xxxx\-xxxxxxxxxxxx\)。|  
  
## 將副檔名加入至語彙基元置換副檔名清單  
 雖然任何屬於套件所含 SharePoint 專案項目的檔案理論上都可以使用語彙基元，但根據預設，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 只會在套件檔案、資訊清單檔和副檔名如下的檔案中搜尋語彙基元：  
  
-   [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
-   ASCX  
  
-   ASPX  
  
-   Webpart  
  
-   DWP  
  
 這些副檔名是由 Microsoft.VisualStudio.SharePoint.targets 檔案中的 `<TokenReplacementFileExtensions>` 項目定義，此檔案位於 …\\\<program files\>\\MSBuild\\Microsoft\\VisualStudio\\v11.0\\SharePointTools 資料夾中。  
  
 不過，您可以將其他副檔名加入至清單。  若要這麼做，請將 `<TokenReplacementFileExtensions>` 項目加入至 SharePoint 專案檔中，定義於 SharePoint 目標檔 \<Import\> 之前的任何 PropertyGroup 中。  
  
> [!NOTE]  
>  由於語彙基元替換發生在專案編譯後，所以請勿加入會進行編譯之檔案類型的副檔名，例如 .cs、.vb 或 .resx。  只有不進行編譯之檔案中的語彙基元會產生替換。  
  
 例如，若要將副檔名 ".myextension" 和 ".yourextension" 加入至語彙基元置換副檔名清單，請將下面這段程式碼加入至 .csproj 檔案：  
  
```  
<Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
.  
.  
.  
    <!-- Define the following property to add your extension to the list of token replacement file extensions.  -->  
<TokenReplacementFileExtensions>myextension;yourextension</TokenReplacementFileExtensions>  
</PropertyGroup>  
```  
  
 除此之外，您也可以直接將副檔名加入至 .target 檔案。  不過，這麼做會變更本機系統上封裝之所有 SharePoint 專案的副檔名清單，而不僅是您自己的專案。  如果您是系統上唯一的開發人員或是大多數專案都有此需求，這麼做可能很方便。  但是由於此方法是系統特定的，不是很容易移植，因此建議您還是將副檔名加入至專案檔。  
  
## 請參閱  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  
---
title: "使用 MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages，使用 MSBuild 編譯"
  - "MSBuild，擴充性"
  - "封裝，使用 MSBuild 編譯"
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# 使用 MSBuild
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

MSBuild 會提供定義完善且可延伸的 XML 格式，來建立專案檔案的完整描述可建立、 建置工作，與組建組態的專案項目。  
  
 根據 MSBuild 語言專案系統的端對端範例，請參閱 IronPython 範例深入了解在[VSSDK 範例](../../misc/vssdk-samples.md)。  
  
## 一般 MSBuild 考量  
 MSBuild 專案檔，例如 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] .csproj 和 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .vbproj 檔包含的資料會在建置階段，但也可以包含在設計階段使用的資料。 在建置階段資料會儲存使用 MSBuild 基本項目，包括 [Item Element \(MSBuild\)](../../msbuild/item-element-msbuild.md) 和 [Property Element \(MSBuild\)](../../msbuild/property-element-msbuild.md)。 設計階段資料，這是特定專案類型，以及任何相關的專案子類型的資料，會儲存在為其保留的任意 XML。  
  
 MSBuild 沒有組態物件的原生支援，但提供條件式屬性來指定特定組態資料。 例如：  
  
```  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 如需條件式屬性的詳細資訊，請參閱 [Conditional Constructs](../../msbuild/msbuild-conditional-constructs.md)。  
  
### MSBuild 擴充您的專案類型  
 MSBuild 介面和 Api 均有可能在未來版本中的變更 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 因此，最好使用受管理的封裝架構 \(MPF\) 類別，因為它們提供防護的變更。  
  
 管理封裝個專案的架構 \(MPFProj\) 提供建立和管理新的專案系統的協助程式類別。 您可以在程式碼並編譯指示找出來源 [專案\-Visual Studio 2013 的 MPF](http://mpfproj12.codeplex.com/)。  
  
 特定專案的 MPF 類別如下所示︰  
  
|類別|實作|  
|--------|--------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement` 類別是 MSBuild 項目的包裝函式。  
  
#### 單一檔案產生器與MSBuild 工作  
 單一檔案產生器是可在執行階段，但可以使用 MSBuild 工作，在設計階段和建置時間。 最大的彈性，因此，使用 MSBuild 工作來轉換和產生的程式碼。 如需詳細資訊，請參閱[自訂工具](../../extensibility/internals/custom-tools.md)。  
  
## 請參閱  
 [MSBuild Reference](../../msbuild/msbuild-reference.md)   
 [MSBuild](http://msdn.microsoft.com/zh-tw/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)   
 [自訂工具](../../extensibility/internals/custom-tools.md)
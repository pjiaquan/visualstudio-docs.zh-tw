---
title: "LC Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#LC"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, LC task"
  - "LC task [MSBuild]"
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# LC Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包裝 LC.exe，該程式從 .licx 檔案產生 .license 檔案。  如需 LC.exe 的詳細資訊，請參閱[Lc.exe \(License Compiler\)](../Topic/Lc.exe%20\(License%20Compiler\).md)。  
  
## 參數  
 下表說明 `LC` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`LicenseTarget`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定要產生 .licenses 檔案的可執行檔。|  
|`NoLogo`|選擇性 `Boolean` 參數。<br /><br /> 隱藏 Microsoft 程式啟始資訊顯示。|  
|`OutputDirectory`|選擇性 `String` 參數。<br /><br /> 指定要放置輸出 .licenses 檔案的目錄。|  
|`OutputLicense`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 輸出參數。<br /><br /> 指定 .licenses 檔案的名稱。  如果沒有指定名稱，便會使用 .licx 檔案的名稱，並將 .licenses 檔案置於含有 .licx 檔案的目錄中。|  
|`ReferencedAssemblies`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要在產生 .license 檔案時載入的參考元件。|  
|`SdkToolsPath`|選擇性 `String` 參數。<br /><br /> 指定 SDK 工具 \(例如 resgen.exe\) 的路徑。|  
|`Sources`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定含有授權元件的項目以包括在 .licenses 檔案中。  如需詳細資訊，請參閱[Lc.exe \(License Compiler\)](../Topic/Lc.exe%20\(License%20Compiler\).md) 之中 `/complist` 參數的文件。|  
  
 除了以上列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.ToolTask> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md)。  
  
## 範例  
 下列範例使用 `LC` 工作來編譯授權。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
<!-- Item declarations, etc -->  
  
    <Target Name="CompileLicenses">  
        <LC  
            Sources="@(LicxFile)"  
            LicenseTarget="$(TargetFileName)"  
            OutputDirectory="$(IntermediateOutputPath)"  
            OutputLicenses="$(IntermediateOutputPath)$(TargetFileName).licenses"  
            ReferencedAssemblies="@(ReferencePath);@(ReferenceDependencyPaths)">  
  
            <Output  
                TaskParameter="OutputLicenses"  
                ItemName="CompiledLicenseFile"/>  
        </LC>  
    </Target>  
</Project>  
```  
  
## 請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)
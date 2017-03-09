---
title: "AspNetCompiler Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#AspNetCompiler"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, AspNetCompiler task"
  - "AspNetCompiler task [MSBuild]"
ms.assetid: f811c019-a67b-4d54-82e6-e29549496f6e
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# AspNetCompiler Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`AspNetCompiler` 工作包裝 aspnet\_compiler.exe，這是先行編譯 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式的公用程式。  
  
## 工作參數  
 下表說明 `AspNetCompiler` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`AllowPartiallyTrustedCallers`|選擇性 `Boolean` 參數。<br /><br /> 如果此參數為 `true`，則強式名稱組件允許部分信任的呼叫端。|  
|`Clean`|選擇性 `Boolean` 參數。<br /><br /> 如果此參數為 `true`，先行編譯的應用程式就會進行清除建置。  之前編譯過的任何元件都會重新編譯。  預設值是 `false`。  這個參數對應於 aspnet\_compiler.exe 上的 **\-c** 選項。|  
|`Debug`|選擇性 `Boolean` 參數。<br /><br /> 如果這個參數為 `true`，在編譯 \(Compilation\) 期間便會發出偵錯資訊 \(.PDB 檔\)。  預設值是 `false`。  這個參數對應於 aspnet\_compiler.exe 上的 **\-d** 選項。|  
|`DelaySign`|選擇性 `Boolean` 參數。<br /><br /> 如果此參數為 `true`，則建立組件時不會完整簽署該組件。|  
|`FixedNames`|選擇性 `Boolean` 參數。<br /><br /> 如果此參數為 `true`，則會為編譯的組件指定固定的名稱。|  
|`Force`|選擇性 `Boolean` 參數。<br /><br /> 如果這個參數為 `true`，工作便會覆寫目標 \(Target\) 目錄 \(如果已經存在\)。  現有的內容都會遺失。  預設值是 `false`。  這個參數對應於 aspnet\_compiler.exe 上的 **\-f** 選項。|  
|`KeyContainer`|選擇性 `String` 參數。<br /><br /> 指定強式名稱金鑰容器。|  
|`KeyFile`|選擇性 `String` 參數。<br /><br /> 指定強式名稱金鑰檔的實體路徑。|  
|`MetabasePath`|選擇性 `String` 參數。<br /><br /> 指定應用程式的完整 IIS Metabase 路徑。  這個參數無法與 `VirtualPath` 或 `PhysicalPath` 參數合併。  這個參數對應於 aspnet\_compiler.exe 上的 **\-m** 選項。|  
|`PhysicalPath`|選擇性 `String` 參數。<br /><br /> 指定要編譯之應用程式的實體路徑。  如果遺失此參數，便會使用 IIS Metabase 來找出應用程式。  這個參數對應於 aspnet\_compiler.exe 上的 **\-p** 選項。|  
|`TargetFrameworkMoniker`|選擇性 `String` 參數。<br /><br /> 指定 TargetFrameworkMoniker，表示應該使用 aspnet\_compiler.exe 的哪個 .NET Framework 版本。  只接受 .NET Framework Moniker。|  
|`TargetPath`|選擇性 `String` 參數。<br /><br /> 指定要將應用程式編譯至的實體路徑。  如果沒有指定，應用程式便會就地先行編譯。|  
|`Updateable`|選擇性 `Boolean` 參數。<br /><br /> 如果此參數為 `true`，先行編譯的應用程式就會是可更新的。  預設值是 `false`。  這個參數對應於 aspnet\_compiler.exe 上的 **\-u** 選項。|  
|`VirtualPath`|選擇性 `String` 參數。<br /><br /> 所要編譯之應用程式的虛擬路徑。  如果有指定 `PhysicalPath`，就會使用實體路徑來找出應用程式。  否則，便會使用 IIS Metabase，並假設應用程式位於預設網站。  這個參數對應於 aspnet\_compiler.exe 上的 **\-v** 選項。|  
  
## 備註  
 除了以上列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.ToolTask> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md)。  
  
## 範例  
 在下列程式碼範例中，使用 `AspNetCompiler` 工作來先行編譯 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="PrecompileWeb">  
        <AspNetCompiler  
            VirtualPath="/MyWebSite"  
            PhysicalPath="c:\inetpub\wwwroot\MyWebSite\"  
            TargetPath="c:\precompiledweb\MyWebSite\"  
            Force="true"  
            Debug="true"  
        />  
    </Target>  
</Project>  
```  
  
## 請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)
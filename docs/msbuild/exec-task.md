---
title: "Exec Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Exec"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Exec task [MSBuild]"
  - "MSBuild, Exec task"
ms.assetid: c9b7525a-b1c9-40fc-8bce-77a5b8f960d8
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Exec Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用指定的引數執行指定的程式或命令。  
  
## 參數  
 下表說明 `Exec` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`Command`|必要的 `String` 參數。<br /><br /> 要執行的命令。  這些命令可能是系統命令 \(例如 attrib\) 或可執行檔 \(例如 program.exe、runprogram.bat 或 setup.msi\)。<br /><br /> 這個參數可以包含多行命令。  或者，您也可以將多個命令放在批次檔中，並使用這個參數來執行它。|  
|`CustomErrorRegularExpression`|選擇性 `String` 參數。<br /><br /> 指定要在工具輸出中找出錯誤行的規則運算式。  這對產生非一般格式輸出的工具非常有用。|  
|`CustomWarningRegularExpression`|選擇性 `String` 參數。<br /><br /> 指定要在工具輸出中找出警告行的規則運算式。  這對產生非一般格式輸出的工具非常有用。|  
|`ExitCode`|選擇性 \(Optional\) `Int32` 輸出唯讀參數。<br /><br /> 指定由執行的命令所提供的結束代碼 \(Exit Code\)。|  
|`IgnoreExitCode`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，則工作會忽略由執行的命令所提供的結束代碼。  否則，如果執行的命令傳回非零的結束代碼，工作便會傳回 `false`。|  
|`IgnoreStandardErrorWarningFormat`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `false`，則選取輸出中符合標準錯誤\/警告格式的文字行，並將其記錄為錯誤\/警告。  如果為 `true`，則停用此行為。|  
|`Outputs`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 含有工作的輸出項目。  `Exec` 工作不會自行設定這些項目。  反之，您可以提供這些項目，就像是工作設定過這些項目一樣，以便以後能在專案中加以使用。|  
|`StdErrEncoding`|選擇性 `String` 輸出參數。<br /><br /> 指定擷取之工作標準錯誤資料流的編碼方式。  預設是目前主控台輸出的編碼方式。|  
|`StdOutEncoding`|選擇性 `String` 輸出參數。<br /><br /> 指定擷取之工作標準輸出資料流的編碼方式。  預設是目前主控台輸出的編碼方式。|  
|`WorkingDirectory`|選擇性 `String` 參數。<br /><br /> 指定將會執行命令的目錄。|  
  
## 備註  
 當無法使用您所執行的工作 \(Job\) 之特定 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 工作 \(Task\) 時，這項工作 \(Task\) 便相當有用。  但是與較特殊的工作不同，`Exec` 工作無法從其所執行的工具或命令收集輸出。  
  
 `Exec` 工作會呼叫 cmd.exe，而不會直接叫用程序。  
  
 除了本文件中列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.ToolTask> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md)。  
  
## 範例  
 下列範例使用 `Exec` 工作來執行命令。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Binaries Include="*.dll;*.exe"/>  
    </ItemGroup>  
  
    <Target Name="SetACL">  
        <!-- set security on binaries-->  
        <Exec Command="echo y| cacls %(Binaries.Identity) /G everyone:R"/>  
    </Target>  
  
</Project>  
```  
  
## 請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)
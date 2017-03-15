---
title: "GetFrameworkSdkPath Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "GetFrameworkSdkPath task [MSBuild]"
  - "MSBuild, GetFrameworkSdkPath task"
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# GetFrameworkSdkPath Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

擷取 [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] 的路徑。  
  
## 工作參數  
 下表說明 `GetFrameworkSdkPath` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`FrameworkSdkVersion20Path`|選擇性的 `String` 唯讀輸出參數。<br /><br /> 傳回 .NET SDK 2.0 版的路徑 \(如果存在\)。  否則會傳回 `String.Empty`。|  
|`FrameworkSdkVersion35Path`|選擇性的 `String` 唯讀輸出參數。<br /><br /> 傳回 .NET SDK 3.5 版的路徑 \(如果存在\)。  否則會傳回 `String.Empty`。|  
|`FrameworkSdkVersion40Path`|選擇性的 `String` 唯讀輸出參數。<br /><br /> 傳回 .NET SDK 4.0 版的路徑 \(如果存在\)。  否則會傳回 `String.Empty`。|  
|`Path`|選擇性 `String` 輸出參數。<br /><br /> 包含 .NET SDK 的最新路徑 \(如果存在任何版本\)。  否則會傳回 `String.Empty`。|  
  
## 備註  
 除了以上列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## 範例  
 下列範例使用 `GetFrameworkSdkPath` 工作，以便在 `SdkPath` 屬性中儲存 [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] 的路徑。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkSdkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="SdkPath" />  
        </GetFrameworkSdkPath>  
        <Message Text="$(SdkPath)"/>  
    </Target>  
</Project>  
```  
  
## 請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)
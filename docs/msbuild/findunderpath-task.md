---
title: "FindUnderPath Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#FindUnderPath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, FindUnderPath task"
  - "FindUnderPath task [MSBuild]"
ms.assetid: 3c6d58b0-36e8-47aa-bfca-b73dd2045d91
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# FindUnderPath Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

判斷在指定的項目集合中，哪些項目的路徑在指定的資料夾之中或之下。  
  
## 參數  
 下表說明 `FindUnderPath` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`Files`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定檔案，這些檔案的路徑會與 `Path` 參數所指定的路徑相比較。|  
|`InPath`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含在指定路徑下找到的項目。|  
|`OutOfPath`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含未在指定路徑下找到的項目。|  
|`Path`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定用來做為參考的資料夾路徑。|  
|`UpdateToAbsolutePaths`|選擇性 `Boolean` 參數。<br /><br /> 如果為 true，則會將輸出項目的路徑更新為絕對路徑。|  
  
## 備註  
 除了以上列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## 範例  
 下列範例使用 `FindUnderPath` 工作來判斷 `MyFiles` 項目中包含的檔案路徑，是否可在 `SearchPath` 屬性指定的路徑下找到。  在工作完成後，`FilesNotFoundInPath` 項目會含有 `File1.txt` 檔，而 `FilesFoundInPath` 項目則會含有 `File2.txt` 檔。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <MyFiles Include="C:\File1.txt" />  
        <MyFiles Include="C:\Projects\MyProject\File2.txt" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <SearchPath>C:\Projects\MyProject</SearchPath>  
    </PropertyGroup>  
  
    <Target Name="FindFiles">  
        <FindUnderPath  
            Files="@(MyFiles)"  
            Path="$(SearchPath)">  
            <Output  
                TaskParameter="InPath"  
                ItemName="FilesFoundInPath" />  
            <Output  
                TaskParameter="OutOfPath"  
                ItemName="FilesNotFoundInPath" />  
        </FindUnderPath>  
    </Target>  
  
</Project>  
```  
  
## 請參閱  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [工作](../msbuild/msbuild-tasks.md)   
 [MSBuild 概念](../msbuild/msbuild-concepts.md)
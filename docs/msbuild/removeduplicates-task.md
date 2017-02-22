---
title: "RemoveDuplicates Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#RemoveDuplicates"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, RemoveDuplicates task"
  - "RemoveDuplicates task [MSBuild]"
ms.assetid: 481cbab6-73ff-488c-aba5-2c09f9eb1e04
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# RemoveDuplicates Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

從指定的項目集合中移除重複的項目。  
  
## 參數  
 下表說明 `RemoveDuplicates` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`Filtered`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含移除所有重複項目的項目集合。|  
|`Inputs`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 要從中移除重複項目的項目集合。|  
  
## 備註  
 此工作不區分大小寫，而且在判斷重複項目時不會比較項目中繼資料 \(Metadata\)。  
  
 除了以上列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## 範例  
 下列範例使用 `RemoveDuplicates` 工作來從 `MyItems` 項目集合中移除重複項目。  當工作完成時，`FilteredItems` 項目集合只會含有一個項目。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyItems Include="MyFile.cs"/>  
        <MyItems Include="MyFile.cs">  
            <Culture>fr</Culture>  
        </MyItems>  
        <MyItems Include="myfile.cs"/>  
    </ItemGroup>  
  
    <Target Name="RemoveDuplicateItems">  
        <RemoveDuplicates  
            Inputs="@(MyItems)">  
            <Output  
                TaskParameter="Filtered"  
                ItemName="FilteredItems"/>  
        </RemoveDuplicates>  
    </Target>  
</Project>  
```  
  
## 請參閱  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [MSBuild 概念](../msbuild/msbuild-concepts.md)   
 [工作](../msbuild/msbuild-tasks.md)
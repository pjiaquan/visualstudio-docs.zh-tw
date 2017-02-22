---
title: "WriteLinesToFile Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "WriteLinesToFile task [MSBuild]"
  - "MSBuild, WriteLinesToFile task"
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# WriteLinesToFile Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

將指定項目的路徑寫入指定的文字檔。  
  
## 工作參數  
 下表說明 `WriteLinestoFile` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`File`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定將項目寫入的檔案。|  
|`Lines`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定將寫入檔案的項目。|  
|`Overwrite`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，則工作會覆寫檔案中的任何現有內容。|  
|`Encoding`|選擇性 `String` 參數。<br /><br /> 選取字元編碼，例如 "Unicode"。  請參閱<xref:System.Text.Encoding>。|  
  
## 備註  
 如果 `Overwrite` 為 `true`，則建立新檔案，將內容寫入檔案，然後關閉檔案。  如果檔案已經存在，則會覆寫該檔案。  如果 `Overwrite` 為 `false`，請將內容附加至檔案，如果檔案不存在，則建立目標檔案。  
  
 除了以上列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## 範例  
 下列範例使用 `WriteLinesToFile` 工作將 `MyItems` 項目集合中的項目路徑，寫入 `MyTextFile` 項目集合所指定的檔案中。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
        <MyItems Include="*.cs"/>  
    </ItemGroup>  
  
    <Target Name="WriteToFile">  
        <WriteLinesToFile  
            File="@(MyTextFile)"  
            Lines="@(MyItems)"  
            Overwrite="true"  
            Encoding="Unicode"/>  
    </Target>  
  
</Project>  
```  
  
## 請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)
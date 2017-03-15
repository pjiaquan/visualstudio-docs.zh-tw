---
title: "AssignCulture Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#AssignCulture"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, AssignCulture task"
  - "AssignCulture task [MSBuild]"
ms.assetid: 8f8314cc-82a6-4f16-a62d-b9f0d1d5e274
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# AssignCulture Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

這項工作可接受一份項目清單，清單中可包含做為檔案名稱一部分的有效  .NET 文化特性 \(Culture\) 識別項，並產生具有 `Culture` 中繼資料 \(Metadata，其中含有對應的文化特性識別項\) 的項目。  例如，Form1.fr\-fr.resx 這個檔名具有內嵌的文化特性識別項 "fr\-fr"，因此這項工作會產生具有相同檔名的項目，並且中繼資料 `Culture` 會等於 `fr-fr`。  這個工作同時也會一份不包含文化特性的檔名清單。  
  
## 工作參數  
 下表說明 `AssignCulture` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`AssignedFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含在 `Files` 參數中接收的項目清單，並在每個項目中加入 `Culture` 中繼資料項目。<br /><br /> 如果從 `Files` 參數收到的項目已經含有 `Culture` 中繼資料項目，就會使用原始的中繼資料項目。<br /><br /> 如果檔名包含有效的文化特性識別項，此工作就只會指派一個 `Culture` 中繼資料項目。  文化特性識別項必須介於檔名的最後兩點之間。|  
|`AssignedFilesWithCulture`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含來自 `AssignedFiles` 參數的項目子集，這些項目具有 `Culture` 中繼資料項目。|  
|`AssignedFilesWithNoCulture`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含來自 `AssignedFiles` 參數的項目子集，這些項目沒有 `Culture` 中繼資料項目。|  
|`CultureNeutralAssignedFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含在 `AssignedFiles` 參數中產生的相同項目清單，不過已經從檔名移除了文化特性。<br /><br /> 此工作只會在出現有效的文化特性識別項時，從檔名中移除文化特性。|  
|`Files`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要指派文化特性的檔案清單，這些檔案具有內嵌的文化特性名稱。|  
  
## 備註  
 除了以上列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## 範例  
 下列範例對 `ResourceFiles` 項目集合執行 `AssignCulture` 工作。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ResourceFiles Include="MyResource1.fr.resx"/>  
        <ResourceFiles Include="MyResource2.XX.resx"/>  
    </ItemGroup>  
  
    <Target Name="Culture">  
        <AssignCulture  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
            <Output TaskParameter="AssignedFilesWithCulture"  
                ItemName="OutAssignedFilesWithCulture"/>  
            <Output TaskParameter="AssignedFilesWithNoCulture"  
                ItemName="OutAssignedFilesWithNoCulture"/>  
            <Output TaskParameter="CultureNeutralAssignedFiles"  
                ItemName="OutCultureNeutralAssignedFiles"/>  
        </AssignCulture>  
    </Target>  
</Project>  
```  
  
 下表描述執行工作後輸出項目的值。  項目中繼資料出現在項目後的括號中。  
  
|項目集合|內容|  
|----------|--------|  
|`OutAssignedFiles`|`MyResource1.fr.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx` \(沒有其他中繼資料\)|  
|`OutAssignedFilesWithCulture`|`MyResource1.fr.resx (Culture="fr")`|  
|`OutAssignedFilesWithNoCulture`|`MyResource2.XX.resx` \(沒有其他中繼資料\)|  
|`OutCultureNeutralAssignedFiles`|`MyResource1.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx (`沒有其他中繼資料\)|  
  
## 請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)
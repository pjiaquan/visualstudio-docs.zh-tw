---
title: "Warning Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Warning"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Warning task [MSBuild]"
  - "MSBuild, Warning task"
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Warning Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在建置期間根據評估的條件陳述式記錄警告。  
  
## 參數  
 下表說明 `Warning` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`Code`|選擇性 `String` 參數。<br /><br /> 與警告關聯的警告程式碼。|  
|`File`|選擇性 `String` 參數。<br /><br /> 指定相關的檔案 \(如果有的話\)。  如果未提供任何檔案，則會使用 Warning 工作。|  
|`HelpKeyword`|選擇性 `String` 參數。<br /><br /> 要與警告產生關聯的 Help 關鍵字。|  
|`Text`|選擇性 `String` 參數。<br /><br /> `Condition` 參數評估為 `true` 時，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 所記錄的警告文字。|  
  
## 備註  
 `Warning` 工作可以讓 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案在進行下一個建置步驟之前，檢查必要的組態或屬性 \(Property\) 是否存在。  
  
 如果 `Warning` 工作的 `Condition` 參數評估為 `true`，則會記錄 `Text` 參數的值並繼續執行建置。  如果沒有 `Condition` 參數，就會記錄警告文字。  如需記錄的詳細資訊，請參閱 [取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)。  
  
 除了以上列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## 範例  
 下列程式碼範例會檢查在命令列上設定的屬性。  如果沒有設定屬性，專案便會發出警告事件，並記錄 `Warning` 工作的 `Text` 參數值。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Warning  
            Text=" The 0 property was not set on the command line."  
            Condition="'$(0)' == ''" />  
        <Warning  
            Text=" The FREEBUILD property was not set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## 請參閱  
 [取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)
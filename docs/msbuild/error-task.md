---
title: "Error Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Error"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Error task [MSBuild]"
  - "MSBuild, Error task"
ms.assetid: e96a90ee-a8ae-4e5b-8ef2-b5cf5fedd8b2
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Error Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

停止建置並根據評估的條件陳述式記錄錯誤。  
  
## 參數  
 下表說明 `Error` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`Code`|選擇性 `String` 參數。<br /><br /> 與錯誤關聯的錯誤碼。|  
|`File`|選擇性 `String` 參數。<br /><br /> 包含錯誤之檔案的名稱。  如果未提供任何檔案名稱，則會使用包含 Error 工作的檔案。|  
|`HelpKeyword`|選擇性 `String` 參數。<br /><br /> 要與錯誤產生關聯的 Help 關鍵字。|  
|`Text`|選擇性 `String` 參數。<br /><br /> `Condition` 參數評估為 `true` 時，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 所記錄的錯誤文字。|  
  
## 備註  
 `Error` 工作可以讓 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案對記錄器發出錯誤文字並停止建置的執行。  
  
 如果 `Condition` 參數評估為 `true`，便會停止建置並記錄錯誤。  如果沒有 `Condition` 參數，便會記錄錯誤，並停止建置的執行。  如需記錄的詳細資訊，請參閱 [取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)。  
  
 除了以上列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## 範例  
 下列的程式碼範例會確認所有必要的屬性都已設定。  如果沒有設定這些屬性，專案便會發出錯誤事件，並記錄 `Error` 工作的 `Text` 參數值。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Error  
            Text=" The 0 property must be set on the command line."  
            Condition="'$(0)' == ''" />  
        <Error  
            Text="The FREEBUILD property must be set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## 請參閱  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)
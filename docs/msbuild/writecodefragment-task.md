---
title: "WriteCodeFragment Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, WriteCodeFragment task"
  - "WriteCodeFragment task [MSBuild]"
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# WriteCodeFragment Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

從指定產生的程式碼片段產生暫存程式碼檔案。  請不要刪除這個檔案。  
  
## 參數  
 下表說明 `WriteCodeFragment` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`AssemblyAttributes`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 要寫入之欄位的描述。  項目 `Include` 的值是屬性的完整型別名稱，例如 "System.AssemblyVersionAttribute"。<br /><br /> 每個中繼資料都是參數的名稱\-值組，這必須是 `String` 的型別。  某些屬性只允許建構函式位置引數。  不過，您可以在任何屬性中使用這樣的參數。  若要設定建構函式位置屬性，請使用類似 "\_Parameter1"、"\_Parameter2" 等的中繼資料名稱。<br /><br /> 無法跳過參數索引。|  
|`Language`|必要的 `String` 參數。<br /><br /> 指定要產生之程式碼的語言。<br /><br /> `Language` 可以是可使用 CodeDom 提供者的任何語言，例如 "C\#" 或 "VisualBasic"。  發出的檔案將會有該語言的預設副檔名。|  
|`OutputDirectory`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定已產生程式碼的目的資料夾 \(一般是中繼資料夾\)。|  
|`OutputFile`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 輸出參數。<br /><br /> 指定已產生之檔案的路徑。  如果此參數是使用檔案名稱所設定，就會在檔案名稱前面加上目的地資料夾。  如果是使用根目錄設定的，則會忽略目的地資料夾。<br /><br /> 如果未設定此參數，則輸出檔案名稱會是目的資料夾、任意檔案名稱，以及指定之語言的預設副檔名。|  
  
## 備註  
 除了會有表中列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## 請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)
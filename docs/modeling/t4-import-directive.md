---
title: "T4 匯入指示詞 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 713ca975-b9aa-4210-bf6d-b7660f5b193b
caps.latest.revision: 3
caps.handback.revision: 3
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# T4 匯入指示詞
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] T4 文字範本的程式碼區塊中，`import` 指示詞可讓您不必提供完整名稱，即可參考另一個命名空間中的項目。  這個指示詞相當於 C\# 中的 `using` 或 [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)] 中的 `imports`。  
  
 如需撰寫 T4 文字範本的一般概觀，請參閱[撰寫 T4 文字範本](../modeling/writing-a-t4-text-template.md)。  
  
## 使用匯入指示詞  
  
```  
<#@ import namespace="namespace" #>  
```  
  
 在這個範例中，範本程式碼會省略 System.IO 成員的明確命名空間。  
  
```  
<#@ import namespace="System.IO" #>  
<#   
   string fileContent = File.ReadAllText("C:\x.txt"); // System.IO.File  
#>   
The file contains: <#=  fileContent #>  
```  
  
## 標準匯入  
 下列命名空間會自動匯入，因此您不需要為它撰寫 import 指示詞：  
  
-   `System`  
  
 此外，如果使用自訂指示詞，指示詞處理器可能會自動匯入一些組件。  
  
 例如，如果撰寫網域指定的語言 \(DSL\)，就不需要為下列命名空間撰寫 import 指示詞：  
  
-   `Microsoft.VisualStudio.Modeling`  
  
-   DSL 的命名空間  
  
## 請參閱  
 [T4 組件指示詞](../modeling/t4-assembly-directive.md)
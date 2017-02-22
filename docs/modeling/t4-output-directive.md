---
title: "T4 輸出指示詞 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: 4
caps.handback.revision: 4
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# T4 輸出指示詞
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 文字範本中，`output` 指示詞用來定義轉換檔案的副檔名和編碼。  
  
 例如，如果 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 專案包括名稱為 **MyTemplate.tt** 且包含下列指示詞的範本檔：  
  
 `<#@output extension=".cs"#>`  
  
 則 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會產生名稱為 **MyTemplate.cs** 的檔案。  
  
 在執行階段 \(前置處理過的\) 文字範本中，不需要 `output` 指示詞。  而是，您的應用程式會呼叫 `TextTransform()` 來取得產生的字串。  如需詳細資訊，請參閱[使用 T4 文字範本在執行階段產生文字](../modeling/run-time-text-generation-with-t4-text-templates.md)。  
  
## 使用輸出指示詞  
  
```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 在每個文字範本中，不應該有多個 `output` 指示詞。  
  
## extension 屬性  
 指定所產生文字輸出檔案的副檔名。  
  
 預設值是 **.cs**。  
  
 例如：  
 `<#@ output extension=".txt" #>`  
  
 `<#@ output extension=".htm" #>`  
  
 `<#@ output extension=".cs" #>`  
  
 `<#@ output extension=".vb" #>`  
  
 可接受值：  
 任何有效的副檔名。  
  
## encoding 屬性  
 指定要在產生輸出檔案時使用的編碼。  例如：  
  
 `<#@ output encoding="utf-8"#>`  
  
 預設值是文字範本檔所使用的編碼。  
  
 可接受值：  
 `us-ascii`  
  
 `utf-16BE`  
  
 `utf-16`  
  
 `utf-8`  
  
 `utf-7`  
  
 `utf-32`  
  
 `0` \(系統預設值\)  
  
 一般而言，您可以使用 <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName> 所傳回之任何編碼的 WebName 字串或 CodePage 號碼。
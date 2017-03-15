---
title: "使用自訂主機處理文字範本 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "文字範本, 自訂指示詞主機"
  - "文字範本, 在應用程式或 VS 擴充功能中"
ms.assetid: affa3296-854d-47d6-9685-285f6d9ba5dc
caps.latest.revision: 33
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 33
---
# 使用自訂主機處理文字範本
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

「*文字範本轉換*」\(Text Template Transformation\) 流程採用「*文字範本*」\(Text Template\) 檔做為輸入，並產生文字檔做為輸出。  您可以從 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 擴充功能，或從執行於已安裝 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 之電腦的獨立應用程式中，呼叫文字轉換引擎。  不過，您必須提供「*文字範本化主應用程式*」\(Text Templating Host\)。  這個類別會將範本連接至環境、尋找資源 \(例如組件和 Include 檔\)，以及處理輸出和錯誤訊息。  
  
> [!TIP]
>  如果您要撰寫將執行於 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的封裝或擴充功能，請考慮使用文字範本化服務，而不是撰寫自己的主應用程式。  如需詳細資訊，請參閱[叫用 VS 擴充功能中的文字轉換](../modeling/invoking-text-transformation-in-a-vs-extension.md)。  
  
> [!NOTE]
>  不建議您在伺服器應用程式中使用文字範本轉換。  除非在單一執行緒中，否則也不建議您使用文字範本轉換。  這是因為文字範本化引擎會重複使用單一 AppDomain 來轉譯、編譯和執行範本。  轉譯過的程式碼並不是安全執行緒。  引擎是專門用來循序處理檔案，就像在設計階段於 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 專案中一樣。  
>   
>  針對執行階段應用程式，請考慮使用前置處理過的文字範本：請參閱[使用 T4 文字範本在執行階段產生文字](../modeling/run-time-text-generation-with-t4-text-templates.md)。  
  
 如果應用程式使用一組在編譯階段固定不變的範本，則使用「前置處理過的範本」會比較簡單。  如果應用程式是在沒有安裝 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的電腦上執行，您也可以這個處理方法。  如需詳細資訊，請參閱[使用 T4 文字範本在執行階段產生文字](../modeling/run-time-text-generation-with-t4-text-templates.md)。  
  
## 在應用程式中執行文字範本  
 若要執行文字範本，可以呼叫 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> 的 ProcessTemplate 方法：  
  
```  
using Microsoft.VisualStudio.TextTemplating;  
...  
Engine engine = new Engine();  
string output = engine.ProcessTemplate(templateString, host);  
```  
  
 您的應用程式必須尋找和提供範本，而且必須處理輸出。  
  
 在 `host` 參數中，必須提供實作 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> 的類別。  引擎會回呼這個類別。  
  
 主應用程式必須能夠記錄錯誤、解析組件和 Include 檔的參考、提供可在其中執行範本的應用程式定義域，以及為每個指示詞呼叫適當的指示詞處理器。  
  
 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> 定義於 **Microsoft.VisualStudio.TextTemplating.\*.0.dll** 中，而 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> 則定義於 **Microsoft.VisualStudio.TextTemplating.Interfaces.\*.0.dll** 中。  
  
## 本章節內容  
 [逐步解說：建立自訂文字範本主機](../modeling/walkthrough-creating-a-custom-text-template-host.md)  
 示範如何建立自訂文字範本主應用程式，讓 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的文字範本功能也可供外部使用。  
  
## 參考資料  
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>  
  
## 相關章節  
 [文字範本轉換流程](../modeling/the-text-template-transformation-process.md)  
 說明文字轉換的運作方式以及可供自訂的部分。  
  
 [建立自訂 T4 文字範本指示詞處理器](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 提供文字範本指示詞處理器的概觀。
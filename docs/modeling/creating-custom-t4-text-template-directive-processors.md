---
title: "建立自訂 T4 文字範本指示詞處理器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "文字範本, 自訂指示詞處理器"
ms.assetid: 422b47af-5441-4b02-b5ad-1b8b328457e3
caps.latest.revision: 29
caps.handback.revision: 29
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 建立自訂 T4 文字範本指示詞處理器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

「*文字範本轉換流程*」\(Text Template Transformation Process\) 採用「*文字範本*」\(Text Template\) 檔做為輸入，並產生文字檔做為輸出。  「*文字範本轉換引擎*」\(Text Template Transformation Engine\) 會控制流程，並與文字範本轉換主應用程式以及一個或多個文字範本「*指示詞處理器*」\(Directive Processor\) 互動來完成流程。  如需詳細資訊，請參閱[文字範本轉換流程](../modeling/the-text-template-transformation-process.md)。  
  
 若要建立自訂指示詞處理器，您可以建立繼承 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 或 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 的類別。  
  
 這兩者之間的差異在於，<xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 會實作從使用者取得參數並產生製作範本輸出檔之程式碼時所需的最基本介面；  <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 則實作需求\/供給設計模式。  <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 會處理 `requires` 和 `provides` 這兩個特別的參數。  例如，自訂指示詞處理器可能接受使用者提供的檔案名稱、開啟和讀取該檔案，然後將檔案的文字儲存在名為 `fileText` 的變數中。  <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 類別的子類別會將使用者提供的檔案名稱做為 `requires` 參數的值，並將用來儲存文字之變數的名稱當做 `provides` 參數的值。  這個處理器接著開啟和讀取該檔案，然後將檔案的文字儲存在指定的變數中。  
  
 您必須先註冊自訂指示詞處理器，才能從 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的文字範本中呼叫它。  
  
 如需如何加入相關登錄機碼的詳細資訊，請參閱[部署自訂指示詞處理器](../modeling/deploying-a-custom-directive-processor.md)。  
  
## 自訂指示詞  
 自訂指示詞看起來如下：  
  
 `<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" … #>`  
  
 當您想要從文字範本存取外部資料或資源時，可以使用自訂指示詞處理器。  
  
 不同的文字範本可以共用單一指示詞處理器提供的功能，因此指示詞處理器可提供重複使用程式碼的方式。  內建的 `include` 指示詞也是同樣的情況，因為它可以用來提供共通的程式碼，在不同的文字範本之間共用。  但還是有些差別，`include` 指示詞所提供的任何功能都是固定的，無法接受參數。  如果您想要在文字範本中提供常用的功能並允許範本傳遞參數，就必須建立自訂指示詞處理器。  
  
 舉例來說，自訂指示詞處理器可以是：  
  
-   接受使用者名稱及密碼做為參數並從資料庫傳回資料的指示詞處理器。  
  
-   接受檔案名稱做為參數並開啟和讀取檔案的指示詞處理器。  
  
### 自訂指示詞處理器的主體部分  
 若要開發指示詞處理器，您必須建立繼承 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 或 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 的類別。  
  
 您必須實作且最為重要的 `DirectiveProcessor` 方法如下。  
  
-   `bool IsDirectiveSupported(string directiveName)`：如果指示詞處理器可以處理具名指示詞，則傳回 `true`。  
  
-   `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)`：範本引擎會在範本中每個出現指示詞的位置上呼叫此方法。  您的處理器應該會儲存這些結果。  
  
 在所有的 ProcessDirective\(\) 呼叫之後，範本引擎將會呼叫下列方法：  
  
-   `string[] GetReferencesForProcessingRun()`：傳回範本程式碼所需之組件的名稱。  
  
-   `string[] GetImportsForProcessingRun()`：傳回可在範本程式碼中使用的命名空間。  
  
-   `string GetClassCodeForProcessingRun()`：傳回範本程式碼可使用之方法、屬性及其他宣告的程式碼。  若要這麼做，最簡單的方式就是建置包含 C\# 或 Visual Basic 程式碼的字串。  若要能夠從使用任何 CLR 語言的範本呼叫指示詞處理器，您可以將陳述式建構成 CodeDom 樹狀結構，然後以範本使用的語言傳回序列化該樹狀結構的結果。  
  
-   如需詳細資訊，請參閱[逐步解說：建立自訂指示詞處理器](../modeling/walkthrough-creating-a-custom-directive-processor.md)。  
  
## 本章節內容  
 [部署自訂指示詞處理器](../modeling/deploying-a-custom-directive-processor.md)  
 說明如何註冊自訂指示詞處理器。  
  
 [逐步解說：建立自訂指示詞處理器](../modeling/walkthrough-creating-a-custom-directive-processor.md)  
 說明如何建立自訂指示詞處理器、如何註冊和測試指示詞處理器，以及如何將輸出檔格式化為 HTML。
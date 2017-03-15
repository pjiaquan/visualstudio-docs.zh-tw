---
title: "自訂 T4 文字轉換 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "文字範本, API"
  - "文字範本, 自訂主機"
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: 28
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 28
---
# 自訂 T4 文字轉換
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

文字範本是 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的一項功能，可讓您透過轉換流程產生程式碼或其他文字檔。  使用 [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] 時，您可以自訂文字範本指示詞處理器或文字範本主應用程式，以擴充預設範本轉換流程。  
  
## 在本節中  
 [文字範本轉換流程](../modeling/the-text-template-transformation-process.md)  
 描述文字轉換的運作方式，並說明範本主應用程式及指示詞處理器的角色。  
  
 [建立自訂 T4 文字範本指示詞處理器](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 指示詞處理器會處理範本中的指示詞，例如 `<#@template#>.`。它可以在編譯範本時執行，並且載入組件和其他資源。  此外，也可以在執行階段插入會載入資源的程式碼。  您可以定義自己的指示詞處理器，降低範本的複雜度。  
  
 [叫用 VS 擴充功能中的文字轉換](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
 如果您要撰寫功能表命令或事件處理常式這類 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 擴充功能，該擴充功能可以使用文字範本化服務來轉換任何文字範本。  使用 Session 物件可以將參數資料傳入範本，使用 `<#@parameter#>` 指示詞可以從範本中取得值。  
  
 [使用自訂主機處理文字範本](../modeling/processing-text-templates-by-using-a-custom-host.md)  
 當文字範本的程式碼執行時，主應用程式 \(Host\) 會讓程式碼能夠存取外部檔案及應用程式 \(Application\) 的狀態。  例如，在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中執行文字轉換的主應用程式會讓您存取方案總管，  也會在錯誤訊息視窗中顯示錯誤。  如果您想要在不同的內容中執行文字轉換，可以定義自己的主應用程式，以便存取可在該內容中使用的服務。  
  
 如果您要撰寫 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 擴充功能，請考慮使用現有的文字轉換服務，而不是撰寫自己的主應用程式。  如需詳細資訊，請參閱[叫用 VS 擴充功能中的文字轉換](../modeling/invoking-text-transformation-in-a-vs-extension.md)。  
  
## 參考  
 [撰寫 T4 文字範本](../modeling/writing-a-t4-text-template.md)  
  
 提供文字範本指示詞及控制區塊的語法。
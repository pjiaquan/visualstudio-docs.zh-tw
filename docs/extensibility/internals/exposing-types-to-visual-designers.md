---
title: "公開型別，以視覺化設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "類型 [Visual Studio SDK]，將公開給視覺化設計工具"
  - "設計工具 [Visual Studio SDK]，公開型別"
  - "公開型別，以視覺化設計工具的自訂工具"
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 公開型別，以視覺化設計工具
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]必須存取類別和型別定義在執行階段以顯示視覺化設計工具。  從一組預先定義的組件，包括完整的相依性的集合目前的專案 \(參考，加上其相依性\) 就會載入類別。  它也可能需要的視覺化設計工具來存取類別和自訂工具所產生的檔案中定義的型別。  
  
 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]和[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]專案系統提供的支援存取產生的類別和型別，透過暫存的可移植執行檔 \(暫時可攜式執行\)。  自訂工具所產生的任何檔案可編譯成一個暫時組件，能夠從這些組件載入及公開給設計工具型別。  每個自訂工具的輸出就會編譯至個別的暫存 PE 時，與此暫存編譯的成敗完全取決於可編譯所產生的檔案。  即使整體而言，可能無法建置專案，個別的暫時可攜式執行可能仍然可以使用設計工具。  
  
 專案系統提供完整支援修訂記錄至輸出檔的自訂工具，前提是這些變更將會執行自訂工具的結果。  每次執行自訂工具時，會產生新的暫存 PE 時，並適當的通知會傳送到設計工具。  
  
> [!NOTE]
>  因為暫時的程式產生可執行檔會在幕後，沒有錯誤會向使用者報告，如果編譯失敗。  
  
 善加利用暫存 PE 支援的自訂工具必須遵循下列規則：  
  
-   `GeneratesDesignTimeSource`必須設定為 1 的登錄中。  
  
     沒有程式可執行檔會進行編譯沒有這個設定。  
  
-   產生的程式碼必須是通用的專案設定相同的語言。  
  
     不論自訂工具報告中要求的延伸為編譯暫存 PE <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>的`GeneratesDesignTimeSource`設為 1，登錄中。  副檔名不需要是.vb、.cs 或.jsl ； 它可以是任何副檔名。  
  
-   自訂工具所產生的程式碼必須是有效的而且必須在編譯時間在它自己使用只存在於專案中參考的組<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A>結束執行。  
  
     當編譯暫存 PE 時，只提供給編譯器的原始程式檔會是自訂工具輸出。  因此，使用暫存 PE 的自訂工具必須產生可獨立於其他檔案專案中編譯的輸出檔。  
  
## 請參閱  
 [Introduction to the BuildManager Object](http://msdn.microsoft.com/zh-tw/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [實作單一檔案產生器](../../extensibility/internals/implementing-single-file-generators.md)   
 [判斷專案的預設命名空間](../../misc/determining-the-default-namespace-of-a-project.md)   
 [註冊單一檔案產生器](../../extensibility/internals/registering-single-file-generators.md)
---
title: "自訂色彩的項目 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "可設定色彩的項目"
  - "語言服務，自訂色彩的項目"
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# 自訂色彩的項目
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

您可以覆寫類型的清單的色彩標示、 關鍵字和註解，例如實作自訂色彩的項目做為語言服務的一部分。  
  
## 使用者設定的色彩的項目  
 您可以顯示 **字型和色彩** \] 對話方塊中，選取 \[ **選項** 上 **工具** \] 功能表，然後選取 \[ **字型和色彩** 下 **環境**。 當您選取顯示，例如 **文字編輯器** 或 **命令視窗**, 、 **顯示項目** 清單方塊會顯示可顯示的所有可設定色彩的項目。 您可以檢視及變更字型、 大小、 前景色彩和每個色彩項目的背景色彩。 您可以選擇在登錄中快取存放及存取依色彩項目的名稱。  
  
## 項目色彩的呈現方式  
 因為 IDE 處理色彩的項目中的使用者覆寫 **字型和色彩** 對話方塊，您需要僅提供每個自訂色彩項目的名稱。 此名稱都會顯示於 **顯示項目** 清單。 依字母順序顯示色彩的項目。 語言服務的自訂色彩的項目分組，您就可以開始每個名稱和您語言的名稱，例如 **NewLanguage\-註解** 和 **NewLanguage\-關鍵字**。  
  
> [!CAUTION]
>  您應該避免與現有色彩項目的名稱衝突的色彩項目的名稱包含語言名稱。 如果您在開發期間變更其中一個色彩的項目名稱，您必須重設快取所建立的第一次您可設定色彩的項目可供存取。 您可以重設其 CreateExpInstance 工具，它會隨 Visual Studio SDK，通常在目錄中的實驗性快取  
>   
>  **C:\\Program 檔案 \(x86\) \\Microsoft Visual Studio 14.0\\VSSDK\\VisualStudioIntegration\\Tools\\Bin**  
>   
>  若要重設快取，請呼叫 `CreateExpInstance /Reset`。 如需 CreateExpInstance 的詳細資訊，請參閱 [CreateExpInstance 公用程式](../../extensibility/internals/createexpinstance-utility.md)。  
  
 永遠不會參考可設定色彩的項目在清單中第一個項目。 第一個項目會對應到色彩項目的索引為 0，和 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 一律會提供的預設文字色彩和該項目的屬性。 最簡單的方式來處理此未參考的項目會提供預留位置色彩項目的第一個項目清單中。  
  
## 實作自訂色彩的項目  
  
1.  定義什麼必須以您的語言，例如關鍵字、 運算子和識別項。  
  
2.  建立這些色彩項目的列舉。  
  
3.  建立關聯的剖析器或掃描器的列舉值傳回的權杖型別。  
  
     例如，代表權杖類型的值可能是自訂色彩的項目列舉型別中相同的值。  
  
4.  在您實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 方法，在您 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 物件，從您對應至從剖析器或掃描器傳回的權杖類型的自訂色彩的項目列舉值來填入屬性清單。  
  
5.  在相同類別中實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 介面，請實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> 介面，以及其兩個方法， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>。  
  
6.  實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> 介面。  
  
7.  如果您想要支援 24 位元或高的色彩值，也必須實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 介面。  
  
8.  在您語言的服務物件，建立一個清單，其中包含您 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> 物件、 一個用於您的剖析器或掃描器可以識別每個色彩的項目。  
  
     您可以使用自訂色彩的項目列舉型別對應的值來存取清單中的每個項目。 使用做為索引的列舉值清單中。 在清單中的第一個項目永遠不會存取，因為它會對應至預設的文字設定樣式 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 永遠會處理本身。 您可以為了彌補這一點預留位置色彩的項目插入清單的開頭。  
  
9. 在您實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> 方法，傳回自訂色彩的項目清單中的項目數。  
  
10. 在您實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> 方法，傳回要求之色彩的項目從您的清單。  
  
 如需如何實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 介面，請參閱 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>。  
  
## 請參閱  
 [舊版語言服務模型](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [語法著色中自訂編輯器](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [語法著色在舊版語言服務](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [實作語法標色](../../extensibility/internals/implementing-syntax-coloring.md)   
 [如何: 使用內建可設定色彩的項目](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
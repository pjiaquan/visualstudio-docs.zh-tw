---
title: "舊版的語言服務介面 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IVsLanguageInfo 介面"
  - "語言服務物件"
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# 舊版的語言服務介面
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

針對任何特定的程式設計語言，可能有語言服務中的，只有一個執行個體一次。  然而，單一語言服務可以做一個以上的編輯器。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]不會使用任何特定編輯器關聯語言服務。  因此，當您要求的語言服務作業，您就必須做為參數識別適當的編輯器。  
  
## 語言服務相關聯的公用介面  
 編輯器\] 中取得您的語言服務藉由呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>上適當的 VSPackage。  在這個呼叫中傳遞的識別碼 \(SID\) 的服務識別所要求的語言服務。  
  
 您可以對任意數量的不同類別來實作核心語言服務介面。  不過，一般的方法是在單一類別中實作下列介面：  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> \(選擇項\)  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>上所有的語言服務必須實作介面。  它提供您語言的服務，例如語言中，「 語言 」 服務，以及如何擷取 colorizer 相關聯的檔案名稱副檔名的當地語系化名稱的相關資訊。  
  
## 其他語言的服務介面  
 與語言服務可提供其他的介面。  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]要求個別的執行個體，這些文字緩衝區中的每一個執行個體的介面。  因此，您應該在它自己的物件上實作這些介面的每一個。  下表是需要文字緩衝區的執行個體的每一個執行個體的介面。  
  
|介面|描述|  
|--------|--------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|管理程式碼視窗裝飾，如 \[鉛版\] 列。  您可以使用，以取得這個介面<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>方法。  還有一個<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>每個程式碼視窗。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|語言關鍵字和分隔符號會以顏色標示。  您可以使用，以取得這個介面<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>方法。  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>會在 \[小畫家\] 階段時所呼叫的方法。  避免大量計算的工作，在<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>或可能降低效能。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|提供 IntelliSense 參數的工具提示。  語言服務能夠辨識的字元，表示該方法的資料應該顯示，例如左括號，它會呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>方法來通知關於文字檢視的語言服務已準備好要顯示參數資訊工具提示。  文字檢視然後回撥到語言服務所使用的方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>介面，以取得所需的資訊，顯示工具提示。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|提供 IntelliSense 陳述式完成。  語言服務準備好要顯示完成清單時，它會呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>上的文字檢視的方法。  文字檢視然後回撥到語言服務所使用的方法上<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>物件。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|准許您進行修改的文字檢視，其使用的命令處理常式。  您實作的類別<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>介面也必須實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面。  文字檢視擷取<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>物件藉由查詢<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>物件傳遞至<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>方法。  應該有一個<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>為每個檢視的物件。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|攔截使用者鍵入程式碼\] 視窗的命令。  監視輸出您<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>實作，以提供自訂完成資訊，並檢視修改<br /><br /> 要傳遞您<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>物件到 \[文字\] 檢視中，呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>。|  
  
## 請參閱  
 [開發語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [檢查清單︰ 建立傳統語言服務](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
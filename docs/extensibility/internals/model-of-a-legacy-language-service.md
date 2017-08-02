---
title: "舊版語言服務模型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "語言服務、 模型"
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# 舊版語言服務模型
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

語言服務定義的項目和功能，針對特定語言，並用來提供該語言特定的資訊中的編輯器\]。  比方說，編輯器\] 中，需要知道的項目和語言的關鍵字，才能支援語法標色。  
  
 語言服務密切管理編輯器\] 和 \[檢視\] 中包含編輯器\] 中的文字緩衝區中。  Microsoft IntelliSense **快速諮詢**選項是一種語言服務所提供的功能的範例。  
  
## 最小的語言服務  
 最基本的語言服務包含下列兩個物件：  
  
-   *語言服務*實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>介面。  語言服務有語言，包括其名稱、 副檔名、 程式碼視窗管理員 」 和 colorizer 的相關資訊。  
  
-   *Colorizer* 實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>介面。  
  
 下列的概念圖顯示基本語言服務的模型。  
  
 ![語言服務模型圖形](~/docs/extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
基本語言服務模型  
  
 文件視窗的主機*文件檢視*的編輯器中，在這種情況下[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]核心編輯器。  文件檢視\] 和 \[文字緩衝區均屬編輯器\]。  這些物件將會使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用特殊的文件\] 視窗中，呼叫*程式碼\] 視窗*。  程式碼\] 視窗包含在<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> ，建立且由 IDE 控制的物件。  
  
 當載入具有指定副檔名的檔案時，編輯器\] 中尋找該副檔名相關聯的語言服務並傳遞至其程式碼\] 視窗點撥打<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>方法。  語言服務，則傳回*的程式碼視窗管理員*，哪一個實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>介面。  
  
 下表概要說明模型中的物件。  
  
|元件|物件|Function|  
|--------|--------|--------------|  
|文字緩衝區|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>|Unicode 讀取\/寫入文字資料流。  很可能使用其他編碼方式的文字。|  
|程式碼\] 視窗|<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>|文件視窗，其中包含一或多個文字檢視。  當[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]是在多重文件介面 \(MDI\) 模式中，程式碼\] 視窗是 MDI 子系。|  
|文字檢視|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>|這種視窗可讓使用者瀏覽，然後使用鍵盤和滑鼠來檢視文字。  文字檢視會顯示給使用者，作為編輯者。  您可以使用一般的編輯器視窗、 \[輸出\] 視窗和 \[即時運算\] 視窗中的文字檢視。  此外，您可以設定一或多個程式碼\] 視窗內的文字檢視。|  
|文字管理員|由<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>服務，從您取得<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>指標|這種元件會維護先前所述的所有元件所共用的一般資訊。|  
|語言服務|實作相關。 實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>|語言特定的資訊，例如語法反白顯示、 陳述式完成和括號對稱會提供編輯器\] 中的物件。|  
  
## 請參閱  
 [文件資料，以及在自訂編輯器中的文件檢視](../../extensibility/document-data-and-document-view-in-custom-editors.md)
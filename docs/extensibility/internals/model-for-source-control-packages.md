---
title: "原始檔控制套件的模型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "原始檔控制 [Visual Studio SDK]，模型"
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 原始檔控制套件的模型
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

下列模型代表來源控制項實作的範例。  在模型中，您會看到必須實作的介面，您必須呼叫環境服務。  如同所有的服務，您實際上會呼叫您取得的一種服務的特定介面的方法。  若要讓它看起來更清楚如何執行序的原始檔控制識別之類別的名稱。  
  
 ![SCC&#95;TUP 範例](~/extensibility/internals/media/scc_tup.gif "SCC\_TUP")  
範例的原始檔控制專案  
  
## 介面  
 您可以執行原始檔控制的 Visual Studio，使用下表所示的介面清單中還包含新的專案類型。  
  
|介面|使用|  
|--------|--------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|呼叫專案和之前儲存它們，或變更 \(dirty\) 檔案的編輯器。  這個介面用來存取<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>服務。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|呼叫要求權限，才能新增、 移除或重新命名檔案或目錄的專案。  通知環境時已核准的新增、 移除或重新命名動作已經完成的專案也會呼叫這個介面。  它用來存取<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>服務。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|實作之任何實體的專案新增、 重新命名或移除檔案或目錄時收到通知時暫存器。  若要註冊事件告知，呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|呼叫以原始檔控制套件來登錄，並取得原始檔控制狀態的相關資訊的專案。  這個介面用來存取<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>服務。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|實作專案來回應檔案的相關資訊的來源控制項要求，並取得原始檔控制設定所需的專案檔。|  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [支援的原始檔控制](../../extensibility/internals/supporting-source-control.md)
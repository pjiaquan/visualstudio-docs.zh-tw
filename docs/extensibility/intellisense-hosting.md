---
title: "IntelliSense 裝載 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，舊版的 IntelliSense 裝載"
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# IntelliSense 裝載
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 可讓 IntelliSense 裝載。  IntellSense 裝載可讓您提供 IntelliSense 不由 Visual Studio 的文字編輯器的程式碼。  
  
## IntelliSense 裝載的使用方式  
 Visual Studio，以存取完成組和文字緩衝區的任何程式碼可以從任何地方取得 IntelliSense windows 使用者介面 \(UI\) 中。  某些範例案例，這會在完成**監看式** 視窗或在 \[中斷點屬性\] 視窗的 \[條件\] 欄位中。  
  
### 實作介面  
  
#### IVsIntellisenseHost  
 裝載 \(host\) IntelliSense 的快顯視窗的任何 UI 元件都必須支援<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>介面。  預設的核心編輯器文字檢視包含有股票<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>介面實作以保留目前的 IntelliSense 功能。  大多數的情況下，方法的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>介面的代表的項目子集實作於<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>介面。  子集合會包含 IntelliSense UI 處理、 插入號並選取項目管理和簡單的文字取代功能。  此外， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>介面會啟用不同的 IntelliSense 「 主題 」 和 「 內容 」，讓 IntelliSense 可以供直接不會用於內容文字緩衝區中的主題。  
  
#### IVsIntellisenseHost.GetHostFlags  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>必須實作介面的提供者<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A>方法，讓用戶端，以判斷哪一種 IntelliSense 的特色主應用程式支援。  
  
 中所定義的主應用程式旗標[IntelliSenseHostFlags](../extensibility/intellisensehostflags.md)，摘要如下。  
  
|IntelliSense 主應用程式旗標|描述|  
|--------------------------|--------|  
|IHF\_READONLYCONTEXT|設定這個旗標表示內容的緩衝區唯讀屬性，然後編輯只內發生的主旨文字。|  
|IHF\_NOSEPERATESUBJECT|設定這個旗標代表，並為沒有個別的 IntelliSense 主旨。  主旨中有內容的緩衝區，例如在傳統<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> IntelliSense 系統。|  
|IHF\_SINGLELINESUBJECT|設定這個旗標表示主旨不在多行功能，例如在同一行中編輯**監看式**視窗。|  
|IHF\_FORCECOMMITTOCONTEXT|如果這個旗標設定，且必須更新內容的緩衝區，唯讀旗標，內容緩衝區被忽略並繼續編輯，可讓主應用程式。|  
|IHF\_OVERTYPE|編輯 \(在主旨或內容\) 應該取代模式中。|  
  
#### IVsIntellisenseHost.BeforeCompletorCommit 和 IVsIntellisenseHost.AfterCompletorCommit  
 這些回呼方法稱為 \[完成\] 視窗中前, 及段後文字經過認可時，為了讓正在前置處理和後續處理。  
  
#### IVsIntellisenseCompletor  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor>介面是標準的完成視窗所使用的整合式的開發環境 \(IDE\) 的 co\-creatable 版。  任何<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>介面可以快速地利用這個 completor 介面實作 IntelliSense。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop>
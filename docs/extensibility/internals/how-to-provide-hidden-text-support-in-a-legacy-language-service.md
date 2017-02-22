---
title: "如何︰ 隱藏的文字中提供支援舊版語言服務 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "隱藏文字，支援"
  - "編輯器 [Visual Studio SDK]、 隱藏文字"
  - "語言服務，實作隱藏的文字區域"
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# 如何︰ 隱藏的文字中提供支援舊版語言服務
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

您可以建立隱藏的文字區域中，除了大綱區域。  用戶端控制或編輯器控制，可以是隱藏的文字區域，並且完全隱藏的文字區域。  編輯器會顯示隱藏的區域，以水平的線條。  這個範例是在 HTML 編輯器中的 \[僅指令碼\] 檢視。  
  
## 程序  
  
#### 若要實作一個隱藏的文字區域  
  
1.  Call `QueryService` for <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.  
  
     此舉會讓變數的指標， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>。  
  
2.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>、 passing 中指定的文字緩衝區的指標。  這會決定是否隱藏的文字工作階段已經存在於緩衝區。  
  
3.  如果序數已存在的話，那麼您不需要建立一個，變數的指標，現有的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>會傳回物件。  使用這個指標來列舉並建立隱藏的文字區域。  否則，呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>來建立緩衝區的隱藏的文字工作階段。  
  
     變數的指標， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>會傳回物件。  
  
    > [!NOTE]
    >  當您呼叫`CreateHiddenTextSession`，您可以指定隱藏的文字用戶端 \(也就是<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>\)。  當您展開或摺疊使用者隱藏的文字\] 或 \[大綱時，隱藏的文字用戶端會通知您。  
  
4.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>來加入一個或更多新大綱區域一次指定下列資訊在`reHidReg` \(<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>\) 參數：  
  
    1.  指定其值為`hrtConcealed`在`iType`成員的<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>結構，以指出您正在建立了隱藏的區域，而不是大綱區域。  
  
        > [!NOTE]
        >  隱藏的區域而隱藏時，編輯器便會自動顯示隱藏的區域，以指出其周圍的行數。  
  
    2.  指定的區域用戶端控制，或在編輯器控制`dwBehavior`成員的<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>結構。  智慧型的分層顯示實作可以混合控制編輯器和用戶端的大綱和隱藏的文字區域。
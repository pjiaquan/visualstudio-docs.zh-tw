---
title: "CA2232：以 STAThread 標記 Windows Form 進入點 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MarkWindowsFormsEntryPointsWithStaThread"
  - "CA2232"
helpviewer_keywords: 
  - "CA2232"
  - "MarkWindowsFormsEntryPointsWithStaThread"
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2232：以 STAThread 標記 Windows Form 進入點
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|MarkWindowsFormsEntryPointsWithStaThread|  
|CheckId|CA2232|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 組件 \(Assembly\) 會參考 <xref:System.Windows.Forms> 命名空間 \(Namespace\)，且它的進入點 \(Entry Point\) 並未以 <xref:System.STAThreadAttribute?displayProperty=fullName> 屬性 \(Attribute\) 標示。  
  
## 規則描述  
 <xref:System.STAThreadAttribute> 表示應用程式的 COM 執行緒模型為單一執行緒 Apartment。  在使用 Windows Form 的任何應用程式之進入點上必須有此屬性。如果省略的話，Windows 元件就無法正常運作。  若沒有該屬性，應用程式會使用 Windows Form 不支援的多執行緒 Apartment Model \(Multithreaded Apartment Model\)。  
  
> [!NOTE]
>  使用應用程式架構的 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 專案，並不需要以 STAThread 標記 **Main** 方法。  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 編譯器會自動進行這項工作。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將 <xref:System.STAThreadAttribute> 屬性加入至進入點。  如果有 <xref:System.MTAThreadAttribute?displayProperty=fullName> 屬性，請加以移除。  
  
## 隱藏警告的時機  
 如果針對 .NET Compact Framework 進行開發時，不需要而且不支援 <xref:System.STAThreadAttribute> 屬性，則您可以放心地隱藏這項規則的警告。  
  
## 範例  
 下列為 <xref:System.STAThreadAttribute> 之正確使用方式的範例。  
  
 [!code-cs[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
 [!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]
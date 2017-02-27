---
title: "How to: 實作 [尋找和取代機制 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，舊版-尋找和取代"
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# How to: 實作 [尋找和取代機制
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 提供兩種實作 \[尋找\/取代。  方法之一是將文字影像傳遞到殼層，並讓它處理搜尋、 反白顯示，並取代文字。  這可讓使用者指定多個文字 span。  或者，您的 VSPackage 可以控制這項功能本身。  這兩種情況中，您必須通知有關目前的目標及所有開啟的文件時所針對的殼層。  
  
### 若要實作 \[尋找\/取代  
  
1.  實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>介面，在 \[框架屬性所傳回的物件之一的<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>或<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>。  如果您要建立自訂的編輯器，您應該實作這個介面，為自訂編輯器類別的一部分。  
  
2.  使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A>方法來指定您的編輯器支援的選項，以及指示是否實作文字的影像搜尋。  
  
     如果您的編輯器支援文字的影像搜尋，實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>。  
  
     否則，實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>。  
  
3.  如果您決定使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>方法，可以簡化您的搜尋工作，藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>介面。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
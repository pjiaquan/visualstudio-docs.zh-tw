---
title: "How to: 裝載在另一個編輯器中的編輯器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，舊版-裝載巢狀的編輯器"
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# How to: 裝載在另一個編輯器中的編輯器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 Visual Studio 中，您可以藉由指定主控視窗最上層視窗裝載在另一個編輯器。  若要這麼做，請設定 \[參數<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>和<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>在子視窗外框上。  
  
### 若要設定裝載的編輯器視窗外框  
  
1.  指定的編輯器做為裝載的編輯器，藉由建立子視窗窗格。  
  
     此窗格是編輯器\] 的文字會去的地方。  
  
2.  使用控管編輯器建立<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>方法。  
  
3.  設定<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>和<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>在視窗框架的實作中裝載的編輯器做為參數傳遞這些屬性的屬性<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>方法中，分別。  
  
     如果您需要擷取這些參數，傳遞這些屬性，以<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>方法。  
  
4.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>被收納的編輯器的方法。  
  
     在編輯器\] 會顯示在包含編輯器裝載窗格。  
  
## 穩固程式設計  
 **應用程式設計工具\] 中** Visual Studio 的小組版的架構設計人員會裝載其他編輯器編輯器視窗外框的範例。  **應用程式設計工具\] 中**主控其右側窗格中的其他設計工具。  設計工具的面板 \(或**屬性**頁面\) 的每個被收納的設計工具會加入至包含視窗框架。
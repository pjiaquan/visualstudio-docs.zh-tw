---
title: "如何: 引發事件時，編輯器會失去焦點 | Microsoft Docs"
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
  - "編輯器 [Visual Studio SDK]，舊版-引發事件，在失去焦點"
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# 如何: 引發事件時，編輯器會失去焦點
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

有時候，它就必須知道當編輯器失去焦點放在視窗框架。  例如，您可能需要在編輯器\] 中的焦點不再位於它之後，從程式碼\] 視窗中擷取程式碼。  下列的程序提供相關步驟，以便接收通知的編輯器失去焦點。  
  
### 若要引發編輯器失去焦點來回應事件  
  
1.  取得監視選取事件<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>獲取<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>。  
  
2.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> ，並提供您<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>物件。  
  
3.  在您呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>，尋找`elementid==SEID_WindowFrame`。  
  
4.  測試`varValueNew`參數兩件事：  
  
    1.  您要尋找的視窗框架。  
  
    2.  您的程式遺失了該視窗外框至選取範圍點。
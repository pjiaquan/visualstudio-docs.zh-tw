---
title: "如何: 提供適用於 Windows 的自動化 | Microsoft Docs"
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
  - "自動化 [Visual Studio SDK]，工具視窗"
  - "工具視窗自動化"
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# 如何: 提供適用於 Windows 的自動化
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

您可以提供自動化的文件和工具視窗。  提供自動化是建議的只要您想要在視窗中，使用 automation 物件，且環境已經也不會提供一種現成的自動化物件，，但工作清單。  
  
## 自動化工具視窗  
 此環境提供工具視窗上自動化，藉由傳回一種標準<xref:EnvDTE.Window>物件，如下列程序所述：  
  
#### 提供自動化的工具視窗  
  
1.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>環境中，以透過方法<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>與`VSFPROPID`參數，以取得`Window`物件。  
  
2.  當呼叫端要求的工具視窗，透過 VSPackage 專屬自動化物件<xref:EnvDTE.Window.Object%2A>，環境呼叫`QueryInterface`的`IExtensibleObject`， <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>，或`IDispatch`介面。  Both `IExtensibleObject` and `IVsExtensibleObject` provide a <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> method.  
  
3.  接著再呼叫環境`GetAutomationObject`方法傳遞`NULL`，回應傳送回 VSPackage 特定物件。  
  
4.  如果呼叫`QueryInterface`的`IExtensibleObject`和`IVsExtensibleObject`失敗，那麼環境呼叫`QueryInterface`的`IDispatch`。  
  
## 自動化的文件視窗  
 一種標準<xref:EnvDTE.Document>物件也是可以從環境中，雖然編輯器可以有它自己的實作的`T:EnvDTE.Document`物件藉由實作`IExtensibleObject`介面，以及回應`GetAutomationObject`。  
  
 此外，編輯器可以提供特定 VSPackage 的自動化物件，透過擷取<xref:EnvDTE.Document.Object%2A>方法，藉由實作`IVsExtensibleObject`或`IExtensibleObject`介面。  [VSSDK 範例](../../misc/vssdk-samples.md)促成 RTF 文件特定的自動化物件。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
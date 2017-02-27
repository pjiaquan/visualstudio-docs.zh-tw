---
title: "實作連接埠提供者 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯 [偵錯 SDK]，請實作連接埠供應商"
  - "連接埠供應商實作"
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 實作連接埠提供者
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

連接埠提供者會提供給工作階段的偵錯專案經理 \(SDM\) 的要求上的連接埠。  連接埠提供者需要至非 DCOM 的電腦進行偵錯時，或當新的裝置需要支援實作。  比方說，來提供行動電話的偵錯，您可能會實作一個提供連接至行動電話 \(可能是透過數紅外線或儲存格連線\)，並列舉的程序和在電話上執行程式的連接埠的連接埠供應商。  
  
 \(包括遠端偵錯\) 的 windows 電腦上的偵錯程式中 Visual Studio 會提供連接埠的供應商，以原生和通用語言執行階段 \(CLR\) 處理程序，因此並不需要在這些情況下實作您自己的連接埠提供者。  
  
## 在本節中  
 [實作和登錄連接埠提供者](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 說明 SDM 與連接埠提供者和連接埠的互動方式。  
  
 [必要的連接埠供應商介面](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 文件以取得連接埠提供者就必須實作的介面。  
  
## 相關章節  
 [偵錯工具的概念](../../extensibility/debugger/debugger-concepts.md)  
 描述主要的偵錯架構概念。  
  
## 請參閱  
 [Visual Studio 偵錯工具擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
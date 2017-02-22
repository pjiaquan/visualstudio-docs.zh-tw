---
title: "IDebugDocumentPositionOffset2 | Microsoft Docs"
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
  - "IDebugDocumentPositionOffset2 介面"
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentPositionOffset2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

代表原始程式檔中的字元位移的位置。  
  
## 語法  
  
```  
IDebugDocumentPositionOffset2 : IUnknown  
```  
  
## 實作器注意事項  
 實作由 IDE，並且由偵錯引擎。  
  
## 方法  
 下表顯示的方法`IDebugDocumentPositionOffset2`。  
  
|方法|描述|  
|--------|--------|  
|[GetRange](../Topic/IDebugDocumentPositionOffset2::GetRange.md)|擷取目前的文件位置的範圍。|  
  
## 備註  
 這會傳回相同的資訊[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)但在`char`位移的文件的開頭。  它會存在於磁碟上，也就是字元，而非通常傳回的列和資料行資訊的一維陣列一樣，這代表文件。  
  
## 需求  
 標頭: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
---
title: "IDebugDisassemblyStream2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2 介面"
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugDisassemblyStream2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示指令資料的流。  
  
## 語法  
  
```  
IDebugDisassemblyStream2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎會實作這個介面以支援該應用程式的程式碼的反組譯碼。  
  
## 呼叫者的備忘稿  
 呼叫[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)方法會傳回這個介面。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugDisassemblyStream2`。  
  
|方法|描述|  
|--------|--------|  
|[讀取](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|讀取指令從 \[反組譯碼資料流的目前位置開始。|  
|[搜尋](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|將讀取的指標移至反組譯碼資料流指定數目之指示相對於指定的位置中。|  
|[GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md)|傳回特定的程式碼內容的程式碼位置識別項。|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|傳回指定的程式碼的位置識別碼相對應的程式碼內容物件。|  
|[GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md)|傳回代表目前的程式碼所在位置的程式碼位置識別項。|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|取得與這個反組譯碼資料流關聯的來源文件。|  
|[GetScope](../Topic/IDebugDisassemblyStream2::GetScope.md)|取得這個反組譯碼資料流的範圍。|  
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|取得這個反組譯碼資料流的大小。|  
  
## 備註  
 反組譯碼資料流可以建立代表整個地址空間或只是函式或模組的空間內。  每個指示由[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)的呼叫所傳回的結構[讀取](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)方法。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
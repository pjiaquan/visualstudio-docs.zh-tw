---
title: "IEnumDebugFrameInfo2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugFrameInfo2"
helpviewer_keywords: 
  - "IEnumDebugFrameInfo2"
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumDebugFrameInfo2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會列舉[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構。  
  
## 語法  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 會實作這個介面來提供一份結構描述目前呼叫堆疊。  
  
## 呼叫者的備忘稿  
 Visual Studio 的呼叫[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)以取得這個介面的存取中斷點，例外狀況或停止發生在偵錯的程式。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IEnumDebugFrameInfo2`。  
  
|方法|描述|  
|--------|--------|  
|[下一步](../Topic/IEnumDebugFrameInfo2::Next.md)|擷取指定的數目的[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)列舉型別序列中的結構。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|略過指定的數目的[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)列舉型別序列中的結構。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|將列舉型別序列重設至開頭。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|建立列舉值，包含目前的列舉值的列舉型別狀態。|  
|[GetCount](../Topic/IEnumDebugFrameInfo2::GetCount.md)|取得的[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)列舉值中的結構。|  
  
## 備註  
 Visual Studio 會取得這個介面來處理中斷點、 例外狀況或在偵錯程式使用者所產生的暫停的第一個步驟。  清單中的[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構表示的目前呼叫堆疊、 目前的函式呼叫，在清單\] 及 \[最舊的函式的開頭與呼叫的清單結尾。  每個`FRAMEINFO`表示堆疊框架上，在其中可以評估運算式，區域變數在觀看過的內容。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
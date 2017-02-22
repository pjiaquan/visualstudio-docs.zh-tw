---
title: "IEnumDebugReferenceInfo2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugReferenceInfo2"
helpviewer_keywords: 
  - "IEnumDebugReferenceInfo2"
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugReferenceInfo2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會列舉[DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)結構。  
  
## 語法  
  
```  
IEnumDebugReferenceInfo2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 會實作這個介面，其支援的物件參考的一部分，在記憶體中。  支援的參考時，才必須實作這個介面。  
  
## 呼叫者的備忘稿  
 Visual Studio 的呼叫[EnumChildren](../Topic/IDebugReference2::EnumChildren.md)以取得這個介面。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IEnumDebugReferenceInfo2`。  
  
|方法|描述|  
|--------|--------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|擷取指定的數目的[DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)列舉型別序列中的結構。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|略過指定的數目的[DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)列舉型別序列中的結構。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|將列舉型別序列重設至開頭。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|建立列舉值，包含目前的列舉值的列舉型別狀態。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|取得的[DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)列舉值中的結構。|  
  
## 備註  
 參考是本質上為型別和地址，而屬性是名稱、 類型及地址。  參考仍然存在，只要物件參照到存在於記憶體中。  如需詳細資訊，請參閱 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [EnumChildren](../Topic/IDebugReference2::EnumChildren.md)
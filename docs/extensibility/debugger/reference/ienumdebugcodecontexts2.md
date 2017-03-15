---
title: "IEnumDebugCodeContexts2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugCodeContexts2"
helpviewer_keywords: 
  - "IEnumDebugCodeContexts2"
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IEnumDebugCodeContexts2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面會列舉與偵錯工作階段中，或與特定程式或文件相關聯的程式碼內容。  
  
## 語法  
  
```  
IEnumDebugCodeContexts2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 會實作這個介面來代表在程式中，特定的文字位置的程式碼內容的清單或特定的文件內容的程式碼內容的清單。  
  
## 呼叫者的備忘稿  
 呼叫[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)以取得這個介面表示一份該應用程式的來源文件中特定的文字位置的程式碼內容。  
  
 呼叫[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)以取得這個介面表示一份特定的來源文件中的所有程式碼內容。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IEnumDebugCodeContexts2`。  
  
|方法|描述|  
|--------|--------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|擷取指定列舉型別序列中的程式碼內容之內。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|略過指定的數目的列舉型別序列中的程式碼內容。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|將列舉型別序列重設至開頭。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|建立列舉值，包含目前的列舉值的列舉型別狀態。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|列舉值中取得的程式碼內容的數目。|  
  
## 備註  
 Visual Studio 的呼叫[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)來填入清單中的程式碼內容的使用者可以選擇從何時設定下一個陳述式，或顯示反組譯碼的原始程式檔。  比方說，有多個 c \+ \+ 樣式範本執行個體時，就可以發生多個程式碼的內容。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
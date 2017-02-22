---
title: "IDebugDocumentTextEvents2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentTextEvents2"
helpviewer_keywords: 
  - "IDebugDocumentTextEvents2 介面"
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentTextEvents2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面用來 Visual Studio 的通知來源文件由偵錯引擎所提供的變更。  
  
## 語法  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## 實作器注意事項  
 DE 會實作這個介面以支援原始程式檔的變更後。  通常會實作這個介面上實作的同一個物件[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)介面。  
  
## 呼叫者的備忘稿  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]取得這個介面，透過呼叫<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A>方法。  <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>介面取自呼叫<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A>方法。  <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>介面藉由呼叫[QueryInterface](/visual-cpp/atl/queryinterface)上的方法[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)介面。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugDocumentTextEvents2`。  
  
|方法|描述|  
|--------|--------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|表示整份文件已被摧毀。|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|告知偵錯封裝文字已插入到文件。|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|告知偵錯封裝文字已經從文件中移除。|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|告知偵錯封裝的文件中取代文字。|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|告知偵錯封裝文字屬性，已更新文件中。|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|已更新文件屬性會通知收件者的事件。|  
  
## 備註  
 只提供自己的文件的偵錯引擎會利用`IDebugDocumentTextEvent2`介面。  舉例而言，這是指令碼的偵錯引擎。  解譯指令碼的過程中新的程式碼可能會產生不存在於任何磁碟檔案中，只有知道 DE。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
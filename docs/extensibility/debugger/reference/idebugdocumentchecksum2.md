---
title: "IDebugDocumentChecksum2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugDocumentChecksum2 介面"
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugDocumentChecksum2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

代表總和檢查碼的偵錯的文件，可讓元件之間傳遞的加總檢查碼。  
  
## 語法  
  
```  
IDebugDocumentChecksum2 : IUnknown  
```  
  
## 實作器注意事項  
 可以實作這個介面來公開 \(expose\) 任何元件[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)介面。  不過，它是 \(class\) 實作偵錯引擎，這樣可以傳回給 IDE 和尋找來源時所使用的符號檔 \(\*.pdb\) 中內嵌的總和檢查碼。  
  
## 方法  
 下表顯示的方法`IDebugDocumentChecksum2`。  
  
|方法|描述|  
|--------|--------|  
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|擷取指定要使用的位元組最大的數字的文件加總檢查碼和演算法識別項。|  
  
## 需求  
 標頭: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll
---
title: "IDebugSymbolProviderDirect | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSymbolProviderDirect 介面"
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugSymbolProviderDirect
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

代表符號提供者都能直接存取到中繼資料和核心符號介面。  
  
## 語法  
  
```  
IDebugSymbolProviderDirect: IUnknown  
```  
  
## 方法  
 這個介面會實作下列方法：  
  
|方法|描述|  
|--------|--------|  
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|擷取指定偵錯位址的應用程式定義域識別項。|  
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|擷取 \[符號\] 群組中模組的相關資訊。|  
|[GetCurrentModulesState](../Topic/IDebugSymbolProviderDirect::GetCurrentModulesState.md)|擷取的符號提供者為成員的符號群組的相關資訊。|  
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|擷取中繼資料匯入資訊。|  
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|擷取位於指定的偵錯位址的方法的相關資訊。|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|擷取 unmanaged 程式碼的符號讀取的器。|  
  
## 備註  
 可以使用這個介面，而不是大部分的其他符號提供者介面。  它提供直接存取中繼資料和`CorSym`介面。  
  
## 需求  
 標頭: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll
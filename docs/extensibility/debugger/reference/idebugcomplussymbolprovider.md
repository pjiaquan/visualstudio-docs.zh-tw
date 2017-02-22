---
title: "IDebugComPlusSymbolProvider | Microsoft Docs"
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
  - "IDebugComPlusSymbolProvider 介面"
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugComPlusSymbolProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

使用專屬於 managed 程式碼的方法表示 COM \+ 符號提供者。  
  
## 語法  
  
```  
IDebugComPlusSymbolProvider : IDebugSymbolProvider  
```  
  
## 實作器注意事項  
 雖然很有用處的運算式評估工具 \(EE\) 的介面，以及那些適用於偵錯引擎 \(DE\) 之間沒有分隔，下列方法可能會感興趣 DE 開發者專用： AreSymbolsLoaded，GetAddressesInModuleFromPosition，GetEntryPoint，GetFunctionLineOffset，GetLocalVariableLayout，IsFunctionStale，LoadSymbols，LoadSymbolsFromStream，ReplaceSymbols，UnloadSymbols 和 UpdateSymbols。  
  
## 方法  
 除了在方法[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)介面，這個介面會實作下列方法：  
  
|方法|描述|  
|--------|--------|  
|[AreSymbolsLoaded](../Topic/IDebugComPlusSymbolProvider::AreSymbolsLoaded.md)|決定是否將偵錯符號載入指定的模組，指定應用程式定義域識別項。|  
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|從指定的原始型別建立型別。|  
|[GetAddressesInModuleFromPosition](../Topic/IDebugComPlusSymbolProvider::GetAddressesInModuleFromPosition.md)|將指定的模組中的文件位置對應到偵錯位址的陣列。|  
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|擷取輸入指定的陣列給它的偵錯位址的相關資訊。|  
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|擷取指定的模組和應用程式定義域的組件的名稱。|  
|[GetAttributedClassesForLanguage](../Topic/IDebugComPlusSymbolProvider::GetAttributedClassesForLanguage.md)|擷取與指定的屬性的類別會實作指定的程式語言。|  
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|擷取與指定的模組中指定的屬性類別。|  
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|擷取應用程式的進入點。|  
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|擷取表示指定的行位移的函式中的位址。|  
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|擷取的一組方法的區域變數的配置。|  
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|傳回與指定語彙基元指定的中繼資料物件相關聯的名稱。|  
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|擷取與指定的父屬性指定模組的偵錯符號。|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|擷取 unmanaged 程式碼所使用的符號讀取器。|  
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|擷取指定它的偵錯位址的符號型別。|  
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|決定是否在指定的偵錯位址的函式會被刪除。|  
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|決定是否在指定的偵錯位址的函式會被視為過期。|  
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|決定是否要隱藏指定的偵錯工具的地址的程式碼。|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|載入指定的偵錯符號，在記憶體中。|  
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|載入偵錯符號，指定資料流。|  
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|目前的偵錯符號以取代所指定的資料流中。|  
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|卸載記憶體中指定的模組的偵錯符號。|  
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|以所指定的資料流更新記憶體中的偵錯符號。|  
  
## 需求  
 標頭: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll
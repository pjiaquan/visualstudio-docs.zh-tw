---
title: "SymTagEnum | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SymTagEnum 列舉"
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# SymTagEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定符號的類型。  
  
## 語法  
  
```cpp#  
enum SymTagEnum {   
   SymTagNull,  
   SymTagExe,  
   SymTagCompiland,  
   SymTagCompilandDetails,  
   SymTagCompilandEnv,  
   SymTagFunction,  
   SymTagBlock,  
   SymTagData,  
   SymTagAnnotation,  
   SymTagLabel,  
   SymTagPublicSymbol,  
   SymTagUDT,  
   SymTagEnum,  
   SymTagFunctionType,  
   SymTagPointerType,  
   SymTagArrayType,   
   SymTagBaseType,   
   SymTagTypedef,   
   SymTagBaseClass,  
   SymTagFriend,  
   SymTagFunctionArgType,   
   SymTagFuncDebugStart,   
   SymTagFuncDebugEnd,  
   SymTagUsingNamespace,   
   SymTagVTableShape,  
   SymTagVTable,  
   SymTagCustom,  
   SymTagThunk,  
   SymTagCustomType,  
   SymTagManagedType,  
   SymTagDimension,  
   SymTagCallSite,  
   SymTagInlineSite,  
   SymTagBaseInterface,  
   SymTagVectorType,  
   SymTagMatrixType,  
   SymTagHLSLType  
};  
```  
  
## 項目  
 `SymTagNull`  
 表示符號已沒有型別。  
  
 `SymTagExe`  
 表示該符號是.exe 檔案。  只有一個`SymTagExe`每個符號存放區的符號。  它可以做為全域範圍，並沒有語彙的父代。  
  
 `SymTagCompiland`  
 表示符號存放區的每一個編譯元件的編譯符號。  對於原生應用程式， `SymTagCompiland`符號會對應到 \[連結至映像的目的檔。  對於部份 Microsoft 中繼語言 \(MSIL\) 影像，還有一個編譯每個類別。  
  
 `SymTagCompilandDetails`  
 表示符號包含擴充的屬性的編譯。  擷取這些屬性可能會需要載入編譯符號。  
  
 `SymTagCompilandEnv`  
 表示符號是定義為編譯環境字串。  
  
 `SymTagFunction`  
 表示該符號是一項功能。  
  
 `SymTagBlock`  
 表示該符號是巢狀的區塊。  
  
 `SymTagData`  
 指出該符號的資料。  
  
 `SymTagAnnotation`  
 表示程式碼註解符號。  此符號的子系都是常數資料字串 \(`SymTagData`， `LocIsConstant`， `DataIsConstant`\)。  大多數的用戶端會忽略這個符號。  
  
 `SymTagLabel`  
 表示該符號是一個標籤。  
  
 `SymTagPublicSymbol`  
 表示該符號是公用的符號。  對於原生應用程式中，這個符號會是連結影像時，遇到 COFF 外部符號。  
  
 `SymTagUDT`  
 表示該符號是使用者定義型別 \(結構、 類別或等位\)。  
  
 `SymTagEnum`  
 表示該符號是列舉型別。  
  
 `SymTagFunctionType`  
 表示該符號是函式簽章的型別。  
  
 `SymTagPointerType`  
 表示該符號是指標型別。  
  
 `SymTagArrayType`  
 表示該符號是陣列型別。  
  
 `SymTagBaseType`  
 表示該符號是基底型別。  
  
 `SymTagTypedef`  
 表示該符號是`typedef`，也就是另一種類型的別名。  
  
 `SymTagBaseClass`  
 表示該符號是使用者定義型別的基底類別。  
  
 `SymTagFriend`  
 表示該符號是使用者定義型別的一位朋友。  
  
 `SymTagFunctionArgType`  
 表示該符號是函式引數。  
  
 `SymTagFuncDebugStart`  
 表示該符號是函式的初構程式碼的結束位置。  
  
 `SymTagFuncDebugEnd`  
 表示該符號的函式終程式碼的開頭位置。  
  
 `SymTagUsingNamespace`  
 表示該符號是命名空間名稱，在目前範圍中使用中。  
  
 `SymTagVTableShape`  
 表示該符號的虛擬資料表的描述。  
  
 `SymTagVTable`  
 表示該符號的虛擬資料表指標。  
  
 `SymTagCustom`  
 表示符號是以自訂的符號，且不會被解譯的 DIA.  
  
 `SymTagThunk`  
 表示該符號用於 16 和 32 位元程式碼之間共用資料的 thunk。  
  
 `SymTagCustomType`  
 表示符號自訂編譯器符號。  
  
 `SymTagManagedType`  
 表示該符號是在中繼資料中。  
  
 `SymTagDimension`  
 表示符號 FORTRAN 多維陣列。  
  
 `SymTagCallSite`  
 指出該符號表示呼叫站台。  
  
 `SymTagInlineSite`  
 表示該符號代表內嵌站台。  
  
 `SymTagBaseInterface`  
 表示該符號是基底介面。  
  
 `SymTagVectorType`  
 表示該符號是向量型別。  
  
 `SymTagMatrixType`  
 表示該符號是矩陣的型別。  
  
 `SymTagHLSLType`  
 表示該符號是高級別著色器的語言類型。  
  
## 備註  
 在偵錯檔案內的所有符號都有指定符號的型別識別標記。  
  
 這個列舉型別中的值會傳回由呼叫[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)方法。  
  
 這個列舉型別中的值會傳遞至下列方法來限制成特定的符號型別搜尋的範圍：  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../Topic/IDiaSession::findSymbolByRVA.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::findSymbolByVA](../Topic/IDiaSession::findSymbolByVA.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## 需求  
 標頭: cvconst.h  
  
## 請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)   
 [IDiaSession::findSymbolByRVA](../Topic/IDiaSession::findSymbolByRVA.md)   
 [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)   
 [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)   
 [IDiaSession::findSymbolByVA](../Topic/IDiaSession::findSymbolByVA.md)   
 [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
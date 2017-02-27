---
title: "結構和等位 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "結構 [Visual Studio SDK]"
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 結構和等位
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

下列是結構和等位 Visual Studio 的偵錯 SDK 中。  
  
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)  
 指定處理序識別碼，它可能是系統識別碼或 GUID。  
  
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)  
 描述在其下會引發的中斷點的條件。  
  
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)  
 描述錯誤的中斷點，包括位置、 程式及執行緒的解析度。  
  
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)  
 指定用來描述，中斷點的位置的結構的型別。  
  
 [BP\_LOCATION\_CODE\_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)  
 定義描述的程式碼中的地址中的中斷點位置的元件。  
  
 [BP\_LOCATION\_CODE\_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)  
 說明與偵錯程式中的地址的直接繫結中斷點的位置。  
  
 [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)  
 描述程式碼的原始程式檔中的列中的中斷點位置。  
  
 [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)  
 描述在程式碼中的函式中斷點的位移的位置。  
  
 [BP\_LOCATION\_CODE\_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)  
 用來進行設定，使用者可以從 IDE 中輸入的字串為基礎的程式碼中斷點。  
  
 [BP\_LOCATION\_DATA\_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)  
 用來進行設定，使用者可以從 IDE 中輸入的字串為基礎的資料中斷點。  
  
 [BP\_LOCATION\_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)  
 說明解決方案的特定位置的中斷點。  
  
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)  
 描述計數和條件的項目，將之後已先前通過引發的中斷點。  
  
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)  
 包含中斷點的實作所需的資訊。  
  
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)  
 包含中斷點的實作所需的資訊 \(相同的[BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)結構，但包括廠商的 GUID、 條件約束和追蹤點的資訊\)。  
  
 [BP\_RESOLUTION\_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)  
 描述程式碼中斷點的位置。  
  
 [BP\_RESOLUTION\_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)  
 描述繫結資料中斷點的結果。  
  
 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)  
 描述繫結的中斷點資訊的程式碼的中斷點或資料中斷點。  
  
 [BP\_RESOLUTION\_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)  
 指定中斷點的解析度位置的結構。  
  
 [BSTR\_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)  
 描述字串的陣列。  
  
 [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)  
 指定從中繼資料欄位型別的相關資訊。  
  
 [CODE\_PATH](../../../extensibility/debugger/reference/code-path.md)  
 描述呼叫函式或方法。  
  
 [COMPUTER\_INFO](../../../extensibility/debugger/reference/computer-info.md)  
 說明偵錯工具執行所在的電腦。  
  
 [CONST\_GUID\_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)  
 說明 Guid 的清單。  
  
 [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md)  
 描述 「 記憶體內容 」 或 「 程式碼的內容。  
  
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)  
 說明偵錯程式中的地址。  
  
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)  
 表示其中一個為數種不同類型的地址。  
  
 [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)  
 識別自訂的檢視器，或鍵入視覺化檢視。  
  
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)  
 說明偵錯\] 屬性會描述階層的特性具有名稱、 類型和值的物件。  
  
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)  
 描述的參考。  
  
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)  
 描述 \[反組譯碼對顯示 IDE。  
  
 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)  
 描述例外狀況或偵錯的程式所擲回執行階段錯誤。  
  
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)  
 說明本機變數、 參數或另一個欄位。  
  
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)  
 說明堆疊框架。  
  
 [GUID\_ARRAY](../../../extensibility/debugger/reference/guid-array.md)  
 說明可用的偵錯引擎的唯一識別項的陣列。  
  
 [JMC\_CODE\_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)  
 用來設定 JustMyCode 模組的資訊。  
  
 [MACHINE\_INFO](../../../extensibility/debugger/reference/machine-info.md)  
 說明特定的電腦。  
  
 [METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)  
 說明陣列中的項目陣列。  
  
 [METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)  
 說明類別或結構的欄位的位址。  
  
 [METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)  
 描述 \(通常是函式或方法\) 的範圍內的區域變數的位址。  
  
 [METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)  
 描述類別的方法的位址。  
  
 [METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)  
 描述方法或函式的參數。  
  
 [METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)  
 描述從方法或函式的傳回值。  
  
 [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)  
 描述來自中繼資料欄位型別。  
  
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)  
 描述特定模組 \(DLL、 執行檔或組件\)。  
  
 [MODULE\_SYMBOL\_SEARCH\_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)  
 說明中搜尋的符號搜尋路徑的狀態資訊。  
  
 [NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md)  
 說明原生的地址。  
  
 [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)  
 描述取自 PDB 符號的欄位型別。  
  
 [PENDING\_BP\_STATE\_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)  
 說明已準備好要繫結至程式碼位置中斷點的狀態。  
  
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)  
 描述處理程序。  
  
 [PROGRAM\_NODE\_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)  
 將告訴您一份[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)物件，表示程式節點。  
  
 [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md)  
 說明在電腦上執行的程序。  
  
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)  
 描述在指定的文字行和資料行的位置。  
  
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)  
 說明執行緒的屬性。  
  
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)  
 說明欄位的類型。  
  
 [UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)  
 描述實體位址。  
  
 [UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)  
 告訴您，相對應的地址`this`指標 \(`Me` Visual Basic 中\)。  
  
## 需求  
 標頭: msdbg.h、 sh.h 或 ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [應用程式開發介面參考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
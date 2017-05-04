---
title: "IActiveScriptParse::AddScriptlet | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParse.AddScriptlet
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParse_AddScriptlet"
ms.assetid: 824929f4-4dd3-473a-92d9-0b96acea2f14
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParse::AddScriptlet
將程式碼加入至 scriptlet 指令碼。  這個方法用於指令碼持續性 \(Persistent\) 狀態切換錯誤與主應用程式文件的環境，然後主應用程式會還原指令碼管理，而非透過 `IPersist*` 介面。  主要範例是指令碼 \(例如允許在 HTML 文件中內嵌的程式碼 Scriptlet 會附加至內建事件之語言的 HTML， ONCLICK\= button1.text\='Exit \("」\)。  
  
## 語法  
  
```  
HRESULT AddScriptlet(  
    LPCOLESTR pstrDefaultName,       // address of default name of scriptlet  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    LPCOLESTR pstrSubItemName,       // address of subitem name  
    LPCOLESTR pstrEventName,         // address of event name  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    BSTR *pbstrName,                 // address of actual name of scriptlet  
    EXCEPINFO *pexcepinfo            // address of exception information  
);  
```  
  
#### 參數  
 `pstrDefaultName`  
 \[in\] 要與相關聯的預設名稱的地址。scriptlet。  如果 scriptlet 不包含命名資訊 \(在上述範例中 ONCLICK\)，該名稱將用來識別 scriptlet。  如果此參數為 `NULL`，指令碼引擎會產生一個唯一的名稱，如果需要。  
  
 `pstrCode`  
 \[in\] 要加入的 scriptlet 文字的位址。  這個字串解譯為而定的指令碼語言。  
  
 `pstrItemName`  
 \[in\] 包含項目名稱緩衝區的位址與這個 scriptlet。  這個參數，除了之外， `pstrSubItemName`識別 scriptlet 是一個事件處理常式的物件。  
  
 `pstrSubItemName`  
 \[in\] 包含具名項目的名稱 `subobject` 這 scriptlet 關聯緩衝區的位址，在具名項目的型別資訊必須找到這個名稱。  如果 scriptlet 要與具名項目而不 `subitem`，這個參數為 null。  這個參數，除了之外， `pstrItemName`識別 scriptlet 是一個事件處理常式處理特定物件。  
  
 `pstrEventName`  
 \[in\] 包含事件的名稱 scriptlet 是一個事件處理常式緩衝區的位址。  
  
 `pstrDelimiter`  
 \[in\] 位址結束 scriptlet 符號。  當 `pstrCode` 參數從文字資料流剖析時，主應用程式通常會使用分隔符號 \(例如，兩個單引號 \("\)， scriptlet 偵測到的結尾。  這個參數指定 \(例如使用的主機，允許指令碼引擎提供了一些條件約束基底前置處理符號 \(，取代使用單引號 \(『\) 與兩個單引號做為分隔符號\)。  \(和\)，如果指令碼引擎完全如何利用這項資訊決定指令碼引擎。  如果未使用分隔符號 scriptlet 指令的結束，請將此參數設定為 NULL。  
  
 `dwSourceContextCookie`  
 \[in\] 使用於偵錯用途的應用程式定義的值。  
  
 `ulStartingLineNumber`  
 \[in\] 指定之以零起始的值會解析哪一行開始。  
  
 `dwFlags`  
 \[in\] 旗標與 scriptlet。  可以是下列值的組合:  
  
|傳回值|意義|  
|---------|--------|  
|SCRIPTTEXT\_ISVISIBLE|表示指令碼文字應該可見 \(，，因此可呼叫的名稱\) 做為指令碼的名稱空間的全域方法。|  
|SCRIPTTEXT\_ISPERSISTENT|表示應該儲存在此呼叫期間加入的程式碼，如果指令碼引擎儲存 \(例如，傳遞至 `IPersist*::Save`的呼叫\)，則為，如果指令碼引擎透過轉換會重設為這個初始狀態。  如需這個狀態的詳細資訊，請參閱指令碼引擎狀態。|  
  
 `pbstrName` ,  
 \[out\] 用來的實際名稱識別 scriptlet。  這是依照優先順序:在 scriptlet 文字明確指定的名稱，在 `pstrDefaultName`所提供的預設名稱或指令碼引擎複合的唯一名稱。  
  
 `pexcepinfo` ,  
 \[in\] 包含例外狀況資訊結構的位址。  如果傳回， DISP\_E\_EXCEPTION，應填入這個結構。  
  
## 傳回值  
 下列值的傳回一個值:  
  
|傳回值|意義|  
|---------|--------|  
|`S_OK`|成功。|  
|`DISP_E_EXCEPTION`|例外狀況在剖析發生 scriptlet。  `pexcepinfo` 參數包含例外狀況的資訊。|  
|`E_INVALIDARG`|引數無效。|  
|`E_NOTIMPL`|這個方法不受支援，指令碼引擎不支援將事件接收 Scriptlet。|  
|`E_POINTER`|無效的指標被指定。|  
|`E_UNEXPECTED`|這個呼叫不需要 \(例如，指令碼引擎尚未載入或未初始化\) 也不會失敗。|  
|`OLESCRIPT_E_INVALIDNAME`|所提供的預設名稱是無效的。這個指令碼語言。|  
|`OLESCRIPT_E_SYNTAX`|未指定中的語法錯誤。scriptlet 發生。|  
  
## 請參閱  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)
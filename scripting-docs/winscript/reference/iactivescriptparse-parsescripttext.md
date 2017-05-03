---
title: "IActiveScriptParse::ParseScriptText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParse.ParseScriptText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParse_ParseScriptText"
ms.assetid: 2d237d6c-cc65-415b-8808-72791304a136
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptParse::ParseScriptText
解析指定的程式碼片段，加入宣告至命名空間並視情況評估程式碼。  
  
## 語法  
  
```  
HRESULT ParseScriptText(  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // cookie for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    VARIANT *pvarResult,             // address of buffer for results  
    EXCEPINFO *pexcepinfo            // address of buffer for error data  
);  
```  
  
#### 參數  
  
|||  
|-|-|  
|`pstrCode`|\[in\] 評估的 scriptlet 文字的位址。  這個字串的解譯取決於指令碼語言。|  
|`pstrItemName`|\[in\] 提供評估 scriptlet 的內容之項目名稱的位址。  如果這個參數為 NULL，則會在指令碼引擎的全域內容中評估程式碼。|  
|`punkContext`|\[in\] 內容物件的位址。  這個物件是保留用於偵錯環境，這類內容可由偵錯工具提供以表示現用執行階段內容。  如果這個參數為 NULL，則引擎會使用 `pstrItemName` 識別內容。|  
|`pstrDelimiter`|\[in\] scriptlet 結束分隔符號的位址。  當 `pstrCode` 從文字資料流剖析時，主應用程式通常會使用分隔符號，例如兩個單引號 \(''\)，偵測 scriptlet 結尾。  這個參數指定主機使用的分隔符號，允許指令碼引擎提供一些條件式基本前置處理 \(例如，將單引號 \['\] 取代為兩個單引號以做為分隔符號\)。  指令碼引擎實際使用這項資訊的方式 \(如果有的話\) 取決於指令碼引擎。  如果主應用程式不使用分隔符號標示程式碼片段的結束，請將此參數設定為 `NULL`。|  
|`dwSourceContextCookie`|\[in\] 用於偵錯的 Cookie。|  
|`ulStartingLineNumber`|\[in\] 以零為起始的值，指定剖析將從哪一行開始。|  
|`dwFlags`|\[in\] 與 scriptlet 相關的旗標。  可以是下列值的組合：|  
  
|值|意義|  
|-------|--------|  
|SCRIPTTEXT\_ISEXPRESSION|如果計算運算式和陳述式之間的差異很重要，但在指令碼語言中語法上模稜兩可，則這個旗標會指定將 scriptlet 解譯成運算式，而不是陳述式或陳述式清單。  預設會假設陳述式, 除非可以從 scriptlet 文字的語法判斷正確選擇。|  
|SCRIPTTEXT\_ISPERSISTENT|表示如果指令碼引擎已儲存 \(例如，藉由呼叫 `IPersist*::Save`\)，或者指令碼引擎透過轉換重設為初始狀態時，則應儲存此呼叫期間加入的程式碼。|  
|SCRIPTTEXT\_ISVISIBLE|表示指令碼文字應做為可見於指令碼命名空間中 \(因此可依據名稱呼叫\) 的全域方法。|  
  
|||  
|-|-|  
|`pvarResult`|\[ou\] 接收 scriptlet 處理序結果的緩衝區的位址，若呼叫端不預期結果則為 `NULL` \(即 SCRIPTTEXT\_ISEXPRESSION 值未設定\)。|  
|`pexcepinfo`|\[out\] 接收例外狀況資訊的結構的位址。  如果 `IActiveScriptParse::ParseScriptText` 傳回 DISP\_E\_EXCEPTION，會填入這個結構。|  
  
## 傳回值  
 傳回下列其中一個值：  
  
|傳回值|意義|  
|---------|--------|  
|`S_OK`|成功。|  
|`DISP_E_EXCEPTION`|處理 scriptlet 時發生的例外狀況。  包含例外狀況相關資訊的 `pexcepinfo` 參數。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|指定了無效的指標。|  
|`E_NOTIMPL`|不支援這個方法。  指令碼引擎不支援運算式或陳述式的執行階段評估。|  
|`E_UNEXPECTED`|不需要呼叫 \(例如，指令碼引擎處於未初始化或關閉狀態，或者 SCRIPTTEXT\_ISEXPRESSION 旗標已設定，而且指令碼引擎處於初始化狀態\)。|  
|`OLESCRIPT_E_SYNTAX`|scriptlet 中發生未指定的語法錯誤。|  
  
## 備註  
 如果指令碼引擎處於初始化狀態，則在此呼叫期間不會實際評估程式碼；而這類程式碼會佇列，並且在指令碼引擎轉換為 \(或是經過\) 啟動狀態時執行。  由於不允許在初始化狀態中執行，因此在初始化狀態中以 SCRIPTTEXT\_ISEXPRESSION 旗標呼叫這個方法是錯誤的。  
  
 程式碼片斷可以是運算式、陳述式清單或指令碼語言允許的任何項目。  例如，這個方法用於評估 HTML \<SCRIPT\>，它允許在建構 HTML 頁面時執行陳述式，而不只是將它們編譯成指令碼狀態。  
  
 傳遞至此方法的程式碼必須是程式碼的有效完整部分。  例如，在 VBScript 中使用 Sub Function\(x\) 呼叫這個方法第一次，然後使用 `End Sub` 呼叫第二次是不合法的。  由於副程式宣告已啟動但未完成，剖析器無法等候第二個呼叫完成副程式，而是必須產生剖析錯誤。  
  
 如需指令碼狀態的詳細資訊，請參閱 [Windows 指令碼引擎](../../winscript/windows-script-engines.md)的＜指令碼引擎狀態＞一節。  
  
## 請參閱  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)
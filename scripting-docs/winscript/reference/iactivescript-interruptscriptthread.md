---
title: "IActiveScript::InterruptScriptThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.InterruptScriptThread
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_InterruptScriptThread"
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::InterruptScriptThread
會中斷執行指令碼執行緒 \(事件接收、立即執行或巨集引動過程\) 執行。  此方法可用來結束 \(例如卡的指令碼 \(，在無限迴圈\)。  它可以從非 Base 執行緒呼叫未使非基底 Callout 裝載物件或加入至 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 方法。  
  
## 語法  
  
```  
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### 參數  
 `stidThread`  
 \[in\] 中斷執行緒的識別項或下列其中一個特殊執行緒識別項的值:  
  
|值|意義|  
|-------|--------|  
|SCRIPTTHREADID\_ALL|所有執行緒。  這個中斷目前套用至程序中所有指令碼的方法。  請注意，除非呼叫端要求指令碼已中斷連接，下一個指令化事件造成指令碼可再次呼叫與 SCRIPTSTATE\_DISCONNECTED 或 SCRIPTSTATE\_INITIALIZED 旗標集的 [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) 方法所執行的。|  
|SCRIPTTHREADID\_BASE|基本的執行緒;也就是指令碼引擎執行個體化的執行緒。|  
|SCRIPTTHREADID\_CURRENT|目前正在執行的執行緒。|  
  
 `pexcepinfo`  
 \[in\] 包含應該向中止的指令碼所報告的錯誤資訊的 `EXCEPINFO` 結構的位址。  
  
 `dwFlags`  
 \[in\] 選項旗標與此中斷。  可能是下列其中一個值：  
  
|值|意義|  
|-------|--------|  
|SCRIPTINTERRUPT\_DEBUG|如果支援，輸入指令碼引擎的偵錯工具在目前指令碼執行點。|  
|SCRIPTINTERRUPT\_RAISEEXCEPTION|如果支援指令碼引擎的語言，請讓指令碼處理例外狀況。  否則，指令碼方法會中止，並錯誤碼傳回給呼叫端;也就是事件來源或巨集呼叫端。|  
  
## 傳回值  
 下列值的傳回一個值:  
  
|傳回值|意義|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|無效的指標被指定。|  
|`E_UNEXPECTED`|這個呼叫不需要 \(例如，指令碼引擎尚未載入或未初始化\)。|  
  
## 請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)
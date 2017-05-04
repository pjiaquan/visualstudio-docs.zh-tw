---
title: "IActiveScript::Close | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.Close
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_Close"
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScript::Close
使指令碼引擎會放棄所有目前載入的指令碼，會遺失必須其他物件之狀態和釋放任何介面指標，因此輸入已關閉狀態。  事件接收、立即執行的指令碼文字和已在進行中的巨集引動過程在狀態變更 \(使用 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) 之前完成取消執行指令碼執行緒\)。  在釋放介面可避免循環參考問題之前，必須由建立的主應用程式會呼叫這個方法。  
  
## 語法  
  
```  
HRESULT Close(void);  
```  
  
## 傳回值  
 下列值的傳回一個值:  
  
|值|意義|  
|-------|--------|  
|`S_OK`|成功。|  
|`E_UNEXPECTED`|這個呼叫不需要 \(例如，指令碼引擎已處於關閉狀態\)。|  
|`OLESCRIPT_S_PENDING`|方法已成功加入佇列，，但是這個狀態未變更。  當狀態變更時，網站會在 [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) 要呼叫的方法。|  
|`S_FALSE`|方法會成功，但是，指令碼已關閉。|  
  
## 請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)
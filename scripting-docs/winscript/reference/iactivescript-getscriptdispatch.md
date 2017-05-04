---
title: "IActiveScript::GetScriptDispatch | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptDispatch
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptDispatch"
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::GetScriptDispatch
擷取方法和屬性的 `IDispatch` 介面與目前執行的指令碼。  
  
## 語法  
  
```  
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### 參數  
 `pstrItemName`  
 \[in\] 包含項目名稱呼叫端要求關聯的分派物件緩衝區的位址。  如果此參數為， `NULL`分派物件包含做為它的成員指令碼和屬性中定義的所有全域方法。  藉由 `IDispatch` 介面和關聯的 `ITypeInfo` 介面，主應用程式可以叫用指令碼方法或檢視和修改指令碼變數。  
  
 `ppdisp`  
 \[out\] 接收物件指標變數的位址與指令碼的全域方法和屬性。  如果指令碼引擎不支援這類物件， `NULL` 傳回。  
  
## 傳回值  
 下列值的傳回一個值:  
  
|傳回值|意義|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|無效的指標被指定。|  
|`E_UNEXPECTED`|這個呼叫不需要 \(例如，指令碼引擎尚未載入或未初始化\)。|  
|`S_FALSE`|指令碼引擎不支援分派物件; `ppdisp` 參數設定為 NULL。|  
  
## 備註  
 由於方法和屬性可以藉由呼叫 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) 加入介面，則傳回的 `IDispatch` 介面可以動態地將這個方法支援新的方法和屬性。  同樣的，在中，當方法和加入此屬性時， `IDispatch::GetTypeInfo` 方法應該傳回新，唯一的 `ITypeInfo` 介面。  不過，請注意，語言引擎無法變更 `IDispatch` 介面是與先前的所有 `ITypeInfo` 介面不相容的方法傳回。  這表示，例如，永遠不會重複使用介面。  
  
## 請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)
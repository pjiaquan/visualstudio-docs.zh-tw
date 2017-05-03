---
title: "IActiveScriptSite::OnScriptTerminate | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnScriptTerminate
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnScriptTerminate"
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnScriptTerminate
告知主應用程式指令碼已完成執行。  
  
## 語法  
  
```  
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### 參數  
 `pvarResult`  
 \[in\] 包含指令碼的結果變數位址或 `NULL` ，如果指令碼不會產生任何結果。  
  
 `pexcepinfo`  
 \[in\] 包含例外狀況資訊 `EXCEPINFO` 結構的位址產生指令碼何時終止或 `NULL` 例外狀況，則不會產生。  
  
## 傳回值  
 如果成功，會傳回 `S_OK`。  
  
## 備註  
 [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) ，在對方法的呼叫，以 SCRIPTSTATE\_INITIALIZED 旗標，完成之前，指令碼引擎會呼叫這個方法。  這個方法可以用來傳回完整的狀態和結果給主應用程式。  請注意許多指令碼語言，根據主機接收的事件，但為主應用程式定義的壽命。  在這個案例中，這個方法可能不會呼叫。  
  
## 請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)
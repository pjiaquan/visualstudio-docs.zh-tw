---
title: "IActiveScriptAuthor::GetEventHandler | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetEventHandler
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetEventHandler"
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptAuthor::GetEventHandler
傳回具有指定之屬性的 scriptlet。  
  
## 語法  
  
```  
HRESULT GetEventHandler(  
   IDispatch          *pdisp,  
   LPCOLESTR          pszItem,  
   LPCOLESTR          pszSubItem,  
   LPCOLESTR          pszEvent,  
   IScriptEntry       **ppse  
);  
```  
  
#### 參數  
 `pdisp`  
 \[in\] 對應至 `NamedItem` scriptlet 附加的 `IDispatch` 物件。  
  
 `pszItem`  
 \[in\] 完整名稱的 scriptlet 最上層識別項之緩衝區的位址在主應用程式。  
  
 `pszSubItem`  
 \[in\] 完整名稱的 scriptlet 第二層項目識別項的緩衝區的位址在主應用程式。  此名稱，則只有一個層級，則設為 null。  
  
 `pszEvent`  
 \[in\] 包含事件名稱緩衝區的位址。  scriptlet 為這個事件的事件處理常式。  
  
 `ppse`  
 \[out\] 接收指標 scriptlet `IScriptEntry` 介面具有指定屬性之變數的位址。  
  
## 傳回值  
 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
  
## 請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)
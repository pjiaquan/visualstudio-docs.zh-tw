---
title: "IScriptNode:: CreateChildEntry | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode. CreateChildEntry
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::CreateChildEntry"
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# IScriptNode:: CreateChildEntry
將 `IScriptEntry`子執行個體。  
  
## 語法  
  
```  
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### 參數  
 `isn`  
 \[in\] 父代的子系的索引。  
  
 `dwCookie`  
 \[out\] 用來的應用程式定義的值相關聯的子項目與主應用程式物件。  
  
 `pszDelimiter`  
 \[in\] 結束指令碼區塊符號的位址。  若要解析，主應用程式通常會使用分隔符號 \(例如兩個單引號\)，偵測指令碼區塊的結尾。  
  
 這個符號可以啟用撰寫引擎的指令碼的前置處理作業。  例如，引擎會使用兩個單引號取代一個單引號做為分隔符號。  引擎會決定使用此符號。  
  
 符號，則不會將指令碼區塊的結尾，則設為 null。  
  
 `ppse`  
 \[out\] 接收指標子執行個體的介面 `IScriptEntry` 變數的位址。  
  
 對於表示 Web 網頁 `IScriptNode` 物件，這個參數傳回指定指令碼區塊的 `IScriptEntry` 執行個體。  
  
 針對代表指令碼區塊的 `IScriptEntry` 物件，這個參數傳回指定函式 `IScriptEntry` 物件的執行個體。  
  
 針對代表函式物件的 `IScriptEntry` 物件，這個方法會失敗。  
  
 對於 `IScriptScriptlet` 物件，這個方法會失敗。  
  
## 傳回值  
 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 `IScriptNode` 介面代表網頁或其項目。  從 `IScriptNode`衍生自\) 的 `IScriptEntry` 介面 \(表示指令碼區塊或函式物件。  從 `IScriptEntry`衍生自\) 的 `IScriptScriptlet` 介面 \(表示事件處理常式。  
  
## 請參閱  
 [IScriptNode 介面](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)
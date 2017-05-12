---
title: "IScriptNode::CreateChildHandler | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.CreateChildHandler
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::CreateChildHandler"
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# IScriptNode::CreateChildHandler
將 scriptlet 做為 `IScriptNode`的子執行個體。  
  
## 語法  
  
```  
HRESULT CreateChildHandler(  
   LPCOLESTR          pszDefaultName,  
   LPCOLESTR          *prgpszNames,  
   ULONG              cpszNames,  
   LPCOLESTR          pszEvent,  
   LPCOLESTR          pszDelimiter,  
   ITypeInfo*         ptiSignature,  
   ULONG              iMethodSignature,  
   ULONG              isn,  
   DWORD              dwCookie,  
   IScriptEntry       **ppse  
);  
```  
  
#### 參數  
 `pszDefaultName`  
 \[in\] 要與相關聯的預設名稱的地址。scriptlet。  
  
 `prgpszNames`  
 \[in， size\_is \(`cpszNames`\)\]。從完整名稱的識別項的清單會在主應用程式。  
  
 `cpszNames`  
 \[in\] 識別項的數目。 `prgpszNames` 參數的。  
  
 `pszEvent`  
 \[in\] 識別事件名稱的緩衝區的位址與 scriptlet。  
  
 `pszDelimiter`  
 \[in\] 結束指令碼區塊符號的位址。  若要解析，主應用程式通常會使用分隔符號 \(例如兩個單引號\)，偵測指令碼區塊的結尾。  
  
 這個符號所撰寫的指令碼引擎啟用前置處理。  例如，引擎會使用兩個單引號取代一個單引號做為分隔符號。  引擎會決定使用此符號。  
  
 如果某個符號不是用來識別指令碼區塊的結尾，則設為 null。  
  
 `ptiSignature`  
 \[in\] 函式物件的型別資訊。  
  
 `iMethodSignature`  
 \[in\] 此函式的索引。 `ITypeInfo``ptiSignature` 參數的。  
  
 `isn`  
 \[in\] 父代的子系的索引。  
  
 `dwCookie`  
 \[in\] 用來使項目與主應用程式物件的應用程式定義的值。  
  
 `ppse`  
 \[out\] 接收指標子執行個體的介面 `IScriptEntry` 變數的位址。  
  
## 傳回值  
 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 scriptlet 指定事件處理常式。  這個方法會建立 scriptlet，若以表示 Web 網頁 `IScriptNode` 物件呼叫。  如果它是由其他介面，呼叫這個方法不會成功。  
  
## 請參閱  
 [IScriptNode 介面](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)
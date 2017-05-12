---
title: "IScriptNode::GetChild | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetChild
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetChild"
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptNode::GetChild
傳回位於節點中的指定索引處的子系。  
  
## 語法  
  
```  
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### 參數  
 `isn`  
 \[in\] 父代的子系的索引。  
  
 `ppsn`  
 \[out\] 接收指標子執行個體的介面 `IScriptNode` 變數的位址。  
  
 對於表示 Web 網頁 `IScriptNode` 物件，這個參數會傳回包含一個指令碼區塊的物件。  
  
 如需指定指令碼區塊的 `IScriptEntry` 物件，這個參數傳回指定函式的物件。  
  
## 傳回值  
 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 對於 `IScriptScriptlet` 物件指定函式的 `IScriptEntry` 物件和物件，這個方法會失敗，因為沒有子項目。  
  
## 請參閱  
 [IScriptNode 介面](../../winscript/reference/iscriptnode-interface.md)
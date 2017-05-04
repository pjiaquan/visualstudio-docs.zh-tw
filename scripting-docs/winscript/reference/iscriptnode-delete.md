---
title: "IScriptNode::Delete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.Delete
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::Delete"
ms.assetid: 6765ff80-a9a8-40a3-a669-7fcc284c87af
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptNode::Delete
刪除此物件樹狀結構。  
  
## 語法  
  
```  
HRESULT Delete();  
```  
  
#### 參數  
 方法不使用參數。  
  
## 傳回值  
 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 在 `Delete` 呼叫方法之後， [IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md) 方法應該指示指令碼節點不在使用中。  
  
## 請參閱  
 [IScriptNode 介面](../../winscript/reference/iscriptnode-interface.md)
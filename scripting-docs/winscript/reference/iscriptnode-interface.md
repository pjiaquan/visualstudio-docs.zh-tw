---
title: "IScriptNode 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IScriptNode 介面"
ms.assetid: cfa76c4a-6543-48e8-a946-d212cd0bf934
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# IScriptNode 介面
物件會實作介面 `IScriptNode` 代表網頁。  
  
 除了繼承自 `IUnknown` 的方法之外，`IScriptNode` 介面還會公開下列方法。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|指出物件是否為作用中。|  
|[IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|將 `IScriptEntry`子執行個體。|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|將 scriptlet 做為 `IScriptNode`的子執行個體。|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|刪除物件樹狀結構。|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|傳回位於節點中的指定索引處的子系。|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|傳回用來使 scriptlet 與主應用程式物件的應用程式定義的值。|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|傳回物件的索引父代的子清單的。|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|傳回目前節點使用指令碼的指令碼語言。|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|傳回物件的 `IScriptNode` 子節點的數目。|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|會傳回物件的父代的 `IScriptNode` 物件。|  
  
## 請參閱  
 [動態指令碼撰寫的介面](../../winscript/reference/active-script-authoring-interfaces.md)
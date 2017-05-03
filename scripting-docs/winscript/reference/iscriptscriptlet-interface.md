---
title: "IScriptScriptlet 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IScriptScriptlet 介面"
ms.assetid: b9981908-a337-4228-864c-c741f111ab2d
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptScriptlet 介面
實作的物件 `IScriptScriptlet` 介面表示事件處理常式指令碼。  
  
 除了繼承自 `IScriptEntry` 的方法之外，`IScriptScriptlet` 介面還會公開下列方法。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IScriptScriptlet::GetEventName](../../winscript/reference/iscriptscriptlet-geteventname.md)|傳回與 scriptlet 事件的名稱。|  
|[IScriptScriptlet:: GetSimpleEventName](../../winscript/reference/iscriptscriptlet-getsimpleeventname.md)|傳回與 scriptlet 的簡單的事件名稱。  這是不含任何泛空白字元的單一動詞命令名稱。|  
|[IScriptScriptlet::GetSubItemName](../../winscript/reference/iscriptscriptlet-getsubitemname.md)|傳回在 scriptlet 物件的主應用程式的完整名稱的最後一個識別項。|  
|[IScriptScriptlet::SetEventName](../../winscript/reference/iscriptscriptlet-seteventname.md)|設定與 scriptlet 事件的名稱。|  
|[IScriptScriptlet::SetSimpleEventName](../../winscript/reference/iscriptscriptlet-setsimpleeventname.md)|設定與 scriptlet 的簡單的事件名稱。  這是不含任何泛空白字元的單一動詞命令名稱。|  
|[IScriptScriptlet::SetSubItemName](../../winscript/reference/iscriptscriptlet-setsubitemname.md)|設定物件的 scriptlet 主應用程式的完整名稱的最後一個識別項。|  
  
## 請參閱  
 [動態指令碼撰寫的介面](../../winscript/reference/active-script-authoring-interfaces.md)
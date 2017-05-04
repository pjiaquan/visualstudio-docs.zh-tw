---
title: "IScriptEntry 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IScriptEntry 介面"
ms.assetid: 86da3bc1-58b7-4d73-87ab-bc3ce34e3f41
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IScriptEntry 介面
實作的物件 `IScriptEntry` 介面表示指令碼區塊或函式物件。  
  
 除了繼承自 `IScriptNode` 的方法之外，`IScriptEntry` 介面還會公開下列方法。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|傳回對應於 `IScriptEntry` 指令碼區塊、區塊或 scriptlet 函式主體中的文字。|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|傳回可識別 `IScriptEntry` 物件的項目名稱。|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|針對代表單一物件的項目 \(例如函式\)，則會傳回物件的名稱。|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|傳回項目的起始位置和長度。|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|物件 `IScriptEntry` 函式的傳回型別資訊。|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|傳回對應於 `IScriptEntry` 指令碼區塊的文字，或在 `IScriptScriptlet` 事件處理常式中的原始程式碼。|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|設定 `IScriptEntry` 指令碼區塊或 `IScriptScriptlet` scriptlet 主體中的文字。|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|設定辨識 `IScriptEntry` 物件的項目名稱。|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|針對代表單一物件的項目 \(例如函式\)，設定物件的名稱。|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|設定 `IScriptEntry` 函式物件的型別資訊。|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|設定對應於 `IScriptEntry` 指令碼區塊的文字，或在 `IScriptScriptlet` 事件處理常式中的原始程式碼。|  
  
## 請參閱  
 [動態指令碼撰寫的介面](../../winscript/reference/active-script-authoring-interfaces.md)
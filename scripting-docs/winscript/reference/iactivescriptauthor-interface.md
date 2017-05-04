---
title: "IActiveScriptAuthor 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptAuthor 介面"
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthor 介面
建立服務，包括資訊的 IntelliSense 和定序的表示。  
  
 除了繼承自 `IUnknown` 的方法之外，`IActiveScriptAuthor` 介面還會公開下列方法。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|加入根層級項目的名稱變更為撰寫引擎的命名空間的指令碼。  *根層次的* 項目是可以包含屬性和方法，，也可以包含事件來源的物件。|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|將程式碼 scriptlet 做為根層級 `IScriptNode` 物件的子系。  在主應用程式， scriptlet 完整名稱只能有兩個層級。|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|將型別程式庫加入至指令碼的命名空間。|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|傳回一組要求的完成內容的完成字元。|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|傳回具有指定之屬性的 scriptlet。|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|傳回型別資訊和錨定特定字元的位置在程式碼區塊。  這個成員的 IntelliSense，全域清單和參數有關的資訊。|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|傳回語言資訊。|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|傳回建立者的指令碼 `IScriptNode` 樹狀結構的根。|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|傳回 scriptlet 文字屬性。|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|傳回指令碼區塊的文字屬性變更為。|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|傳回指出指定的字元是否應由應用程式執行陳述式完成。|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|解析指令碼文字，將文字加入至撰寫引擎的建立指令碼，並建立對應於指令碼區塊的 `IScriptEntry` 物件。|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|從建立的指令碼引擎的命名空間 `NamedItem` 移除物件。|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|從建立引擎命名空間的指令碼移除型別程式庫。|  
  
## 請參閱  
 [動態指令碼撰寫的介面](../../winscript/reference/active-script-authoring-interfaces.md)
---
title: "IActiveScriptSite | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSite 介面"
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite
實作是由主應用程式建立視窗之網站指令碼引擎。  通常，網站就會與 \(例如\) 會對指令碼的容器中的所有物件 \(， ActiveX 控制項\)。  一般來說，此容器會對應到文件或呼叫來檢視。  Microsoft Internet Explorer\) 資源管理員時，例如，將會建立每個顯示 HTML 網頁的這類容器。  每一個 ActiveX 控制項 \(或其他 Automation 物件\) 在網頁和指令碼引擎，在這個容器中都是可列舉的。  
  
## 依照 Vtable 順序的方法  
  
|||  
|-|-|  
|方法|描述|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|擷取主機以顯示使用者介面項目使用的地區設定識別項。|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|取得與加入至引擎會傳遞至 [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) 方法呼叫之項目的相關資訊。|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|擷取可唯一識別目前文件版本從主應用程式檢視的主應用程式定義的字串。|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|呼叫時，指令碼已完成執行。|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|告知主應用程式指令碼引擎已變更狀態。|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|告知主應用程式執行時發生錯誤，當引擎執行指令碼時。|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|告知主應用程式指令碼引擎開始執行指令碼。|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|告知主應用程式指令碼引擎從執行指令碼傳回。|  
  
## 請參閱  
 [動態指令碼的介面](../../winscript/reference/active-script-interfaces.md)
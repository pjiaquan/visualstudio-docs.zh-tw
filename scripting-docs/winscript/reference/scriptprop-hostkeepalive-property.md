---
title: "SCRIPTPROP_HOSTKEEPALIVE 屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# SCRIPTPROP_HOSTKEEPALIVE 屬性
用於指定是否應該保持指令碼引擎完整功能，如果有未完成的參考。  
  
 使用 [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) 將這個屬性設定為 `true`。  如果這個屬性設定為 `true`，指令碼引擎會保持完整功能，只要有至少一個未完成的參考或對指令碼引擎或加入至 JavaScript 物件的 `IDispatch` 指標是使用指令碼引擎。  當這個屬性設定為 `true`時，您可以使用 [IActiveScript::Close](../../winscript/reference/iactivescript-close.md) 或 [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) 方法，您不應該明確關閉或重設指令碼引擎。  最後一個參考版本的指令碼物件的關閉指令碼引擎。  
  
## 語法  
  
```  
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## 需求  
 這個屬性只會出現在與 [!INCLUDE[win8](../../javascript/includes/win8-md.md)]一起安裝，與 Internet Explorer 8 KB 2707082 在 [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)]，或與 Internet Explorer 9 的 KB 2722913 [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)] 或 [!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)]的 activscp.idl 的版本。
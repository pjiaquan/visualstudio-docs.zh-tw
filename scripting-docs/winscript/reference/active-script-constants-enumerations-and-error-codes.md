---
title: "動態指令碼的常數、列舉和錯誤碼 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: aab24471-5817-45c0-be07-ffe4648923ed
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# 動態指令碼的常數、列舉和錯誤碼
本節說明用來視窗和錯誤碼的列舉型別 \(Enumeration\) 指令碼引擎。  
  
## 常數  
  
|常數|描述|  
|--------|--------|  
|[SCRIPTTHREADID 的常數](../../winscript/reference/scriptthreadid-constants.md)|指定執行緒的型別。|  
  
## 屬性  
  
|屬性|描述|  
|--------|--------|  
|[SCRIPTPROP\_HOSTKEEPALIVE 屬性](../../winscript/reference/scriptprop-hostkeepalive-property.md)|用於指定是否應將指令碼引擎完整功能，如果有未完成的參考。|  
  
## 列舉  
  
|列舉|描述|  
|--------|--------|  
|[SCRIPTGCTYPE 列舉](../../winscript/reference/scriptgctype-enumeration.md)|執行記憶體回收的類型。|  
|[SCRIPTLANGUAGEVERSION 列舉](../../winscript/reference/scriptlanguageversion-enumeration.md)|指定可能的指令碼的版本。|  
|[SCRIPTSTATE 列舉](../../winscript/reference/scriptstate-enumeration.md)|指定一個指令碼引擎的狀態。|  
|||  
|[SCRIPTTHREADSTATE 列舉](../../winscript/reference/scriptthreadstate-enumeration.md)|在一個指令碼引擎指定執行緒的狀態。|  
|[SCRIPTTRACEINFO 列舉](../../winscript/reference/scripttraceinfo-enumeration.md)|表示要追蹤的指令碼事件。  使用在 [IActiveScriptSiteTraceInfo::SendScriptTraceInfo 方法](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md)。|  
|[SCRIPTUICHANDLING 列舉](../../winscript/reference/scriptuichandling-enumeration.md)|表示應該處理 UI 控制項的方法。|  
|[SCRIPTUICITEM 列舉](../../winscript/reference/scriptuicitem-enumeration.md)|代表 UI 項目的型別。  使用在 [IActiveScriptSiteUIControl::GetUIBehavior 方法](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md)。|  
  
## 錯誤碼  
  
|錯誤碼|描述|  
|---------|--------|  
|[SCRIPT\_E\_PROPAGATE 錯誤碼](../../winscript/reference/script-e-propagate-error-code.md)|指令碼錯誤會傳播至呼叫端，可能是在不同的執行緒。|  
|[SCRIPT\_E\_RECORDED 錯誤碼](../../winscript/reference/script-e-recorded-error-code.md)|錯誤已傳遞指令碼引擎與主機之間。|  
|[SCRIPT\_E\_REPORTED 錯誤碼](../../winscript/reference/script-e-reported-error-code.md)|指令碼引擎未處理的例外狀況向主應用程式報告。|  
  
## 請參閱  
 [動態指令碼的介面](../../winscript/reference/active-script-interfaces.md)
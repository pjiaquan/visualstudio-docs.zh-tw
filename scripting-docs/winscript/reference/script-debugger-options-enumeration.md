---
title: "SCRIPT_DEBUGGER_OPTIONS 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "SCRIPT_DEBUGGER_OPTIONS 列舉"
ms.assetid: aef41ec0-6f65-48e8-a69e-44b4e4fb929f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# SCRIPT_DEBUGGER_OPTIONS 列舉
表示套用至附加偵錯工具的一組選項和功能。  使用在 [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) 和 [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  這些常數都是 PDM v10.0 實作和更大。  位於 activdbg100.h。  
  
## 語法  
  
```  
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## Members  
  
|成員|值|描述|  
|--------|-------|--------|  
|SDO\_NONE|0x00000000|未設定任何選項。|  
|SDO\_ENABLE\_FIRST\_CHANCE\_EXCEPTIONS|0x00000001|表示指令碼執行階段應該 BREAKREASON\_ERROR 引發事件，當擲回例外狀況。  這個選項可能會由偵錯工具設定或由使用者設定的程式碼會 `Debug.enableFirstChanceExceptions(<true&#124;false>)`。|  
|SDO\_ENABLE\_WEB\_WORKER\_SUPPORT|0x00000002|表示附加偵錯工具支援的工作。|  
  
## 請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)
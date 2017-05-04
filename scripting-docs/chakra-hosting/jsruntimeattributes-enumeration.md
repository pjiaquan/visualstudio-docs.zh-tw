---
title: "JsRuntimeAttributes 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsRuntimeAttributes"
helpviewer_keywords: 
  - "JsRuntimeAttributes 列舉"
ms.assetid: f76d82e9-a695-4d6a-96c1-b3a4d27fed68
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# JsRuntimeAttributes 列舉
執行階段的屬性。  
  
## 語法  
  
```  
enum JsRuntimeAttributes;  
```  
  
## 成員  
  
### 值  
  
|名稱|描述|  
|--------|--------|  
|`JsRuntimeAttributeAllowScriptInterrupt`|執行階段應該支援可靠的指令碼中斷。 這樣會增加執行階段檢查指令碼中斷要求的位置數，但是會稍微降低執行階段的效能。|  
|`JsRuntimeAttributeDisableBackgroundWork`|執行階段將不會在背景執行緒上執行任何作業 \(例如，記憶體回收\)。|  
|`JsRuntimeAttributeDisableEval`|使用 `eval` 或 `function` 建構函式將會擲回例外狀況。|  
|`JsRuntimeAttributeDisableNativeCodeGeneration`|執行階段不會產生機器碼。|  
|`JsRuntimeAttributeEnableExperimentalFeatures`|執行階段會啟用所有實驗性功能。|  
|`JsRuntimeAttributeEnableIdleProcessing`|主機將會呼叫 `JsIdle`，因此，請啟用閒置處理。 否則執行階段將會稍微積極地管理記憶體。|  
|`JsRuntimeAttributeDispatchSetExceptionsToDebugger`|呼叫 `JsSetException` 也會將例外狀況分派至指令碼偵錯工具 \(如果有\)，讓偵錯工具有機會中斷例外狀況。|  
|`JsRuntimeAttributeNone`|沒有特殊屬性。|  
  
## 需求  
 **標頭：**jsrt.h  
  
## 請參閱  
 [參考 \(JavaScript 執行階段\)](../chakra-hosting/reference-javascript-runtime.md)
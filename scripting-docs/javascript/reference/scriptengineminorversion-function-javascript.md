---
title: "ScriptEngineMinorVersion 函式 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "ScriptEngineMinorVersion"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ScriptEngineMinorVersion 函式"
ms.assetid: caa506a5-e61d-4b2a-8b83-83d56a2f26cd
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# ScriptEngineMinorVersion 函式 (JavaScript)
取得使用中指令碼引擎的次要版本號碼。  
  
## 語法  
  
```  
ScriptEngineMinorVersion()  
```  
  
## 備註  
 傳回值直接對應到使用中指令碼語言的動態連結程式庫 \(DLL\) 中所含的版本資訊。  
  
## 範例  
 下面範例說明如何使用 `ScriptEngineMinorVersion` 函式：  
  
```javascript  
if (window.ScriptEngineMinorVersion) {  
    console.log(window.ScriptEngineMinorVersion());  
}  
  
//Output: <current minor version>  
  
```  
  
## 需求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## 請參閱  
 [ScriptEngine 函式](../../javascript/reference/scriptengine-function-javascript.md)   
 [ScriptEngineBuildVersion 函式](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [ScriptEngineMajorVersion 函式](../../javascript/reference/scriptenginemajorversion-function-javascript.md)
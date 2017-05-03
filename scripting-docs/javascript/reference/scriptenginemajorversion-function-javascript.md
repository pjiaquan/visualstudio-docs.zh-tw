---
title: "ScriptEngineMajorVersion 函式 (JavaScript) | Microsoft Docs"
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
  - "ScriptEngineMajorVersion"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ScriptEngineMajorVersion 函式"
ms.assetid: 3e251bce-1e14-4cb5-b79f-53845d1920fd
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# ScriptEngineMajorVersion 函式 (JavaScript)
取得使用中指令碼引擎的主要版本號碼。  
  
## 語法  
  
```  
ScriptEngineMajorVersion()  
```  
  
## 備註  
 傳回值直接對應到使用中指令碼語言的動態連結程式庫 \(DLL\) 中所含的版本資訊。  
  
## 範例  
 下面範例說明如何使用 `ScriptEngineMajorVersion` 函式：  
  
```javascript  
if (window.ScriptEngineMajorVersion) {  
    console.log(window.ScriptEngine());   
}  
  
Output: <current major version>  
  
```  
  
## 需求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## 請參閱  
 [ScriptEngine 函式](../../javascript/reference/scriptengine-function-javascript.md)   
 [ScriptEngineBuildVersion 函式](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [ScriptEngineMinorVersion 函式](../../javascript/reference/scriptengineminorversion-function-javascript.md)
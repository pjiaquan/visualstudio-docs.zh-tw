---
title: "IActiveScriptParse::InitNew | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParse.InitNew
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParse_InitNew"
ms.assetid: 3a582bd6-fc0d-43a5-812f-5ea55a8517a1
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParse::InitNew
初始化指令碼引擎。  
  
## 語法  
  
```  
HRESULT InitNew(void);  
```  
  
## 傳回值  
 傳回 `S_OK` ，如果成功或 `E_FAIL` ，在初始化時發生錯誤。  
  
## 備註  
 在使用前指令碼引擎，必須呼叫下列其中一種方法: `IPersist*::Load`、 `IPersist*::InitNew`或 `IActiveScriptParse::InitNew`。  此方法之語意與 `IPersistStreamInit::InitNew`相同，這個方法呼叫指令碼引擎初始化其本身。  請注意它是無效的呼叫 `IPersist*::InitNew` 或 `IActiveScriptParse::InitNew` 和 `IPersist*::Load`，也不是有效的多次呼叫 `IPersist*::InitNew`、 `IActiveScriptParse::InitNew`或 `IPersist*::Load` 。  
  
## 請參閱  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)
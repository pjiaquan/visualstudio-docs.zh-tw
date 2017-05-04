---
title: "IActiveScriptParseProcedureOld 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParseProcedureOld
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParseProcedureOld 介面"
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptParseProcedureOld 介面
允許程序的原始程式碼文字加入至指令碼。  對於沒有獨立建立的環境，例如 VBScript 的解譯的指令碼語言，這提供替代的機制 \(除了 `IActiveScriptParse` 或 `IPersist*`之外\) 加入指令碼程序加入至命名空間。  
  
> [!NOTE]
>  這個介面已被取代而建議使用 `IActiveScriptParseProcedure` 介面。  
  
## 方法  
 除了繼承自 `IUnknown` 的方法之外，`IActiveScriptParseProcedureOld` 介面還會公開下列方法。  
  
|方法|描述|  
|--------|--------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|解析指定編碼程序並加入程序加入至命名空間。|  
  
## 請參閱  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)
---
title: "IActiveScript::AddTypeLib | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.AddTypeLib
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_AddTypeLib"
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::AddTypeLib
將型別程式庫至指令碼的命名空間。  這類似於在 C\/C\+\+ 上 `#include` 指示詞。  它可讓一組預先定義的項目 \(例如類別定義、 `typedefs`和要加入的具名常數加入至這個執行階段環境中可用的指令碼。  
  
## 語法  
  
```  
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### 參數  
 `guidTypeLib`  
 \[in\] 型別加入之程式庫的 CLSID。  
  
 `dwMaj`  
 \[in\] 主要版本號碼。  
  
 `dwMin`  
 \[in\] 次要版本號碼。  
  
 `dwFlags`  
 \[in\] 選項旗標。  可以是下列項目:  
  
|值|意義|  
|-------|--------|  
|SCRIPTTYPELIB\_ISCONTROL|型別程式庫描述主機使用的 ActiveX 控制項。|  
  
## 傳回值  
 下列值的傳回一個值:  
  
|傳回值|意義|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_UNEXPECTED`|這個呼叫不需要 \(例如，指令碼引擎尚未載入或未初始化\)。|  
|`TYPE_E_CANTLOADLIBRARY`|指定型別程式庫無法載入。|  
  
## 請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)
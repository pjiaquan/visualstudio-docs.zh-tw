---
title: "ISetNextStatement::CanSetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISetNextStatement.CanSetNextStatement
apilocation: scrobj.dll
ms.assetid: e2a54634-31ec-4d16-84e8-2b123845d876
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# ISetNextStatement::CanSetNextStatement
這個方法會判斷執行點，決定要執行的程式碼下一個陳述式，是否可以設定為指定的位置。  
  
## 語法  
  
```  
HRESULT CanSetNextStatement(  
   IDebugStackFrame*  pStackFrame,  
   IDebugCodeContext*  pCodeContext  
)  
```  
  
#### 參數  
 `pStackFrame`  
 \[out\] 堆疊框架物件的指標。  
  
 `pCodeContext`  
 \[out\] 程式碼內容物件的指標。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|下一個陳述式可更新指定之程式碼的內容。|  
|`S_FALSE`|下一個陳述式不能更新為指定之程式碼的內容。|  
  
## 備註  
  
## 請參閱  
 [ISetNextStatement 介面](../../winscript/reference/isetnextstatement-interface.md)
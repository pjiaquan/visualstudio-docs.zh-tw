---
title: "IDispatchEx::DeleteMemberByName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.DeleteMemberByName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DeleteMemberByName 方法"
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::DeleteMemberByName
依名稱刪除成員。  
  
## 語法  
  
```  
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### 參數  
 `bstrName`  
 成員的名稱會刪除。  
  
 `grfdex`  
 判斷成員名稱是否區分大小寫。  這可以是下列其中一個值:  
  
|值|意義|  
|-------|--------|  
|fdexNameCaseSensitive|該要求的名稱搜尋完成以區分大小寫。  可以支援不區分大小寫的查詢的物件會忽略。|  
|fdexNameCaseInsensitive|該名稱的要求完成搜尋不區分大小寫的方式。  可以由不支援不區分大小寫的查詢的物件會忽略。|  
  
## 傳回值  
 下列值的傳回一個值:  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`S_FALSE`|成員存在，但無法刪除。|  
  
## 備註  
 如果成員刪除，用做需要會持續有效。 `GetNextDispID`。  
  
 如果具有指定名稱的成員刪除，並具有相同名稱的成員之後重新建立，用做應該是相同的。  \(只有大小寫不同的成員是「相同的」是物件而定\)。  
  
## 範例  
  
```  
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## 請參閱  
 [IDispatchEx 介面](../../winscript/reference/idispatchex-interface.md)
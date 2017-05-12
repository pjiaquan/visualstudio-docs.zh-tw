---
title: "IDispatchEx::DeleteMemberByDispID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.DeleteMemberByDispID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DeleteMemberByDispID 方法"
ms.assetid: f61231e5-ba93-4ac3-bde8-d363548356b3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::DeleteMemberByDispID
由 DISPID 刪除成員。  
  
## 語法  
  
```  
HRESULT DeleteMemberByDispID(  
    DISPID id  
);  
```  
  
#### 參數  
 `id`  
 成員識別項。  使用 `GetDispID` 或 `GetNextDispID` 取得分派識別項。  
  
## 傳回值  
 下列值的傳回一個值:  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`S_FALSE`|成員存在，但無法刪除。|  
  
## 備註  
 如果成員刪除，用做需要會持續有效。 `GetNextDispID`。  
  
 如果具有指定名稱的成員刪除，並具有相同名稱的成員之後重新建立，用做應該是相同的。  \(只有大小寫不同的成員名稱是「相同的」是物件而定\)。  
  
## 範例  
  
```  
BSTR bstrName;  
DISPID dispid;  
IDispatchEx *pdex;   
  
// Assign to pdex and bstrName  
if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
    pdex->DeleteMemberByDispID(dispid);  
```  
  
## 請參閱  
 [IDispatchEx 介面](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)
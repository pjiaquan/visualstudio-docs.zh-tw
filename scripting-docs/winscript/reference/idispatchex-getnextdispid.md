---
title: "IDispatchEx::GetNextDispID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetNextDispID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetNextDispID 方法"
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetNextDispID
列舉物件的成員。  
  
## 語法  
  
```  
HRESULT GetNextDispID(  
   DWORD grfdex,  
   DISPID id,  
   DISPID *pid  
);  
```  
  
#### 參數  
 `grfdex`  
 判斷哪一組項目時的列舉型別。  這可以是下列值的組合:  
  
|值|意義|  
|-------|--------|  
|fdexEnumDefault|要求物件列舉型別預設項目。  物件允許列舉型別的項目。|  
|fdexEnumAll|要求物件列舉所有項目。  物件允許列舉型別的項目。|  
  
 `id`  
 識別目前成員。  GetNextDispID 在這個節點之後會擷取列舉型別的項目。  使用 GetDispID 或為 GetNextDispID\) 的呼叫取得此識別項。  使用 DISPID\_STARTENUM 值取得第一個項目的第一個識別項。  
  
 `pid`  
 接收到下一個項目識別項的列舉型別中的物件變數的位址。  
  
 如果成員是由 `DeleteMemberByName` 或 `DeleteMemberByDispID`刪除， `DISPID` 需要會持續有效。 `GetNextDispID`。  
  
## 傳回值  
 下列值的傳回一個值:  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`S_FALSE`|列舉型別 \(Enumeration\) 完成。|  
  
## 範例  
  
```  
HRESULT hr;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
  
   // Assign to pdex  
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
   while (hr == NOERROR)  
   {  
      hr = pdex->GetMemberName(dispid, &bstrName);  
      if (!wcscmp(bstrName, OLESTR("Bar")))  
      {  
         SysFreeString(bstrName);  
         return TRUE;  
      }  
      SysFreeString(bstrName);  
      hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);  
   }  
```  
  
## 請參閱  
 [IDispatchEx 介面](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](#lrfidispatchexgetnextdispid)   
 [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)   
 [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)
---
title: "IDiaStackFrame::get_rawLVarInstanceValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaStackFrame::get_rawLVarInstanceValue 方法"
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaStackFrame::get_rawLVarInstanceValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

這個方法會擷取指定的本機變數的值，以未經處理位元組。  
  
## 語法  
  
```cpp#  
HRESULT get_rawLVarInstanceValue(  
   IDiaLVarInstance* pInstance,  
   DWORD             cbDataMax,  
   DWORD*            pcbData,  
   BYTE*             pbData  
);  
```  
  
#### 參數  
 `pInstance`  
 \[in\]`IDiaLVarInstance`物件，表示要取得其值為區域變數的執行個體。  
  
 `cbDataMax`  
 \[in\]最大緩衝區中的位元組數所指`pbData`。  這可能是最多 8 個位元組 \(`sizeof(ULONGLONG)`\)。  
  
 `pcbData`  
 \[\] out傳回的實際儲存在緩衝區的位元組數。  
  
 `pbData`  
 \[\] out若要填入資料的緩衝區。  這不能是 `NULL`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
---
title: "IDiaSourceFile::get_checksumType | Microsoft Docs"
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
  - "IDiaSourceFile::get_checksumType 方法"
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSourceFile::get_checksumType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取加總檢查碼型別。  
  
## 語法  
  
```cpp#  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回總和檢查碼型別。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 加總檢查碼型別是一個可對應到 \[加總檢查碼演算法的值。  例如，標準的 PDB 檔案格式可以通常有下列值之一：  
  
|加總檢查碼的型別|CryptoAPI 標籤|描述|  
|--------------|------------------|--------|  
|0|\<無\>|不存在的總和檢查碼。|  
|1|`CALG_MD5`|使用 MD5 雜湊演算法產生總和檢查碼。|  
|2|`CALG_SHA1`|使用 SHA1 雜湊演算法產生總和檢查碼。|  
  
 `CryptoAPI`標籤是從`ALG_ID`列舉型別。  如需有關雜湊演算法的詳細資訊，請參閱`CryptoAPI`一節的 Microsoft [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)]。  
  
 若要取得原始程式檔的實際的總和檢查碼位元組，呼叫[IDiaSourceFile::get\_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)方法。  
  
## 請參閱  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get\_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)
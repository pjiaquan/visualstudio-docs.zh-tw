---
title: "NameSearchOptions | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NameSearchOptions 列舉"
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# NameSearchOptions
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定符號和檔案名稱的搜尋的選項。  
  
## 語法  
  
```cpp#  
enum NameSearchOptions {   
   nsNone,  
   nsfCaseSensitive     = 0x1,  
   nsfCaseInsensitive   = 0x2,  
   nsfFNameExt          = 0x4,  
   nsfRegularExpression = 0x8,  
   nsfUndecoratedName   = 0x10,  
  
// For backward compatibility:  
   nsCaseSensitive           = nsfCaseSensitive,  
   nsCaseInsensitive         = nsfCaseInsensitive,  
   nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,  
   nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,  
   nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive  
};  
```  
  
## 項目  
 `nsNone`  
 未指定任何選項。  
  
 `nsfCaseSensitive`  
 套用大小寫視為相異的名稱相符的項目。  
  
 `nsfCaseInsensitive`  
 適用於不區分大小寫的名稱相符的項目。  
  
 `nsfFNameExt`  
 將名稱視為路徑，並套用 filename.ext 名稱相符的項目。  
  
 `nsfRegularExpression`  
 套用大小寫視為相異的名稱相符項目使用星號 \(\*\) 和問號 \(?\) 作為萬用字元。  
  
 `nsfUndecoratedName`  
 僅適用於符號的有兩個裝飾和裝飾名稱。  
  
## 備註  
 這個列舉型別中的值會傳遞至下列方法：  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## 需求  
 標頭: dia2.h  
  
## 請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
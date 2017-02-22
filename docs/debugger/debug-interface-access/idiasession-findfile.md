---
title: "IDiaSession::findFile | Microsoft Docs"
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
  - "IDiaSession::findFile 方法"
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findFile
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

以編譯和名稱擷取原始程式檔。  
  
## 語法  
  
```cpp#  
HRESULT findFile (   
   IDiaSymbol*           pCompiland,  
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSourceFiles** ppResult  
);  
```  
  
#### 參數  
 `pCompiland`  
 \[in\] 表示編譯的 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件會使用做為內容的搜尋。  將參數設定為 `NULL` 尋找在所有編譯的原始程式檔。  
  
 `name`  
 \[in\] 指定要擷取的原始程式檔 \(Source File\) 的名稱。  將參數設定為包含要擷取的所有原始程式檔的 `NULL` 。  
  
 `option`  
 \[in\] 指定比較選項套用到名稱搜尋。  從 [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md) 列舉型別的值可單獨使用或在組合。  
  
 `ppResult`  
 \[out\] 傳回包含擷取的原始程式檔清單的 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) 物件。  
  
## 傳回值  
 如果成功，則傳回 `S_OK`，否則傳回錯誤碼。  
  
## 範例  
  
```cpp#  
IDiaEnumSourceFiles* pEnum;  
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );  
```  
  
## 請參閱  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)
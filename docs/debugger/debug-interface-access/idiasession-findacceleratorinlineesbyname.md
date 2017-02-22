---
title: "IDiaSession::findAcceleratorInlineesByName | Microsoft Docs"
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
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findAcceleratorInlineesByName
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

傳回符號的列舉型別內嵌框架的與指定的內嵌函式名稱對應。  
  
## 語法  
  
```cpp#  
HRESULT findAcceleratorInlineeLinesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### 參數  
 `name`  
 \[in\] 要搜尋的失敗函式名稱。  
  
 `option`  
 \[in\] 名稱搜尋選項，用於搜尋對應至 `name`內嵌框架時。  如需詳細資訊，請參閱 [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)。  
  
 `ppResult`  
 \[out\] 會使用這個結果的 `IDiaEnumSymbols` 介面指標的指標。  
  
## 傳回值  
 如果成功，則傳回 `S_OK`，否則傳回錯誤碼。  
  
## 備註  
 這個函式只搜尋 inlinees 在快速 Stub 函式中。  它會覆寫原生 C\+\+ 程序資料錄。  
  
## 請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
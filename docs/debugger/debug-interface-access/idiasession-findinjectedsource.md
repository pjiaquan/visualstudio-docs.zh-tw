---
title: "IDiaSession::findInjectedSource | Microsoft Docs"
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
  - "IDiaSession::findInjectedSource 方法"
ms.assetid: 907531b6-1ef8-4153-986d-b72611a1632d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findInjectedSource
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取已放入符號存放區提供者屬性的來源清單或編譯程序的其他元件。  
  
## 語法  
  
```cpp#  
HRESULT findInjectedSource (   
   LPCOLESTR                 srcFile,  
   IDiaEnumInjectedSources** ppResult  
);  
```  
  
#### 參數  
 srcFile  
 \[in\]要搜尋的原始程式檔的名稱。  
  
 ppResult  
 \[\] out傳回[IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)物件，其中包含一份所有插入的來源。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
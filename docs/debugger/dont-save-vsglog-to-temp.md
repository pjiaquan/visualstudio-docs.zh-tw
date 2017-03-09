---
title: "DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DONT_SAVE_VSGLOG_TO_TEMP
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

由其圖形記錄檔是否儲存在使用者的本機暫存檔目錄來定義。  
  
## 語法  
  
```cpp  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## 值  
 由前置處理器符號的存在與否決定的圖形記錄檔是否儲存在使用者的本機暫存檔目錄。  如果這個符號已定義，則 `VSG_DEFAULT_RUN_FILENAME` 所定義的檔名是相對於所擷取之應用程式的目前目錄，或為絕對路徑;否則， `VSG_DEFAULT_RUN_FILENAME` 所定義的檔名是相對於使用者的暫存檔目錄，且不可以是絕對路徑。  
  
## 備註  
 根據使用者的權限，圖形記錄檔可能無法在任意位置儲存。  我們建議您優先儲存圖形記錄到使用者的暫存檔目錄，或另一個已知的位置，如果您並不確定您選擇的位置是否可由使用者撰寫。  
  
 要防止圖形記錄檔儲存至暫存檔目錄，在包含`vsgcapture.h` 之前您必須先定義 `DONT_SAVE_VSGLOG_TO_TEMP`。  
  
## 範例  
 這個範例顯示如何將圖形記錄檔的存至主機的絕對路徑。  
  
```  
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  
  
#include <vsgcapture.h>  
  
```  
  
## 請參閱  
 [VSG\_DEFAULT\_RUN\_FILENAME](../debugger/vsg-default-run-filename.md)
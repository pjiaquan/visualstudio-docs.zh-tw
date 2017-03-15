---
title: "列出模組命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listmodules"
helpviewer_keywords: 
  - "Debug.ListModules 命令"
  - "列出模組命令"
  - "ListModules 命令"
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# 列出模組命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

列出目前處理序的模組。  
  
## 語法  
  
```  
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]  
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]  
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]  
```  
  
#### 參數  
 \/Address:`yes|no`  
 選擇項。  指定是否顯示模組的記憶體位址。  預設值為 `yes`。  
  
 \/Name:`yes|no`  
 選擇項。  指定是否顯示模組的名稱。  預設值為 `yes`。  
  
 \/Order:`yes|no`  
 選擇項。  指定是否顯示模組的順序。  預設值為 `no`。  
  
 \/Path:`yes|no`  
 選擇項。  指定是否顯示模組的路徑。  預設值為 `yes`。  
  
 \/Process:`yes|no`  
 選擇項。  指定是否顯示模組的處理序。  預設值為 `no`。  
  
 \/SymbolFile:`yes|no`  
 選擇項。  指定是否顯示模組的符號檔案。  預設值為 `no`。  
  
 \/SymbolStatus:`yes|no`  
 選擇項。  指定是否顯示模組的符號狀態。  預設值為 `yes`。  
  
 \/Timestamp:`yes|no`  
 選擇項。  指定是否顯示模組的時間戳記。  預設值為 `no`。  
  
 \/Version:`yes|no`  
 選擇項。  指定是否顯示模組的版本。  預設值為 `no`。  
  
## 備註  
  
## 範例  
 此範例列出目前處理序的模組名稱、位址和時間戳記。  
  
```  
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no  
```  
  
## 請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [如何：使用模組視窗](../../debugger/how-to-use-the-modules-window.md)
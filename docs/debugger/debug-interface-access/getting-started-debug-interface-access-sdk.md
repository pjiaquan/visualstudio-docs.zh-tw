---
title: "使用者入門 (偵錯介面存取 SDK) | Microsoft Docs"
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
  - ".dbg 檔案"
  - "DBG 檔案"
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# 使用者入門 (偵錯介面存取 SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

偵錯介面存取 \(DIA\) SDK 會提供您指示的文件與說明如何使用 DIA API 的範例。  DIA SDK 中使用的介面和方法來開發自訂的應用程式開啟.pdb 和.dbg 檔，並搜尋其內容的符號、 值、 屬性、 地址，以及其他的偵錯資訊。  此 SDK 也提供與 C\+\+ 應用程式中找到的符號相關的屬性參考資料表。  
  
 徹底運用 DIA SDK，您應該先熟悉下列各項：  
  
-   C \+ \+ 程式語言  
  
-   COM 程式設計  
  
-   Visual Studio 整合式的開發環境 \(IDE\) 編譯範例  
  
 DIA SDK 通常會隨 Visual Studio，而它的預設位置是 *\[磁碟機\]*\\Program Files\\Microsoft Visual Studio 9.0\\DIA SDK。  安裝的一部分，msdia90.dll，它實作 DIA SDK 時，會自動註冊，所有您所要使用它做為包含`dia2.h`在您的程式及連結至`diaguids.lib`。  
  
 標頭: include\\dia2.h  
  
 媒體櫃： lib\\diaguids.lib  
  
 DLL： bin\\msdia80.dll  
  
 IDL： idl\\dia2.idl  
  
## 本章節內容  
 [概觀](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 檢閱 DIA.的基本架構  
  
 [查詢 .Pdb 檔案](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 提供如何使用 DIA API 查詢.pdb 檔的逐步指示。  
  
## 請參閱  
 [偵錯 \(偵錯介面存取 SDK\)](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
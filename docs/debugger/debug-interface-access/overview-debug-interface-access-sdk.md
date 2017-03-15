---
title: "概觀 (偵錯介面存取 SDK) | Microsoft Docs"
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
  - "使用者定義類型"
  - ".dbg 檔案"
  - "模組"
  - "介面 [DIA SDK]"
  - "DBG 檔案"
  - "程序 [DIA SDK]"
  - "可執行檔"
  - "COM 物件，在 DIA SDK 中"
  - "編譯單位"
  - "可執行檔映像"
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 概觀 (偵錯介面存取 SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

您可以使用 DIA SDK 存取 Microsoft 偵錯資訊。  DIA SDK 提供 COM API 集，就不用重新撰寫程式碼，只要 Microsoft 變更偵錯資訊的格式。  DIA SDK 也可讓您從一組選定之先前版本的偵錯資訊，所產生的.pdb 和.dbg 檔案中讀取[!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 5.0 或更新版本。  
  
 DIA SDK 中的每個介面，將不同的 COM 物件，表示除了在指定的地方。  其他的介面，因此其他的物件，藉由利用建立明確的查詢，例如[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)或[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)，而不是呼叫`QueryInterface`上現有的介面指標。  
  
## 請參閱  
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
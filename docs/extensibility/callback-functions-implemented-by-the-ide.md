---
title: "IDE 所實作的回呼函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "原始檔控制外掛程式，回呼函式"
  - "回呼函式，原始檔控制外掛程式"
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# IDE 所實作的回呼函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

若要進行整合與整合式的開發環境 \(IDE\)，以順暢越好，並提供統一的使用者體驗，原始檔控制外掛程式可以使用 IDE 所實作的回呼函式。 外掛程式可以呼叫這些函式在適當的時間，在原始檔控制作業，將資訊傳遞至 IDE。IDE 就可以顯示這項資訊做為其原生 UI 中的內嵌項目。 使用者會有較分散的經驗，在此案例中比如果外掛程式使用它自己的 UI。  
  
 必要的標頭檔是 scc.h。 預設位置是 \\Program Files\\VSIP 8.0\\EnvSDK\\common\\inc\\。 此外也會在 \\Program Files\\VSIP 有原始檔控制外掛程式範例的 VSIP 資料夾中 8.0\\MSSCCI\\。  
  
## 在本節中  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 描述使用的回呼函數 [SccOpenProject](../extensibility/sccopenproject-function.md) 顯示從原始檔控制外掛程式透過 IDE 的訊息。  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 描述使用的回呼函數 [SccPopulateList](../extensibility/sccpopulatelist-function.md) 當 IDE 沒有完整的存取權僅適用於原始檔控制外掛程式，例如版本控制下的檔案的完整清單的資訊。  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 描述使用的回呼函數 [SccQueryChanges](../extensibility/sccquerychanges-function.md) 作業。  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 描述使用的回呼函數 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) 作業。  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 描述設定呼叫的回呼函式 [SccSetOption](../extensibility/sccsetoption-function.md) ，可讓外掛程式通訊 IDE 將名稱變更回原始檔控制。  
  
## 相關章節  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 開啟專案。  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 會檢查其目前狀態的檔案清單。 此外，使用 `pfnPopulate` 函式的檔案不相符的準則時，通知呼叫端 `nCommand`。  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 檢查目錄和檔案的專案或專案原始檔控制下的清單。 找到的每個目錄和檔案名稱會傳遞至回呼函式。  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 會檢查檔案的清單所做的變更名稱。 每個檔案名稱會傳遞至回呼函式，以及其變更狀態。  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 設定各種不同的選項。 每個選項的開頭 `SCC_OPT_xxx` 而且有它自己組定義的值。  
  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)  
 描述原始檔控制外掛程式 SDK 的參考章節的內容。
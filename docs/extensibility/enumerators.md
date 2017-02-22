---
title: "列舉值 | Microsoft Docs"
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
  - "原始檔控制外掛程式，列舉值"
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# 列舉值
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此區段會列出原始檔控制外掛程式必須了解的原始檔控制外掛程式 API 中的列舉值資料型別。  
  
## 在本節中  
 [指令碼](../extensibility/command-code-enumerator.md)  
 列舉的選項 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) 和 [SccPopulateList](../extensibility/sccpopulatelist-function.md) 函式。  
  
 [訊息](../extensibility/message-enumerator.md)  
 列舉旗標用於列印的回呼， [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)。  
  
 [檔案狀態碼](../extensibility/file-status-code-enumerator.md)  
 包含指定的原始檔控制下的檔案狀態的具名常數值。  
  
 [目錄狀態碼](../extensibility/directory-status-code-enumerator.md)  
 包含具名常數的值，指定狀態的原始檔控制下的目錄。  
  
## 相關章節  
 [建立原始檔控制外掛程式](../extensibility/internals/creating-a-source-control-plug-in.md)  
 定義原始檔控制外掛程式 SDK，並說明內含的資源。  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 提示使用者輸入指定命令的進階選項。  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 會檢查其目前狀態的檔案清單。 此外，使用 `pfnPopulate` 函式的檔案不相符的準則時，通知呼叫端 `nCommand`。  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 描述使用的回呼函數 [SccOpenProject](../extensibility/sccopenproject-function.md) 顯示從原始檔控制外掛程式透過 IDE 的訊息。  
  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)  
 提供完整的原始檔控制外掛程式 API 中的所有項目清單。
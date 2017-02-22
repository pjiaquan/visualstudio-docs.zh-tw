---
title: "指令碼列舉值 | Microsoft Docs"
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
  - "指令碼列舉值"
  - "原始檔控制外掛程式，指令碼列舉"
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 指令碼列舉值
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

這個列舉值的選項中使用 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) 和 [SccPopulateList](../extensibility/sccpopulatelist-function.md)，表示指定之選項的命令。  
  
## 語法  
  
```  
enum SCCCOMMAND {  
   SCC_COMMAND_GET,  
   SCC_COMMAND_CHECKOUT,  
   SCC_COMMAND_CHECKIN,  
   SCC_COMMAND_UNCHECKOUT,  
   SCC_COMMAND_ADD,  
   SCC_COMMAND_REMOVE,  
   SCC_COMMAND_DIFF,  
   SCC_COMMAND_HISTORY,  
   SCC_COMMAND_RENAME,  
   SCC_COMMAND_PROPERTIES,  
   SCC_COMMAND_OPTIONS  
};  
```  
  
## 成員  
 SCC\_COMMAND\_GET  
 對應至 [SccGet](../extensibility/sccget-function.md)。  
  
 SCC\_COMMAND\_CHECKOUT  
 對應至 [SccCheckout](../extensibility/scccheckout-function.md)。  
  
 SCC\_COMMAND\_CHECKIN  
 對應至 [SccCheckin](../extensibility/scccheckin-function.md)。  
  
 SCC\_COMMAND\_UNCHECKOUT  
 對應至 [SccUncheckout](../extensibility/sccuncheckout-function.md)。  
  
 SCC\_COMMAND\_ADD  
 對應至 [SccAdd](../extensibility/sccadd-function.md)。  
  
 SCC\_COMMAND\_REMOVE  
 對應至 [SccRemove](../extensibility/sccremove-function.md)。  
  
 SCC\_COMMAND\_DIFF  
 對應至 [SccDiff](../extensibility/sccdiff-function.md)。  
  
 SCC\_COMMAND\_HISTORY  
 對應至 [SccHistory](../extensibility/scchistory-function.md)。  
  
 SCC\_COMMAND\_RENAME  
 對應至 [SccRename](../extensibility/sccrename-function.md)。  
  
 SCC\_COMMAND\_PROPERTIES  
 對應至 [SccProperties](../extensibility/sccproperties-function.md)。  
  
 SCC\_COMMAND\_OPTIONS  
 對應至 [SccSetOption](../extensibility/sccsetoption-function.md)。  
  
## 請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)   
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)
---
title: "如何：逐步執行 WCF 服務 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "偵錯, WCF"
  - "WCF, 偵錯"
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# 如何：逐步執行 WCF 服務
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中，您可以逐步執行 WCF 服務。  如果 WCF 服務與用戶端都位於相同的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 方案，您就可以執行到達 WCF 服務內部的中斷點。  
  
 您必須在 app.config 或 Web.config 檔案內啟用偵錯，才能使用逐步執行。  如需如何啟用偵錯，以及逐步執行 WCF 服務之限制的詳細資訊，請參閱 [WCF 偵錯的限制](../debugger/limitations-on-wcf-debugging.md)。  
  
### 若要逐步執行 WCF 服務  
  
1.  建立 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 方案，其中包含 WCF 用戶端和 WCF 服務專案。  
  
2.  在 \[方案總管\] 中，以滑鼠右鍵按一下 WCF 用戶端專案，然後按一下 \[**設定為啟始專案**\]。  
  
3.  在 app.config 或 web.config 檔案內啟用偵錯。  如需詳細資訊，請參閱 [WCF 偵錯的限制](../debugger/limitations-on-wcf-debugging.md)。  
  
4.  在用戶端專案中要開始逐步執行的位置設定中斷點。  這通常會是在 WCF 服務呼叫之前。  
  
5.  執行至中斷點，然後開始逐步執行。  偵錯工具將自動逐步執行服務。  
  
## 請參閱  
 [偵錯 WCF 服務](../debugger/debugging-wcf-services.md)   
 [WCF 偵錯的限制](../debugger/limitations-on-wcf-debugging.md)   
 [如何：偵錯自我裝載的 WCF 服務](../debugger/how-to-debug-a-self-hosted-wcf-service.md)
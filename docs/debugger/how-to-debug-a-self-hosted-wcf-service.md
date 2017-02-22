---
title: "如何：偵錯自我裝載的 WCF 服務 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
  - "WCF, 自我裝載的服務"
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：偵錯自我裝載的 WCF 服務
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

「*自我裝載的服務*」\(Self\-Hosted Service\) 是一項不會在 IIS、WCF 服務主機或 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 程式開發伺服器內部執行的 WCF 服務。  對自我裝載的 WCF 進行偵錯的最簡單方式，就是將 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 設定為當您選擇了 \[**偵錯**\] 功能表上的 \[**啟動偵錯**\] 時，啟動用戶端和伺服器。  
  
 如果 WCF 服務會在內部自我裝載，或是處理序無法以這種方式啟動 \(例如 NT 服務\)，您就無法使用這個方法進行。  您可以改用下列其中一種方法：  
  
-   將偵錯工具手動附加至裝載處理序。  如需詳細資訊，請參閱[附加至執行中處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
     \-或\-  
  
-   開始偵錯用戶端，然後逐步執行對服務的呼叫。  您必須在 app.config 檔案內啟用偵錯功能，才能執行這項作業。  如需詳細資訊，請參閱 [WCF 偵錯的限制](../debugger/limitations-on-wcf-debugging.md)。  
  
### 若要從 Visual Studio 啟動用戶端和主機  
  
1.  建立 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 方案，其中包含用戶端和伺服器專案。  
  
2.  將方案設定為當您選擇 \[**偵錯**\] 功能表上的 \[**啟動**\] 時，啟動用戶端和伺服器處理序。  
  
    1.  以滑鼠右鍵按一下 \[**方案總管**\] 中的方案名稱。  
  
    2.  按一下 \[**設定啟始專案**\]。  
  
    3.  在 \[**方案 \<名稱\> 屬性**\] 對話方塊中，選取 \[**多個啟始專案**\]。  
  
    4.  在 \[**多個啟始專案**\] 方格中，於對應至伺服器專案那一行，按一下 \[**動作**\]，然後選擇 \[**啟動**\]。  
  
    5.  在對應至用戶端專案那一行，按一下 \[**動作**\]，然後選擇 \[**啟動**\]。  
  
    6.  按一下 \[**確定**\]。  
  
## 請參閱  
 [偵錯 WCF 服務](../debugger/debugging-wcf-services.md)   
 [WCF 偵錯的限制](../debugger/limitations-on-wcf-debugging.md)   
 [如何：逐步執行 WCF 服務](../debugger/how-to-step-into-wcf-services.md)
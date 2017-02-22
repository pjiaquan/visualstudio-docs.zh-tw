---
title: "偵錯已部署的 Web 應用程式 | Microsoft Docs"
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
  - "ASP.NET Web 應用程式"
  - "ASP.NET, 偵錯 Web 應用程式"
  - "偵錯 Web 服務"
  - "Web 服務, 偵錯"
  - "XML Web Service, 偵錯"
  - "XML, 偵錯 Web 服務"
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 偵錯已部署的 Web 應用程式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果您必須對實際執行伺服器 \(Production Server\) 上執行的 Web 應用程式偵錯，則應該謹慎執行這個動作。  例如，若您附加至 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序來偵錯，並遇到中斷點，則背景處理工作序中的所有 Managed 程式碼都會中止。  中止背景工作處理序中所有 Managed 程式碼可能會使伺服器上所有使用者的作業停止。  在實際執行伺服器上偵錯之前，請務必考慮對實際執行工作的可能影響。  
  
 若要使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 偵錯已部署的應用程式，您必須附加至 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序，並且確定偵錯工具可以存取應用程式的符號。  您還必須找出並開啟應用程式的原始程式檔 \(Source File\)。  如需詳細資訊，請參閱[指定符號 \(.pdb\) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)、[如何：尋找 ASP.NET 處理序的名稱](../debugger/how-to-find-the-name-of-the-aspnet-process.md)和 [系統需求](../debugger/aspnet-debugging-system-requirements.md)。  
  
> [!NOTE]
>  許多 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式都會參考到包含商務邏輯或其他實用程式碼的 DLL。  這類的參考會自動從本機電腦，將 DLL 複製到 Web 應用程式虛擬目錄的 \\bin 資料夾。  在偵錯時請記住，您的 Web 應用程式是參考該 DLL 的複本而非本機電腦上的複本。  
  
 用來附加至 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序的處理序，和附加至其他任何遠端處理序一樣。  一旦附加之後，如果您沒有開啟正確的專案，則在應用程式中斷時會出現對話方塊。  這個對話方塊會要求您輸入應用程式原始程式檔的位置。  您在對話方塊中所指定的檔名，必須符合偵錯符號 \(位於 Web 伺服器上\) 中指定的檔名。  如需詳細資訊，請參閱[附加至執行中處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
## 請參閱  
 [偵錯 ASP.NET 和 AJAX 應用程式](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [偵錯 Web 應用程式和指令碼](../debugger/debugging-web-applications-and-script.md)   
 [如何：啟用 ASP.NET 應用程式的偵錯](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [如何：尋找 ASP.NET 處理序的名稱](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [指定符號 \(.pdb\) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
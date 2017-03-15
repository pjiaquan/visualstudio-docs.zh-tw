---
title: "如何：尋找 ASP.NET 處理序的名稱 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "ASP.NET 偵錯, ASP.NET 處理序"
  - "ASP.NET 處理序"
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：尋找 ASP.NET 處理序的名稱
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

若要附加至執行中的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式，您必須知道 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 處理序的名稱：  
  
-   如果您執行的是 IIS 6.0 或 IIS 7.0，則名稱是 w3wp.exe。  
  
-   如果您執行的是 IIS 的先前版本，則名稱是 aspnet\_wp.exe。  
  
 對於使用 [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)] \(含\) 以後版本建置的應用程式，[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 程式碼可位於檔案系統上，並在 WebDev.WebServer.exe 測試伺服器下執行。  在此情況下，您需要附加至 WebDev.WebServer.exe，而非 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 處理序。  本案例僅適用於本機偵錯。  
  
 舊版 ASP 應用程式會在它們以同處理序 \(In\-Process\) 方式執行時，於 IIS 處理序 inetinfo.exe 中執行。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選取 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要判斷專案程式碼是位於檔案系統或 IIS 上  
  
1.  如果尚未開啟 \[**方案總管**\]，請在 Visual Studio 中將其開啟。  
  
2.  選取包含應用程式名稱的最上層節點。  
  
3.  如果 \[**屬性**\] 視窗標題包含檔案路徑，則應用程式碼是在檔案系統上。  
  
     否則，\[**屬性**\] 視窗標題將包含網站名稱。  
  
### 若要判斷應用程式在哪一個 IIS 版本下執行  
  
1.  尋找 \[**系統管理工具**\] 並且執行它。  依照您的作業系統而定，這可能是 \[**控制台**\] 中的圖示，或是當您按一下 \[**開始**\] 時出現的功能表項目。  
  
     在 Windows XP 中，\[**控制台**\] 可能位於「類別目錄檢視」或「傳統檢視」內。  在「類別目錄檢視」內，您必須按一下 \[**切換到傳統檢視**\] 或 \[**效能及維護**\]，以檢視 \[**系統管理工具**\] 圖示。  
  
2.  從 \[**系統管理工具**\] 執行網際網路資訊服務。  MMC 對話方塊就會出現。  
  
3.  如果左邊窗格中列出一部以上的電腦，請選取應用程式程式碼所在的電腦。  
  
4.  IIS 版本是位於右邊窗格的 \[**版本**\] 一欄。  
  
## 請參閱  
 [Web 應用程式遠端偵錯的必要條件](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [系統需求](../debugger/aspnet-debugging-system-requirements.md)   
 [準備偵錯 ASP.NET](../debugger/preparing-to-debug-aspnet.md)   
 [偵錯 Web 應用程式和指令碼](../debugger/debugging-web-applications-and-script.md)
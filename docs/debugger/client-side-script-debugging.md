---
title: "用戶端指令碼偵錯 | Microsoft Docs"
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
  - "偵錯 [Visual Studio], 用戶端指令碼"
  - "用戶端指令碼, 偵錯"
ms.assetid: bb668527-2288-47bd-a6c8-cecbad76dde2
caps.latest.revision: 30
caps.handback.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 用戶端指令碼偵錯
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 偵錯工具提供完整的偵錯環境，以找出並修正 ASP.NET 頁面中用戶端指令碼的錯誤。  
  
## 開啟指令碼文件  
 您可以在 \[方案總管\] 查看伺服器端與用戶端指令碼文件清單並加以檢視。 您可以從 \[**方案總管**\] 開啟任何指令碼文件。 如需詳細資訊，請參閱[如何：檢視指令碼文件](../debugger/how-to-view-script-documents.md)。  
  
## 中斷點對應  
 在 Visual Studio 中，您無法直接對伺服器端程式碼進行偵錯，但是可以在伺服器端檔案內設定中斷點。 Visual Studio 會自動將中斷點對應至用戶端檔案內對應的位置，並且在用戶端程式碼中建立對應的中斷點。  
  
## 手動或自動附加至指令碼  
 若要開始在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 內偵錯指令碼，您必須將偵錯工具附加至要偵錯的指令碼。 這可以手動執行，也可以自動發生。  
  
 您可以使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 偵錯工具介面選擇要附加之執行中指令碼處理序，以手動方式附加至指令碼。 如需詳細資訊，請參閱[如何：附加至指令碼](../debugger/how-to-attach-to-script.md)。  
  
 偵錯工具會在發生下列其中一種情況時，自動附加至指令碼：  
  
-   您到達了在指令碼中設定的中斷點。  
  
-   您到達了指令碼中 VBScript 的 `Stop` 陳述式或 JScript 的 `debugger` 陳述式。  
  
-   瀏覽器或伺服器遇到了指令碼中的語法或執行階段錯誤。 發生這種情況時會出現對話方塊，其中含有開始進行偵錯的選項。  
  
 當您以手動方式附加至指令碼時，指令碼處理序會繼續執行，直到由於某種未知的原因而暫止為止。 您可以選擇 \[**偵錯**\] 功能表上的 \[**中斷**\] 來暫止指令碼處理序。  
  
 當偵錯工具自動附加至指令碼時，指令碼會在中斷點所在的那一行、`Stop` 陳述式或 `debugger` 陳述式、發生錯誤時，或您選擇要在 Internet Explorer 內啟動偵錯的所在點暫止。  
  
 此時，您可以使用一般偵錯工具的功能開始偵錯。 例如，您可以使用 \[**步驟**\] 命令，繼續逐行執行程式碼。 您可以使用 \[**呼叫堆疊**\] 視窗來檢視和控制指令碼流程。 您可以使用 \[變數\] 視窗或 \[**即時運算**\] 視窗來檢視或變更變數和屬性。  
  
## 增強型指令碼偵錯錯誤訊息  
 Visual Studio 針對一般指令碼偵錯問題提供了增強的錯誤訊息。 除非您以手動方式附加至 Internet Explorer，否則不會顯示這些錯誤訊息。 如果您在 Internet Explorer 自動開啟時發生錯誤，請嘗試以手動方式附加，以便查看錯誤訊息。  
  
## 偵錯 AJAX 指令碼應用程式  
 啟用 AJAX 功能的 Web 應用程式會使用大量指令碼，在偵錯時特別困難。 如需 AJAX 偵錯技術的詳細資訊，請參閱  
  
 [Debugging and Tracing Ajax Applications Overview](../Topic/Debugging%20and%20Tracing%20Ajax%20Applications%20Overview.md).  
  
## 請參閱  
 [偵錯 ASP.NET 和 AJAX 應用程式](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [指令碼偵錯的限制](../debugger/limitations-on-script-debugging.md)   
 [變數視窗](../Topic/Variable%20Windows.md)   
 [即時運算視窗](../ide/reference/immediate-window.md)   
 [Debugging and Tracing Ajax Applications Overview](../Topic/Debugging%20and%20Tracing%20Ajax%20Applications%20Overview.md)
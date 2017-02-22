---
title: "如何：偵錯 ASP.NET 例外狀況 | Microsoft Docs"
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
  - "ASP.NET, 例外狀況"
  - "偵錯 [Visual Studio], ASP.NET 例外狀況"
  - "例外狀況, ASP.NET"
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：偵錯 ASP.NET 例外狀況
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在開發強固的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式時，偵錯例外狀況是很重要的部分。  如需如何偵錯例外狀況的一般資訊，請參閱[使用偵錯工具管理例外狀況](../debugger/managing-exceptions-with-the-debugger.md)。  
  
 若要偵錯未處理的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 例外狀況，您必須確定偵錯工具會因為這些例外狀況而停止。  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 執行階段擁有最上層例外狀況處理常式。  因此，偵錯工具預設為絕不會在未處理的例外狀況中斷。  若要在擲回例外狀況時中斷偵錯工具，您必須在 \[**例外狀況**\] 對話方塊中，為該特定例外狀況選取 \[**例外狀況為下列時中斷: Thrown**\] 設定。  
  
 如果您已啟用 Just My Code，而當 .NET Framework 方法或其他系統程式碼擲回例外狀況時，\[**例外狀況為下列時中斷: Thrown**\] 則不會導致偵錯工具立即中斷，  而是直到偵錯工具叫用非系統程式碼後才會停止執行。  因此，您不需要在發生例外狀況時，逐步執行系統程式碼。  
  
 Just My Code 提供另一個更有用的選項：\[**例外狀況為下列時中斷: User\-unhandled**\]。  如果為例外狀況選擇這個設定，偵錯工具則會在使用者程式碼中斷執行 \(但是只有在使用者程式碼並未攔截和處理例外狀況時\)。  因為這個處理常式是在非使用者程式碼中，所以這個設定會取消最上層 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 例外狀況處理常式的效果。  
  
### 若要使用 Just My Code 啟用 ASP.NET 例外狀況的偵錯  
  
1.  在 \[**偵錯**\] 功能表上，按 \[**例外狀況**\]。  
  
     \[**例外狀況**\] 對話方塊隨即出現。  
  
2.  在 \[**Common Language Runtime 例外狀況**\] 資料列中，選取 \[**擲回**\] 或 \[**使用者未處理**\]。  
  
     若要使用 \[**使用者未處理**\] 設定，則必須啟用 \[**Just My Code**\]。  
  
### 若要使用 ASP.NET 例外狀況處理的最佳作法  
  
-   對於您可以預期會發生例外狀況並知道如何處理的程式碼，請將 `try … catch` 區塊置於此程式碼周圍。  例如，如果應用程式正在呼叫 XML Web Service 或直接呼叫 SQL Server 時，這段程式碼則應該是在 \[**try … catch**\] 區塊中，因為許多例外狀況可能會發生。
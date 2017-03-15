---
title: "錯誤：使用者無法執行預存程序 sp_enable_sql_debug | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.sqlde_accessdenied"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 11957495-c238-4cc5-8937-e4026f5e10e1
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 錯誤：使用者無法執行預存程序 sp_enable_sql_debug
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

預存程序 sp\_enable\_sql\_debug 無法在伺服器上執行。  可能的原因如下：  
  
-   連接問題。  您需要穩定的連接到伺服器。  
  
-   沒有必要的伺服器使用權限。  若要在 SQL Server 2005 上進行偵錯，執行 Visual Studio 的帳戶和用來連接至 SQL Server 的帳戶都必須是系統管理員角色的成員。  用來連接至 SQL Server 的帳戶就是您的 Windows 使用者帳戶 \(如果您使用 Windows 驗證\)，或具有使用者 ID 和密碼的帳戶 \(如果您使用 SQL 驗證\)。  
  
 如需詳細資訊，請參閱 [How to: Set SQL Server Permissions for Debugging](http://msdn.microsoft.com/zh-tw/84e088d0-0409-41d4-841b-f5d4b0fda414)。  
  
## 請參閱  
 [How to: Set SQL Server Permissions for Debugging](http://msdn.microsoft.com/zh-tw/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Setting Up SQL Debugging](http://msdn.microsoft.com/zh-tw/3db09e68-edcc-42de-9c22-4e97cfd55ab3)
---
title: "Web 控制項程式庫 (Managed 程式碼) | Microsoft Docs"
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
  - "偵錯 [Visual Studio], Web 控制項程式庫"
  - "偵錯 DLL"
ms.assetid: 2413883f-9e88-406d-b874-0ed743b75d40
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Web 控制項程式庫 (Managed 程式碼)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Web 控制項程式庫專案範本會建立 DLL。  因為類別庫是 DLL，所以您不能直接執行。  您必須建立嵌入該控制項的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 頁面。  如需詳細資訊，請參閱 [Web Control Library Template](http://msdn.microsoft.com/zh-tw/00666b07-71d2-4ace-a13c-cc130a3ce372)。  
  
### 若要偵錯 Web 控制項程式庫 \(方法 1\)  
  
1.  開啟現有的 Web 控制項程式庫專案，或建立一個新專案。  
  
2.  建立嵌入該控制項的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 頁面。  
  
3.  在裝載 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Test Harness 的網站中，建立名為 `/Code` 的子目錄。  
  
4.  將該控制項的原始程式碼複製到 `/Code` 子目錄。  
  
5.  在 `/Code` 子目錄中開啟原始程式碼，並設定中斷點。  
  
6.  開啟瀏覽器視窗，輸入指向 Test Harness 的 URL。  該控制項的中斷點會被叫用，然後您就可以開始偵錯。  
  
### 若要偵錯 Web 控制項程式庫 \(方法 2\)  
  
1.  在同一方案中建立主應用程式專案和 Web 控制項專案。  
  
2.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下主應用程式，然後再選擇 \[**加入參考**\]。  
  
3.  將參考加入至 Web 控制項專案。  
  
## 請參閱  
 [ASP.NET Web 應用程式](../debugger/debugging-preparation-aspnet-web-applications.md)
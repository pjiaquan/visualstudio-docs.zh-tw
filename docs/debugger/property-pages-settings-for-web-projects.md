---
title: "Web 專案的屬性頁設定 | Microsoft Docs"
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
  - "偵錯組建, 專案設定"
  - "偵錯組態, Web 專案"
  - "偵錯 [Visual Studio], Web 應用程式"
  - "偵錯 Web 應用程式, 專案設定"
  - "專案設定 [Visual Studio], 偵錯組態"
  - "專案 [Visual Studio], 偵錯組態"
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Web 專案的屬性頁設定
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以在 \[**屬性頁**\] 對話方塊中使用[偵錯和發行組態](../debugger/how-to-set-debug-and-release-configurations.md)中所討論的方法，變更網站偵錯組態的屬性設定。  下表顯示 \[**屬性頁**\] 對話方塊中，與偵錯工具相關的設定位置。  
  
### 組態屬性資料夾 \(起始選項分類\)  
  
|**設定**|**說明**|  
|------------|------------|  
|**起始動作**|標題，用以分類與應用程式啟動相關的選項。|  
|**使用目前的頁面**|指定目前的頁面為偵錯的起始點。|  
|**特定的頁面:**|指定您要開始偵錯的網頁。|  
|**起始外部程式:**|指定用來啟動您要偵錯的應用程式之命令。|  
|**命令列引數**|指定上述指定命令的引數。|  
|**工作目錄**|指定為程式偵錯時的工作目錄。  在 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 中，工作目錄預設為啟動應用程式的來源目錄：\\bin\\debug。|  
|**起始 URL**|指定您要偵錯的 Web 應用程式之位置。|  
|**不要開啟頁面。  等候來自外部應用程式的要求**|等候來自外部應用程式的要求。  這個選項不會啟動 Internet Explorer 或其他應用程式。  只會在應用程式呼叫時準備進行偵錯。|  
|**伺服器**|標題，用以分類與使用的伺服器相關的選項。|  
|**使用預設 Web 伺服器**|使用預設的 Web 伺服器。|  
|**使用自訂伺服器**|允許您輸入基礎 URL 用以做為伺服器。|  
|**偵錯工具**|標題，用以分類與要進行之偵錯類型相關的選項。|  
|**ASP.NET 偵錯**|啟用為 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 開發平台所撰寫的伺服器頁面偵錯。  您必須在 \[**起始 URL**\] 中指定 URL。|  
|**機器碼偵錯**|讓您可以從 Managed 應用程式偵錯原生 \(Unmanaged\) Win32 程式碼的呼叫。|  
|**SQL Server 偵錯**|允許 SQL Server 資料庫物件偵錯。|  
|**Silverlight 偵錯**|允許偵錯 Silverlight 元件。|  
  
## 請參閱  
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)
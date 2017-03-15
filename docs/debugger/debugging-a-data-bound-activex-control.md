---
title: "偵錯資料繫結的 ActiveX 控制項 | Microsoft Docs"
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
  - "ActiveX 控制項, 偵錯"
  - "控制項 [Visual Studio], ActiveX"
  - "資料繫結控制項, ActiveX"
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# 偵錯資料繫結的 ActiveX 控制項
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果您正在開發一個將繫結至資料來源控制項的 ActiveX 控制項，您可建立自己的容器應用程式，並使用該容器來偵錯 ActiveX 控制項。  
  
 例如，您可建立一個對話方塊架構的 MFC 應用程式，並將您的資料繫結控制項和資料來源控制項放在該對話方塊上。  您可將此 MFC 應用程式用於執行階段測試以及做為容器可執行檔，以便偵錯您的資料繫結 ActiveX 控制項。  
  
## 使用測試容器  
 如果您希望有一個可輕鬆修改的容器，以便在控制項或容器上支援不同的介面，請使用 ActiveX 測試容器 \(Test Container\) 做為偵錯工作階段的可執行檔。  在 ActiveX 測試容器中，按一下 \[**容器**\] 功能表內的 \[**選項**\]，以啟用不同的介面。  如需詳細資訊，請參閱[使用測試容器測試屬性和事件](/visual-cpp/mfc/testing-properties-and-events-with-test-container)。  
  
 如果您在偵錯時，需要逐步執行容器的程式碼，請使用容器的偵錯版本，或使用 ActiveX 測試容器的偵錯版本。  如需詳細資訊，請參閱 [TSTCON Sample: ActiveX Control Test Container](http://msdn.microsoft.com/zh-tw/72fa40ef-27d3-400c-813f-10b03236e600)。  
  
## 請參閱  
 [偵錯 COM 和 ActiveX](../debugger/com-and-activex-debugging.md)   
 [ActiveX 控制項](/visual-cpp/mfc/activex-controls)
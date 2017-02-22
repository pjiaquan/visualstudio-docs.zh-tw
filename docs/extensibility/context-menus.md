---
title: "內容功能表 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，舊版的內容功能表"
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 內容功能表
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

快顯功能表會顯示在使用者按一下滑鼠右鍵在 \[工作區的使用中的區域時，並清除 \[當使用者放開滑鼠按鈕。  
  
## 編輯器內容功能表  
 藉由攔截`ECMD_SHOWCONTEXTMENU`，您的語言服務可以控制將會顯示在編輯器中的快顯功能表。  若要顯示您自己的快顯功能表，請處理這個命令時傳遞至您<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>。  如果您不一定要處理這項指令，IDE 會顯示編輯器提供標準的快顯功能表。  您也可以控制每個資料標記為基礎的快顯功能表的內容。  如需詳細資訊，請參閱[使用舊版 API 中的文字標記](../extensibility/using-text-markers-with-the-legacy-api.md)和[攔截舊版語言服務命令](../extensibility/internals/intercepting-legacy-language-service-commands.md)。  
  
## 請參閱  
 [開發語言服務](../extensibility/internals/developing-a-legacy-language-service.md)   
 [擴充的功能表和命令](../extensibility/extending-menus-and-commands.md)
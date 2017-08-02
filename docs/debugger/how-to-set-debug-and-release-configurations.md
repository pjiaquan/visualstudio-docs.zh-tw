---
title: "如何：設定偵錯和發行組態 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.builds"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "組建組態, 偵錯"
  - "組建組態, 發行"
  - "組態, 發行"
  - "偵錯組建"
  - "偵錯組建, 變更組態設定"
  - "偵錯組建, 切換至發行組建"
  - "偵錯組態"
  - "偵錯 [Visual Studio], 偵錯組態"
  - "偵錯 [Visual Studio], 發行組態"
  - "專案 [Visual Studio], 偵錯組態"
  - "專案 [Visual Studio], 發行組態"
  - "發行組建, 變更設定"
  - "發行組建, 切換至偵錯組建"
  - "Visual Basic 專案, 偵錯與發行組建"
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
caps.latest.revision: 45
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 45
---
# 如何：設定偵錯和發行組態
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 專案針對您的程式具有不同的版本和偵錯組態。  依照名稱提示，您可以建置用來偵錯的偵錯版本，和最後發行散發的發行版本。  
  
 程式的偵錯組態會使用完整符號偵錯資訊，在沒有最佳化的情況下進行編譯。  最佳化會使偵錯變得複雜，因為原始程式碼與產生的指令之間關係較為複雜。  
  
 程式的發行組態不包含符號偵錯資訊，而且會完全最佳化。  依照所用的編譯器選項而定，PDB 檔案中可能會產生偵錯資訊。  如果您日後必須偵錯發行版本，建立 PDB 檔可能會非常有用。  
  
 如需建置組態的詳細資訊，請參閱[了解組建組態](../ide/understanding-build-configurations.md)。  
  
 您可以從 \[建置\] 功能表、從工具列，或在專案的屬性頁中變更組建組態。  專案屬性頁因語言而異。  下列程序示範如何從功能表和工具列變更組建組態。  如需如何變更不同語言專案中組建組態的詳細資訊，請參閱以下的＜相關主題＞一節。  
  
### 若要變更組建組態  
  
1.  從 \[建置\] 功能表：按一下 \[建置\] \/ \[組態管理員\]，然後選取 \[偵錯\] 或 \[發行\]。  
  
2.  在工具列的 \[方案組態\] 清單方塊中，選擇 \[偵錯\] 或 \[發行\]。  
  
     ![工具列組建組態](~/debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     在 Express 版中無法使用此工具列。  您可以使用 \[**建置方案 F6**\] 和 \[**開始偵錯 F5**\] 功能表項目選擇組態。  
  
## 請參閱  
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)   
 [C\+\+ 偵錯組態的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [C\# 偵錯組態的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic 偵錯組態的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [如何：建立和編輯組態](../ide/how-to-create-and-edit-configurations.md)   
 [Debug and Release Project Configurations](http://msdn.microsoft.com/zh-tw/0440b300-0614-4511-901a-105b771b236e)
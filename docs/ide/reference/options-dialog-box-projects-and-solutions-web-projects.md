---
title: "選項對話方塊、專案和方案、Web 專案 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Projects.WebProjects"
ms.assetid: ea813046-1ae6-4c9f-9784-dc41494101b9
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 選項對話方塊、專案和方案、Web 專案
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

設定 Web 專案將用來在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 內進行開發的 Web 伺服器。  若要存取此對話方塊，請按一下 \[**工具選項**\]。  展開 \[**專案和方案**\]，然後按一下 \[**Web 專案**\]。  
  
 根據預設，當您在 Visual Studio 中執行 Web 專案時 \(例如，使用 F5 或 Ctrl\+F5\)，Visual Studio 會使用 Visual Studio 程式開發伺服器。  如需詳細資訊，請參閱 [Web Servers in Visual Studio for ASP.NET Web Projects](http://msdn.microsoft.com/zh-tw/31d4f588-df59-4b7e-b9ea-e1f2dd204328)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊可用選項，以及功能表命令的名稱和位置，可能會與 \[說明\] 中描述的有所不同。  撰寫此說明頁時，主要是以 \[**Web 設定**\] 為考量。  若要檢視或變更您的設定，請在 \[**工具**\] 功能表上選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 設定  
 **將 64 位元版本的 IIS Express 用於網站和專案**  
 選取此選項會使用 IIS Express，而不使用 Visual Studio 程式開發伺服器。  如需詳細資訊，請參閱 [IIS Express 簡介](http://go.microsoft.com/?linkid=9747914)和 [IIS Express 概觀](http://go.microsoft.com/?linkid=9747915)。  此選項預設為停用。  
  
 **當錯誤清單中有錯誤時，在執行 Web 應用程式前提出警告**  
 如果已核取此方塊，當您嘗試執行 Web 應用程式，而它在編譯時並非沒有錯誤，則會出現警告。
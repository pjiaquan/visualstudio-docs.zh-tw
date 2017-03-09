---
title: "How to: Add an Application Configuration File to a C# Project | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "app.config files, adding to C# projects"
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# How to: Add an Application Configuration File to a C# Project
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

將應用程式組態檔 \(app.config 檔案\) 加入至 C\# 專案中，您可以自訂 Common Language Runtime 如何找出並載入組件檔。  如需應用程式組態檔的詳細資訊，請參閱[執行階段如何找出組件](../Topic/How%20the%20Runtime%20Locates%20Assemblies.md)。  
  
> [!NOTE]
>  Windows 市集中不支援 <xref:System.Configuration>。  因此，市集應用程式不包含 app.config 範本。  
  
 當您建置專案時，開發環境會自動複製到您的 app.config 檔案，將複製到符合項目的檔案名稱可執行檔，然後移動複製到 bin 目錄。  
  
### 若要將應用程式組態檔加入至 C\# 專案中  
  
1.  在功能表列上，選擇 \[**專案**\]\]，則 \[**加入新項目。**\]。  
  
     \[**加入新項目**\] 對話方塊隨即出現。  
  
2.  展開 \[**安裝**\]，展開 \[**Visual C\# 項目**\]，然後選取 \[**應用程式組態檔**\] 範本。  
  
3.  在 \[**名稱**\] 文字方塊中，輸入名稱，然後選擇 \[**加入**\] 按鈕。  
  
     名為 app.config 的檔案加入至您的專案。  
  
## 請參閱  
 [管理應用程式設定 \(.NET\)](../ide/managing-application-settings-dotnet.md)   
 [組態檔結構描述](../Topic/Configuration%20File%20Schema%20for%20the%20.NET%20Framework.md)   
 [設定應用程式](../Topic/Configuring%20Apps%20by%20using%20Configuration%20Files.md)   
 [How to: Configure an App to Target a .NET Framework Version](http://msdn.microsoft.com/zh-tw/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [Using the Visual C\# Development Environment](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)
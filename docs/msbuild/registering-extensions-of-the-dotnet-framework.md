---
title: "註冊 .NET Framework 的擴充功能 | Microsoft Docs"
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
  - "加入參考對話方塊，註冊 .NET Framework 的擴充功能"
  - "MSBuild，註冊 .NET Framework 的擴充功能"
  - ".NET Framework 擴充功能，註冊"
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 註冊 .NET Framework 的擴充功能
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以開發可擴充特定 .NET Framework 版本的組件。  若要讓組件出現在 Visual Studio 的 \[**加入參考**\] 對話方塊中，您必須將包含該組件的資料夾加入至系統登錄。  
  
 例如，假設 Trey Research 公司已開發可擴充 .NET Framework 4 的程式庫，並希望程式庫組件會在專案的目標設為 .NET Framework 4 時出現於 \[**加入參考**\] 對話方塊中。  同時，還會假設這些組件是在 32 位元電腦上執行的 32 位元組件，或是在 64 位元電腦上執行的 64 位元組件，以及假設這些組件將安裝在 C:\\TreyResearch\\Extensions4\\ 資料夾中。  
  
 註冊這個資料夾時，請使用右列機碼：HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework\\v4.0.21006\\AssemblyFoldersEx\\TreyResearch\\。  為機碼指定右列預設值：C:\\TreyResearch\\Extensions4。  
  
> [!NOTE]
>  .NET Framework 版本的組建編號可能會不同。  
  
 若要在 64 位元電腦上註冊 32 位元組件，請使用 Wow6432 節點，例如：HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.NETFramework\\v4.0.21006\\AssemblyFoldersEx\\TreyResearch\\。  
  
## 請參閱  
 [Visual Studio 整合](../msbuild/visual-studio-integration-msbuild.md)
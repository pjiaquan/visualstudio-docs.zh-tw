---
title: "MSBuild Response Files | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "response files, MSBuild"
  - "MSBuild, response files"
  - "MSBuild, .rsp files"
  - ".rsp files"
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
caps.latest.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 3
---
# MSBuild Response Files
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

回應 \(.rsp\) 檔是包含 MSBuild.exe 命令列參數的文字檔，  每個參數可位於不同行，或者所有參數可在同一行。  註解行前面會有 **\#** 符號。  **@** 參數用於傳遞其他回應檔給 MSBuild.exe。  
  
 自動回應檔是一個特殊的 .rsp 檔案，MSBuild.exe 在建置專案時會自動使用它。  這個檔案 MSBuild.rsp 必須位於與 MSBuild.exe 相同的目錄內，否則會找不到此檔案。  您可以編輯這個檔案，以指定要傳遞給 MSBuild.exe 的預設命令列參數。  例如，如果您每次在建置專案時都使用相同的記錄器，便可以將 **\/logger** 參數加到 MSBuild.rsp 中，如此一來，MSBuild.exe 每次在建置專案時便會使用此記錄器。  
  
## 請參閱  
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)
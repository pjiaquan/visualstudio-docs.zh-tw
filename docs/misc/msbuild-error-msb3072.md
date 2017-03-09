---
title: "MSBuild 錯誤 MSB3072 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.Exec.MissingCommandError"
helpviewer_keywords: 
  - "MSB3072"
ms.assetid: c8468e1c-d8c7-441c-b274-123ac856f147
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3072
**"Exec" 工作需要有命令才能執行。**  
  
 `Command` 屬性是 `Exec` 工作的必要屬性。  
  
### 若要更正這個錯誤  
  
1.  在專案檔中，指定 `Exec` 工作的 `Command` 屬性。  
  
## 請參閱  
 [Exec Task](../msbuild/exec-task.md)   
 [工作](../msbuild/msbuild-tasks.md)
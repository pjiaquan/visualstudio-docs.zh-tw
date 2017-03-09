---
title: "MSBuild 錯誤 MSB4140 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB4140"
ms.assetid: 13546558-4ed4-44c2-89a6-f69a2b43ed07
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB4140
**MSB4140: 指定的預設工具版本不在登錄中，也不在組態檔中。**  
  
 專案沒有指定預設 `ToolsVersion` 值。  因此，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 不知道要使用哪一個值。  
  
### 若要更正這個錯誤  
  
-   確定在登錄中定義工具組的位置或在組態檔 \(例如 msbuild.exe.config\) 中，已指定 `DefaultToolsVersion` 值。  
  
## 請參閱  
 [標準和自訂工具組的組態](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [其他資源](../msbuild/additional-msbuild-resources.md)
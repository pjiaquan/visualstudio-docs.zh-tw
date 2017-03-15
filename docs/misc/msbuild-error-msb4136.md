---
title: "MSBuild 錯誤 MSB4136 | Microsoft Docs"
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
  - "MSB4136"
ms.assetid: 6f0543d3-f8c0-44e1-8748-8a71be599bf4
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB4136
**MSB4136: 從組態檔讀取資訊時發生錯誤。**  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 嘗試從 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 組態檔 \(msbuild.exe.config\) 讀取工具組資訊時，收到錯誤。  
  
### 若要更正這個錯誤  
  
-   確定組態檔無誤且語式正確 \(Well\-Formed\)。  例如，如果加入工具組來自訂 .config 檔，請檢查工具組定義。  
  
## 請參閱  
 [覆寫 ToolsVersion 設定](../msbuild/overriding-toolsversion-settings.md)   
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [其他資源](../msbuild/additional-msbuild-resources.md)
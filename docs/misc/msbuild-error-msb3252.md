---
title: "MSBuild 錯誤 MSB3252 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSB3252"
helpviewer_keywords: 
  - "MSB3252"
ms.assetid: 4e6982b8-84b3-4d21-94e1-05cc10bf1393
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3252
**MSB3252：專案擁有組件 \<name\> 的參考。  此組件不是 .NET Framework Client Profile 的一部分。  若沒有此參考，可能會發生編譯錯誤或執行階段錯誤。**  
  
 已呼叫組件或相依組件中的成員，該組件不是 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] 的一部分。  因此，無法解析此呼叫，也無法編譯應用程式。  
  
 如需 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] 的詳細資訊，請參閱[.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md)。  
  
### 若要更正這個錯誤  
  
-   從專案移除指定的組件參考，或以完整的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 為目標，而不要以 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] 子集程式庫為目標。  如需如何以完整的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 為目標的詳細資訊，請參閱 [如何：以 .NET Framework 版本為目標](../ide/how-to-target-a-version-of-the-dotnet-framework.md)。  
  
## 請參閱  
 [目標 Framework 和目標平台](../msbuild/msbuild-target-framework-and-target-platform.md)   
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [其他資源](../msbuild/additional-msbuild-resources.md)
---
title: "在建置大型專案時有效使用記憶體 | Microsoft Docs"
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
  - "快取 (MSBuild)"
  - "記憶體使用 (MSBuild)"
  - "msbuild, 有效率的記憶體使用建置大型的樹狀結構"
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 在建置大型專案時有效使用記憶體
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

大型專案通常包含許多子專案和其他相依性，而這些可能會在建置階段消耗大量的系統記憶體。  隨著可用的系統記憶體減少，系統效能也可能跟著降低。  舊版的 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案會保留在記憶體中，而在 3.5 版中會移除專案，但是會將建置結果保留在快取中，以供稍後擷取。  
  
 4.0 版會自動處理此記憶體管理，因此專案不必使用 `UnloadProjectsOnCompletion` 和 `UseResultsCache` 這類屬性。  
  
## 請參閱  
 [同時建置多個專案](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
---
title: "/Edit (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/Edit Devenv 參數"
  - "Devenv, /edit 參數"
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Edit (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的現有執行個體中開啟指定的檔案。  
  
## 語法  
  
```  
Devenv /edit [file1[ file2]]  
```  
  
## 引數  
 `file1`  
 選擇項。  這是要在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的現有執行個體中開啟的檔案。  如果沒有 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的執行個體，則以簡易視窗配置建立新的執行個體，並在新執行個體中開啟 `file1`。  
  
 `file2`  
 選擇項。  這是要在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的現有執行個體中開啟的一或多個其他檔案。  
  
## 備註  
 如果未指定檔案，而且 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 有現有的執行個體，則 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的現有執行個體會接收焦點。  如果未指定檔案，而且 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 沒有現有的執行個體，則以簡易視窗配置建立 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的執行個體。  
  
 如果 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的現有執行個體在強制回應狀態中 \(例如，已開啟 [&#91;選項&#93; 對話方塊](../../ide/reference/options-dialog-box-visual-studio.md)\)，則檔案將在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 結束強制回應狀態後於現有執行個體中開啟。  
  
## 範例  
 這個範例會在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的現有執行個體中開啟 `MyFile.cs`，如果還沒有 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的執行個體，則在新執行個體中開啟此檔案。  
  
```  
devenv /edit MyFile.cs  
```  
  
## 請參閱  
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
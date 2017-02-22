---
title: "MSBuild 特殊字元 | Microsoft Docs"
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
  - "逸出"
  - "逸出字元"
  - "MSBuild 逸出字元"
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild 特殊字元
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 保留某些字元，以供特定情況下的特殊用途。  如果要在這些字元保留的情況下使用做為常值，唯一方法就是將字元逸出。  例如，星號只有在項目定義的 `Include` 和 `Exclude` 屬性以及 `CreateItem` 的呼叫中具有特殊的意義。  如果您要星號在這些情況下顯示為星號，就必須將之逸出。  其他情況下，則只需在想要的位置輸入星號即可。  
  
 若要存取特殊字串，請使用 %*xx* 語法，其中 *xx* 代表 ASCII 字元的十六進位值。  如需詳細資訊，請參閱 [如何：在 MSBuild 中逸出特殊字元](../msbuild/how-to-escape-special-characters-in-msbuild.md)。  
  
## 特殊字元  
 下表列出 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 的特殊字元：  
  
|**字元**|**ASCII**|**保留用途**|  
|------------|---------------|--------------|  
|%|%25|參考中繼資料|  
|$|%24|參考屬性|  
|@|%40|參考項目清單|  
|'|%27|條件與其他運算式|  
|;|%3B|清單分隔符號|  
|?|%3F|`Include` 和 `Exclude` 屬性中的檔名萬用字元|  
|\*|%2A|`Include` 和 `Exclude` 屬性中檔名使用的萬用字元|  
  
## 請參閱  
 [進階概念](../msbuild/msbuild-advanced-concepts.md)   
 [項目](../msbuild/msbuild-items.md)
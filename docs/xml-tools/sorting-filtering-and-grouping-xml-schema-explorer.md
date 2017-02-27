---
title: "排序、篩檢與群組 (XML 結構描述總管) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# 排序、篩檢與群組 (XML 結構描述總管)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主題描述可透過 XML 結構描述總管工具列上的 \[**排序、篩選與群組選項**\] 功能表使用的選項。  
  
## 篩選選項  
 以下是可用的篩選選項。根據預設，\[**顯示命名空間**\] 和 \[**顯示結構描述檔案**\] 選項會處於已選取狀態。  
  
-   \[**顯示命名空間**\]。  
  
-   \[**顯示結構描述檔案**。  
  
-   **顯示撰寫 \(sequence\/choice\/all\)**\]。  
  
## 排序選項  
 以下是可用的排序選項。預設值為 \[**依類型排序**\]。排序依據選項不適用於檔案和命名空間。  
  
-   \[**依類型排序**\]。  
  
-   \[**依名稱排序**\]。  
  
-   \[**文件順序**\]。  
  
### 依類型排序  
 選取 \[**依類型排序**\] 選項時，全域節點都會依照下列順序排序。然後，節點會在每個群組內部依字母順序排序。  
  
1.  `import` 節點。  
  
2.  `include` 節點。  
  
3.  `redefine` 節點。  
  
4.  `attribute` 節點。  
  
5.  `attributeGroup` 節點。  
  
6.  `complexType` 節點。  
  
7.  `simpleType` 節點。  
  
8.  `element` 節點。  
  
9. `group` 節點。  
  
### 依名稱排序  
 選取 \[**依名稱排序**\] 選項時，全域節點都會依照下列順序排序：  
  
1.  `import` 節點 \(依照命名空間的字母順序\)。  
  
2.  `include` 節點 \(依照 `schemaLocation` 屬性的字母順序\)。  
  
3.  `redefine` 節點 \(依照 `schemaLocation` 屬性的字母順序\)。  
  
4.  其他全域節點 \(依照字母順序\)。  
  
### 文件順序  
 當您選取 \[**顯示結構描述檔案**\] 選項時，才能使用 \[**文件順序**\] 選項。選取 \[**文件順序**\] 之後，全域節點就會依照它們出現在結構描述檔案中的順序顯示。  
  
## 持續排序\/篩選選項  
 無論變更設定時開啟哪一個方案或檔案，排序、篩選與群組選項都會儲存至每位使用者的登錄。
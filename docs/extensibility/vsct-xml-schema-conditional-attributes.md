---
title: "VSCT XML 結構描述條件式屬性 | Microsoft Docs"
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
  - "VSCT XML 結構描述項目、 條件式屬性"
  - "條件式屬性 (VSCT XML 結構描述)"
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# VSCT XML 結構描述條件式屬性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

條件式屬性可能會套用至所有清單和項目。 邏輯運算子和符號擴充運算式評估為 true 或 false。 如果為 true，相關聯的清單或項目包含在產生的輸出中。  
  
 權杖的擴充功能可以通過其他語彙基元的擴充功能或常數。 Defined\(\) 函式用來測試是否已定義特定的名稱，即使它沒有任何值。  
  
 當條件屬性套用至清單時，條件被套用至清單中每個子元素。 如果子系項目本身包含條件屬性，然後其條件結合父運算式的 AND 運算。  
  
 1、 '1' 和 'true' 的值會評估為 true，而且 0、 '0' 和 'false' 會評估為 false。  
  
## 運算子  
 下列運算子可用來評估條件運算式。  
  
|運算子|定義|  
|---------|--------|  
|\(,\)|群組|  
|\!|邏輯 NOT|  
|\<, \>, \<\=, \>\=, \=\=, \!\=|關係與相等|  
|和|布林值|  
|或|Boolean|  
  
## 範例  
  
```  
<Menu Condition="Defined(DEBUG)" … </Menu> <Menu Condition="%(SKU_MODE) = 'Demo'" … </Menu> <Menus Condition="Defined(DEBUG)"> <Menu … </Menu> </Menus> <Menus Condition="Defined(DEMO_SKU)"> <Menus Condition="!Defined(DEBUG)"> <Menu … </Menu> </Menus> <Menu … </Menu> </Menus> <Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU)) and !Defined(DEBUG)"> <Menu … </Menu> </Menus>  
```  
  
## 請參閱  
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
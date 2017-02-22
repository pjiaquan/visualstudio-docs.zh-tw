---
title: "於項目 | Microsoft Docs"
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
  - "於項目 (VSCT XML 結構描述)"
  - "VSCT XML 結構描述項目於"
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# 於項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此欄位可讓您指定各種功能表中出現的文字。 根據預設， `ButtonText` 元素會出現在功能表控制器。`ButtonText` 項目也會成為預設值，如果其他的文字欄位為空白。`ButtonText` 元素不能是空白，即使指定的文字欄位。  
  
## 語法  
  
```  
<ButtonText>My Command</ButtonText>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[字串的項目](../extensibility/strings-element.md)|群組文字項目，例如 `ButtonText` 和 `CommandName`。|  
  
## 文字值  
 文字值 `ButtonText` 項目提供的功能表項目、 組合和其他使用者介面 \(UI\) 項目所顯示的文字會顯示的文字。  
  
## 請參閱  
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
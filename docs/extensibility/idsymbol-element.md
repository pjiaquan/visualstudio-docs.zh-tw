---
title: "IDSymbol 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDSymbol 項目 (VSCT XML 結構描述)"
  - "IDSymbol，VSCT XML 結構描述項目"
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDSymbol 項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`IDSymbol` 項目包含 GUID:ID 組，表示功能表、 群組或命令的識別碼。 GUID 是來自父 `GuidSymbol` 項目。`IDSymbol` 項目具有 `name` 屬性，提供易記名稱的 id，包含在 `value` 屬性。  
  
## 語法  
  
```  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|name|必要項。 識別碼的符號名稱。|  
|值|必要項。 識別碼符號的數值識別碼值。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[GuidSymbol 項目](../extensibility/guidsymbol-element.md)|包含代表功能表、 群組或命令 GUID:ID 組的 GUID。 將 `IDSymbol` 項目設為群組。|  
  
## 備註  
 每個 `IDSymbol` 中的項目指定 `GuidSymbol` 項目必須具有唯一 `value`。 不過， `IDSymbol` 封裝中可以存在具有相同值的項目，前提是它們有不同的父項。  
  
## 請參閱  
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
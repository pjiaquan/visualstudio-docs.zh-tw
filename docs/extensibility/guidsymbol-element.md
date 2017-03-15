---
title: "GuidSymbol 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GuidSymbol，VSCT XML 結構描述項目"
  - "GuidSymbol 項目 (VSCT XML 結構描述)"
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# GuidSymbol 項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`GuidSymbol` 項目包含代表功能表、 群組或命令 GUID:ID 組的 GUID。 識別碼來自 `IDSymbol` 中的項目 `GuidSymbol` 項目。`GuidSymbol` 項目具有 `name` 屬性，提供好記名稱的 GUID，包含在 `value` 屬性。  
  
## 語法  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|name|必要項。 GUID 符號名稱。|  
|值|必要項。 GUID 符號的 GUID。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[IDSymbol 項目](../extensibility/idsymbol-element.md)|包含代表功能表、 群組或命令 GUID:ID 組識別碼。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[符號的項目](../extensibility/symbols-element.md)|群組 `GuidSymbol` .vsct 檔中的項目。|  
  
## 備註  
 .Vsct 檔通常包含三種 `GuidSymbol` 中的項目及其 `Symbols` 區段，一個用於封裝本身，一個命令集 \(功能表、 群組和封裝可產生命令的集合\)，而另一個按鈕和其他視覺化元件提供圖示的點陣圖。 每個 `IDSymbol` 中的項目指定 `GuidSymbol` 項目必須具有唯一 `value`。不過， `IDSymbol` 封裝中可以存在具有相同值的項目，前提是它們有不同的父項。  
  
## 請參閱  
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
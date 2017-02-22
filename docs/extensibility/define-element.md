---
title: "定義項目 | Microsoft Docs"
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
  - "VSCT XML 結構描述項目定義"
  - "定義項目 (VSCT XML 結構描述)"
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# 定義項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

定義的符號名稱和值組。 這個符號可以評估的條件式屬性。 如需詳細資訊，請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。 另請參閱 [符號的項目](../extensibility/symbols-element.md)。  
  
## 語法  
  
```  
<Define name="Mode" value="Standard" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|name|必要項。 符號名稱:<br /><br /> 名稱 \= 「 模式 」|  
|值|必要項。 符號的值:<br /><br /> 值 \= 「 標準 」|  
|條件|選擇項。 如需詳細資訊，請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[CommandTable 項目](../extensibility/commandtable-element.md)|定義代表命令的 VSPackage 提供整合式的開發環境 \(IDE\) 的所有項目。 例如，功能表項目、 功能表、 工具列和下拉式方塊。|  
  
## 範例  
  
```  
<Define name="DEMO_UI"/> <Define name="MODE" value="Standard"/>  
```  
  
## 請參閱  
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
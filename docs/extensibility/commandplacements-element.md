---
title: "CommandPlacements 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CommandPlacements"
helpviewer_keywords: 
  - "CommandPlacements 項目 (VSCT XML 結構描述)"
  - "CommandPlacements，VSCT XML 結構描述項目"
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# CommandPlacements 項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

CommandPlacements 項目群組 CommandPlacement 項目和其他 CommandPlacements 群組。  
  
 CommandPlacements 項目是選擇性的。 沒有命令、 群組或功能表，都必須包含在次要位置，如果您沒有在.vsct 檔中包含這一節。  
  
## 語法  
  
```  
<CommandPlacements>  
  <CommandPlacement>... </CommandPlacement>  
  <CommandPlacement>... </CommandPlacement>  
</CommandPlacements>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|條件|選擇項。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|CommandPlacements|群組 CommandPlacement 項目和其他 CommandPlacements 群組。|  
|[CommandPlacement 項目](../extensibility/commandplacement-element.md)|可讓按鈕、 群組及包含在一個以上的群組或功能表的功能表。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[CommandTable 項目](../extensibility/commandtable-element.md)|定義代表命令的所有項目。|  
  
## 範例  
  
```  
<CommandPlacements> <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions" priority="0x0300"> <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/> </CommandPlacement> </CommandPlacements>  
```  
  
## 請參閱  
 [CommandPlacement 項目](../extensibility/commandplacement-element.md)   
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
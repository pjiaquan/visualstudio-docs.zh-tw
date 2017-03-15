---
title: "VisibilityConstraints 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VisibilityConstraints"
helpviewer_keywords: 
  - "VisibilityConstraints，VSCT XML 結構描述項目"
  - "VisibilityConstraints 項目 (VSCT XML 結構描述)"
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# VisibilityConstraints 項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VisibilityConstraints 項目決定靜態群組的命令和工具列可見。 可見性會先受到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 不載入 VSPackage 的整合式的開發環境 \(IDE\)。  
  
## 語法  
  
```  
<VisibilityConstraints>  
  <VisibilityConstraint>... </VisibilityConstraint>  
  <VisibilityConstraint>... </VisibilityConstraint>  
</VisibilityConstraint>  
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
|[VisibilityItem 項目](../extensibility/visibilityitem-element.md)|決定命令和工具列的靜態的可見性。|  
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|決定靜態群組的命令和工具列可見。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[CommandTable 項目](../extensibility/commandtable-element.md)|定義代表 VSPackage 會提供 IDE 的命令 \(例如，功能表項目、 功能表、 工具列和下拉式方塊\) 的所有項目。|  
  
## 範例  
  
```  
<VisibilityConstraints> <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget" context="guidNotViewSourceMode"/> </VisibilityConstraints>  
```  
  
## 請參閱  
 [VisibilityItem 項目](../extensibility/visibilityitem-element.md)   
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
---
title: "組合的項目 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "組合的項目 (VSCT XML 結構描述)"
  - "VSCT XML 結構描述項目組合"
ms.assetid: ef48d2d2-0c47-4f93-8cfe-52026b6c463e
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# 組合的項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

將 [下拉式項目](../extensibility/combo-element.md) 項目設為群組。  
  
## 語法  
  
```  
<Combos>  
  <Combo>... </Combo>  
  <Combo>... </Combo>  
</Combos>  
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
|[Combos Element](../extensibility/combos-element.md)|分組下拉式項目。|  
|[下拉式項目](../extensibility/combo-element.md)|定義會出現在下拉式方塊中的命令。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[Commands 元素](../extensibility/commands-element.md)|表示 VSPackage 工具列上的命令集合。|  
  
## 範例  
  
```  
<Combos> <Combo guid="guidWidgetPackage" id="cmdidInsertOptions" defaultWidth="100" idCommandList="cmdidGetInsertOptionsList"> <CommandFlag>DynamicVisibility</CommandFlag> <Strings> <ButtonText>Select Insert Options</ButtonText> </Strings> </Combo> <Combo guid="guidWidgetPackage" id="cmdidInsertOptions" priority="0x0500" type="DropDownCombo" defaultWidth="100" idCommandList="cmdidGetInsertOptionsList"> <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"> <CommandFlag>DynamicVisibility</CommandFlag> <Strings> <ButtonText>Select Insert Options</ButtonText> </Strings> </Combo> </Combos>  
```  
  
## 請參閱  
 [VSPackages 如何新增使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
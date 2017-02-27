---
title: "群組項目 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT XML 結構描述項目: 群組"
  - "群組項目 (VSCT XML 結構描述)"
ms.assetid: 740ca4ec-79fa-4b98-8f9a-2a137f9f7f98
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 群組項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包含定義的 VSPackage 的命令群組的項目。  
  
## 語法  
  
```  
<Groups>  
  <Group>... </Group>  
  <Group>... </Group>  
</Groups>  
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
|[群組項目](../extensibility/group-element.md)|代表單一命令群組。|  
|[Groups Element](../extensibility/groups-element.md)|包含定義的 VSPackage 的命令群組的項目。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[Commands 元素](../extensibility/commands-element.md)|表示 VSPackage 工具列上的命令集合。|  
  
## 範例  
  
```  
<Groups> <Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"> <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/> </Group> </Groups>  
```  
  
## 請參閱  
 [VSPackages 如何新增使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
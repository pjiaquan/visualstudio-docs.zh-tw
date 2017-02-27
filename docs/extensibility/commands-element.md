---
title: "Commands 元素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Commands"
helpviewer_keywords: 
  - "Commands 元素 (VSCT XML 結構描述)"
  - "VSCT XML 結構描述元素，但是命令"
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Commands 元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

表示 VSPackage 工具列上的命令集合。 集合可以有最多五個的各小節，如下所示: 功能表、 群組、 按鈕、 組合和點陣圖。  
  
 每個小節子項目，例如，\<\] 功能表 \> 會識別唯一的命令 ID 的 GUID 和數字識別項組。 GUID 識別的 「 命令集 」，而用來將邏輯上相關的命令。 VSPackage 應該定義它自己的命令集以避免與其他 VSPackages 所定義的命令 Id 衝突。  
  
## 語法  
  
```  
<Commands package="GuidMyPackage" >  
  <Menus>... </Menus>  
  <Groups>... </Groups>  
  <Buttons>... </Buttons>  
  <Combos>... </Combos>  
  <Bitmaps>... </Bitmaps>  
</Commands>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|封裝|識別提供命令的 VSPackage 的 GUID。<br /><br /> 例如，封裝 \="guidVsPackage1Pkg"。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[功能表項目](../extensibility/menus-element.md)|定義所有 VSPackage 實作的功能表。|  
|[群組項目](../extensibility/groups-element.md)|包含在 VSPackage 中定義的命令群組的項目。|  
|[按鈕項目](../extensibility/buttons-element.md)|分組按鈕項目。|  
|[點陣圖的項目](../extensibility/bitmaps-element.md)|分組點陣圖項目。|  
|[組合的項目](../extensibility/combos-element.md)|分組下拉式項目。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[CommandTable 項目](../extensibility/commandtable-element.md)|定義代表 VSPackage 會提供 IDE 的命令的所有項目。 可能的項目是功能表項目、 功能表、 工具列和下拉式方塊。|  
  
## 範例  
 下列範例示範如何使用 [Commands Element](../extensibility/commands-element.md)。  
  
```  
<Commands package="guidMyPackage"> <Menus> <Menu Condition="'%(DEBUG)' != 'true'" guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu" priority="0x0000" type="Menu"> <Annotation> <Documentation>this is an annotation</Documentation> <AppInfo> <CustomData> <CustomSubElement>Some data</CustomSubElement> </CustomData> </AppInfo> </Annotation> <CommandFlag>AlwaysCreate</CommandFlag> <Strings> <ButtonText>MainMenu</ButtonText> </Strings> </Menu> </Menus> <Commands>  
```  
  
## 請參閱  
 [VSPackages 如何新增使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
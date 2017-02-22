---
title: "點陣圖的項目 | Microsoft Docs"
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
  - "點陣圖，VSCT XML 結構描述項目"
  - "點陣圖項目 (VSCT XML 結構描述)"
ms.assetid: 74652e1b-fcfa-421b-aa9f-fbc081d3b476
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# 點陣圖的項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

將 [點陣圖的項目](../extensibility/bitmap-element.md) 項目設為群組。  
  
## 語法  
  
```  
<Bitmaps>  
  <Bitmap>... </Bitmap>  
  <Bitmap>... </Bitmap>  
</Bitmaps>  
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
|[Bitmaps Element](../extensibility/bitmaps-element.md)|分組點陣圖項目。|  
|[點陣圖的項目](../extensibility/bitmap-element.md)|定義點陣圖。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[Commands 元素](../extensibility/commands-element.md)|表示 VSPackage 工具列上的命令集合。|  
  
## 範例  
  
```  
<Bitmaps> <Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" /> <Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS" usedList="1, 2, 3, 4"/> </Bitmaps>  
```  
  
## 請參閱  
 [VSPackages 如何新增使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
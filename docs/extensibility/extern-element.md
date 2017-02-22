---
title: "Extern 項目 | Microsoft Docs"
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
  - "Extern"
helpviewer_keywords: 
  - "Extern，VSCT XML 結構描述項目"
  - "Extern 項目 (VSCT XML 結構描述)"
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Extern 項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Extern 項目會參考在編譯時期合併使用.vsct 檔的任何外部標頭 \(.h\) 檔。 要合併的檔案必須是指定給 VSCT 編譯器或所參考的 Include 路徑上 [包含項目](../extensibility/include-element.md)。 檔案可能是其他.vsct 檔案或 c \+ \+ 標頭檔。  
  
 標頭檔中的定義的格式必須為"\#define \[符號\] \[Value\]"的值可能另一個符號，如果先前已定義。 定義可用於條件陳述式的命令項目。 將捨棄未實際使用中的所有符號。  
  
 CommandTable Element  
Extern Element  
  
## 語法  
  
```  
<Extern href="stdidcmd.h" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|href|必要項。 標頭檔的路徑:<br /><br /> href\="stdidcmd.h 」|  
|條件|選擇項。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
|語言|選擇項。 所有的預設語言 [\< 字串 \>](../extensibility/strings-element.md) 命令表中的項目:<br /><br /> 語言 \="en\-我們 」|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|無。|無。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[CommandTable 項目](../extensibility/commandtable-element.md)|定義的所有項目代表命令 — 也就是功能表項目、 功能表、 工具列和下拉式方塊 — VSPackage 提供 ide。|  
  
## 範例  
  
```  
<?xml version="1.0" encoding="utf-8"?> <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10- 18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema"> <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/> … <Commands package="guidMyPackage"> </CommandTable>  
```  
  
## 請參閱  
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSPackages 如何新增使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
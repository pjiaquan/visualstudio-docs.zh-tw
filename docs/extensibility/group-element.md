---
title: "群組項目 | Microsoft Docs"
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
  - "VSCT XML 結構描述項目: 群組"
  - "群組項目 (VSCT XML 結構描述)"
ms.assetid: 69faee18-cbf4-470a-b952-c1919c583df8
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# 群組項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

定義 VSPackage 命令群組。  
  
## 語法  
  
```  
<Group guid="guidMyCommandSet" id="MyGroup" priority="0x101">  
  <Parent>... </Parent>  
</Group>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|guid|必要項。 GUID ID 的命令識別項的 GUID。|  
|id|必要項。 GUID ID 的命令識別項的識別碼。|  
|priority|選擇項。 數值，指定的優先權。|  
|條件|選擇項。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|父代|選擇項。 按鈕的父項目。|  
|註釋|選擇性註解。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[群組項目](../extensibility/groups-element.md)|包含定義的 VSPackage 的命令群組的項目。|  
  
## 範例  
  
```  
<Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"> <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/> </Group>  
```  
  
## 請參閱  
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
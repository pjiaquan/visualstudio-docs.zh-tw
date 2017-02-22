---
title: "按鍵組合的項目 | Microsoft Docs"
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
  - "KeyBindings"
helpviewer_keywords: 
  - "按鍵組合，VSCT XML 結構描述項目"
  - "按鍵組合的項目 (VSCT XML 結構描述)"
ms.assetid: 26a15d5c-ddea-4977-af7f-d795ff09c7ad
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# 按鍵組合的項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

按鍵組合的項目群組鍵組項目和其他按鍵組合群組。  
  
## 語法  
  
```  
<KeyBindings>  
  <KeyBinding>... </KeyBinding>  
  <KeyBinding>... </KeyBinding>  
</KeyBindings>  
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
|[KeyBinding 項目](../extensibility/keybinding-element.md)|指定命令的鍵盤快速鍵。|  
|[KeyBindings](../extensibility/keybindings-element.md)|群組鍵組項目和其他按鍵組合的群組。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[CommandTable 項目](../extensibility/commandtable-element.md)|定義代表命令的所有項目。|  
  
## 範例  
  
```  
<KeyBindings> <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget" editor="guidWidgetEditor" key1="VK_F5"/> <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget" editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/> </KeyBindings>  
```  
  
## 請參閱  
 [KeyBinding 項目](../extensibility/keybinding-element.md)   
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
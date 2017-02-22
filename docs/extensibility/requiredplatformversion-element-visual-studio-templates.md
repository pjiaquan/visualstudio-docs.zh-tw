---
title: "RequiredPlatformVersion 項目 (Visual Studio 樣板) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# RequiredPlatformVersion 項目 (Visual Studio 樣板)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定最小的專案範本正常運作所需的作業系統版本。 這個項目用於建立的專案範本 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 應用程式。  
  
 `RequiredPlatformVersion` 與作業系統的版本直接進行比較的值。 如果 `RequiredPlatformVersion` 高於作業系統版本中，範本不會出現在 **新的專案** 對話方塊。 若要指定的範本 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 或更高版本，請將 `RequiredPlatformVersion` 到 6.2.0。 若要指定的範本 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 或更高版本，請將 RequiredPlatformVersion 到 6.3.0。  
  
 指定範本 `RequiredPlatformVersion`\= 8 都與先前的客戶相容 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 範本。  
  
 VSTemplate  
TemplateData  
…..TargetPlatformName  
RequiredPlatformVersion  
  
## 語法  
  
```xml  
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>  
```  
  
## 屬性和項目  
 無。  
  
### 屬性  
 無。  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|指定專案範本的目標平台。|  
  
## 文字值  
 需要文字值。  
  
## 備註  
 此文字會指定此範本所需的最低作業系統版本。  
  
## 範例  
 這個範例會指定專案範本以 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 或更新版本為目標。  
  
```xml  
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <TargetPlatformName>Windows</TargetPlatformName>  
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>  
  
    </TemplateData>  
    <TemplateContent>  
  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 請參閱  
 [TargetPlatformName 項目 \(Visual Studio 樣板\)](../extensibility/targetplatformname-element-visual-studio-templates.md)   
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
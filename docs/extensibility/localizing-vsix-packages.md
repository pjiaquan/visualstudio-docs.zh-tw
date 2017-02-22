---
title: "當地語系化 VSIX 套件 | Microsoft Docs"
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
  - "當地語系化封裝"
  - "當地語系化延伸模組"
  - "當地語系化的部署"
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 當地語系化 VSIX 套件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以當地語系化 VSIX 套件所建立的每個目標語言 Extension.vsixlangpack 檔案，然後將它們放在正確的資料夾。 安裝當地語系化的封裝時，延伸模組的當地語系化的名稱會顯示，並顯示當地語系化的說明。 如果您提供當地語系化的授權檔案或指向當地語系化資訊的 URL，也會顯示它們。  
  
 如果內容 VSIX 套件包含 VSPackage 將功能表命令或其他 UI，請參閱 [當地語系化的功能表命令](../extensibility/localizing-menu-commands.md) 有關當地語系化新 UI 項目。  
  
## 目錄結構  
 當使用者安裝某個擴充功能， **擴充功能和更新** 檢查最上層資料夾，其名稱符合目標電腦的 Visual Studio 地區設定的 VSIX 套件。 如果 **擴充功能和更新** .vsixlangpack 的尋找檔案的資料夾中，以取代.vsixmanifest 檔案中的對應值的該檔案中的當地語系化的值。 正在安裝延伸模組時，會顯示這些值。 下列範例會顯示當地語系化成西班牙文 \(es ES\) 和法文 \(FR\-FR\) 的 VSIX 套件的目錄結構。  
  
 MyExtension.dll  
  
 Extension.vsixmanifest  
  
 \[Content\_Types\].xml  
  
 es\-ES  
  
 Extension.vsixlangpack  
  
 fr\-FR  
  
 Extension.vsixlangpack  
  
> [!NOTE]
>  VSIX 支援中的專案範本 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 產生 VSIX 資訊清單，並將它命名為 source.extension.vsixmanifest。 當 Visual Studio 建置專案時，會複製該檔案的內容到 Extension.VsixManifest VSIX 套件中。  
  
## Extension.vsixlangpack 檔案  
 Extension.vsixlangpack 檔案會遵循 [VSIX 語言組件的結構描述](../extensibility/vsx-language-pack-schema-reference.md)。 此結構描述具有 [VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md) 根項目，以及這些四個子元素︰ [LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md), ，[LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md), ，[MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md), ，和 [授權](../extensibility/license-element-vsix-language-pack-schema.md)。 這些子元素對應到 `Name`, ，`Description`, ，`MoreInfoURL`, ，和 `License` 子項目的 `Identifier` Extension.vsixmanifest 檔案項目。  
  
 當您建立 vsixlangpack 檔案時，您必須設定 `Include in Vsix` 屬性 `true`。 否則，會忽略安裝當地語系化的文字。  
  
#### 若要設定 Vsix 屬性中包含  
  
1.  在 **方案總管\] 中**, Extension.vsixlangpack 檔案中，按一下滑鼠右鍵，然後按 **屬性**。  
  
2.  在屬性方格中，按一下 \[ **Include in Vsix**, ，並將其值設定為 `true`。  
  
## 範例  
  
### 描述  
 下列範例會顯示相關 Extension.vsixmanifest 檔案，以及對應的 Extension.vsixlangpack 檔案西班牙文的部分。 如果 Visual Studio 電腦的地區設定目標設定為西班牙文語言套件中的值會取代從資訊清單的值。  
  
### 程式碼  
 \[\] Extension.vsixmanifest  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VSIX ...>  
  <Identifier ...>  
    <Name>Family Tree</Name>  
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>  
    <License>EULA.rtf</License>  
    <MoreInfoURL>http://www.contoso.com/products/FamilyTree.htm</MoreInfoURL>  
    ...  
  </Identifier>  
  <References .../>  
  <Content .../>  
</VSIX>  
```  
  
 \[\] Extension.vsixlangpack  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VsixLanguagePack Version="1.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema-lp/2010">  
  <LocalizedName>Arbol de Familia</LocalizedName>  
  <LocalizedDescription> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</LocalizedDescription>  
  <License>es\Eula.rtf</License>  
  <MoreInfoUrl> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfoUrl>  
</VsixLanguagePack>  
```  
  
## 請參閱  
 [VSIX LanguagePack 項目](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [VSIX 套件的剖析](../extensibility/anatomy-of-a-vsix-package.md)   
 [VSIX 專案範本](../extensibility/vsix-project-template.md)
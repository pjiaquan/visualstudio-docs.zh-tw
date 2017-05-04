---
title: "ProjectItem Element | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ProjectItem element"
ms.assetid: df588235-12a1-4798-bc56-ef81843de17f
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# ProjectItem Element
  表示 SharePoint 專案項目。  這是 .spdata 檔案必要的根項目。  
  
## 語法  
  
```  
<ProjectItem DefaultFile = "File that opens in the editor when you open the project item"  
    FeatureReceiverClass = "Class that implements a feature receiver for the project item"  
    FeatureReceiverAssembly = "Assembly that defines a feature receiver for the project item"  
    SupportedTrustLevels = "Trust levels that the project item supports"  
    SupportedDeploymentScopes = "Deployment scopes that the project item supports"  
    Type="Identifier for the project item">  
  <Files>...</Files>  
  <ProjectItemFolder>...</ProjectItemFolder>  
  <SafeControls>...</SafeControls>  
  <FeatureProperties>...</FeatureProperties>  
  <ExtensionData>...</ExtensionData>  
</ProjectItem>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|**DefaultFile**|選擇性 **xs:string** 屬性。<br /><br /> 當您在 \[**方案總管**\] 中開啟 SharePoint 專案項目時，會在 Visual Studio 編輯器中開啟之檔案的相對路徑 \(包含檔案名稱\)。  路徑相對於包含 .spdata 檔的資料夾。|  
|**FeatureReceiverClass**|選擇性 **xs:string** 屬性。<br /><br /> 這個 SharePoint 專案項目之功能接收器類別的完整名稱。  如需功能接收器的詳細資訊，請參閱[提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。|  
|**FeatureReceiverAssembly**|選擇性 **xs:string** 屬性。<br /><br /> 指定定義這個 SharePoint 專案項目之功能接收器的組件的完全名稱。  如需功能接收器的詳細資訊，請參閱[提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。  如需完整組件名稱的詳細資訊，請參閱[組件名稱](http://msdn.microsoft.com/library/8f8c2c90-f15d-400e-87e7-a757e4f04d0e)。|  
|**SupportedTrustLevels**|選擇性 **xs:string** 屬性。<br /><br /> 指定這個 SharePoint 專案項目支援的信任層級。  這個值可以是下列其中一個字串：Sandboxed、FullTrust 或 All。  All 值會同時指定 Sandboxed 和 FullTrust。<br /><br /> 在自訂 SharePoint 專案項目型別中，這個屬性的值會對應到您在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> 方法的實作中指派給 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> 屬性的值。  如果為這個屬性指定不同的值，Visual Studio 會覆寫該值，使該値指定您在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> 屬性中指定的相同信任層級。|  
|**SupportedDeploymentScopes**|選擇性 **xs:string** 屬性。<br /><br /> 指定這個 SharePoint 專案項目支援的部署範圍。  這個值是以逗號分隔的字串，其中包含一或多個下列字串：Farm、Site、Web、WebApplication 或 Package。  例如「Web, Site」。<br /><br /> 在自訂 SharePoint 專案項目型別中，這個屬性的值會對應到您在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> 方法的實作中指派給 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> 屬性的值。  如果為這個屬性指定不同的值，Visual Studio 會覆寫該值，使該値指定您在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> 屬性中指定的相同信任層級。|  
|**Type**|必要的 **xs:string** 屬性。<br /><br /> SharePoint 專案項目的識別項。  在自訂 SharePoint 專案項目類型中，識別項是傳遞至 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> 的字串。  如需詳細資訊，請參閱 [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。<br /><br /> 如需 Visual Studio 隨附之內建 SharePoint 專案項目 的識別項完整清單，請參閱[Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|選擇性項目。<br /><br /> 表示與 SharePoint 專案項目關聯之自訂資料項目的集合。<br /><br /> 您可以只包含一個 **ExtensionData** 項目。|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|選擇性項目。<br /><br /> 表示將「功能」部署至 SharePoint 時「功能」中所含屬性值的集合。<br /><br /> 您可以只包含一個 **FeatureProperties** 項目。|  
|[檔案](../sharepoint/files-element.md)|選擇性 **FileCollectionType** 項目。<br /><br /> 指定要以 SharePoint 專案項目部署的檔案，例如 Feature 項目檔案，以及相依非 SharePoint 專案的輸出檔案。<br /><br /> 您必須包含 **Files** 或 **ProjectItemFolder** 項目，但不可同時包含兩者。|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|選擇性 **ProjectItemFolderType** 項目。<br /><br /> 表示對應資料夾。<br /><br /> 您必須包含 **Files** 或 **ProjectItemFolder** 項目，但不可同時包含兩者。|  
|[SafeControls](../sharepoint/safecontrols-element.md)|選擇性項目。<br /><br /> 表示為了讓任何使用者可存取 SharePoint 網站上的任何 ASPX 頁面而指定為安全的 ASPX 控制項和 Web 組件集合。<br /><br /> 您可以只包含一個 **SafeControls** 項目。|  
  
### 父項目  
 無。  
  
## 項目資訊  
  
|||  
|-|-|  
|**命名空間**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**結構描述名稱**|SharePoint 專案項目結構描述|  
|**驗證檔**|ProjectItemModelSchema.xsd|  
|**可否空白**|否|  
  
## 請參閱  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  
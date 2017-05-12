---
title: "Saving Data in Extensions of the SharePoint Project System"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SharePoint project items, saving string data"
  - "project items [SharePoint development in Visual Studio], saving string data"
  - "projects [SharePoint development in Visual Studio], saving string data"
  - "SharePoint projects, saving string data"
ms.assetid: 903b9da7-2eea-404c-9a7a-7bc15cb90d6c
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Saving Data in Extensions of the SharePoint Project System
  擴充 SharePoint 專案系統時，您可以儲存 SharePoint 專案關閉後仍然存在的字串資料。  這種資料通常與特定專案項目或專案本身相關聯。  
  
 如果有不需要保存的資料，您可以將資料加入至實作 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> 介面的 SharePoint 工具物件模型中的任何物件。  如需詳細資訊，請參閱[Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)。  
  
## 儲存與專案項目關聯的資料  
 如果有與特定 SharePoint 專案項目關聯的資料，例如專案項目中加入的屬性值，您可以將資料儲存到專案項目的 .spdata 檔案。  若要這麼做，請使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> 物件的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> 屬性。  您加入至此屬性的資料會儲存在專案項目 \(Item\) 之 .spdata 檔案的 **ExtensionData** 項目 \(Element\) 中。  如需詳細資訊，請參閱 [ExtensionData Element](../sharepoint/extensiondata-element.md)。  
  
 下列程式碼範例會示範如何使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> 屬性來儲存在自訂 SharePoint 專案項目類型中定義的字串屬性值。  若要在完整的範例內容中查看這個範例，請參閱 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)。  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypeproperty.cs#14)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypeproperty.vb#14)]  
  
## 儲存與專案關聯的資料  
 如果有專案層級資料，例如 SharePoint 專案中加入的屬性值，您可以將資料儲存到專案檔 \(.csproj 檔案或 .vbproj 檔案\) 或專案使用者選項檔 \(.csproj.user 檔案或 .vbproj.user 檔案\)。  您選擇儲存資料的檔案取決於您要使用資料的方式：  
  
-   如果想要讓所有開啟 SharePoint 專案的開發人員都能使用資料，請將資料儲存到專案檔。  這個檔案永遠會簽入原始檔控制資料庫，因此其他簽出專案的開發人員都能使用這個檔案中的資料。  
  
-   如果只想要讓目前在 Visual Studio 中開啟 SharePoint 專案的開發人員使用資料，請將資料儲存到專案使用者選項檔。  這個檔案通常不會簽入原始檔控制資料庫，因此其他簽出專案的開發人員無法使用這個檔案中的資料。  
  
### 將資料儲存到專案檔  
 若要將資料儲存到專案檔，請將 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 物件轉換成 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 物件，然後使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> 方法。  下列程式碼範例會示範如何使用這個方法來將專案屬性值儲存到專案檔。  若要在完整的範例內容中查看這個範例，請參閱 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)。  
  
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../snippets/csharp/VS_Snippets_OfficeSP/spext_spcustomprjproperty/cs/customspproperty/customproperty.cs#3)]
 [!code-vb[SpExt_SPCustomPrjProperty#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_spcustomprjproperty/vb/customspproperty/customproperty.vb#3)]  
  
 如需將 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 物件轉換成 Visual Studio Automation 物件模型或整合物件模型中的其他類型的詳細資訊，請參閱[Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)。  
  
### 將資料儲存到專案使用者選項檔  
 若要將資料儲存到專案使用者選項檔，請使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 物件的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> 屬性。  下列程式碼範例會示範如何使用這個屬性來將專案屬性值儲存到專案使用者選項檔。  若要在完整的範例內容中查看這個範例，請參閱 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)。  
  
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../snippets/csharp/VS_Snippets_OfficeSP/spext_spcustomprjproperty/cs/customspproperty/customproperty.cs#2)]
 [!code-vb[SpExt_SPCustomPrjProperty#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_spcustomprjproperty/vb/customspproperty/customproperty.vb#2)]  
  
## 請參閱  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)  
  
  
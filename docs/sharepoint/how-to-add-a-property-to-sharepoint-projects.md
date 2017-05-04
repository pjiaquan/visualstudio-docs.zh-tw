---
title: "How to: Add a Property to SharePoint Projects | Microsoft Docs"
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
  - "projects [SharePoint development in Visual Studio], extending"
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint projects, extending"
ms.assetid: c5eb4900-c35f-490a-b856-bf167da2d293
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# How to: Add a Property to SharePoint Projects
  您可以使用專案擴充功能，將屬性加入至任何 SharePoint 專案。  當在 \[**方案總管**\] 中選取專案項目時，這個屬性就會出現在 \[**屬性**\] 視窗中。  
  
 下列步驟假設您已經建立專案擴充功能。  如需詳細資訊，請參閱 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。  
  
### 若要將屬性加入至 SharePoint 專案  
  
1.  定義類別，這個類別具有表示要加入至 SharePoint 專案的公用屬性。  如果想要加入多個屬性，您可以在同一類別或不同類別中定義所有屬性。  
  
2.  在您的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 實作 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> 方法中，處理 *projectService* 參數的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> 事件。  
  
3.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> 事件的事件處理常式中，將屬性類別的執行個體加入至事件引數參數的 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> 集合。  
  
## 範例  
 下列程式碼範例會示範如何將兩個屬性加入至 SharePoint 專案。  一個屬性會在專案使用者選項檔 \(.csproj.user 檔案或 .vbproj.user 檔案\) 中保存其資料。  另一個屬性會在專案檔 \(.csproj 檔案或 .vbproj 檔案\) 中保存其資料。  
  
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../snippets/csharp/VS_Snippets_OfficeSP/spext_spcustomprjproperty/cs/customspproperty/customproperty.cs#1)]
 [!code-vb[SpExt_SPCustomPrjProperty#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_spcustomprjproperty/vb/customspproperty/customproperty.vb#1)]  
  
### 了解程式碼  
 為了確保在每次發生 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> 事件時都使用 `CustomProjectProperties` 類別的同一個執行個體，程式碼範例會在第一次發生此事件時，將屬性物件加入至專案的 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 屬性。  每當重新發生此事件時，程式碼都會擷取這個物件。  如需使用 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 屬性使資料與專案產生關聯的詳細資訊，請參閱[Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)。  
  
 為了保存屬性值的變更，屬性的 **set** 存取子會使用下列 API：  
  
-   `CustomUserFileProperty` 會使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> 屬性將其值儲存到專案使用者選項檔。  
  
-   `CustomProjectFileProperty` 會使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> 方法將其值儲存到專案檔。  
  
 如需在這些檔案中保存資料的詳細資訊，請參閱[Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。  
  
### 指定自訂屬性的行為  
 您可以在 \[**屬性**\] 視窗中定義自訂屬性 \(Property\) 的外觀和行為，方法是將屬性 \(Attribute\) 從 <xref:System.ComponentModel> 命名空間套用至屬性 \(Property\) 定義。  下列屬性在許多情節中都十分有用：  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>：指定在 \[**屬性**\] 視窗中出現的屬性名稱。  
  
-   <xref:System.ComponentModel.DescriptionAttribute>：指定當選擇該屬性時，在 \[**屬性**\] 視窗底部出現的說明字串。  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>：指定屬性的預設值。  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>：指定在 \[**屬性**\] 視窗中顯示的字串與非字串屬性值之間的自訂轉換。  
  
-   <xref:System.ComponentModel.EditorAttribute>：指定用來修改屬性的自訂編輯器。  
  
## 編譯程式碼  
 這個範例需要參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.Shell  
  
-   Microsoft.VisualStudio.Shell.Interop  
  
-   Microsoft.VisualStudio.Shell.Interop.8.0  
  
-   System.ComponentModel.Composition  
  
## 部署擴充功能  
 若要部署擴充功能，請針對組件以及要與擴充功能一起散發的任何其他檔案建立 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 擴充功能 \(VSIX\) 套件。  如需詳細資訊，請參閱[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 請參閱  
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  
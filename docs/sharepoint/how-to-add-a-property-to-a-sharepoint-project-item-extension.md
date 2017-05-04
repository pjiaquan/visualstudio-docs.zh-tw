---
title: "How to: Add a Property to a SharePoint Project Item Extension | Microsoft Docs"
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
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: 4fd97ef2-86e7-4d92-8e34-5b0ec3cc43a0
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# How to: Add a Property to a SharePoint Project Item Extension
  您可以使用專案項目擴充功能，將屬性加入至 Visual Studio 中已安裝的任何 SharePoint 專案項目。  當在 \[**方案總管**\] 中選取專案項目時，這個屬性就會出現在 \[**屬性**\] 視窗中。  
  
 下列步驟假設您已經建立專案項目擴充功能。  如需詳細資訊，請參閱 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)。  
  
### 若要將屬性加入至專案項目擴充功能  
  
1.  定義類別，這個類別具有表示要加入至專案項目類型的公用屬性。  如果想要將多個屬性加入至專案項目類型，您可以在同一類別或不同類別中定義所有屬性。  
  
2.  在您的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 實作 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> 方法中，處理 *projectItemType* 參數的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> 事件。  
  
3.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> 事件的事件處理常式中，將屬性類別的執行個體加入至事件引數參數的 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> 集合。  
  
## 範例  
 下列程式碼範例示範如何將名為 \[**範例屬性**\] 的屬性加入至 \[事件接收器\] 專案項目。  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemextensionproperty.vb#8)]  
  
### 了解程式碼  
 為了確保在每次發生 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> 事件時都使用 `CustomProperties` 類別的同一個執行個體，程式碼範例會在第一次發生此事件時，將屬性物件加入至專案項目的 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 屬性。  每當重新發生此事件時，程式碼都會擷取這個物件。  如需使用 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 屬性使資料與專案項目產生關聯的詳細資訊，請參閱[Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)。  
  
 為了保存屬性值的變更，`ExampleProperty` 的 **set** 存取子會將新值儲存至與該屬性相關聯之 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> 物件的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> 屬性。  如需使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> 屬性來保存專案項目資料的詳細資訊，請參閱[Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。  
  
### 指定自訂屬性的行為  
 您可以在 \[**屬性**\] 視窗中定義自訂屬性 \(Property\) 的外觀和行為，方法是將屬性 \(Attribute\) 從 <xref:System.ComponentModel> 命名空間套用至屬性 \(Property\) 定義。  下列屬性在許多情節中都十分有用：  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>：指定在 \[**屬性**\] 視窗中出現的屬性名稱。  
  
-   <xref:System.ComponentModel.DescriptionAttribute>：指定當選擇該屬性時，在 \[**屬性**\] 視窗底部出現的說明字串。  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>：指定屬性的預設值。  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>：指定在 \[**屬性**\] 視窗中顯示的字串與非字串屬性值之間的自訂轉換。  
  
-   <xref:System.ComponentModel.EditorAttribute>：指定用來修改屬性的自訂編輯器。  
  
## 編譯程式碼  
 這些範例需要類別庫專案並參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 部署擴充功能  
 若要部署擴充功能，請針對組件以及要與擴充功能一起散發的任何其他檔案建立 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 擴充功能 \(VSIX\) 套件。  如需詳細資訊，請參閱[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 請參閱  
 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  
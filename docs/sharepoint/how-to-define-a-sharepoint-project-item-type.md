---
title: "How to: Define a SharePoint Project Item Type"
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
  - "SharePoint project items, defining your own types"
  - "project items [SharePoint development in Visual Studio], defining your own types"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: 18b56e7c-4efb-47a2-abfc-e9018ae38267
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# How to: Define a SharePoint Project Item Type
  如果您要建立自訂 SharePoint 專案項目，請定義專案項目類型。  如需詳細資訊，請參閱[Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)。  
  
### 若要定義專案項目類型  
  
1.  建立類別庫專案。  
  
2.  加入下列組件的參考：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  建立實作 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 介面的類別。  
  
4.  將下列屬性加入到類別：  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>.  此屬性可讓 Visual Studio 探索並載入 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 實作。  將 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 型別傳遞至屬性建構函式。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  在專案項目類型定義中，此屬性會指定新專案項目的字串識別項。  建議您使用 \<*公司名稱*\>.\<*功能名稱*\> 格式，以確保所有專案項目都有唯一的名稱。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>.  此屬性會指定在 \[**方案總管**\] 中顯示此專案項目的圖示。  此屬性是選用的；如果您未將屬性套用至類別，則 Visual Studio 會顯示專案項目的預設圖示。  如果您設定此屬性，請傳遞組件中內嵌的圖示或點陣圖的完整名稱。  
  
5.  在 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> 方法的實作中，使用 *projectItemTypeDefinition* 參數的成員來定義專案項目類型的行為。  這個參數是 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> 物件，可用來存取 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> 和 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> 介面中定義的事件。  若要存取專案項目類型的特定執行個體，請處理 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> 事件，例如 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> 和 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>。  
  
## 範例  
 下列程式碼範例示範如何定義簡單的專案項目類型。  當使用者將此類型的專案項目加入至專案時，該專案項目類型就會將訊息寫入 \[**輸出**\] 視窗和 \[**錯誤清單**\] 視窗。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/projectitemtype.cs#2)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/projectitemtype.vb#2)]  
  
 此範例會使用 SharePoint 專案服務，將訊息寫入 \[**輸出**\] 視窗和 \[**錯誤清單**\] 視窗。  如需詳細資訊，請參閱[Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)。  
  
## 編譯程式碼  
 這個範例需要參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 部署專案項目  
 若要讓其他開發人員使用您的專案項目，請建立專案範本或專案項目範本。  如需詳細資訊，請參閱[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
 若要部署專案項目，請針對組件、範本以及要與專案項目一起散發的任何其他檔案建立 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) 套件。  如需詳細資訊，請參閱[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## 請參閱  
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [逐步解說：使用專案範本建立網站欄專案項目 &#40;第 1 部分&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)  
  
  
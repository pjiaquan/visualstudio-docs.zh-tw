---
title: "Creating Item Templates and Project Templates for SharePoint Project Items"
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
  - "SharePoint project items, creating custom templates"
  - ".spdata files"
  - "projects [SharePoint development in Visual Studio], creating custom templates"
  - "SharePoint projects, creating custom templates"
  - "SharePoint development in Visual Studio, creating custom project and item templates"
  - "project items [SharePoint development in Visual Studio], creating custom templates"
ms.assetid: c95b5e35-76c4-4f0a-b645-0467ae683659
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Creating Item Templates and Project Templates for SharePoint Project Items
  定義自訂 SharePoint 專案項目類型時，可以將其與項目範本或專案範本相關聯，以便其他開發人員可以在 Visual Studio 中使用此專案項目。  您也可以為範本建立精靈。  
  
 例如， Visual Studio 不包含專案範本或項目範本加入的欄位加入至 SharePoint 網站。  您可以定義代表欄位的 SharePoint 專案項目類型，然後建構項目範本，以便讓其他開發人員將欄位項目加入至 SharePoint 專案。  或者，您可以建構專案範本，以便讓開發人員建立含有欄位項目的新 SharePoint 專案。在這兩種情況下，您也可以提供外觀的精靈當開發人員使用您的範本。  這個精靈可以向開發人員收集資訊來設定新的項目或專案。  
  
 項目範本和專案範本都是 .zip 檔案，其中包含 Visual Studio 用來建立專案項目或專案的檔案。  如需項目範本和專案範本之基本知識的詳細資訊，請參閱 [在 Visual Studio 中建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)。  
  
##  <a name="creatingitemtemplates"></a> 建立項目範本  
 當您為 SharePoint 專案項目建立項目範本時，會用到一些必要的檔案，以及某些專案項目類型可能用到的選擇性檔案。  如需示範如何定義 SharePoint 專案項目類型並為其建立項目範本的逐步解說，請參閱[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)。  
  
 下表列出為 SharePoint 專案項目建立項目範本時所需的檔案。  
  
|必要檔案|描述|  
|----------|--------|  
|.spdata 檔案|這是指定專案項目之內容和預設行為的 XML 檔案。  這個檔案必須包含在項目範本中。  如需 .spdata 檔案內容的詳細資訊，請參閱 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)。|  
|.vstemplate 檔案。|這個檔案提供 Visual Studio 顯示 \[**加入新項目**\] 對話方塊中的範本，以及從範本建立專案項目時所需的資訊。  這個檔案必須包含在項目範本中。  如需詳細資訊，請參閱[NIB: Visual Studio Template Metadata Files](http://msdn.microsoft.com/zh-tw/129d59b5-7f9c-4daf-9832-eaedb3c4c961)。|  
|實作 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 介面的 Visual Studio 擴充功能組件。|這個組件會定義專案項目的執行階段行為。  這個組件必須包含在項目範本的 VSIX 套件中。  如需詳細資訊，請參閱[Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)與[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。|  
  
 下表列出可包含在項目範本中一些最常見的選擇性檔案。  某些專案項目類型可能需要其他未列於此的檔案。  
  
|選擇性檔案|描述|  
|-----------|--------|  
|Elements.xml|「*功能項目*」\(Feature Element\) 檔案。  這個檔案會定義專案項目所建立之自訂的 UI 和行為。  每種類型的自訂 \(例如，清單執行個體、內容類型或自訂動作\) 都具有定義此檔案內容的不同結構描述。  如需詳細資訊，請參閱[建置組塊：功能](http://go.microsoft.com/fwlink/?LinkId=169183) \(英文\) 和[功能結構描述](http://go.microsoft.com/fwlink/?LinkId=169192) \(英文\)。|  
|Schema.xml|清單定義的結構描述檔案。  如需詳細資訊，請參閱[建置組塊：清單和文件庫](http://go.microsoft.com/fwlink/?LinkId=177792) \(英文\) 和 [Schema.xml](http://go.microsoft.com/fwlink/?LinkId=177793) \(英文\)。|  
|.webpart|「*Web 組件定義*」\(Web Part Definition\) 檔案。  這個檔案含有 Web 組件的屬性設定。  如需詳細資訊，請參閱[建置組塊：Web 組件](http://go.microsoft.com/fwlink/?LinkId=177791) \(英文\)。|  
|.ascx|ASP.NET UserControl 檔案。  這個檔案會定義視覺 Web 組件的 UI。|  
|.aspx|ASP.NET 網頁檔。  這個檔案含有定義應用程式頁面的 XML 標記。|  
|.cs 或 .vb 檔|這些程式碼檔案 \(例如，應用程式頁面、Web 組件或工作流程\) 會定義 SharePoint 自訂的行為，您可以從 Visual C\# 或 Visual Basic 程式碼存取 SharePoint 自訂所具有的程式設計模型。|  
  
## 建立專案範本  
 當您建立 SharePoint 專案範本時，會用到一些必要的檔案，以及某些專案類型可能用到的選擇性檔案。  SharePoint 專案通常至少會有一個 SharePoint 專案項目，  但這個項目並不是必要的。  例如，您可能會定義這樣一種 SharePoint 專案範本：僅用於部署其他專案中建立的 SharePoint 方案。  
  
 如需示範如何定義 SharePoint 專案項目類型並為其建立專案範本的逐步解說，請參閱[逐步解說：使用專案範本建立網站欄專案項目 &#40;第 1 部分&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)。  
  
 下表列出 SharePoint 專案範本中必須包含的檔案。  
  
|必要檔案|描述|  
|----------|--------|  
|.vstemplate 檔案|這個檔案提供 Visual Studio 顯示 \[**新增專案**\] 對話方塊中的範本，以及從範本建立專案時所需的資訊。  如需詳細資訊，請參閱[NIB: Visual Studio Template Metadata Files](http://msdn.microsoft.com/zh-tw/129d59b5-7f9c-4daf-9832-eaedb3c4c961)。|  
|.csproj 或 .vbproj 檔案|這是專案檔。  它會定義專案的內容和組態設定。|  
|Package.package|這個檔案會定義專案的部署套件。  使用「封裝設計工具」自訂專案的方案套件時，Visual Studio 會將與方案套件相關的資料儲存在此檔案中。<br /><br /> 建立自訂 SharePoint 專案範本時，我們建議您在 Package.package 檔案中只納入最少的必要內容，並使用與專案範本相關聯之擴充功能中 <xref:Microsoft.VisualStudio.SharePoint.Packages> 命名空間的 API 來設定方案套件。  這麼一來，即使以後 Package.package 檔案的結構有任何變動，您的專案範本也不會受到任何影響。  如需示範如何建立只有最少必要內容之 Package.package 檔案的範例，請參閱[逐步解說：使用專案範本建立網站欄專案項目 &#40;第 1 部分&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)。<br /><br /> 如果要直接修改 Package.package 檔案，則可以使用 %Program Files \(x86\)%\\Microsoft Visual Studio 11.0\\Xml\\Schemas\\PackageModelSchema.xsd 中的結構描述來驗證內容。|  
|Package.Template.xml|這個檔案針對從專案產生的 SharePoint 方案套件 \(.wsp\)，提供方案資訊清單檔 \(manifest.xml\) 的基準。  如果要指定不允許專案類型使用者變更的某些行為，則可以將內容加入至這個檔案。  如需詳細資訊，請參閱[建置組塊：方案](http://go.microsoft.com/fwlink/?LinkId=169186) \(英文\) 和[方案結構描述](http://go.microsoft.com/fwlink/?LinkId=177794) \(英文\)。<br /><br /> 從專案建置方案套件時，Visual Studio 會將 Package.package 與 Package.Template.xml 檔案的內容合併成方案資訊清單檔。  如需建置方案套件的詳細資訊，請參閱 [How to: Create a SharePoint Solution Package \(wsp\)](http://msdn.microsoft.com/zh-tw/b24be45c-e91d-49bb-afb0-7b265404214b)。|  
  
 下表列出可包含在專案範本中的選擇性檔案。  
  
|選擇性檔案|描述|  
|-----------|--------|  
|SharePoint 專案項目|您可以包含一個或多個定義 SharePoint 專案項目類型的 .spdata 檔案。  在專案範本的 VSIX 套件中所包含的擴充功能組件內，每個 .spdata 檔案都必須有相符的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 實作。  如需詳細資訊，請參閱[建立項目範本](#creatingitemtemplates)。<br /><br /> SharePoint 專案通常至少會有一個 SharePoint 專案項目，  但這個項目並不是必要的。|  
|*featureName*.feature|這個檔案會定義將用於分組數個專案項目，以進行部署的 SharePoint 功能。  使用「功能設計工具」自訂專案中的功能時，Visual Studio 會將與功能相關的資料儲存在此檔案中。  如果要將專案項目分組成不同的功能，則可以納入多個 .feature 檔案。<br /><br /> 建立自訂 SharePoint 專案範本時，我們建議您在每個 .feature 檔案中只納入最少的必要內容，並使用與專案範本相關聯之擴充功能中 <xref:Microsoft.VisualStudio.SharePoint.Features> 命名空間的 API 來設定功能。  如果這樣做，便會保護您的專案範本，使得 .feature 檔案結構日後不會遭到變更。  如需示範如何建立只有最少必要內容之 .feature 檔案的範例，請參閱[逐步解說：使用專案範本建立網站欄專案項目 &#40;第 1 部分&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)。<br /><br /> 如果要直接修改 .feature 檔案，則可以使用 %Program Files \(x86\)%\\Microsoft Visual Studio 11.0\\Xml\\Schemas\\FeatureModelSchema.xsd 中的結構描述來驗證內容。|  
|*featureName*.Template.xml|這個檔案針對從專案產生的每個功能，提供功能資訊清單檔 \(Feature.xml\) 的基準。  如果要指定不允許專案類型使用者變更的某些行為，則可以將內容加入至這個檔案。  如需詳細資訊，請參閱[建置組塊：功能](http://go.microsoft.com/fwlink/?LinkId=169183) \(英文\) 和 [Feature.xml](http://go.microsoft.com/fwlink/?LinkId=177795) \(英文\) 檔案。<br /><br /> 從專案建置方案套件時，Visual Studio 會將每對 *featureName*.feature 檔案與 *featureName*.Template.xml 檔案的內容合併成功能資訊清單檔。  如需建置方案套件的詳細資訊，請參閱 [How to: Create a SharePoint Solution Package \(wsp\)](http://msdn.microsoft.com/zh-tw/b24be45c-e91d-49bb-afb0-7b265404214b)。|  
  
## 為項目範本和專案範本建立精靈  
 在您定義 SharePoint 專案項目型別，並建立其與項目或專案範本之間的關聯後，您也可以建立精靈。  當開發人員使用項目範本將 SharePoint 專案項目加入至專案，或開發人員使用專案範本建立包含 SharePoint 專案項目的新專案時，精靈即會顯示。  精靈可用以向開發人員收集資訊，以及初始化新的 SharePoint 專案項目。  
  
 如需示範如何為項目範本和專案範本建立精靈的逐步解說，請參閱[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)和[逐步解說：使用專案範本建立網站資料行專案項目 &#40;第 2 部分&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。  
  
## 請參閱  
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [逐步解說：使用專案範本建立網站欄專案項目 &#40;第 1 部分&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [逐步解說：使用專案範本建立網站資料行專案項目 &#40;第 2 部分&#41;](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [在 Visual Studio 中建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)  
  
  
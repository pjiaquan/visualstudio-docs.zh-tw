---
title: "建立 SharePoint 的網站資料行、內容類型和清單 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.ListDesigner.ContentTypeSetting"
  - "VS.SharePointTools.ContentTypeDesigner.CommonPropertiesPage"
  - "VS.SharePointTools.ListDesigner.CreatingLists"
  - "VS.SharePointTools.ListDesigner.ListPage"
  - "VS.SharePointTools.ListDesigner.ViewPage"
  - "VS.SharePointTools.ListDesigner.CommonPropertiesPage"
  - "VS.SharePointTools.ContentTypeDesigner.ColumnsPage"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 9ceed263-3aec-41dc-8708-63cb37a08fa8
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# 建立 SharePoint 的網站資料行、內容類型和清單
  Visual Studio 為許多不同的基本 SharePoint 項目提供專案項目範本，包含 *清單* 和 *內容類型*，兩者都可以合併網站欄 \(或 *欄位*\)。  內容類型和清單的新設計工具讓您可以容易的建立這些項目。  
  
## 網站資料行  
 網站欄是您可以加入至 SharePoint 專案的其中一個最基本項目。  網站資料行表示資料的型別，例如電話號碼、註解、或是連絡人清單中連絡人的居住縣市。  
  
 新網站欄專案項目範本讓您比在舊版 Visual Studio 中更容易的建立網站欄。  在建立新的網站資料行之後，您可以修改在網站欄 Elements.xml 檔案中的 XML，以包含您想要的資訊，例如它的顯示名稱、資料型別的資訊和您想要在 SharePoint 中顯示的群組。  如需網站欄的詳細資訊，請參閱 [資料欄的簡介](http://go.microsoft.com/fwlink/?LinkId=224996)。  
  
## 內容類型和清單  
 內容類型和清單是 SharePoint 中經常使用的項目。  
  
 內容型別在 SharePoint 清單或文件庫中定義中繼資料、工作流程和項目分類的行為。  例如，您可以為連絡人清單或工作清單的資訊建立一個內容型別。  連絡人內容型別可能包含資料行 \(例如名稱、電子郵件、電話號碼和位址\)。  您在網站層級定義的內容類型與任何網站的清單或文件庫是沒有相依性的。  您可以在 SharePoint 網站上使用相同的內容類型搭配不同的清單或文件庫。  您也可以使用幾個內容類型搭配相同的清單或文件庫。  
  
 清單是您在 SharePoint 中可以與其他人共用的資訊集合。  清單由包含資料的資料行與欄所組成。  清單的範例包括：工作清單、連絡人清單，以及公告清單。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的新內容類型和清單設計工具，讓建立網站內容類型和清單比在舊版 Visual Studio 中更簡單而直覺。  UI 可讓您以視覺化及熟悉的方式建構內容類型和清單，並且讓您可以在清單排序和分組資料，以及使用群組標頭。  如需內容類型的詳細資訊，請參閱 [內容類型](http://go.microsoft.com/fwlink/?LinkId=224997)。  如需清單的詳細資訊，請參閱 [清單形式](http://go.microsoft.com/fwlink/?LinkId=224998) 和 [清單檢視](http://go.microsoft.com/fwlink/?LinkId=224999)。  
  
## 相關主題  
  
|標題|說明|  
|--------|--------|  
|[逐步解說：建立 SharePoint 的網站資料行、內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|示範如何建立用於自訂內容類型的網站欄。  這個內容類型之後可在自訂清單中使用。|  
  
## 請參閱  
 [開始在 SharePoint 2010 開發](http://go.microsoft.com/fwlink/?LinkId=225000)  
  
  
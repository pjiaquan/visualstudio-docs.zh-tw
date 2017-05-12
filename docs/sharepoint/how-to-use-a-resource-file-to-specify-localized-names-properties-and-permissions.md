---
title: "如何：使用資源檔來指定當地語系化名稱、屬性和使用權限 | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [Visual Studio 中的 SharePoint 開發], 當地語系化字串"
  - "BDC [Visual Studio 中的 SharePoint 開發], 屬性"
  - "BDC [Visual Studio 中的 SharePoint 開發], 資源檔"
  - "BDC [Visual Studio 中的 SharePoint 開發], 資源字串"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 當地語系化字串"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 屬性"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 資源檔"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 資源字串"
ms.assetid: 72bb744d-818b-4e5a-9da2-295412025680
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# 如何：使用資源檔來指定當地語系化名稱、屬性和使用權限
  藉由使用資源檔，您可以提供當地語系化名稱和定義屬性，或是套用權限在商務資料連接 \(BDC\) 模型中定義的物件。  若要指定這項資訊，請將 \[**商務資料連接資源**\] 項目加入至包含 \[**商務資料連接模型**\] 項目的專案。  然後編輯資源檔的 XML，以指定名稱、屬性和權限。  
  
### 若要在 SharePoint 專案中加入 BDC 資源檔  
  
1.  在 \[**方案總管**\] 中展開 SharePoint 專案的資料夾，然後選取包含 BDC 模型的資料夾。  
  
2.  在功能表列中，選擇 \[**專案**\]、\[**加入新項目**\]。  
  
3.  展開 \[**SharePoint**\] 節點，然後選取 \[**2010**\] 節點。  
  
4.  選取 \[**加入新項目**\] 對話方塊中的 \[**商務資料連接資源項目**\]。  
  
5.  在 \[**名稱**\] 方塊中，指定資源檔的名稱，然後選擇 \[**加入**\] 按鈕。  
  
     副檔名為 .bdcr 的資源檔隨即加入至專案並開啟以等待編輯。  
  
6.  加入 XML 以定義您要套用 BDC 模型的當地語系化名稱、屬性以及權限。  
  
     如需如何定義這些項目的詳細資訊，請參閱 [模型和資源檔](http://go.microsoft.com/fwlink/?LinkID=169283)。  
  
## 請參閱  
 [如何：將現有的 BDC 模型檔案加入至 SharePoint 專案](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [如何：建立 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)   
 [如何：在 BDC 功能中包含自訂組件](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [將商業資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  
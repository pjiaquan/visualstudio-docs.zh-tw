---
title: "工作流程中的表單支援"
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
  - "Visual Studio 中的 SharePoint 開發, 工作流程"
  - "工作流程 [Visual Studio 中的 SharePoint 開發]"
ms.assetid: 1706f6a2-ea84-4234-85ae-19feb8540507
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# 工作流程中的表單支援
  工作流程可使用四種類型的表單：關聯、初始、工作和修改。  這些表單類型可以根據 ASPX 表單或 InfoPath 表單。  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 針對特定表單提供的支援層級取決於幾個因素，下表將說明這些因素。  如需工作流程表單類型的詳細資訊，請參閱 MSDN 網站的 [工作流程內概觀](http://go.microsoft.com/fwlink/?LinkId=185228)。  
  
## XML 重構  
 當您將 ASPX 關聯或初始表單加入至 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 工作流程專案項目時，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會自動重構工作流程 Elements.xml 檔案中的 XML，如此一來，每當更新表單名稱或部署路徑或者刪除表單時，都能維持參考此關聯或初始表單之屬性的同步狀態。  但是，當您在工作流程中使用其他表單類型時 \(例如工作或修改表單\)，Elements.xml 檔案將不會重構。  
  
## 新的 Visual Studio 工作流程中的表單支援  
 下表列出在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中建立的工作流程內，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 對於 ASPX 或 InfoPath 表單上不同表單類型的支援。  
  
|表單類型|在 Visual Studio 中使用 ASPX 表單建立的工作流程|在 Visual Studio 中使用 InfoPath 表單建立的工作流程|  
|----------|----------------------------------------|--------------------------------------------|  
|關聯|-   可以使用 \[**工作流程關聯表單**\] 項目範本，將 ASPX 關聯表單加入至工作流程。<br />-   當加入、重新命名或刪除表單或者變更其部署路徑時，都會重構工作流程的 Elements.xml 檔案。<br />-   如需詳細資訊，請參閱[逐步解說：使用關聯與初始化表單建立工作流程](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)。|-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中沒有 InfoPath 關聯表單範本。<br />-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 與 InfoPath Designer 之間沒有整合。<br />-   工作流程的 Elements.xml 檔案不會進行重構。|  
|初始|-   可以使用 \[**工作流程初始表單**\] 項目範本，將 ASPX 初始表單加入至工作流程。<br />-   當加入、重新命名或刪除表單或者變更其部署路徑時，都會重構工作流程的 Elements.xml 檔案。<br />-   如需詳細資訊，請參閱[逐步解說：使用關聯與初始化表單建立工作流程](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)。|-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中沒有 InfoPath 關聯表單範本。<br />-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 與 InfoPath Designer 之間沒有整合。<br />-   工作流程的 Elements.xml 檔案不會進行重構。|  
|工作|-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中沒有可用的 ASPX 工作表單範本。  您必須建立應用程式頁面，並在其中加入程式碼。<br />-   工作流程的 Elements.xml 檔案不會進行重構。<br />-   如需詳細資訊，請參閱 [工作流程工作表單 \(SharePoint Foundation\)](http://go.microsoft.com/fwlink/?LinkId=187674)|-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中沒有 InfoPath 工作表單範本。<br />-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 與 InfoPath Designer 之間沒有整合。<br />-   工作流程的 Elements.xml 檔案不會進行重構。|  
|修改|-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中沒有可用的 ASPX 修改表單範本。  若要加入修改表單，您必須建立應用程式頁面，並在其中加入程式碼。<br />-   工作流程的 Elements.xml 檔案不會進行重構。  您必須適當地手動加以編輯。<br />-   如需詳細資訊，請參閱 [工作流程修改表單 \(SharePoint Foundation\)](http://go.microsoft.com/fwlink/?LinkId=187675)|-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中沒有 InfoPath 修改表單範本。<br />-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 與 InfoPath Designer 之間沒有整合。<br />-   工作流程的 Elements.xml 檔案不會進行重構。|  
  
## 匯入的 SharePoint 可重複使用的工作流程中的表單支援  
 下表列出匯入 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的 SharePoint 可重複使用的工作流程內，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 對於 ASPX 或 InfoPath 表單上不同表單類型的支援。  
  
|表單類型|可重複使用的工作流程，其中包含從 SharePoint Designer 匯入的 ASPX 表單。|可重複使用的工作流程，其中包含從 SharePoint Designer 匯入的 InfoPath 表單。|  
|----------|-------------------------------------------------------|-----------------------------------------------------------|  
|關聯|-   在工作流程的 Elements.xml 檔案中參考表單。<br />-   當重新命名或刪除表單或者變更其部署路徑時，都會重構工作流程的 Elements.xml 檔案。|-   表單已匯入，但並未在工作流程的 Elements.xml 中參考。<br />-   工作流程的 Elements.xml 檔案不會進行重構。|  
|初始|-   表單會在工作流程的 Elements.xml 檔案中由工作流程所參考。<br />-   當重新命名或刪除表單或者變更其部署路徑時，都會重構工作流程的 Elements.xml 檔案。|-   表單已匯入，但並未在工作流程的 Elements.xml 中參考。<br />-   工作流程的 Elements.xml 檔案不會進行重構。 **Note:**  必須加入及變更規則和屬性，此案例才能運作。|  
|工作|-   在工作流程的 Elements.xml 檔案中參考表單。<br />-   工作流程的 Elements.xml 檔案不會進行重構。|-   表單已匯入，但並未在工作流程的 Elements.xml 中參考。<br />-   工作流程的 Elements.xml 檔案不會進行重構。 **Note:**  必須加入及變更規則和屬性，此案例才能運作。|  
|修改|不適用。  ASPX 修改表單無法在 SharePoint Designer 中建立。|不適用。  InfoPath 修改表單無法在 SharePoint Designer 中建立，但是內建 SharePoint Server 工作流程除外，當匯出此工作流程時，它不會包含在 .wsp 檔案中。|  
  
## 請參閱  
 [逐步解說：使用關聯與初始化表單建立工作流程](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [建立 SharePoint 工作流程方案](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [從現有的 SharePoint 網站匯入項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)  
  
  
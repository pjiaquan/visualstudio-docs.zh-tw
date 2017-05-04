---
title: "如何：建立實體之間的關聯 | Microsoft Docs"
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
  - "AssociationGroupTool"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [Visual Studio 中的 SharePoint 開發], 關聯外部內容類型"
  - "BDC [Visual Studio 中的 SharePoint 開發], 實體之間的關聯"
  - "BDC [Visual Studio 中的 SharePoint 開發], 建立關聯"
  - "BDC [Visual Studio 中的 SharePoint 開發], 相關實體"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 關聯外部內容類型"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 實體之間的關聯"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 建立關聯"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 相關實體"
ms.assetid: 0c095df8-1f40-4c4d-9fed-e125a8429724
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# 如何：建立實體之間的關聯
  您可以藉由建立關聯的方式，定義商務資料連接 \(BDC\) 模型中實體之間的關聯性。  Visual Studio 會產生方法，為模型的消費者提供各個關聯的相關資訊。  這些方法可以由 SharePoint Web 組件、清單或自訂應用程式加以使用，以便在使用者介面 \(UI\) 中顯示資料關聯性。  
  
 您可以在 BDC 設計工具中建立兩種關聯類型，分別是以外部索引鍵為基礎的關聯，以及無外部索引鍵的關聯。  如需詳細資訊，請參閱[建立實體之間的關聯](../sharepoint/creating-an-association-between-entities.md)。  
  
### 若要在實體之間建立關聯  
  
1.  在\[**工具箱**\] 的 \[**BusinessDataConnectivity**\] 索引標籤中，選擇 \[**關聯**\] 項目。  
  
2.  在 \[BDC 設計工具\] 中選取來源實體，然後選擇目的實體。  
  
     \[**關聯編輯器**\] 隨即出現。  
  
3.  如果您要建立以外部索引鍵為基礎的關聯，請選取 \[**是外部索引鍵關聯**\] 核取方塊。  
  
    1.  在 \[**識別項對應**\] 資料表的 \[**來源 ID**\] 資料行中，選取 \[**欄位**\] 資料行中顯示在各個相符之型別描述元旁邊的識別項。  
  
         例如，在 \[**來源 ID**\] 資料行中，選取 `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` 型別描述元和 `ReadItem.salesOrder.SalesOrder.ContactID` 型別描述元旁的 `ContactID`。  
  
4.  如果您要建立無外部索引鍵的關聯，請清除 \[**是外部索引鍵關聯**\] 核取方塊。  
  
5.  選擇 \[**確定**\] 按鈕。  
  
6.  在 \[BDC 設計工具\] 上，來源實體和目的實體之間隨即出現一條表示關聯的線。  
  
     Visual Studio 會將關聯巡覽方法分別加入至目的實體和來源實體的服務類別。  如需關聯巡覽方法的詳細資訊，請參閱 [支援的作業](http://go.microsoft.com/fwlink/?LinkId=169286)。  
  
7.  在來源實體的關聯巡覽方法中，加入可傳回目的實體之集合的程式碼。  
  
8.  在目的實體的關聯巡覽方法中，加入可傳回相關來源實體的程式碼。  
  
     如需關聯巡覽方法的範例，請參閱[建立實體之間的關聯](../sharepoint/creating-an-association-between-entities.md)。  
  
## 請參閱  
 [建立實體之間的關聯](../sharepoint/creating-an-association-between-entities.md)   
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [如何：加入搜尋方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何：加入特定搜尋方法](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [如何：加入建立者方法](../sharepoint/how-to-add-a-creator-method.md)   
 [如何：加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)   
 [如何：加入更新者方法](../sharepoint/how-to-add-an-updater-method.md)   
 [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何：將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何：定義方法執行個體](../sharepoint/how-to-define-a-method-instance.md)   
 [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [逐步解說：使用商務資料在 SharePoint 中建立外部清單](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)  
  
  
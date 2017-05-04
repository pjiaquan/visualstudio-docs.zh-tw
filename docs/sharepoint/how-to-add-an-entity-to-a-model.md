---
title: "如何：將實體加入至模型 | Microsoft Docs"
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
  - "EntityTool"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [Visual Studio 中的 SharePoint 開發], 加入實體"
  - "BDC [Visual Studio 中的 SharePoint 開發], 實體"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 加入實體"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 實體"
ms.assetid: 139a6639-dabe-4e14-bb64-e5f4efb6f2fb
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# 如何：將實體加入至模型
  若要建立實體，請將實體從 Visual Studio 的 \[**工具箱**\] 加入至商務資料連接 \(BDC\) 設計工具上。  
  
### 若要在模型中新增實體  
  
1.  建立 BDC 專案或開啟現有的 BDC 專案。  如需詳細資訊，請參閱[建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
2.  在 \[**工具箱**\] 中，將**實體**控制項從 \[**BusinessDataCatalog**\] 群組加入至設計工具。  
  
     新實體隨即出現在設計工具中。  Visual Studio 會將 `<Entity>` 項目新增至專案內 BDC 模型檔案的 XML。  如需實體項目屬性的詳細資訊，請參閱 [實體](http://go.microsoft.com/fwlink/?LinkId=169296)。  
  
3.  在設計工具中，開啟實體的捷徑功能表，選擇 \[**新增**\]，然後選擇 \[**識別項**\]。  
  
     新識別項隨即出現在實體上。  
  
    > [!NOTE]  
    >  您可以在 \[**屬性視窗**\] 中變更實體名稱和識別項。  
  
4.  在類別中定義實體的欄位。  您可以使用物件關聯式設計工具 \(O\/R 設計工具\) 等其他工具將新類別加入至專案，也可以使用現有的類別。  下列範例顯示名為 Contact 的實體類別。  
  
     [!code-csharp[SP_BDC_Entity_Data_Class#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc_entity_data_class/cs/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc_entity_data_class/vb/bdcmodel1/contact.vb#1)]  
  
## 請參閱  
 [如何：加入建立者方法](../sharepoint/how-to-add-a-creator-method.md)   
 [如何：加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)   
 [如何：加入更新者方法](../sharepoint/how-to-add-an-updater-method.md)   
 [如何：加入搜尋方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何：加入特定搜尋方法](../sharepoint/how-to-add-a-specific-finder-method.md)  
  
  
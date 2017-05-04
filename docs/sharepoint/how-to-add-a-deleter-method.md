---
title: "如何：加入刪除者方法 | Microsoft Docs"
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
  - "BDC [Visual Studio 中的 SharePoint 開發], 刪除者"
  - "BDC [Visual Studio 中的 SharePoint 開發], 刪除資料"
  - "BDC [Visual Studio 中的 SharePoint 開發], 刪除實體執行個體"
  - "BDC [Visual Studio 中的 SharePoint 開發], 移除資料"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 刪除者"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 刪除資料"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 刪除實體執行個體"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 移除資料"
ms.assetid: 3362eaf4-5dc7-4450-9009-b296308ae61f
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# 如何：加入刪除者方法
  您可以將「*刪除者*」\(Deleter\) 方法加入至模型，讓使用者在 SharePoint 網站上刪除外部清單中的資料記錄。  如需詳細資訊，請參閱[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
### 若要建立刪除者方法  
  
1.  在 BDC 設計工具上，選取實體。  
  
2.  在功能表列上，選擇 \[**檢視**\]，\[**其他視窗**\]， \[**BDC 方法詳細資料**\]。  
  
     \[**BDC 方法詳細資料**\] 視窗隨即開啟。  如需這個視窗的詳細資訊，請參閱 [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)。  
  
3.  在 \[**加入方法**\] 清單中，選取 \[**建立刪除者方法**\]。  
  
     Visual Studio 會將下列項目加入至模型。  這些項目會顯示在 \[**BDC 方法詳細資料**\] 視窗中。  
  
    -   名為 **Delete** 的方法。  
  
    -   此方法的輸入參數。  
  
    -   此參數的型別描述元。  
  
    -   此方法的方法執行個體。  
  
     如需詳細資訊，請參閱[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
4.  在 \[**方案總管**\] 中，開啟針對實體所產生的服務程式碼檔案之捷徑功能表，然後選擇 \[**檢視程式碼**\]。  
  
     實體服務程式碼檔案會在程式碼編輯器中開啟。  如需實體服務程式碼檔案的詳細資訊，請參閱[建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
5.  將程式碼加入至刪除者方法以刪除一筆記錄。  下列範例會使用 SQL Server 的 AdventureWorks 範例資料庫來刪除銷售訂單項目。  
  
    > [!NOTE]  
    >  這個範例的方法使用了兩個輸入參數。  
  
    > [!NOTE]  
    >  將 `ServerName` 欄位的值替換成您的伺服器名稱。  
  
     [!code-csharp[SP_BDC#6](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderdetailservice.cs#6)]
     [!code-vb[SP_BDC#6](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderdetailservice.vb#6)]  
  
## 請參閱  
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [如何：加入搜尋方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何：加入特定搜尋方法](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [如何：加入建立者方法](../sharepoint/how-to-add-a-creator-method.md)   
 [如何：加入更新者方法](../sharepoint/how-to-add-an-updater-method.md)   
 [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何：將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何：定義方法執行個體](../sharepoint/how-to-define-a-method-instance.md)  
  
  
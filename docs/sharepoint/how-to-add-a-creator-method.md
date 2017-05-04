---
title: "如何：加入建立者方法 | Microsoft Docs"
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
  - "BDC [Visual Studio 中的 SharePoint 開發], 加入實體"
  - "BDC [Visual Studio 中的 SharePoint 開發], 加入實體執行個體"
  - "BDC [Visual Studio 中的 SharePoint 開發], 建立者"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 加入實體"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 加入實體執行個體"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 建立者"
ms.assetid: 52f0382f-10a0-4a51-83fe-6f22f4647df8
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# 如何：加入建立者方法
  建立者方法可將新資料加入至實體的資料來源。  使用者選擇位在以模型為基礎之清單功能區上的 \[**新增項目**\] 按鈕時，商務資料連接 \(BDC\) 服務就會呼叫這個方法。  如需詳細資訊，請參閱[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
### 若要加入建立者方法  
  
1.  在 BDC 設計工具上，選取實體。  
  
2.  在功能表列上，選擇 \[**檢視**\]，\[**其他視窗**\]， \[**BDC 方法詳細資料**\]。  
  
     \[**BDC 方法詳細資料**\] 視窗隨即開啟。  如需這個視窗的詳細資訊，請參閱 [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)。  
  
3.  在 \[**加入方法**\] 清單中，選取 \[**建立建立者方法**\]。  
  
     Visual Studio 會將下列項目加入至模型，這些項目會顯示在 \[**BDC 方法詳細資料**\] 視窗中。  
  
    -   名為 **Create** 的方法。  
  
    -   此方法的輸入參數。  
  
    -   方法的傳回參數。  
  
    -   此參數的型別描述元。  
  
    -   此方法的方法執行個體。  
  
     如需詳細資訊，請參閱[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
4.  在 \[**方案總管**\] 中，開啟針對實體所產生的服務程式碼檔案之捷徑功能表，然後選擇 \[**檢視程式碼**\]。  
  
     實體服務程式碼檔案會在程式碼編輯器中開啟。  如需實體服務程式碼檔案的詳細資訊，請參閱[建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
5.  在可將資料加入至資料來源的建立者方法中加入程式碼。  下列範例會將一位連絡人加入至 SQL Server 的 AdventureWorks 範例資料庫。  
  
    > [!NOTE]  
    >  將 `ServerName` 欄位的值替換成您的伺服器名稱。  
  
     [!code-csharp[SP_BDC#4](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#4)]
     [!code-vb[SP_BDC#4](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#4)]  
  
## 請參閱  
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [如何：加入搜尋方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何：加入特定搜尋方法](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [如何：加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)   
 [如何：加入更新者方法](../sharepoint/how-to-add-an-updater-method.md)   
 [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何：將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何：定義方法執行個體](../sharepoint/how-to-define-a-method-instance.md)  
  
  
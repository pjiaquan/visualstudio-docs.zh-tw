---
title: "如何：加入搜尋方法"
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
  - "BDC [Visual Studio 中的 SharePoint 開發], 搜尋方法"
  - "BDC [Visual Studio 中的 SharePoint 開發], 取得實體"
  - "BDC [Visual Studio 中的 SharePoint 開發], 傳回實體"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 搜尋方法"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 取得實體"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 傳回實體"
ms.assetid: 5de2cae3-d1f7-4a68-aac0-458967aca692
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# 如何：加入搜尋方法
  若要啟用商務資料連接服務，以便在 Web 組件或清單中顯示實體清單，您必須建立「*搜尋\(Finder\)*」方法。  搜尋方法是一種特殊方法，可傳回實體執行個體的集合。  如需詳細資訊，請參閱[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
### 若要建立搜尋方法  
  
1.  在 BDC 設計工具上，選取實體。  
  
     如需詳細資訊，請參閱[如何：將實體加入至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)。  
  
2.  在功能表列上，選擇 \[**檢視**\]，\[**其他視窗**\]， \[**BDC 方法詳細資料**\]。  
  
     \[**BDC 方法詳細資料**\] 視窗隨即開啟。  如需 \[**BDC 方法詳細資料**\] 視窗的詳細資訊，請參閱 [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)。  
  
3.  在 \[**加入方法**\] 清單中，選取 \[**建立搜尋方法**\]。  
  
     Visual Studio 會加入方法、傳回參數以及型別描述元。  
  
4.  將型別描述元設定為實體集合型別描述元。  如需如何建立實體集合型別描述元的詳細資訊，請參閱 [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)。  
  
    > [!NOTE]  
    >  如果您已經在實體中加入了特定搜尋方法，就不需執行此步驟。  Visual Studio 會使用您在特定搜尋方法中定義的型別描述元。  
  
5.  在 \[**方案總管**\] 中，開啟針對實體所產生的服務程式碼檔案之捷徑功能表，然後選擇 \[**檢視程式碼**\]。  如需服務程式碼檔案的詳細資訊，請參閱[建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
6.  將程式碼加入至搜尋方法。  這個程式碼會執行下列工作：  
  
    -   擷取資料來源中的資料。  
  
    -   將實體清單傳回至 BDC 服務。  
  
     下列範例會使用 SQL Server 之 AdventureWorks 範例資料庫中的資料，傳回 `Contact` 實體的集合。  
  
    > [!NOTE]  
    >  將 `ServerName` 欄位的值替換成您的伺服器名稱。  
  
     [!code-csharp[SP_BDC#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#2)]  
  
## 請參閱  
 [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)   
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [如何：加入特定搜尋方法](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [如何：加入建立者方法](../sharepoint/how-to-add-a-creator-method.md)   
 [如何：加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)   
 [如何：加入更新者方法](../sharepoint/how-to-add-an-updater-method.md)   
 [如何：將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何：定義方法執行個體](../sharepoint/how-to-define-a-method-instance.md)  
  
  
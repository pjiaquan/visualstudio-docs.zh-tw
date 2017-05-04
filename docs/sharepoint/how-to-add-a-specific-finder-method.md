---
title: "如何：加入特定搜尋方法 | Microsoft Docs"
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
  - "BDC [Visual Studio 中的 SharePoint 開發], 取得實體"
  - "BDC [Visual Studio 中的 SharePoint 開發], 傳回實體"
  - "BDC [Visual Studio 中的 SharePoint 開發], 特定搜尋"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 取得實體"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 傳回實體"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 特定搜尋"
ms.assetid: 7bbc5986-2828-4755-96fa-9f1dc0f8dc75
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# 如何：加入特定搜尋方法
  您可以建立「*特定搜尋*」\(Specific Finder\) 方法，傳回單一實體執行個體。  當使用者在商務資料 Web 組件或外部清單中選取實體時，商務資料連接 \(BDC\) 服務就會執行特定搜尋方法。  如需詳細資訊，請參閱[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
### 若要建立特定搜尋方法  
  
1.  在 BDC 設計工具上，選取實體。  
  
     如需如何將實體加入至 Visual Studio \[BDC 設計工具\] 的詳細資訊，請參閱 [如何：將實體加入至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)。  
  
2.  在功能表列上，選擇 \[**檢視**\]，\[**其他視窗**\]， \[**BDC 方法詳細資料**\]。  
  
     \[**BDC 方法詳細資料**\] 視窗隨即開啟。  如需這個視窗的詳細資訊，請參閱 [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)。  
  
3.  在 \[**加入方法**\] 清單中，選取 \[**建立特定搜尋方法**\]。  
  
     Visual Studio 會將下列項目加入至模型。  這些項目會顯示在 \[**BDC 方法詳細資料**\] 視窗中。  
  
    -   方法。  
  
    -   此方法的輸入參數。  
  
    -   方法的傳回參數。  
  
    -   各個參數的型別描述元。  
  
    -   此方法的方法執行個體。  
  
     如需詳細資訊，請參閱[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
4.  開啟 Visual Studio 的 \[**屬性視窗**\]。  
  
5.  將傳回參數的型別描述元設定為實體型別描述元。  如需如何建立實體型別描述元的詳細資訊，請參閱 [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)。  
  
    > [!NOTE]  
    >  如果您已經在實體中加入了搜尋方法，就不需執行此步驟。  Visual Studio 會使用您在搜尋方法中定義的型別描述元。  
  
    > [!NOTE]  
    >  如果實體型別的識別碼欄位代表資料庫資料表中某個自動產生的欄位，請將識別碼欄位的 \[**唯讀**\] 屬性設定為 \[**True**\]。  
  
6.  在 \[**方法詳細資料**\] 視窗中，選取方法的方法執行個體。  
  
7.  在 \[**屬性視窗**\] 中，將 \[**傳回參數名稱**\] 屬性設為方法之傳回參數的名稱。  如需方法執行個體的屬性的詳細資訊，請參閱 [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282)。  
  
8.  在 \[**方案總管**\] 中，開啟針對實體所產生的服務程式碼檔案之捷徑功能表，然後選擇 \[**檢視程式碼**\]。  
  
     實體服務程式碼檔案會在程式碼編輯器中開啟。  如需實體服務程式碼檔案的詳細資訊，請參閱[建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
9. 將程式碼加入至特定搜尋方法。  這個程式碼會執行下列工作：  
  
    -   從資料來源擷取記錄。  
  
    -   將實體傳回至 BDC 服務。  
  
     下列範例會從 SQL Server 的 AdventureWorks 範例資料庫傳回連絡人。  
  
    > [!NOTE]  
    >  將 `ServerName` 欄位的值替換成您的伺服器名稱。  
  
     [!code-csharp[SP_BDC#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#3)]  
  
## 請參閱  
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [如何：加入搜尋方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何：加入建立者方法](../sharepoint/how-to-add-a-creator-method.md)   
 [如何：加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)   
 [如何：加入更新者方法](../sharepoint/how-to-add-an-updater-method.md)   
 [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何：將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何：定義方法執行個體](../sharepoint/how-to-define-a-method-instance.md)  
  
  
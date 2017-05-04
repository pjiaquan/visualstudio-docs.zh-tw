---
title: "如何：將篩選描述元加入至搜尋方法 | Microsoft Docs"
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
  - "BDC [Visual Studio 中的 SharePoint 開發], 加入篩選條件"
  - "BDC [Visual Studio 中的 SharePoint 開發], 篩選描述元"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 加入篩選條件"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 篩選描述元"
ms.assetid: 228a6190-8cb8-4182-b6d9-d4c656f4a164
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：將篩選描述元加入至搜尋方法
  篩選描述元可讓模型的消費者在方法執行前將值傳入方法。  如需詳細資訊，請參閱[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
 一種常見的情節就是 SharePoint 中的使用者想要擷取符合某些準則之外部內容類型的執行個體。  您可以將篩選描述元加入至搜尋工具方法，以便支援此情節。  
  
### 若要將篩選描述元加入至搜尋工具方法  
  
1.  在 \[**BDC 方法詳細資料**\] 視窗中，依次展開搜尋工具方法的節點和 \[**參數**\] 節點，然後加入輸入參數。  如需詳細資訊，請參閱[如何：將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)。  
  
2.  在 \[**方法詳細資料**\] 視窗中，選取參數的型別描述元。  
  
3.  在功能表上選擇 \[**檢視**\]、\[**屬性視窗**\]。  
  
4.  在 \[**屬性**\] 視窗中，將 \[**型別名稱**\] 屬性設定為適用於該篩選的資料型別。  
  
     例如，篩選條件可能會使用訂單日期來限制方法所傳回的銷售訂單數目。  若要支援該篩選，必須將型別描述元的 \[**型別名稱**\] 屬性設定為 **System.DateTime**。  
  
5.  在 \[**方法詳細資料**\] 視窗中，展開 \[**篩選描述元**\] 節點。  
  
6.  在 \[**新增篩選描述元**\] 清單中，選取 \[**建立篩選描述元**\]。  
  
     新的篩選描述元隨即出現在 \[**篩選描述元**\] 節點的下方。  
  
7.  在功能表上選擇 \[**檢視**\]、\[**屬性視窗**\]。  
  
8.  在 \[**屬性**\] 視窗中，選取 \[**型別**\] 屬性。  
  
9. 在位 \[**型別**\] 屬性出現的清單中，選取您想要的篩選模式。  
  
     例如，若要建立一種篩選，以使用訂單日期來限制搜尋工具方法中傳回的銷售訂單數目，請選取 \[**比較**\]。  比較篩選器確保搜尋方法只傳回符合特定條件的執行個體。  如需每個篩選模式的詳細資訊，請參閱 [BDC 支援之篩選器的型別](http://go.microsoft.com/fwlink/?LinkId=169287)。  
  
10. 在 \[**屬性**\] 視窗中，選取 \[**關聯的型別描述元**\] 屬性。  
  
11. 在為 \[**關聯的型別描述元**\] 出現的清單中，選取您之前在這個程序中所建立的型別描述元。  如此便會將篩選條件與搜尋工具方法的輸入參數相關聯。  
  
12. 將程式碼加入至傳回資料的搜尋工具方法。  您可以將輸入參數用做 SELECT 查詢中的條件。  
  
     下列範例會傳回具有指定訂單日期的銷售訂單。  
  
    > [!NOTE]  
    >  將 `ServerName` 欄位的值替換成您的伺服器名稱。  
  
     [!code-csharp[SP_BDC#11](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderservice.vb#11)]  
  
## 請參閱  
 [如何：加入搜尋方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何：加入特定搜尋方法](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [如何：將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [將商業資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  
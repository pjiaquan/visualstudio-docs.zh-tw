---
title: "建立實體之間的關聯 | Microsoft Docs"
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
  - "VS.SharePointTools.BDC.Association_Dialog"
dev_langs: 
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
ms.assetid: c908448c-13d3-4d2f-89ad-8d709b2958fb
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 建立實體之間的關聯
  您可以藉由建立關聯的方式，定義商務資料連接 \(BDC\) 模型中實體之間的關聯性。  Visual Studio 會產生方法，為模型的消費者提供各個關聯的相關資訊。  這些方法可以由 SharePoint Web 組件、清單或自訂應用程式加以使用，以便在使用者介面 \(UI\) 中顯示資料關聯性。  
  
## 建立關聯  
 在 Visual Studio \[**工具箱**\] 中選取 \[**關聯**\] 控制項，然後選擇第一個實體 \(稱為來源實體\) 和第二個實體 \(稱為目的實體\)，即可建立關聯。  您可以在 \[**關聯編輯器**\] 中定義關聯的詳細資料。  如需詳細資訊，請參閱[如何：建立實體之間的關聯](../sharepoint/how-to-create-an-association-between-entities.md)。  
  
## 關聯方法  
 應用程式 \(例如 SharePoint 商務資料 Web 組件\) 是在實體的服務類別中呼叫方法來使用關聯。  您可以在 \[**關聯編輯器**\] 中選取方法，將方法加入至實體的服務類別。  
  
 在預設情況下，\[**關聯編輯器**\] 會將「關聯巡覽」方法加入來源實體和目的實體中。  來源實體中的關聯巡覽方法可讓消費者擷取目的實體清單，  目的實體中的關聯巡覽方法則可以讓消費者擷取與目的實體相關之來源實體。  
  
 您必須將程式碼加入至各個方法中，以傳回適當的資訊。  或者，您也可以新增其他類型的方法，以支援進階案例。  如需每個方法的詳細資訊，請參閱 [支援的作業](http://go.microsoft.com/fwlink/?LinkId=169286)。  
  
## 關聯的類型  
 您可以在 BDC 設計工具中建立兩種關聯類型，分別是以外部索引鍵為基礎的關聯，以及無外部索引鍵的關聯。  
  
### 以外部索引鍵為基礎的關聯  
 您可以為來源實體中的識別項和目的實體中定義的型別描述元建立關聯，建立以外部索引鍵為基礎的關聯。  此關聯性可讓模型的消費者為他們的使用者提供增強的 UI，  比如說可讓使用者建立能夠在下拉式清單中顯示客戶之銷售訂單的 Outlook 表單，或者是 SharePoint 中可讓使用者開啟客戶設定檔頁面的銷售訂單清單。  
  
 若要建立以外部索引鍵為基礎的關聯，請為共用相同名稱和型別的識別項和型別描述元產生關聯。  比方說，您可以在 `Contact` 實體和 `SalesOrder` 實體之間建立以外部索引鍵為基礎的關聯。  `SalesOrder` 實體會傳回 `ContactID` 型別描述元，做為「搜尋」方法或「特定搜尋」方法之傳回參數的一部分。  這兩種型別描述元都會出現在 \[**關聯編輯器**\] 中。  若要在 `Contact` 實體和 `SalesOrder` 實體之間建立以外部索引鍵為基礎的關聯性，請選取各個欄位旁邊的 `ContactID` 識別項。  
  
 將程式碼加入至可傳回目的實體集合之來源實體的關聯巡覽方法。  下列範例會傳回連絡人的銷售訂單。  
  
 [!code-csharp[SP_BDC#7](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#7)]  
  
 將程式碼加入至可傳回來源實體之目的實體的關聯巡覽方法，  下列範例會傳回與銷售訂單相關的連絡人。  
  
 [!code-csharp[SP_BDC#8](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderservice.vb#8)]  
  
### 無外部索引鍵的關聯  
 在不將識別項對應至欄位型別描述元的情況下，您仍然可以建立關聯。  當來源實體與目的實體之間沒有直接關聯性時，請建立這種關聯。  例如，`SalesOrderDetail` 資料表並沒有對應到 `Contact` 資料表之主索引鍵的外部索引鍵。  
  
 如果想在與 `Contact` 相關的 `SalesOrderDetail` 資料表中顯示資訊，您可以在 `Contact` 實體和 `SalesOrderDetail` 實體之間建立無外部索引鍵的關聯。  
  
 在 `Contact` 實體的關聯巡覽方法中，利用聯結資料表或呼叫預存程序的方式傳回 `SalesOrderDetail` 實體。  
  
 下列範例會藉由聯結資料表的方式，傳回所有銷售訂單的詳細資料。  
  
 [!code-csharp[SP_BDC#9](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#9)]  
  
 在 `SalesOrderDetail` 實體的關聯巡覽方法中，傳回相關的 `Contact`。  以下範例就是示範這項作業。  
  
 [!code-csharp[SP_BDC#10](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderdetailservice.vb#10)]  
  
## 請參閱  
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [如何：建立實體之間的關聯](../sharepoint/how-to-create-an-association-between-entities.md)  
  
  
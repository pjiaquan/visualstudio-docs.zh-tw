---
title: "如何：將參數加入至方法"
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
  - "BDC [Visual Studio 中的 SharePoint 開發], 將方法加入至參數"
  - "BDC [Visual Studio 中的 SharePoint 開發], 方法參數"
  - "BDC [Visual Studio 中的 SharePoint 開發], 參數"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 將方法加入至參數"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 方法參數"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 參數"
ms.assetid: c5b6fd32-bf85-4b2a-a01e-f9199f0fb26e
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# 如何：將參數加入至方法
  您可以使用參數將資訊傳遞至方法，或從方法傳回資訊。  所有方法至少都必須有一個參數。  如需如何設計參數以支援您要建立之方法型別的詳細資訊，請參閱[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
 將參數新增至方法時，Visual Studio 會將 `<Parameter>` 項目加入至專案內模型檔案的 XML。  如需 `<Parameter>` 項目屬性的詳細資訊，請參閱 [Parameter](http://go.microsoft.com/fwlink/?LinkId=169284)。  
  
### 若要將參數加入至方法  
  
1.  將方法加入至實體。  
  
2.  在功能表列上，選擇 \[**檢視**\]，\[**其他視窗**\]， \[**BDC 方法詳細資料**\]。  
  
     \[**BDC 方法詳細資料**\] 視窗隨即開啟。  如需詳細資訊，請參閱[BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)。  
  
3.  在 \[**BDC 方法詳細資料**\] 視窗中展開方法的節點，然後展開 \[**參數**\] 節點。  
  
4.  在 \[**加入參數**\] 清單中，選取 \[**建立參數。**\]。  
  
     新的參數隨即會出現在 \[**參數**\] 節點下。  
  
5.  在功能表上選擇 \[**檢視**\]、\[**屬性視窗**\]。  
  
6.  在 \[**屬性視窗**\] 中，將 \[**名稱**\] 屬性設為任何有意義的名稱，  例如，如果該方法會傳回客戶，您就可以將方法命名為 GetCustomers。  
  
7.  在 \[**BDC 方法詳細資訊**\] 視窗中，開啟顯示的清單，以取得參數的方向，然後選擇 \[**In**\]、\[**InOut**\]、\[**Out**\] 或 \[**Return**\]。  
  
     針對您建立的型別方法，如需為該型別方法選擇之方向的詳細資訊，請參閱[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
8.  修改參數的型別描述元。  如需詳細資訊，請參閱[How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)。  
  
## 請參閱  
 [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何：將實體加入至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [如何：定義方法執行個體](../sharepoint/how-to-define-a-method-instance.md)   
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  
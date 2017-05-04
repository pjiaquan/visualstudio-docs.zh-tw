---
title: "如何：定義方法執行個體 | Microsoft Docs"
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
  - "BDC [Visual Studio 中的 SharePoint 開發], 方法"
  - "BDC [Visual Studio 中的 SharePoint 開發], 方法執行個體"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 方法"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 方法執行個體"
ms.assetid: f0c8a686-c0de-414e-8de9-f228f59d1eb3
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：定義方法執行個體
  您必須為模型中的每個方法定義至少一個方法執行個體。  
  
 請使用 \[**BDC 方法詳細資料**\] 視窗來新增方法執行個體。  新增方法執行個體時，Visual Studio 會將 `<MethodInstance>` 項目加入至專案內模型檔案的 XML。  如需 `<MethodInstance>` 項目屬性的詳細資訊，請參閱 [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282)。  
  
### 若要定義方法執行個體  
  
1.  在 \[**BDC 方法詳細資料**\] 視窗中展開方法的節點，然後展開 \[**執行個體**\] 節點。  
  
2.  在 \[**加入方法執行個體**\] 清單中，選擇 \[**建立搜尋執行個體**\]，  
  
     \[**執行個體**\] 節點下方隨即出現新的方法執行個體。  
  
3.  在功能表上選擇 \[**檢視**\]，然後選擇 \[**屬性視窗**\]。  
  
4.  在 \[**屬性視窗**\] 中設定方法執行個體的屬性。  如需個別屬性的詳細資訊，請參閱 [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282)。  
  
## 請參閱  
 [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何：將實體加入至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [如何：將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  
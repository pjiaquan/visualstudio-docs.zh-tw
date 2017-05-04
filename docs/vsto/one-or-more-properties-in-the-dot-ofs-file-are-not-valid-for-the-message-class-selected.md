---
title: ".ofs 檔案的一個或多個屬性對於所選取的訊息類別是無效的 | Microsoft Docs"
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
  - "VSTO.NewFormRegionWizard.OFSPropertyError"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: ca9e2ec1-df96-45ca-9611-cec47edfe1e4
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# .ofs 檔案的一個或多個屬性對於所選取的訊息類別是無效的
  當您匯入在 Outlook 中設計的表單區域，但表單區域上的一或多個欄位與您在 \[新增表單區域精靈\] 最後一頁選取的訊息類別不相容時，就會出現這個錯誤。  
  
 例如，您可能會在 \[新增表單區域精靈\] 的最後一頁選取 \[工作 \(IPM.Task\)\]。 如果表單區域包含 \[商務地址\] 欄位，則可能會因為此工作沒有商務地址而收到這個錯誤。 因此，\[商務地址\] 欄位與 IPM.Task 訊息類別不相容。  
  
### 更正這個錯誤  
  
-   在 \[新增表單區域精靈\] 的最後一頁，選取與表單區域上的欄位相容的訊息類別。  
  
-   在 Outlook 的表單設計工具中，移除與您規劃在 \[新增表單區域精靈\] 最後一頁選取的訊息類別不相容的欄位。  
  
## 請參閱  
 [逐步解說：匯入在 Outlook 中設計的表單區域](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  
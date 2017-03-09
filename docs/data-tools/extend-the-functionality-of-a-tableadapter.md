---
title: "如何：擴充 TableAdapter 的功能 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "資料 [Visual Studio], 擴充 TableAdapters"
  - "資料 [Visual Studio], TableAdapter"
  - "TableAdapter, 加入功能"
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：擴充 TableAdapter 的功能
您可以擴充 TableAdapter 的功能，方法是將程式碼加入 TableAdapter 的部分類別檔。  
  
 當您對 TableAdapter \(在 \[**DataSet 設計工具**\] 中\) 進行任何變更，或在執行修改 TableAdapter 設定的任何精靈時進行變更，就會重新產生定義 TableAdapter 的程式碼。  若要防止在 TableAdapter 重新產生期間刪除您的程式碼，請將程式碼加入至 TableAdapter 的部分類別檔。  
  
 \(部分類別可讓特定類別的程式碼分割為多個實體檔案。  如需詳細資訊，請參閱 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) 或 [partial \(類型\)](/dotnet/csharp/language-reference/keywords/partial-type)\)。  
  
## 找出程式碼中的 TableAdapter  
 雖然 TableAdapter 是以 \[**DataSet 設計工具**\] 所設計，但產生的 TableAdapter 類別不是 <xref:System.Data.DataSet> 的巢狀類別。  TableAdapter 會根據 TableAdapter 之關聯資料集的名稱，位於命名空間中。  例如，如果您的應用程式含有名為 `HRDataSet` 的資料集，TableAdapter 就會位於 `HRDataSetTableAdapters` 命名空間中   \(命名慣例會遵循此模式：*DatasetName* \+ `TableAdapters`\)。  
  
 下列範例是假設在專案中含有名為 `CustomersTableAdapter` 的 TableAdapter 以及 `NorthwindDataSet`。  
  
#### 若要建立 TableAdapter 的部分類別  
  
1.  選擇 \[**專案**\] 功能表中的 \[**加入類別**\]，即可在專案中加入一個新的類別。  
  
2.  將此類別命名為 `CustomersTableAdapterExtended`。  
  
3.  按一下 \[**加入**\]。  
  
4.  將程式碼取代成適用於專案的命名空間及部分類別名稱。  例如：  
  
     [!CODE [VbRaddataTableAdapters#2](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataTableAdapters#2)]  
  
## 請參閱  
 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)   
 [如何：建立 TableAdapter](../data-tools/create-and-configure-tableadapters.md)   
 [如何：建立 TableAdapter 查詢](../data-tools/how-to-create-tableadapter-queries.md)   
 [如何：擴充資料集的功能](../Topic/How%20to:%20Extend%20the%20Functionality%20of%20a%20Dataset.md)   
 [資料逐步解說](../Topic/Data%20Walkthroughs.md)   
 [將 Windows Form 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio 資料應用程式的概觀](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [儲存資料](../data-tools/saving-data.md)
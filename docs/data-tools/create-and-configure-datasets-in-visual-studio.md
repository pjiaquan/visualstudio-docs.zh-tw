---
title: "如何：建立具類型資料集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "資料集 [Visual Basic], 建立"
  - "具類型資料集, 建立"
ms.assetid: 58f33b43-24e1-43b1-b08b-b74329960bd6
caps.latest.revision: 36
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：建立具類型資料集
您可以使用 \[**資料來源組態精靈**\] 或 [建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)，建立具型別 <xref:System.Data.DataSet>。  
  
> [!NOTE]
>  如需以程式設計方式建立資料集的詳細資訊，請參閱[建立 DataSet](../Topic/Creating%20a%20DataSet.md)。  
  
## 使用資料來源組態精靈或 DataSet 設計工具建立具型別資料集  
  
#### 以資料來源組態精靈建立資料集  
  
1.  選取 \[**資料**\] 功能表上的 \[**加入新資料來源**\]，啟動 \[**資料來源組態精靈**\]。  
  
2.  請選取 \[**選擇資料來源類型**\] 頁面上的 \[**資料庫**\]。  
  
3.  完成精靈，具型別資料集隨即加入至專案。  如需詳細資訊，請參閱[資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png)。  
  
#### 以 DataSet 設計工具建立資料集  
  
1.  在 \[**專案**\] 功能表上，按一下 \[**加入新項目**\]。  
  
2.  從 \[**加入新項目**\] 對話方塊選取 \[**資料集**\]。  
  
3.  輸入資料集名稱。  
  
4.  按一下 \[**加入**\]。  
  
     資料集隨即加入至專案，並且在 \[**DataSet 設計工具**\] 中開啟。  
  
5.  從 \[**工具箱**\] 的 \[**資料集**\] 索引標籤，將項目拖曳至設計工具。  如需詳細資訊，請參閱 [如何：編輯資料集](../Topic/How%20to:%20Edit%20a%20Dataset.md)。  
  
     \-或\-  
  
     將作用中連接的項目從 \[**伺服器總管**\]\/\[**資料庫總管**\] 拖曳到 \[**DataSet 設計工具**\]。  
  
## 請參閱  
 [逐步解說：連接至資料庫中的資料 \(Windows Form\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Database%20\(Windows%20Forms\).md)   
 [建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)   
 [如何：編輯資料集](../Topic/How%20to:%20Edit%20a%20Dataset.md)   
 [TableAdapter](../Topic/TableAdapters.md)   
 [資料集中的關聯性](../data-tools/relationships-in-datasets.md)   
 [使用 Visual Studio 中的資料集](../data-tools/dataset-tools-in-visual-studio.md)   
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)
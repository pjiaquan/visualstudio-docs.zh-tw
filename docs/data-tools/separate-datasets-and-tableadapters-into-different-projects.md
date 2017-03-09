---
title: "如何：將資料集和 TableAdapters 分成不同的專案 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "N-Tier 應用程式, 區隔資料集和 TableAdapter"
  - "TableAdapter, N-Tier 應用程式"
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
caps.latest.revision: 18
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：將資料集和 TableAdapters 分成不同的專案
具型別資料集經過強化，所以 [TableAdapter](../Topic/TableAdapters.md) 和資料集類別可以產生至不同的專案中。  可以讓您迅速區隔應用程式層，並產生 N\-Tier 資料應用程式。  
  
 下列程序描述使用 [建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)將資料集程式碼產生至專案中的程序，此專案不同於內含產生的 `TableAdapter` 程式碼之專案。  
  
## 區隔資料集和 TableAdapter  
 當您區隔資料集程式碼和 `TableAdapter` 程式碼時，內含資料集程式碼的專案必須位於目前方案中。  如果這個專案不在目前的方案中，就不會列在 \[**屬性**\] 視窗中的 \[**DataSet 專案**\] 清單中。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### 若要將資料集分成不同的專案  
  
1.  開啟內含資料集的方案 \(.xsd 檔案\)。  
  
    > [!NOTE]
    >  如果方案中不含您要分隔資料集程式碼的專案，請建立一個專案或將現有專案加入至方案中。  
  
2.  在 \[**方案總管**\] 中，按兩下具型別資料集檔案 \(.xsd 檔案\)，在 \[**DataSet 設計工具**\] 中開啟資料集。  
  
3.  按一下 \[**DataSet 設計工具**\] 中空白的區域。  
  
4.  找出 \[**屬性**\] 視窗中的 \[**DataSet 專案**\] 節點。  
  
5.  在 \[**DataSet 專案**\] 清單中，按一下您要在其中產生資料集程式碼的專案名稱。  
  
     在您按一下要產生資料集程式碼的專案後，\[**DataSet 檔案**\] 屬性中就會填入預設的檔案名稱。  如果需要，您可以變更這個名稱。  此外，如果您要將資料集程式碼產生至特定目錄中，可以將 \[**Project 資料夾**\] 屬性設定為資料夾的名稱。  
  
    > [!NOTE]
    >  當您藉由設定 \[**資料集專案**\] 屬性分隔 TableAdapter 和資料集時，專案中現有的部分資料集類別不會自動移動。  您必須將現有的資料集部分類別手動移至資料集專案。  
  
6.  儲存資料集。  
  
     資料集程式碼會產生至您在 \[**DataSet 專案**\] 屬性中所選取的專案，而 **TableAdapter** 程式碼會產生至目前的專案。  
  
 根據預設，當您分隔資料集和 `TableAdapter` 程式碼時，產生的結果是每一個專案中都有一個類別檔。  原始專案都有一個名稱為 DatasetName.Designer.vb \(或 DatasetName.Designer.cs\) 的檔案，內含 `TableAdapter` 程式碼。  \[**資料集專案**\] 屬性中指定的專案有一個名稱為 DatasetName.DataSet.Designer.vb \(或 DatasetName.DataSet.Designer.cs\) 的檔案，內含資料集程式碼。  
  
> [!NOTE]
>  選取資料集或 `TableAdapter` 專案後，請按一下 \[**方案總管**\] 中的 \[**顯示所有檔案**\] 以檢視產生的類別檔。  
  
## 請參閱  
 [多層式架構資料應用程式概觀](../data-tools/n-tier-data-applications-overview.md)   
 [逐步解說：建立 N\-Tier 資料應用程式](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [階層式更新](../data-tools/hierarchical-update.md)   
 [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)   
 [ADO.NET](../Topic/ADO.NET.md)
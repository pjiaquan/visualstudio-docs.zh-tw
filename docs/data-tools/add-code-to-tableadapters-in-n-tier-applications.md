---
title: "如何：將程式碼加入 N-Tier 應用程式中的 TableAdapters | Microsoft Docs"
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
  - "N-Tier 應用程式, 擴充 TableAdapters"
  - "TableAdapter, N-Tier 應用程式"
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: 19
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：將程式碼加入 N-Tier 應用程式中的 TableAdapters
您可以建立 `TableAdapter` 的部分類別檔案並將程式碼加入其中 \(不是將程式碼加入 *DatasetName*.DataSet.Designer 檔案中\)，藉此擴充 `TableAdapter` 的功能   \(部分類別可讓特定類別的程式碼分割為多個實體檔案。  如需詳細資訊，請參閱 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) 或 [partial \(類型\)](/dotnet/csharp/language-reference/keywords/partial-type)\)。  
  
 每次對 `TableAdapter` \(在 [建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)中\) 進行變更時，就會產生定義 `TableAdapter` 的程式碼。  在執行任何會修改 `TableAdapter` 設定的精靈時，如果進行任何變更也會產生這個程式碼。  為了防止在重新產生 `TableAdapter` 的期間刪除您的程式碼，請將程式碼加入至 `TableAdapter` 的部分類別檔。  
  
 根據預設，當您分隔資料集和 `TableAdapter` 程式碼時，產生的結果是每一個專案中都有一個類別檔。  原始專案都有一個名稱為 *DatasetName*.Designer.vb \(或 *DatasetName*.Designer.cs\) 的檔案，內含 `TableAdapter` 程式碼。  \[**資料集專案**\] 屬性中指定的專案有一個名稱為 *DatasetName*.DataSet.Designer.vb \(或 *DatasetName*.DataSet.Designer.cs\) 的檔案，內含資料集程式碼。  
  
> [!NOTE]
>  當您藉由設定 \[**資料集專案**\] 屬性分隔 `TableAdapter` 和資料集時，專案中現有的部分資料集類別不會自動移動。  您必須將現有的資料集部分類別手動移至資料集專案。  
  
> [!NOTE]
>  [建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md) 也提供功能，可在應加入驗證程式碼時產生 <xref:System.Data.DataTable.ColumnChanging> 和 <xref:System.Data.DataTable.RowChanging> 事件處理常式。  如需詳細資訊，請參閱 [如何：將驗證加入 N\-Tier 資料集](../data-tools/add-validation-to-an-n-tier-dataset.md)。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### 若要將使用者程式碼加入 N\-Tier 應用程式中的 TableAdapter  
  
1.  找出內含 .xsd 檔案的專案 \([建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)\)。  
  
2.  按兩下 \[**.xsd**\] 檔案開啟 [建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)。  
  
3.  以滑鼠右鍵按一下您要加入程式碼的 `TableAdapter`，然後按一下 \[**檢視程式碼**\]。  
  
     建立一個部分類別並在 \[程式碼編輯器\] 中開啟。  
  
4.  將程式碼加入部分類別宣告中。  
  
5.  下列範例顯示 `NorthwindDataSet` 中，將程式碼加入至 `CustomersTableAdapter` 的位置：  
  
    ```vb#  
    Partial Public Class CustomersTableAdapter  
        ' Add code here to add functionality   
        ' to the CustomersTableAdapter.  
    End Class  
    ```  
  
    ```c#  
    public partial class CustomersTableAdapter  
    {  
        // Add code here to add functionality  
        // to the CustomersTableAdapter.  
    }  
    ```  
  
## 請參閱  
 [多層式架構資料應用程式概觀](../data-tools/n-tier-data-applications-overview.md)   
 [如何：將程式碼加入 N\-Tier 應用程式中的資料集](../data-tools/add-code-to-datasets-in-n-tier-applications.md)   
 [TableAdapter](../Topic/TableAdapters.md)   
 [TableAdapterManager 概觀](../Topic/TableAdapterManager%20Overview.md)   
 [階層式更新概觀](../Topic/Hierarchical%20Update%20Overview.md)   
 [建立資料應用程式](../data-tools/creating-data-applications.md)
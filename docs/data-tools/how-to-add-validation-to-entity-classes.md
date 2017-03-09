---
title: "HOW TO：將驗證加入至實體類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HOW TO：將驗證加入至實體類別
「*驗證*」\(Validate\) 實體類別 \(Class\) 過程會確認資料物件中輸入的值符合物件結構描述中的條件約束，也符合為應用程式建立的規則。先驗證資料再將更新傳送至基礎資料庫是減少錯誤的良好做法。它同時也會降低應用程式與資料庫之間的可能往返次數。  
  
 [物件關聯式設計工具 \(O\/R 設計工具\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md) 提供了部分方法，這種方法可讓使用者對於插入、更新和刪除完整實體時 \(以及變更個別資料行當時和之後\) 執行的設計工具產生的程式碼，加以擴充。  
  
> [!NOTE]
>  本主題提供使用 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]將驗證加入至實體類別時的基本步驟。因為在不參考特定實體類別的情況下遵循這些泛型步驟，將是一件困難的事，所以提供了使用實際資料的逐步解說。如需使用 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]設定驗證的詳細逐步指示，請參閱[逐步解說：將驗證加入至實體類別](../Topic/Walkthrough:%20Adding%20Validation%20to%20Entity%20Classes.md)。  
  
## 加入在特定資料行中的值變更時的驗證  
 這個程序顯示如何在資料行中的值發生變更時驗證資料。因為驗證是在實際類別定義 \(而不是使用者介面\) 內執行，所以如果值無法通過驗證，就會擲回例外狀況 \(Exception\)。請在會嘗試變更資料行值的應用程式的程式碼中實作錯誤處理。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### 若要在資料行值變更期間驗證資料  
  
1.  在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中開啟或建立新的 LINQ to SQL 類別檔案 \(**.dbml** 檔案\) \(按兩下 \[**方案總管**\] 中的 **.dbml** 檔案\)。  
  
2.  在 O\/R 設計工具中，以滑鼠右鍵按一下要加入驗證的類別，然後按一下 \[**檢視程式碼**\]。  
  
     會以所選取實體類別的部分類別開啟 \[程式碼編輯器\]。  
  
3.  將游標放在部分類別中。  
  
4.  如果是 Visual Basic 專案：  
  
    1.  展開 \[**方法名稱**\] 清單。  
  
    2.  尋找要加入驗證的資料行所適用的 **On***COLUMNNAME***Changing** 方法。  
  
    3.  會將 `On`*COLUMNNAME*`Changing` 方法加入至部分類別中。  
  
    4.  加入下列程式碼以先確認已輸入值，然後確定應用程式可接受輸入的資料行值。`value` 引數包含建議值，因此請加入邏輯以確認它是有效值：  
  
        ```vb#  
        If value.HasValue Then  
            ' Add code to ensure that the value is acceptable.  
            ' If value < 1 Then  
            '    Throw New Exception("Invalid data!")  
            ' End If  
        End If  
        ```  
  
     C\# 專案：  
  
    1.  因為 C\# 專案不會自動產生事件處理常式，所以您可以使用 IntelliSense 建立在資料行變更時執行的部分方法。  
  
         輸入 `partial` 和一個空格，以存取可用部分方法的清單。針對要加入驗證的資料行按一下在資料行變更時執行的方法。下列程式碼與選取在資料行變更時執行的部分方法時所產生的程式碼類似：  
  
        ```c#  
        partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)  
            {  
               throw new System.NotImplementedException();  
            }  
  
        ```  
  
## 加入更新實體類別時執行的驗證  
 除了可以檢查變更期間的值以外，您還可以在發生整個實體類別的更新時驗證資料。更新期間執行的驗證可以應商務規則 \(Business Rule\) 的需要，比較多個資料行的值。下列程序顯示如何在發生整個實體類別的更新時進行驗證。  
  
> [!NOTE]
>  整個實體類別的更新驗證程式碼是在部分 <xref:System.Data.Linq.DataContext> 類別 \(而不是在特定實體類別的部分類別\) 中執行。  
  
#### 若要在實體類別更新期間驗證資料  
  
1.  在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中開啟或建立新的 LINQ to SQL 類別檔案 \(**.dbml** 檔案\) \(按兩下 \[**方案總管**\] 中的 **.dbml** 檔案\)。  
  
2.  以滑鼠右鍵按一下 O\/R 設計工具中的空白區域，然後按一下 \[**檢視程式碼**\]。  
  
     會以 `DataContext` 的部分類別開啟 \[程式碼編輯器\]。  
  
3.  將游標放在 `DataContext` 的部分類別中。  
  
4.  如果是 Visual Basic 專案：  
  
    1.  展開 \[**方法名稱**\] 清單。  
  
    2.  按一下 \[**更新***ENTITYCLASSNAME*\]。  
  
    3.  會將 `Update`*ENTITYCLASSNAME* 方法加入至部分類別中。  
  
    4.  使用 `instance` 引數存取個別資料行值，如下列程式碼所示：  
  
        ```vb#  
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then  
            Dim ErrorMessage As String = "Invalid data!"  
            Throw New Exception(ErrorMessage)  
        End If  
        ```  
  
     C\# 專案：  
  
    1.  因為 C\# 專案不會自動產生事件處理常式，所以您可以使用 IntelliSense 建立部分 `Update`*CLASSNAME* 方法。  
  
    2.  輸入 `partial` 和一個空格，以存取可用部分方法的清單。按一下要加入驗證的類別所適用的更新方法。下列程式碼與您選取 `Update`*CLASSNAME* 部分方法時所產生的程式碼類似：  
  
        ```c#  
        partial void UpdateCLASSNAME(CLASSNAME instance)  
        {  
            if ((instance.COLUMNNAME == x) && (instance.COLUMNNAME = y))  
            {  
                string ErrorMessage = "Invalid data!";  
                throw new System.Exception(ErrorMessage);  
            }  
        }  
        ```  
  
## 請參閱  
 [物件關聯式設計工具 \(O\/R 設計工具\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [驗證資料](../Topic/Validating%20Data.md)
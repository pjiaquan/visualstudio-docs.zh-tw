---
title: "逐步解說：設定和使用自訂規則集 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程式碼分析, 逐步解說"
  - "程式碼分析, 規則集"
ms.assetid: 7fe0a4e3-1ce0-4f38-a87a-7d81238ec7cd
caps.latest.revision: 40
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 40
---
# 逐步解說：設定和使用自訂規則集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本逐步解說會示範如何使用已設定在類別庫上使用自訂「*規則集*」\(Rule Set\) 的程式碼分析工具。  您可以選取與方案所指定之專案類型相關的規則集，也可以選取其他規則集來滿足特定需求，例如掃描舊版程式碼來找出可利用非中斷方式解決的問題。  在任一種情況下，您都可以自訂規則集，微調它們來配合專案需求。  
  
 在這個逐步解說中，您將逐步完成下列程序：  
  
-   建立類別庫。  
  
-   選取 \[**Microsoft 基本設計方針規則**\] 程式碼分析規則集。  
  
-   將自己的程式碼加入至類別。  
  
-   執行程式碼分析。  
  
-   自訂規則集。  
  
-   執行程式碼分析並查看規則集自訂的效果。  
  
## 必要條件  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]、[!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] 或 [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
## 使用規則集搭配程式碼分析  
 首先，建立簡單的類別庫。  
  
#### 建立類別庫  
  
1.  按一下 \[**檔案**\] 功能表上的 \[**新增**\]，然後按一下 \[**專案**\]。  
  
2.  在 \[新增專案\] 對話方塊的 \[專案類型\] 下，按一下 \[Visual C\#\]。  
  
3.  在 \[**Visual C\#**\] 底下，選取 \[**類別庫**\]。  
  
4.  在 \[**名稱**\] 文字方塊中輸入 RuleSetSample，然後按一下 \[**確定**\]。  
  
 接下來將選取 \[**Microsoft 基本設計方針規則**\] 規則集並與專案一起儲存。  
  
#### 選取程式碼分析規則集  
  
1.  在 \[**分析**\] 功能表上，按一下 \[**為 RuleSetSample 設定程式碼分析**\]。  
  
     程式碼分析的組態設定隨即出現。  
  
2.  在 \[**執行此規則集**\] 下拉式清單中，選取 \[**Microsoft 所有規則**\]。  
  
     如需可用規則集的詳細資訊，請參閱[程式碼分析規則集參考](../code-quality/code-analysis-rule-set-reference.md)。  
  
     在 \[檔案\] 功能表上按一下 \[**儲存選取項目**\]，以使用您所選取的規則集及其設定的相關資訊更新專案檔。  
  
    > [!TIP]
    >  在實際狀況中，要使用程式碼分析來設定解決問題的優先權，最好先從 \[**最小建議規則**\] 規則集開始，更正了所要解決的問題後，再逐步加入更多規則或規則集來找出並更正其他問題。  
  
 接下來將加入一些程式碼到類別庫，這將用來示範 CA1704「識別項應該使用正確的拼字」程式碼分析規則的違規情形。  如需詳細資訊，請參閱[CA1704：識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。  
  
#### 加入自己的程式碼  
  
-   在 \[方案總管\] 中，開啟 Class1.cs 檔並以下列程式碼取代現有的程式碼：  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
  
    namespace RuleSetSample  
    {  
        public class Class1  
        {  
            //The variable parameter names "a" and "b" will cause  
            //the warning CA 1704 Microsoft.Naming "Consider   
            //providing a more meaningful name" to fire  
            public int AddIntegers(int a, int b)  
            {  
  
                int sum = a + b;  
  
                return (sum);  
            }  
        }  
    }  
  
    ```  
  
 現在您可以對 RuleSetSample 專案執行程式碼分析，並在 \[錯誤清單\] 視窗中查看任何產生的錯誤和警告。  
  
#### 對 RuleSetSample 專案執行程式碼分析  
  
1.  在 \[**分析**\] 功能表上，按一下 \[**針對 RuleSetSample 執行程式碼分析**\]。  
  
2.  在 \[錯誤清單\] 視窗中，按一下 \[**警告**\]，然後按一下 \[**描述**\] 資料行標題，按英數字元順序排序警告。  
  
     在實際應用中，這時可以解決任何值得解決的違規情形，若認為不值得解決，則可以選擇關閉或隱藏規則。  如需詳細資訊，請參閱[使用 SuppressMessage 屬性隱藏警告](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)。  
  
3.  請注意 CA1704 警告。  此規則的這些違規情形表示您應該「為參數提供更具有意義的名稱」。您可以在程式碼中更正此問題，或可以依下面程序所述停用規則。  
  
 接下來將自訂規則集來排除 CA1704 警告「識別項應該使用正確的拼字」。  
  
#### 自訂專案的規則集來停用特定規則  
  
1.  在 \[**分析**\] 功能表上，按一下 \[**為 RuleSetSample 設定程式碼分析**\]。  
  
2.  在 \[**執行此規則集**\] 下拉式清單中，確認仍反白顯示 \[**Microsoft 所有規則**\] 規則集，然後按一下 \[**開啟**\]。  規則集頁面隨即顯示。  
  
3.  展開 \[Microsoft.Naming\] 分類節點，然後選取 CA1704 警告。  
  
4.  在 \[**動作**\] 欄底下，選取 \[**無**\]。如此一來，CA1704 就不會顯示為 \[錯誤清單\] 視窗中的警告或錯誤。  
  
     您現在可以試試各個工具列按鈕和篩選選項來熟悉它們。  例如，您可以使用 \[**群組依據**\] 下拉式清單，協助找出特定規則或規則類別。  另外一個例子是可以使用規則集頁面工具列中的 \[**隱藏停用的規則**\] 按鈕，隱藏或顯示 \[**動作**\] 欄設為 \[**無**\] 的所有規則。  如果您想掃描已關閉的任何規則，以確認是否仍想停用它們，這會非常有用。  
  
5.  在 \[檢視\] 功能表中，按一下 \[屬性視窗\]。  在 \[屬性\] 工具視窗的 \[名稱\] 方塊中，輸入 **My Custom Rule Set**。  這會變更新規則集在 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] IDE 中的顯示名稱。  
  
6.  在 \[**檔案**\] 功能表上，按一下 \[**儲存 Microsoft 所有規則.ruleset**\] 儲存您的自訂規則集。  巡覽至專案的根資料夾。  在 \[**檔名**\] 文字方塊中，輸入 MyCustomRuleSet。  您現在就可以選取自訂規則集來搭配專案使用。  
  
 建立新規則集之後，現在必須設定專案設定，以指定想要搭配它使用新的規則集。  
  
#### 指定新規則集來搭配專案使用  
  
1.  在 \[方案總管\] 中，以滑鼠右鍵按一下專案，然後選取 \[**屬性**\]。  
  
2.  在 \[**屬性**\] 索引標籤中，按一下 \[**程式碼分析**\]。  
  
     在 \[**執行此規則集**\] 下拉式清單中，按一下 \[**\<瀏覽\>**\]。  巡覽至程式碼專案的根資料夾，然後選取 MyCustomRuleSet.ruleset。  這是您在前面程序中建立的新規則集。  
  
3.  在 \[**檔案**\] 功能表上，按一下 \[**儲存**\] 儲存您的專案組態。  您現在就可以使用自訂規則集來搭配專案。  
  
 最後將使用 MyCustomRuleSet 規則集再次執行程式碼分析。  請注意，\[錯誤清單\] 視窗不會顯示 CA1704 效能規則違規情形。  
  
#### 第二次對 RuleSetSample 專案執行程式碼分析  
  
1.  在 \[**分析**\] 功能表上，按一下 \[**針對 RuleSetSample 執行程式碼分析**\]。  
  
2.  請注意，當您在 \[錯誤清單\] 視窗中按一下 \[**警告**\] 時，就不會再看到「識別項應該使用正確的拼字」規則的 CA1704 警告違規。  
  
## 請參閱  
 [如何：設定 Managed 程式碼專案的程式碼分析](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [程式碼分析規則集參考](../code-quality/code-analysis-rule-set-reference.md)
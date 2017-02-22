---
title: "全文檢索搜尋提示 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "hv_search"
helpviewer_keywords: 
  - "說明檢視器 2.0，全文檢索搜尋提示"
  - "全文檢索搜尋提示 [說明檢視器 2.0]"
ms.assetid: bcaad23d-2ca7-4bec-8b54-b884bc34e70b
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 全文檢索搜尋提示
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

其中一個在說明中偵測資訊更有用的方式是執行全文檢索搜尋。  若要精簡和自訂您的結果，您必須了解語法如何影響您的查詢。  本主題提供提示、程序和詳細語法資訊，可幫助您設計更好的查詢。  
  
## 全文檢索搜尋秘訣  
 您可以建立僅傳回您感興趣的這些主題的目標搜尋，如果您知道說明如何解譯在查詢中使用的格式。  這些格式包含特殊字元、保留字和篩選條件。  
  
### 一般方針  
 下表說明包含一些基本規則和方針來開發在說明中的搜尋查詢。  
  
|語法|描述|  
|--------|--------|  
|區分大小寫|搜尋不會區分大小寫。  使用大寫或小寫字母，開發您自己的搜尋準則。  例如， 「OLE」和「OLE」傳回相同的結果。|  
|字元組合|您不能只搜尋個別的字母 \(a–z\) 或數字 \(0\-9\)。  如果您嘗試搜尋特定保留字，例如「and」， 「From」和「with」，則會被忽略。  如需詳細資訊，請稍候參閱本主題的 \[搜尋中忽略的字 \(停止字\)\]一節。|  
|評估順序|搜尋查詢是從左到右評估。|  
  
### 查詢語法  
 如果您指定包含多個單字的搜尋字串，例如「word1 word2」，該字串就等於輸入的「word1 AND word2」，它只傳回包含搜尋字串中所有個別單字的主題。  
  
> [!IMPORTANT]
>  1.  不支援片語搜尋。  如果您在搜尋字串中指定一個以上的單字，則傳回的主題會包含所指定的所有單字，但不一定是完全符合您指定的片語。  
> 2.  使用邏輯運算子在您的搜尋字詞，指定項目之間的關聯性。  您可以加入邏輯運算子，例如 AND、OR、NOT 和 NEAR 進一步修改您的搜尋。  例如，如果您搜尋 "declaring NEAR union"，搜尋結果會包含文字 "declaring" 與 "union" 的主題，而不會比個別文字分開搜尋的結果多。  如需詳細資訊，請參閱 [搜尋運算式中的邏輯運算子](../ide/logical-operators-in-search-expressions.md)。  
  
### 篩選條件  
 您可以使用進階的搜尋運算子，可以進一步限制搜尋結果。  說明包含您可以用來篩選全文檢索搜尋的結果的三個分類: 標題、程式碼和關鍵字。  如需詳細資訊，請參閱 [搜尋運算式中的進階搜尋運算子](../ide/advanced-search-operators-in-search-expressions.md)。  
  
### 搜尋結果順位  
 搜尋演算法套用某些準則可以協助搜尋結果在結果清單中排列較高或較低的順位。  一般來說：  
  
1.  內含標題的搜尋文字之內容會比沒有含的內容順位高。  
  
2.  內含鄰近性高的搜尋文字之內容會比沒有含的內容順位高。  
  
3.  含高密度搜尋文字的內容等級會比於內含低密度的搜尋文字之內容順位高。  
  
### 搜尋中忽略的字 \(停止字\)  
 通常發生的文字或數字，在全文檢索搜尋期間，有時稱為停止文字，會自動加以忽略。  例如，如果您搜尋這個片語 "pass through"，搜尋結果會顯示包含這個字 "pass"，而不是包含這個字 "through" 的主題。  
  
## 請參閱  
 [尋找資訊](../ide/locate-information.md)   
 [搜尋運算式中的邏輯運算子](../ide/logical-operators-in-search-expressions.md)
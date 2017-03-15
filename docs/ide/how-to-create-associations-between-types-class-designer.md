---
title: "How to: Create Associations Between Types (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.classdesigner.associationline"
helpviewer_keywords: 
  - "types [Visual Studio], associations"
  - "association lines, defining (Class Designer)"
  - "defining association lines (Class Designer)"
  - "associations, types"
  - "association lines"
ms.assetid: adccb9c8-2f8a-4086-9fa9-f70f99fb6e00
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# How to: Create Associations Between Types (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

\[類別設計工具\] 中的關聯線會顯示圖表中類別的關聯性。  關聯線表示某類別為專案中其他類別的屬性或欄位的類型。  關聯線通常是用來說明專案中類別之間最重要的關係。  
  
 雖然您可以將所有欄位或屬性顯示為關聯，但是針對要在圖表上突顯的部分而只將重要成員顯示為關聯才更具意義 \(您可以隱藏次要成員或將其顯示為一般成員\)。  
  
> [!NOTE]
>  \[類別設計工具\] 只支援單向關聯。  
  
### 若要在類別圖中定義關聯線  
  
1.  在 \[工具箱\] 的 \[類別設計工具\] 下方選取 \[**關聯**\]。  
  
2.  在您要以關聯連結的兩個圖案之間繪製一條線。  
  
     第一個類別中就會建立新的屬性。  這個屬性會以預設名稱顯示為關聯線 \(而不是圖案區間中的屬性\)。  關聯線所指的圖案即為其類型。  
  
### 若要變更關聯名稱  
  
-   在圖表介面上按一下關聯線的標籤，然後加以編輯。  
  
 \-或\-  
  
1.  按一下其內含屬性顯示為關聯的圖案。  
  
     該圖案就會取得焦點，而且其成員會顯示於 \[類別細節\] 視窗和 \[屬性\] 視窗中。  
  
2.  在 \[類別細節\] 視窗或 \[屬性\] 視窗中編輯該屬性的 \[名稱\] 欄位，然後按 Enter 鍵。  
  
     \[**類別細節**\] 視窗、關聯線、\[屬性\] 視窗和程式碼中的名稱就會隨之變更。  
  
## 請參閱  
 [How to: Change Between Member Notation and Association Notation \(Class Designer\)](../Topic/How%20to:%20Change%20Between%20Member%20Notation%20and%20Association%20Notation%20\(Class%20Designer\).md)
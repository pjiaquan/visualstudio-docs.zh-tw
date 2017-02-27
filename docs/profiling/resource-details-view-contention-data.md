---
title: "資源詳細資料檢視 - 程式碼剖析工具：爭用資料 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.resourcedetails"
helpviewer_keywords: 
  - "資源詳細資料檢視"
ms.assetid: a4ecfe1c-abbc-4fb3-9ab2-34de50486901
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 資源詳細資料檢視 - 程式碼剖析工具：爭用資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

\[資源詳細資料\] 檢視會呈現因爭用所選取資源造成之封鎖事件的時間表圖形。  封鎖事件是在執行緒因為另一個執行緒鎖定資源存取而強制暫停執行時發生。  
  
 此檢視以水平列表示每個執行緒的執行時間表，並且在執行緒時間表上以垂直列表示每個封鎖事件。  必要時，您可以放大時間表的某個區段，以檢視個別事件。  若要檢視造成該事件之函式的執行路徑 \(呼叫堆疊\)，請按一下事件列。  函式會出現在 \[**呼叫堆疊**\] 視窗中。  當函式的原始程式碼可供使用時，您可以按一下函式名稱，在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的介面中編輯原始程式檔。  
  
## 程序  
  
#### 若要放大時間表區段  
  
-   拖曳滑鼠指標到時間表的某個區域上方。  
  
     放開滑鼠按鈕時，檢視會縮放至選取的時間區段。  您可以重複此程序進一步放大此區段。  時間捲軸上的捲動方塊表示檢視中出現的時間區段相對大小。  
  
#### 若要縮小時間表  
  
-   請執行下列其中一個步驟：  
  
    -   按一下 \[**縮小**\] 返回前一個縮放層級。  
  
    -   按一下 \[**顯示比例重設**\]，在檢視中顯示完整的時間表。  
  
#### 若要檢視事件的呼叫堆疊  
  
-   在時間表圖形中按一下事件列。  
  
#### 若要檢視或編輯呼叫堆疊中函式的原始程式碼  
  
-   在 \[**呼叫堆疊**\] 視窗中按一下函式名稱。  
  
 函式的原始程式碼必須是目前專案的一部分。  
  
#### 若要檢視資源爭用事件的呼叫樹狀圖  
  
-   在時間表圖形中按一下 \[**總計**\]。  
  
     資源的 \[爭用\] 檢視隨即出現。  如需詳細資訊，請參閱[資源爭用檢視](../profiling/resource-contentions-view-contention-data.md)。  
  
#### 若要檢視執行緒的所有爭用事件  
  
-   在時間表圖形中，按一下執行緒的名稱或識別碼。  
  
     所選取執行緒的 \[執行緒詳細資料\] 檢視隨即出現。  如需詳細資訊，請參閱[執行緒詳細資料檢視](../profiling/thread-details-view-contention-data.md)。
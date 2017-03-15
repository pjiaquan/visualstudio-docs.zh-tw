---
title: "執行緒詳細資料檢視 - 程式碼剖析工具：爭用資料 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.threaddetails"
helpviewer_keywords: 
  - "執行緒詳細資料檢視"
ms.assetid: 874c3b1c-88d8-479a-bb35-1291d9aa8e67
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 執行緒詳細資料檢視 - 程式碼剖析工具：爭用資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

\[執行緒詳細資料\] 檢視會呈現執行程式碼剖析期間選取的執行緒中，因資源爭用所造成之封鎖事件的時間表圖形。  封鎖事件是在執行緒因為另一個執行緒鎖定資源存取而強制暫停執行時發生。  
  
 此檢視以水平列表示執行緒的執行時間表，並且在執行緒的水平時間表上以垂直列表示封鎖事件。  必要時，您可以放大時間表的某個區段，以檢視個別事件。  若要檢視造成該事件之函式的執行路徑，請按一下事件列。  函式會出現在 \[呼叫堆疊\] 視窗中。  當函式的原始程式碼可供使用時，您可以按一下函式名稱，在 Visual Studio IDE 中編輯原始程式檔。  
  
## 巡覽時間表  
  
#### 若要放大時間表區段  
  
-   按一下並拖曳滑鼠指標，以選取時間表的某個區域。  
  
     放開滑鼠時，檢視會縮放至選取的時間區段。  您可以重複此程序放大更詳細的內容。  時間捲軸上的捲動方塊表示檢視中顯示的時間區段相對大小。  
  
#### 若要縮小時間表  
  
-   按一下 \[**縮小**\] 返回前一個縮放層級。  
  
-   按一下 \[**顯示比例重設**\]，在檢視中顯示完整的時間表。  
  
#### 若要檢視事件的呼叫堆疊  
  
-   在時間表圖形中，按一下代表事件的垂直列。  
  
#### 若要檢視或編輯呼叫堆疊中函式的原始程式碼  
  
-   在 \[呼叫堆疊\] 視窗中按一下函式名稱。  
  
 函式的原始程式碼必須是目前專案的一部分。  
  
#### 若要檢視執行程式碼期間所有執行緒中資源的爭用事件  
  
-   在時間表圖形中，按一下資源的名稱或識別碼。  
  
     所選取資源的[資源詳細資料檢視](../profiling/resource-details-view-contention-data.md)隨即出現。  
  
#### 若要在處理序視窗中檢視執行緒爭用資料  
  
-   在時間表圖形中按一下 \[**總計**\]。  
  
     [處理序檢視](../profiling/process-view-contention-data.md)隨即出現，其中執行緒為已選取狀態。